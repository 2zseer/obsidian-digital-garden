---
{"dg-publish":true,"created":"2022-12-20T16:19:52+09:00","updated":"2022-12-26T22:02:04+09:00","permalink":"/4_IT/청킹노트/Vue/","dgPassFrontmatter":true,"noteIcon":""}
---

필터 사용시


methods 아래 filters 추가 a : filter 형식으로 감싼다.
자주 틀리는 오타
- v-onclick이 아니라 v-on:click이 맞다.

option은 v-for, :selected

1.
```javascript
$(function () {
... 생략
```
로 포함되는 js 를  임포트 하면 생기는 문제인 것 같다.
위에 부분은 없애던지 vue 부분에 
```javascript
window.onload = function () {  
    var app = new Vue({
    ... 생략
```
를 추가하면 해결되는 문제로 보인다.

2.
중괄호로 감싸진 구문은 랜더링이 되던데 api 호출이 안되서 확인 해본 결과 괄호 처리가 제대로 되지 않아서 생긴 케이스

3.
v-for와  v-if가 같이 있을 경우 v-for가 우선 순위를 가진다. 