---


title: VBA 将当前单元格所在行复制插入至某行
date: 2021-08-12 23:59:39
tags: [VBA,Excel]
type:

---


## 一、引言

现有如下工作记录表，每天都需频繁“新增问题”、“跟踪问题”；频繁复制、粘贴、插入日期等操作，现
通过vba简化记录流程。
![](https://gitee.com/qiebzps/pic/raw/master/img/20210812235905.png#alt=)

## 二、代码

```vba
Sub Click_ADD()
    Rows(2).Select
    Selection.Copy
    Rows(3).Insert
    ActiveSheet.Range("B3") = Format(Now, "yyyy-mm-dd hh:MM:ss")
End Sub

Sub Click_Track()
    Dim selectRow As String
    Dim ran As String
    
    Rows(ActiveCell.Row).Select

    selectRow = ActiveCell.Row + 1
    ran = "G" & selectRow
    Selection.Copy
    Rows(3).Insert
    ActiveSheet.Range("B3").Select
    ActiveSheet.Range("B3") = Format(Now, "yyyy-mm-dd hh:MM:ss")
    ActiveSheet.Range("G3") = ActiveSheet.Range(ran) + 1
End Sub
```


## 参考

1. [如何：使用 Excel 中的 Visual Basic 过程选择单元格或区域。 - Office | Microsoft Docs](https://docs.microsoft.com/zh-cn/previous-versions/office/troubleshoot/office-developer/select-cells-rangs-with-visual-basic#how-to-select-a-cell-on-the-active-worksheet)
