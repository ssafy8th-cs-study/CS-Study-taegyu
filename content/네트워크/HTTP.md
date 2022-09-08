# HTTP



## HTTP 0.9

- HTTP 0.9 부터 2버전 까지는 기본적으로 TCP 연결을 사용한다.

  

![image-20220831193559330](D:\SSAFY\CS-Study-taegyu\content\네트워크\img\image-20220831193559330.png)

0.9 버전에서는 메서드와 요청 자원과 그에 대한 응답밖에 없는 간단한 구조 였다.

사용을 확장해서 사용하기에는 힘들다.



## HTTP 1.0

![image-20220831193708132](D:\SSAFY\CS-Study-taegyu\content\네트워크\img\image-20220831193708132.png)



HTTP 1.0에서는  버전 , 상태코드 , 응답데이터에 대한 형식까지 지원을 하게 되었다.



![image](D:\SSAFY\CS-Study-taegyu\content\네트워크\img\79342851-9d439600-7f68-11ea-9a1c-80782d6cbb6e.png)



HTTP 1.0은 요청이 들어올때마다 TCP 연결을 하고 요청에 대한 응답을 보내는 구조였다.

이렇게 통신을 하면 매 요청이 들어올때마다 TCP 연결을 수행하는데 비용이 소모가 되는 단점이 있었다.



![image](D:\SSAFY\CS-Study-taegyu\content\네트워크\img\79683535-bc427080-8265-11ea-84c5-a00e32a07a37.png)

위와 같은 문제점을 해결하기 위해 나온 기법이 Persistent Connection(Keep-alive)이다.

지정한 timeout동안 커넥션을 끝내지 않는 방식이다.

Persistent Connection은 연결을 지속하며 클라이언트와 서버 통신이 끊기지 않고 지속되는 특징이 있다.

클라이언트는 서버에게 HTTP 요청시 요청 Message에 connection:keep-alive 헤더를 추가해서 통신을 하게 된다.

- 서버에서는 클라이언트의 요청을 받아 TCP연결을 HTTP 응답 이후 끊지 않고 사용하겠다는 의미이다.

- Persistent Connection을 사용하면 서버의 단일 시간 내의 TCP 연결의 수를 적게 함으로써 CPU나 메모리 자원을 절약할 수 있고, 네트워크 혼잡을 줄일 수 있다.

  

![HTTP pipelining - Wikipedia](D:\SSAFY\CS-Study-taegyu\content\네트워크\img\1200px-HTTP_pipelining2.svg.png)



또한 하나의 커넥션에서 응답을 기다리지 않고 순차적인 여러 요청을 연속적으로 보내 그 순서에 맞춰 응답을 받는 방식으로 지연 시간을 줄이게 했다.

- 첫번째 요청에 대한 응답시간이 오래걸리면 뒤에 있는 요청에 대한 응답을 보낼 수가 없어서 대기시간이 길어진다.

- 또한 HTTP 1.1에서는 전송한 data를 압축하여 전달하므로 data의 양을 줄이고 있다.

## HTTP 2

- 기존 HTTP/1.X 버전의 성능 향상에 초점을 맞춘 프로토콜

- 표준의 대체가 아닌 확장

## Binary Framing



![img](D:\SSAFY\CS-Study-taegyu\content\네트워크\img\img.png)

HTTP 1.1에서는 text형식으로 전달되던 요청 , 응답 메시지는 프레임 단위로 나누어지고 바이너리 형식으로 인코딩 된다.

- 바이너리는 컴퓨터가 더 이해하기 쉽기때문에 더욱 빠르다

  ![HTTP-vs-with-push-HTTP1](D:\SSAFY\CS-Study-taegyu\content\네트워크\img\HTTP-vs-with-Push-HTTP1.gif)

![HTTP-vs-with-push-HTTP2](D:\SSAFY\CS-Study-taegyu\content\네트워크\img\HTTP-vs-with-Push-HTTP2.gif)



### Multiplex streaming



하나의 TCP 통신에 요청과 응답에 파일들을 묶어서 한번에 보내는 기법

HTTP 1.1에서는 커넥션을 여러개 맺어서 동시에 파일을 받는 방법을 사용했다.



## Header Compression

![img](https://t1.daumcdn.net/cfile/tistory/217B0E3F580371A51A)



첫번째 요청이후 새로운 요청이 들어올 경우 이미 있는 헤더는 존재한다는 가정하에 새로운 헤더만 추가적으로 요청을 받는 방식이다.

![HTTP-vs-with-Push-HTTP2push](D:\SSAFY\CS-Study-taegyu\content\네트워크\img\HTTP-vs-with-Push-HTTP2push.gif)

Header Pusing을 이용하면 좀 더 빠르게 통신이 가능하다.

기존 1.1에서는 HTML을 응답 받으면 의존하고 있는 리소스들을 하나씩 요청을 했어야 했는데,

2.0 버전에서는 한번에 요청이 가능해서 더욱 빠르게 응답이 가능하다.

