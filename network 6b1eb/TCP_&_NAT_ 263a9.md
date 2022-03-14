# TCP_&_NAT_(Transport Layer-L4)

### Transport 계층

![Untitled](TCP_&_NAT_%20263a9/Untitled.png)

![Untitled](TCP_&_NAT_%20263a9/Untitled%201.png)

- 위에서 외부주소는 목적지 IP 정도로 생각하면 됨

### TCP 란?

![Untitled](TCP_&_NAT_%20263a9/Untitled%202.png)

- 전송 제어 프로토콜

![Untitled](TCP_&_NAT_%20263a9/Untitled%203.png)

- TCP 제어 플래그가 중요

![Untitled](TCP_&_NAT_%20263a9/Untitled%204.png)

### UDP 란?

![Untitled](TCP_&_NAT_%20263a9/Untitled%205.png)

ex) 

- 동영상 스트리밍 : 축구 경기중에 끊어져도 끊어진 부분은 무시하고 현재 실시간 상황 전송
- 즉, 데이터를 보내기만 하고 제대로 받았는지 확인은 따로 안함 (TCP와 큰차이점
→ 신뢰성이 낮음

![Untitled](TCP_&_NAT_%20263a9/Untitled%206.png)

---

### TCP 통신

![Untitled](TCP_&_NAT_%20263a9/Untitled%207.png)

![Untitled](TCP_&_NAT_%20263a9/Untitled%208.png)

---

## NAT

![Untitled](TCP_&_NAT_%20263a9/Untitled%209.png)

- 위 그림에서 `**WAN**` 에서 주로 사용하는게 `**공인 IP**`, `**LAN 내부**`에서 사용하는게 `**사설 IP**` 라 생각하면 됨

![Untitled](TCP_&_NAT_%20263a9/Untitled%2010.png)

- 개인 PC 의 사설IP 와 공인IP 확인 방법

- 그럼 연결을 해주는 것은 무엇인가?
    
    → 그게 바로 **NAT**
    

![Untitled](TCP_&_NAT_%20263a9/Untitled%2011.png)

- 1:1 맵핑

![Untitled](TCP_&_NAT_%20263a9/Untitled%2012.png)

![Untitled](TCP_&_NAT_%20263a9/Untitled%2013.png)

- 정적 NAT
    - 1:1 Mapping

![Untitled](TCP_&_NAT_%20263a9/Untitled%2014.png)

![Untitled](TCP_&_NAT_%20263a9/Untitled%2015.png)

- 위 경우는 내부에서 외부로 나갈때의 예시
- 211.203.1.0~100 대에 범위에서 할당 받아 전달

![Untitled](TCP_&_NAT_%20263a9/Untitled%2016.png)

![Untitled](TCP_&_NAT_%20263a9/Untitled%2017.png)

- 1:N

## Port Forwarding

![Untitled](TCP_&_NAT_%20263a9/Untitled%2018.png)

![Untitled](TCP_&_NAT_%20263a9/Untitled%2019.png)

- 공인 IP 1개로 **여러대의 사설 IP를 Port 로 구분해 연결**
    - 회사 내에서 101~107 을 포트만 바꿔가며 접속했던 것 생각

![Untitled](TCP_&_NAT_%20263a9/Untitled%2020.png)

- 기존 웹 서버에서는 요청 패킷이 **같은 IP**에서 온것이므로 **직접 전달**하게됨
→ 그로 인해 기존 커넥션이 아닌 **신규 패킷으로 판단되어 통신이 불가**

- Solution
→ NAT 장비에서 출발지 IP를 NAT 장비 IP 로 변경

![Untitled](TCP_&_NAT_%20263a9/Untitled%2021.png)

![Untitled](TCP_&_NAT_%20263a9/Untitled%2022.png)

- PC 의 `192.168.1.100` 이 NAT 장비에서는 `192.168.1.1` 로 변경됨