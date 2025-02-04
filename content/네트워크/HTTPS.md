# HTTPS

기존 HTTP에 Secure을 붙인 단어

HTTP 요청을 암호화를 해서 요청과 응답을 주고 받는다.

중간 탈취의 위험이 적다.

## SSL  & TLS

HTTP 통신 과정 중간에 SSL 계층을 통과를 하게 되는데 SSL 계층은 서버와 브라우저 사이에 안전하게 암호화된 연결을 만들어 주고 서버와 브라우저가 민감한 정보를 주고 받을 때 해당 정보가 도난당하는 것을 막아준다.

![img](D:\SSAFY\CS-Study-taegyu\content\네트워크\9943623359FF02B105)

서버는 서버만 알 수 있는 개인키를 가지고 있다.

공개키로 암호화된 HTTP 요청이 온다면 서버는 개인키를 이용하여 공개키로 암호화된 문장을 해독하게 된다.

서버에서 요청이 해석이 가능하면 다시 응답을 개인키로 암호화해서보내게 된다



이 과정에서 서버와 클라이언트는 각각의 공개키와 개인키로 암호화가 되어있으니 알맞는 사용자가 보냈다고 인증 할 수 있다.



## HTTPS 통신 흐름

1. 애플리케이션 서버를 만드는 기업은 HTTPS 적용을 위해 공개키와 개인키를 만든다
2. 그 다음 신뢰할 수 있는 CA 기업을 선택하고 그 기업내에 공캐리를 관리해달라고 계약을 한다.
3. CA 기업은 CA 기업만의 공개 키와 개인키가 있다.
4. CA 기업은 기업의 이름 , 공개키 암호화 방법의 정보르 담은 인증서를 만들고 CA 기업의 개인키로 암호화 해서 A 서버에 제공한다.
5. A 서버는 인증서를 갖게 되었으므로 HTTPS 요청이 아닌 요청이 오면 인증서를 클라이언트에게 준다.
6. CA기업의 공개키로 해독을 할 수 있게 된다.



