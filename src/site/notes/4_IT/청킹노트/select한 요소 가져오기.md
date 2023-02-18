---
{"dg-publish":true,"date created":"목요일, 10월 27일 2022, 11:07:34 오전","date modified":"화요일, 12월 20일 2022, 4:20:24 오후","created":"2022-12-27T22:55:51+09:00","updated":"2022-12-27T22:55:51+09:00","permalink":"/4_IT/청킹노트/select한 요소 가져오기/","dgPassFrontmatter":true,"noteIcon":""}
---

``` javascript
var s = document.getElementById("id");  
var value = s.options[s.selectedIndex].value; // 값
var text = s.options[s.selectedIndex].text; // 텍스트
```


