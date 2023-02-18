---
{"date created":"수요일, 12월 21일 2022, 10:02:28 오후","date modified":"수요일, 1월 4일 2023, 8:18:55 오전","dg-publish":true,"permalink":"/4_IT/코드 스니펫/onMessage/","dgPassFrontmatter":true,"noteIcon":""}
---

```javascript
window.opener.postMessage({  
    data: {
	    text: text,  
	    value: value
	}
}, '*');

onMessage: function(e) {
	if (e.data.hasOwnProperty('data')) {  
	    e.data.forEach(function (value) {  
	        console.log('<tr><td><span>' + value.text + '</span></td></tr>');  
	    })
    }
}
```