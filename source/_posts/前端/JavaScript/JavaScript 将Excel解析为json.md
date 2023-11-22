---

title: JavaScript 将Excel解析为json
date: 2021-12-08 16:45
tags: [JavaScript]

---
## 一、引言

目标：将读取Excel中的内容，并将其转换为json。

## 二、解决

使用[SheetJS](https://sheetjs.com/)的[js-xlsx](https://link.segmentfault.com/?enc=1a57k8X1i2xRFb3l%2BHnbYA%3D%3D.zBpCUA3%2BhcN82vaR8hfV%2BPtRCKgfKfVOuPvTZC3UJwosbwkJbKtbBtMJ%2BHfMhDZf)库。

### 2.1 引入

import xlsx from "./xlsx.core.min.js";

![](https://cdn.nlark.com/yuque/0/2021/png/1318699/1638952794437-d2fb06de-95c1-49bb-9aeb-85b2303b9789.png)

### 2.2 读取并解析网络资源

```js
const readExcel = () => {
      console.error("readExcel");
      console.log(xlsx);
      let url = "http://***/receipts.xls";
      let xhr = new XMLHttpRequest();
      xhr.open("get", url, true);
      xhr.responseType = "arraybuffer";
      xhr.onload = (e) => {
        if (xhr.status == 200) {
          let data = new Uint8Array(xhr.response);
          let workbook = xlsx.read(data, { type: "array" });
          console.log(workbook);
          console.table(workbook.Sheets);
          console.table(workbook.WBProps);
          let json = xlsx.utils.sheet_to_json(workbook.Sheets.sheet1);
          console.table(json);
        }
      };
      xhr.send();
    };
```

## ![](https://cdn.nlark.com/yuque/0/2021/png/1318699/1638952934137-fdc60823-2aec-4003-88af-421b0498fba8.png)

`Sheets`中存的是工作簿中的sheet名。![](https://cdn.nlark.com/yuque/0/2021/png/1318699/1638953009134-4f46bbe3-aadc-4d64-beb4-707bd2eeab01.png)

`Workbook`是保存的各个sheet中的内容。![](https://cdn.nlark.com/yuque/0/2021/png/1318699/1638953049191-bc4e9226-b225-4708-9ab4-ce5fed4c14ba.png)

  

## 参考
1.  [在 Node.js 中利用 js-xlsx 处理 Excel 文件 - SegmentFault 思否](https://segmentfault.com/a/1190000004395728)
2.  [GitHub - SheetJS/sheetjs: SheetJS Community Edition -- Spreadsheet Data Toolkit](https://github.com/sheetjs/sheetjs)
3.  [SheetJS - Home](https://sheetjs.com/)