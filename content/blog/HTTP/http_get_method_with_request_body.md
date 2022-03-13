---
title: 'HTTP GET Method에 Body를 붙여 보낼 수 있다'
date: 2022-03-11 12:21:13
category: 'HTTP'
draft: false
---

### 일반적으로는

> HTTP GET Method를 사용할 때는  
Path Parameter나 Query Parameter 방식으로 데이터를 전송한다.

### 그런데
  
> GET Method에 ```Body``` 를 붙여서 보낼 수도 있다.

~~GET 방식에는 Message Body가 없다고도 읽었는데~~  
오늘 일하다가 GET Body에 Json 넣어서 통신했다. 🙄

Body를 붙여 보내면 Spring GetMapping에서도 RequestBody로 받아진다. 
찾아보니 이런 경우는 엘라스틱서치 등에서 사용하는 볼 수 있다고도 한다.  

### 된다.

>그런데 ```그렇게 쓰는 것에 대한 판단```을 어떻게 해야할까?

가장 괜찮은 관점에서 정리된것 같은 문서를 첨부한다.
https://brunch.co.kr/@kd4/158

_간단히 요약하면_
1. 2014년 이후 나온 RFC스펙(RFC 7230-7237) 을 근거로 하여 무리가 없어보인다.
2. 하지만 주의할 점이 있다.
    - 캐싱, 프록시 설계 시 GET의 Body를 참조하지 않는 경우  
    - RESTFul이 강조하는 의미론에는 안맞아..
    - 지원하지 않는 Client가 존재할 수 있다.. 복병주의 ex) Spring RestTemplate


## 결론
> **설계에 따라** 달라지는 부분으로  
큰 무리는 없지만 **주의할점**은 있으며  
조회 조건이 길어질경우 **사용을 고려해 볼 수 있다**고 하겠다.


기타 참고 문서.
https://if1live.github.io/posts/http-get-request-with-body-and-http-library/