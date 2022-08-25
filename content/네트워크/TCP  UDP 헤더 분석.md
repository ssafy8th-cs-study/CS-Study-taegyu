## TCP , UDP

|             | TCP                           | Udp                                      |
| ----------- | ----------------------------- | ---------------------------------------- |
| 신뢰성 제공 | 내용 유실 x                   | 내용 유실 O , 패킷 순서가 바뀔수도 있다. |
| 속도        | 고의적 지연이 존재 , 혼잡제어 | 고의적 지연 X                            |
| 전송 단위   | 바이트                        | 패킷(데이터그램) , send() 함수 호출 단위 |

## TCP의 기능
- 신뢰성 있는 통신
- 내용 변조 탐지 - 패킷이 변조 될때 탐지가 가능하다.
- 혼잡제어 - 네트워크가 혼잡할경우 패킷의 전송을 제어한다.
- 흐름제어 - 패킷이 넘치는 경우 패킷의 전송을 제어 한다.

## TCP의 통신 과정

![img](https://t1.daumcdn.net/cfile/tistory/99FB2A3D5B32ED7B0B)

![img](D:\SSAFY\CS-Study-taegyu\content\네트워크\99423F435B32FBD22A)

1.  클라이언트는 서버에 SYN 요청을 보내고 클라이언트는 ACK 응답을 기다리는 상태가 된다.
2. 서버에서는 SYN을 잘 받았으면 ACK과 SYN Flag를 설정된 패킷을 발송하고 A가 다시 ACK을 응답하기를 기다린다.
3. 클라이언트는 다시 ACK을 보내게 되고 이후부터는 연결이 이루어지고 데이터가 오가게 된다.



### 4 way handshake 과정

TCP 연결을 종료할때 수행되는 절차

![img](D:\SSAFY\CS-Study-taegyu\content\네트워크\img\2152353F52F1C02835)



1. 클라이언트가 종료 요청을 보내게 된다.

2. 서버가 ACK 메시지를 보내고 Close-wait 상태가 되낟.
3. 서버가 통신이 끝났으면 연결이 종료되었다고 FIN 플래그를 보낸다.
4. 클라이언트가 ACK 메시지를 서버에 보내게 된다.

## TCP 패킷의 구조

![](https://images.velog.io/images/suker80/post/34381a2c-56b5-4df4-93b9-7c6f47a76595/image.png)
- 통신을 하면서 각 층에서 헤더 정보를 메시지에 담아서 보낸다.

![](https://images.velog.io/images/suker80/post/a3b31e95-3f86-4ec6-96d2-2331db2fbeea/image.png)
### source port , destination port

![](https://images.velog.io/images/suker80/post/7361d5e3-495b-46dd-a568-f8421b144072/image.png)

- 응용 계층에서 소스포트 번호와 목적지 포트 번호를 담는다.

- Source port와 Destination port는 응용 계층에서 소켓을 구분하고 전송하는데 사용이 된다.
- 응용을 구분하고 각각 사용하는 소켓을 구분 하는데 사용 된다.
- 소켓마다 대응하는 대응되는 소켓이 하나씩 존재한다.

### sequence number ,ack number

![](https://images.velog.io/images/suker80/post/3e6f414f-c7aa-48a3-a4f8-fdf8489a5be3/image.png)

- 신뢰성 있는 통신에 이용이 된다.
- 송신자는 몇번 패킷을 보내는지랑 , 몇 번까지 잘 수신됐다는 ack 번호를 보낸다.
- 수신자는 몇번 패킷까지 잘 받았다는 ack을 보내게된다. 
- 이 방법은 추상화가 가능해야 하므로 go-back-n 기법을 사용한다.

### 기타 헤더 정보 ,window size

- hl : 헤더 길이
- 그외: 제어패킷이냐 아니냐 

-window size : 수신 가능 한 버퍼 크기

![image-20220825203826955](D:\SSAFY\CS-Study-taegyu\content\네트워크\img\image-20220825203826955.png)

### checksum , urgent point

> 체크섬은 내용 변지 탐지를 위해서 사용한다.





### UDP

- 비연결형 서비스를 지원하는 전송계층 프로토콜
- 신뢰할 수 없는 통신
- 속도가 빠름
- 소규모의 데이터 통신에 적합
- UDP 헤더의 고정 크기 8 byte



## UDP 헤더

![img](D:\SSAFY\CS-Study-taegyu\content\네트워크\img\99B12B385BD6DC0F03)



- Source port number : 메시지를 보내는 측에서 사용하는 포트 번호

- Destination port number:  통신을 위해 사용하는 port 번호
- Total length : 헤더와 데이터를 합한 전체 길이
- Checkusm 내용 변지 탐지를 위해 사용



## TCP VS UDP

![img](D:\SSAFY\CS-Study-taegyu\content\네트워크\img.png)