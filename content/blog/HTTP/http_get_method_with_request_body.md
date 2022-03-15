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
API 서버를 개발 중, 동료가 만든 API를 테스트하는데 동료는 정상적으로 된다는데 나는 아무리해도 안 되었다. 요청을 어떻게 보냈냐고 물어봤더니 Get에 Body를 설정해서 보내고 있었고
Body를 붙여 보내면 Spring GetMapping에서 RequestBody로 받아낼 수 있었다. 의도한 것은 아니고 우연이었던 것 같은데,
찾아보니 이런 경우는 엘라스틱서치 등에서 사용하는 것을 볼 수 있다고도 한다.

HTTP를 처음 접하고부터 Rest API 설계를 할 때도 get에 Body를 보내는 것은 한 번도 고려한 적도 없었고 보지도 못했다.
get메소드를 사용할 때 했던 고민은 Restful한 설계를 고려하며 path parameter, query string을 어떻게 적절하게 사용할지였다.
그래서 될줄 몰랐다.

### 된다.

>그런데 ```그렇게 쓰는 것에 대한 판단```을 어떻게 해야할까?

이게 된다고 해서 사용을 해도 될까?  

가장 괜찮은 관점에서 정리된것 같은 [문서](https://brunch.co.kr/@kd4/158) 를 첨부한다.

_간단히 요약하면_
1. 2014년 이후 나온 RFC스펙(RFC 7230-7237) 을 근거로 하여 무리가 없어보인다.
2. 하지만 주의할 점이 있다.
    - 캐싱, 프록시 설계 시 GET의 Body를 참조하지 않는 경우  
    - RESTFul이 강조하는 의미론에는 안맞아..
    - 지원하지 않는 Client가 존재할 수 있다.. 복병주의 ex) Spring RestTemplate

#### *RFC (Request For Comments)
미국의 국제 인터넷 표준화 기구 ```IETF(Internet Engineering Task Force)```에서 관리하는 문서이다. 
[참고문서](https://net-study.club/entry/RFC-Request-for-Comments%EB%9E%80-RFC%EC%9D%98-%EC%97%AD%EC%82%AC-RFC-%EC%A2%85%EB%A5%98-RFC-%ED%91%9C%EC%A4%80%ED%99%94-%EC%A0%88%EC%B0%A8)

표준화를 근거로 판단하는 것은 좋은 기준인것 같다.  
~~본문을 조회하였는데 아직 이해는 잘..~~  
친절하게 설명해준 문서를 힘입어 아래의 정보를 간단히 요약해둔다.


## 결론
> **설계에 따라** 달라지는 부분으로  
큰 무리는 없지만 **주의할점**은 있으며  
조회 조건이 길어질경우 **사용을 고려해 볼 수 있다**고 하겠다.


개인적으로는 반드시 사용해야 하는 특수한 상황이 아니라면 <span style="color:orange">_사용을 고려하지는 않을 것_ </span>같다.
일하면서 배운 생소한 것이어서 정리해보았다.


[기타 참고 문서](https://if1live.github.io/posts/http-get-request-with-body-and-http-library/)
