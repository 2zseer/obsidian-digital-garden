---
{"dg-publish":true,"created":"2022-12-20T16:29:19+09:00","updated":"2022-12-20T16:29:19+09:00","permalink":"/4_IT/청킹노트/dialog 사용/","dgPassFrontmatter":true,"noteIcon":""}
---


```HTML
<dialog id="dialog">  
    <form method="dialog">  
        <a v-on:click="close()"><span>닫기</span></a>  
    </form>  
</dialog>
```

```javascript
dialog.showModal(); // 호출
dialog.close(); // 닫기
```