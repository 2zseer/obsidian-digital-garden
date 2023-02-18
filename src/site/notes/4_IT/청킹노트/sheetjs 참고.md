---
{"banner":"","banner_icon":null,"dg-publish":true,"created":"2022-12-20T16:20:37+09:00","updated":"2022-12-26T22:02:23+09:00","permalink":"/4_IT/청킹노트/sheetjs 참고/","dgPassFrontmatter":true,"noteIcon":""}
---



다운로드시
```javascript
var wb = XLSX.utils.book_new();  
var ws = XLSX.utils.aoa_to_sheet(data);  
wb.SheetNames.push("sheet 1");  
wb.Sheets["sheet 1"] = ws;  
var wbout = XLSX.write(wb, {bookType: 'xlsx', type: 'binary'});  
saveAs(new Blob([s2ab(wbout)], {type: "application/octet-stream"}), document.getElementById('startDate').value + '~' + document.getElementById('endDate').value  + 'fileName.xlsx');
```

업로드시
```javascript
function excelExport(event){  
    var input = event.target;  
    var reader = new FileReader();  
    reader.onload = function(){  
        var fileData = reader.result;  
        var wb = XLSX.read(fileData, {type : 'binary'});  
        wb.SheetNames.forEach(function(sheetName){  
            var rowObj =XLSX.utils.sheet_to_json(wb.Sheets[sheetName]);
        })
    };
}
```
