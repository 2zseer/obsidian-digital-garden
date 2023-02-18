---
{"date created":"목요일, 7월 7일 2022, 8:14:40 오후","date modified":"금요일, 7월 8일 2022, 8:15:19 오전","dg-publish":true,"permalink":"/4_IT/코드 스니펫/jsonString to DTO/","dgPassFrontmatter":true,"noteIcon":""}
---


## ObjectMapper
---
javascript
```Javascript
let item = {};  
item.id = parseInt(id);  
item.name = name;  
item.enabled = enabled;  
item = JSON.stringify(item);  
jsnString.push(JSON.parse(item));

var data = new FormData();  
data.append("menuId", menuId);  
data.append("jsnString", JSON.stringify(jsnString));

$.ajax({  
    type: 'PUT',  
    url: '/test/api/',  
    data: data,  
    processData: false,  
    contentType: false,  
    cache: false  
})
```


jsonString 으로 List형 DTO 변환하기
```Java
@PatchMapping(value = "/test1")
public ResponseEntity<Object> modAuditCategory(@Valid Dto req, HttpServletRequest request) throws JsonProcessingException {  
    ObjectMapper objectMapper = new ObjectMapper();  
    if (req.getJsnString() != null) {  
        List<Dto> list = objectMapper.readValue(req.getJsnString(), new TypeReference<List<Dto>>() {});
		for (int i = 0; i < list.size(); i++) {  
		    list.get(i).setMenuId(req.getMenuId());  
		    service.modUser(list.get(i), request);  
		}  
    }    
    return ResponseEntity.noContent().build();  
}
```
