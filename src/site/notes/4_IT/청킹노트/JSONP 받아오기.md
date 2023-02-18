---
{"tags":[["JSONP"]],"dg-publish":true,"created":"2022-12-27T22:59:40+09:00","updated":"2022-12-27T22:59:40+09:00","date created":"2023-01-03T22:06:22+09:00","date updated":"2023-01-03T22:06:22+09:00","permalink":"/4_IT/청킹노트/JSONP 받아오기/","dgPassFrontmatter":true,"noteIcon":""}
---

입사 후 첫 업무로 타 회사의 API 연동 업무를 받았었는데, DTO로는 받지를 못해 구글링해본 결과 JSONP라는 구조라는 것을 알게 되었다.

규격서 받은 것에는 JSON으로 내려준다고 되어 있었는데.. 이래서 연동규격서를 제대로 쓰는게 중요하구나 느꼈다.

처음 방식으로 먼저 구현을 했었고 두번째는 JQuery로 사용하기가 아쉬워 restTemplate를 통해 구현을 하였다. 

문자열로 받아서 단순하게 변경을 하는거긴한데.. 사실 필요해서 오시는 분이 안 계셨으면 싶은 마음이다. ㅠ


```Javascript
$.ajax({  
    type: 'GET',  
    url: 'https://api.url.com/API/method?parameter1=' + parameter1 + '&parameter2=parameter2&parameter3=parameter3',  
    dataType: 'jsonp',  
    contentType: 'application/javascript; charset=UTF-8',  
    jsonpCallback: 'callback'  
}).done(function (res) {  
    console.log(res);  
    if (res.RESULTCD === '401') {  
        alert('검색이 실패하였습니다.');  
        return;  
    }    
    USERUSE1 = res.USERUSE1.replace(/\([^)]+\)/g, "");
    ... 중략
```

```JAVA
@SneakyThrows  
public Dto method(String parameter1) {  
    Dto result = new Dto();  
    String url = UriComponentsBuilder.fromUriString(url)  
            .queryParam("parameter1", parameter1)  
            .queryParam("parameter2", parameter2)  
            .queryParam("parameter3", parameter3)
            .build()
            .toUriString();  
    ResponseEntity<String> exchange = restTemplate.exchange(url, HttpMethod.GET, new HttpEntity<>(null), String.class);  
  
    String arr = exchange.getBody();  
    arr = arr.replaceAll("callback\\(\\{", "\\{");  
    arr = arr.replaceAll("\\}\\)", "\\}");  
  
    Map<String, Object> jsonMap  = objectMapper.readValue(arr, new TypeReference<Map<String, Object>>() { });    
    result.setParameter1(String.valueOf(jsonMap.get("Parameter1")));  
    result.setParameter2(Long.valueOf((String) jsonMap.get("Parameter2")));  
    result.setParameter3(Integer.valueOf((String) jsonMap.get("Parameter2")));  
	...
    return result;  
}
```

