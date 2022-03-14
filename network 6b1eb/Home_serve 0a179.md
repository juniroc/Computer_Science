# Home_server

[https://www.youtube.com/watch?v=sQBXgccvE98&list=PLuHgQVnccGMA52uRBmSwqcvtI5IMoFclJ](https://www.youtube.com/watch?v=sQBXgccvE98&list=PLuHgQVnccGMA52uRBmSwqcvtI5IMoFclJ)

IPv4 → 0.0.0.0 ~ 255.255.255.255 약 42억개의 아이피 주소

하지만 이게 동이나기 시작해서 IPv6가 나옴 알파벳까지 동원

하지만 당장 Ip 주소를 바꾸기엔 어려움이 있으니 **IPv4와 IPv6가 협력**

→ 그 방법으로 공유기 이용

이러한 공유기를 이용하기 위해서

![Untitled](Home_serve%200a179/Untitled.png)

이것들을 알아야함.

**공유기에 연결되는 컴퓨터를 웹서버로 이용**

### IP address

![Untitled](Home_serve%200a179/Untitled%201.png)

서로 정보를 주고 받으려면 양쪽다 IP address가 필요함

요청하는 컴퓨터가 요청을 보낼때 자신의 IP address를 보내서 받은 주소는 IP address를 알 수 있음.

통신사랑 계약 후 회선을 받고 꽂으면 컴퓨터에는 IP address 가 부여됨

이후 컴퓨터 및 스마트폰 등이 연결되는데.. 이때도 IP address가 부여되어야함

→ 통신사를 2개 더 계약하기에는 비쌈 → 그래서 나온게 공유기

![Untitled](Home_serve%200a179/Untitled%202.png)

![Untitled](Home_serve%200a179/Untitled%203.png)

---

![Untitled](Home_serve%200a179/Untitled%204.png)

통신사 케이블은 WAN 에 붙음 → 그러면 기존의 컴퓨터에 부여되었던 IP address는 공유가에 부여됨

![Untitled](Home_serve%200a179/Untitled%205.png)

이후 자동으로 기기에 아이피 부여됨 (공유기에도 부여됨 - **게이트웨이 주소 또는 라우터 주소** 라고 불림)

![Untitled](Home_serve%200a179/Untitled%206.png)

외부 아이피를 Public IP address라 부르고, 내부망 아이피를 Private IP address라 부름

public IP 는 전세계 어디서도 접근 가능

![Untitled](Home_serve%200a179/Untitled%207.png)

![Untitled](Home_serve%200a179/Untitled%208.png)

표의 앞부분(10 or 172 or 192 )으로 시작하는 IP address는 모두 **Private IP address(사설 아이피)로 약속**

---

### NAT(Network Address Translation)

만약 나의 노트북에서 외부의 위키피디아에 접속하려고 할 경우

![Untitled](Home_serve%200a179/Untitled%209.png)

1. 공유기에 일단 노트북의 Private IP address를 입력해두어야 함
2. 공유기 Public IP address로 변환하여 위키 피디아로 요청을 보냄
3. 위키피디아는 응답을 다시 공유기의 WAN주소 Public IP address로 응답
4. 다시 공유기는 노트북 Private IP address로 전달

이것을 가능하게 해주는 기술이 **NAT**

윈도우는 제어판 → 네트워크 및 공유 → 인터넷 이름 → 자세히 누르면 

![Untitled](Home_serve%200a179/Untitled%2010.png)

IPv4 주소와 IPv4 게이트웨이 (router) 정보를 알 수 있음

게이트웨이 주소를 인터넷에 검색하면

![Untitled](Home_serve%200a179/Untitled%2011.png)

다음과 같이 나옴

### Port

여태까지 위의 것들은 내 노트북을 Client로 보고 외부에 접속하는 기능이었음.

**이제부터는 내 노트북을 server로 보고 외부에서 접속하는 방법에 대해 알아볼 것.**

![Untitled](Home_serve%200a179/Untitled%2012.png)

![Untitled](Home_serve%200a179/Untitled%2013.png)

위에서 0~1023 은 Well-known port로 개인이 이용하지 못하게 되어있음

그리고 **80번은 Web이 쓰도록** 정해져있음 (22는 ssh)

웹서버를 깔면 80번에 연결이 되는데 이를 **Listening** 이라는 표현을 씀(계속 듣고있다는 뜻으로 보면됨)

그럼 웹서버를 하나 더 받으려면 어떻게 해야하나? → 8080 port 이용 (관습적)

![Untitled](Home_serve%200a179/Untitled%2014.png)

8080에 접속하고 싶으면 다음과같이 접속 가능

그러면 저렇게 이용하려면 어떻게해야하나?

→ **Port Forwarding**

![Untitled](Home_serve%200a179/Untitled%2015.png)

### Dynamic vs Static IP Address

유동 IP 주소 vs 정적 IP 주소 

ISP 는 통신사 internet service provider

ISP 에서 집에 IP 주소를 줌

![Untitled](Home_serve%200a179/Untitled%2016.png)

**유동아이피는 만약 윗집이 IP를 오랫동안 안 쓸경우** 

**→ ISP가 윗집 아이피를 회수해 다른 집으로 전달**

그리고 다시 윗집이 돌아오면??

![Untitled](Home_serve%200a179/Untitled%2017.png)

새로운 아이피 부여

그러면 왼쪽사람이 접속하려고 시도하면 아래집으로 접속이 될텐데..?

→ 이 점이 바로 Dynamic IP의 단점

→ 그래서 나온게 Static IP 인데 이것은 통신사에게 **고정** **IP 쓰도록 추가비용**을 내야 함 

### DHCP

![Untitled](Home_serve%200a179/Untitled%2018.png)

아이피를 수동으로 부여하는 방법

제어판 → 네트워크 및 인터넷 → 네트워크 공유센터 → 커넥션 → 속성 → TCP/IPv4 누르고 속성

![Untitled](Home_serve%200a179/Untitled%2019.png)

![Untitled](Home_serve%200a179/Untitled%2020.png)

현재는 자동으로 되어있음

![Untitled](Home_serve%200a179/Untitled%2021.png)

원하는 주소를 사용하려면 서브넷 마스크 등 DNS 서버 등 다양한 지식이 필요

즉, 자동으로 IP, DNS 등을 부여하는 것이 DHCP server 
→ + 이는 공유기에 내장되어있음  
→ + 인터넷 사용 기기는 DHCP client가 깔려있음

노트북 아래 기기마다 특별 식별자가 있는데 (공장부여) 이를 **Mac Address**라고 함

IP 주소 할당 순서 예시

1)

![Untitled](Home_serve%200a179/Untitled%2022.png)

2)

![Untitled](Home_serve%200a179/Untitled%2023.png)

3)

![Untitled](Home_serve%200a179/Untitled%2024.png)

4)

![Untitled](Home_serve%200a179/Untitled%2025.png)

5)

![Untitled](Home_serve%200a179/Untitled%2026.png)

여기에 채워넣음

6)

![Untitled](Home_serve%200a179/Untitled%2027.png)

공유기 서버에 접속 후 

![Untitled](Home_serve%200a179/Untitled%2028.png)

내부 네트워크 설정에 들어가면 DHCP 서버 동작 중지 가능

동적 IP 주소 범위 설정 가능

만약 컴퓨터가 많은 경우 IP 대여시간을 짧게해서 빨리빨리 돌려막기 하도록 하는것이 좋음

특정 Mac address에 특정 IP주소를 주는 것도 가능

---

### 1. MAC address & IP Address

[맥 어드레스란 무엇인가? IP주소와 맥주소(MAC address) 차이, 맥 주소 확인하는 법 - 네트워크 기초](https://jhnyang.tistory.com/404)

### DHCP

- 호스트의 **IP주소**와 각종 **TCP/IP 프로토콜**의 **기본 설정**을 **클라이언트에게 자동**적으로 **제공**해주는 프로토콜

### Proxy server

- **클라이언트**가 자신을 거쳐 **다른 네트워크에 접속**할 수 있도록 **중간에서 대리해주는 서버
즉, 서버**와 **클라이언트** 사이에서 대리로 **통신 수행**해주는 **서버**

![Home_serve%200a179/Untitled%2029.png](Home_serve%200a179/Untitled%2029.png)