---


title: Excel VBA 多选下拉多项选择
date: 2021-05-26 01:28:09
tags: [Excel,VBA,效率]
type:

---


## 一、引言

最近有大量Excel，其中某一栏位所填内容仅为固定的几项，但可能有多项。
正瞌睡来了个枕头，在秋叶Excel公众号中发现满足需求的Excel操作。

## 二、解决方案

```vb
Private Sub ListBox1_Change()
    
    '当列表框内容有变化时，遍历列表框选项，将处于勾选状态的选项储存于content_seleted
    content_seleted = ""
    For i = 0 To ListBox1.ListCount - 1
        If ListBox1.Selected(i) = True Then
            content_seleted = content_seleted & "," & ListBox1.List(i)
        End If
    Next
    
    '更新单元格内容
    ActiveCell = Mid(content_seleted, 2)
End Sub

'选中单元格变动时触发
Private Sub Worksheet_SelectionChange(ByVal Target As Range)

On Error Resume Next

'当前data表中对应列不为空，且当前单元格在第二行以后
If Sheets("data").Cells(2, Target.Column) <> "" And Target.Row > 1 Then
     '设置listbox中的内容
    c = Target.Column'获取对应列的地址
    a = Mid(Sheets("data").Cells(2, c).Address, 2, 1)'获取对应列的下标
    ListBox1.ListFillRange = "data!" & a & "2:" & a & Sheets("data").Cells(1, c).End(xlDown).Row
    
    '设置多选框的位置、宽、高数据后，显示列表框
    With ListBox1
        '列表框中内容的行数
        n = .ListCount
        '单元格所对应的行
        r = Target.Row
        '单元格所对应的列
        c = Target.Column + 1
        'Top设置为所在单元格的底部
        .Top = Cells(r, c).Top + Cells(r, c).Height
        'Left设置为选中单元格+1的左侧
        .Left = Cells(r, c).Left
        .Width = Target.Width
        .Height = Cells(r, c).Height * n
        .Visible = True
		'使其可以通过点击多选
		.MultiSelect = fmMultiSelectMulti
    End With
    
    
    '定义字典，将当前单元格以","拆分为数组，并储存在字典d中
    Set d = CreateObject("scripting.dictionary")
    Arr = Split(Target.Value, ",")
    For i = 0 To UBound(Arr)
        d(Arr(i)) = ""
    Next
    
    '便利列表框选型，用字典d进行匹配，d中有选项i时，选项i的状态为勾选，否则去勾选
    For i = 0 To ListBox1.ListCount - 1
        If d.exists(ListBox1.List(i)) Then
            ListBox1.Selected(i) = True
        Else
            ListBox1.Selected(i) = False
        End If
    Next
    
Else
    '不显示列表框
    ListBox1.Visible = False
End If

End Sub
```


## 参考

1. [比下拉列表强10倍！它才是Excel中数据录入的No.1](https://mp.weixin.qq.com/s/facjJ_PvsjJry6GP96sz3w)
2. [Access (ListBox.ListCount) | Microsoft Docs](https://docs.microsoft.com/zh-cn/office/vba/api/access.listbox.listcount)
3. [Worksheet.SelectionChange 事件 (Excel) | Microsoft Docs](https://docs.microsoft.com/zh-cn/office/vba/api/excel.worksheet.selectionchange)
4. [MultiSelect、Selected 属性示例 | Microsoft Docs](https://docs.microsoft.com/zh-cn/office/vba/language/reference/user-interface-help/multiselect-selected-properties-example)
