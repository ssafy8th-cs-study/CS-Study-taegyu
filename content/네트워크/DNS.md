# DNS

- DNS(Domain Name System) : ip 주소를 사람이 읽을 수 있는 이름으로 변환 하는 시스템
- DNS는 상위 기간과 하위 기간과 같은 계층 구조를 가지는 분산 데이터베이스 구조를 가진다.

![도메인 체계](D:\SSAFY\CS-Study-taegyu\content\네트워크\img\dns.gif)

DNS는 위와같은 트리 형태로 구성이 되어 있다.



1. Root dns  
   - ICANN이 관리하는 최상위 DNS 서버
   - DNS ip 주소를 저장하고 안내하는 역할을 한다.
2. Top level Domain 서버 
   - 도메인 등록기관이 관리하는 서버이다.
   - SecondLevel dns 서버의 주소를 저장하고 안내하는 역할을 한다.
3. Second Level domain Dns 서버
   - 실제 개인 도메인과 ip 주소의 관계가 기록되는 서버이다.
   - 개인 dns를 구축하면 이 서버에 속하게 된다.
4. 3단계 DNS 서버
   - 질의를 통해 ip 주소를 알아내거나 캐시해서 경로로 안내한다.

![도메인 질의 과정](D:\SSAFY\CS-Study-taegyu\content\네트워크\img\dns_query.gif)



## DNS 동작 과정

1. 웹 브라우저에 naver.com을 입력한다.

2. 브라우저는 이전에 방문한적 있는지 찾는다.

   - 브라우저 캐시
   - OS 캐시
   - 라우터 캐시
   - ISP 캐시 확인

3. 없으면 Local dns에 요청

4. 루트 dns에 쿼리를 날리게 된다

5. com dns로 다시 요청을 전송하게 된다

6. local dns는 다시 naver.com dns를 관리하는 서버에 요청을 보낸다

7. naver.com을 ip 주소로 변경해서 브라우저에게 전달한다.

   