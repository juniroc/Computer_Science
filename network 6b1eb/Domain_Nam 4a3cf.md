# Domain_Name_System

![Untitled](Domain_Nam%204a3cf/Untitled.png)

### IP 주소

서로 소통하기위해서는 각각의 IP 주소가 있어야함

다양한 ip장치가 있긴함

이것들을 즉, Host라고 부름

![Untitled](Domain_Nam%204a3cf/Untitled%201.png)

그러나 오른쪽 host로 접속하기 위해서 IP를 외우는건 힘듬

그래서 (예시) [example.com](http://example.com) 라는 주소로 입력해서 접속하려고 함

그러기 위해서는 hosts라는 파일을 통해 domain 네임을 부여할 수 있음.

![Untitled](Domain_Nam%204a3cf/Untitled%202.png)

Hosts 파일 위치

![Untitled](Domain_Nam%204a3cf/Untitled%203.png)

메모장(관리자 권환으로 열고)

위에 나온 대로 윈도우 hosts파일 위치로 가서 hosts를 연다(모든파일로 보기)

![Untitled](Domain_Nam%204a3cf/Untitled%204.png)

```xml
# Copyright (c) 1993-2009 Microsoft Corp.
#
# This is a sample HOSTS file used by Microsoft TCP/IP for Windows.
#
# This file contains the mappings of IP addresses to host names. Each
# entry should be kept on an individual line. The IP address should
# be placed in the first column followed by the corresponding host name.
# The IP address and the host name should be separated by at least one
# space.
#
# Additionally, comments (such as these) may be inserted on individual
# lines or following the machine name denoted by a '#' symbol.
#
# For example:
#
#      102.54.94.97     rhino.acme.com          # source server
#       38.25.63.10     x.acme.com              # x client host

# localhost name resolution is handled within DNS itself.
#	127.0.0.1       localhost
#	::1             localhost
# Added by Docker Desktop
192.168.219.200 host.docker.internal
192.168.219.200 gateway.docker.internal
# To allow the same kube context to work on the host and the container:
127.0.0.1 kubernetes.docker.internal
# End of section
```

추가하고 싶은 주소와 도메인이 있다면 다음과 같이 추가

![Untitled](Domain_Nam%204a3cf/Untitled%205.png)

그러면 이런 주소를

![Untitled](Domain_Nam%204a3cf/Untitled%206.png)

이렇게 접속이 가능

![Untitled](Domain_Nam%204a3cf/Untitled%207.png)

### 도메인

 보안

HTTPS 는 fishing 이라는 해킹 방법을 예방하기 위한 방법

http라는 사이트면 재고해봐야할 수 있음

### DNS의 태동

아이피가 바뀌거나 해도 계속 유지할 수 있는 무언가 있어야 함

Stanford Research Institute 라는 기관에서 관리해줌

![Untitled](Domain_Nam%204a3cf/Untitled%208.png)

![Untitled](Domain_Nam%204a3cf/Untitled%209.png)

![Untitled](Domain_Nam%204a3cf/Untitled%2010.png)

### Domain Name System 원리

왼쪽 서버에서 도메인 네임 시스테 서버에 도메인(example.com)을 등록함

![Untitled](Domain_Nam%204a3cf/Untitled%2011.png)

그리고 접속하는 내 PC에는 이미 Domain Name System Server 가 받아져 있음

![Untitled](Domain_Nam%204a3cf/Untitled%2012.png)

이때 example.com에 접속을 시도했을 때

위에서 작성한 hosts 파일에 따로 명시 된게 없다면 DNS server로 접근함

이를 응답해주고

![Untitled](Domain_Nam%204a3cf/Untitled%2013.png)

![Untitled](Domain_Nam%204a3cf/Untitled%2014.png)

### Publidc DNS

![Untitled](Domain_Nam%204a3cf/Untitled%2015.png)

보통은 아래와 같은 셋팅일 때,

통신사 (ISP)에서 우리 PC(server)에 DNS server 주소를 설치해줌

![Untitled](Domain_Nam%204a3cf/Untitled%2016.png)

따로 public DNS server를 이용하려면

아래는 구글 DNS server 

![Untitled](Domain_Nam%204a3cf/Untitled%2017.png)

![Untitled](Domain_Nam%204a3cf/Untitled%2018.png)

![Untitled](Domain_Nam%204a3cf/Untitled%2019.png)

구글 DNS server 가 좋다면 저걸로 바꿀 수있음 (8.8.8.8)

다양한 DNS server 가 있다. (이를 비교한 것도 있음)

![Untitled](Domain_Nam%204a3cf/Untitled%2020.png)

만약 DNS server를 바꾸고 싶다면 (아래와 같이 진행)

제어판 → 네트워크와 인터넷 → 네트워크 및 공유센터 → 어댑터 설정 변경 → wifi → 속성 → 인터넷 프로토콜 version 4 → 속성

![Untitled](Domain_Nam%204a3cf/Untitled%2021.png)

여기서 아래꺼 이용

![Untitled](Domain_Nam%204a3cf/Untitled%2022.png)

### 도메인 이름의 구조

![Untitled](Domain_Nam%204a3cf/Untitled%2023.png)

![Untitled](Domain_Nam%204a3cf/Untitled%2024.png)

사실상 전세계에 DNS server가 엄청많이 존재

![Untitled](Domain_Nam%204a3cf/Untitled%2025.png)

사실 도메인 주소 뒤에는 . 이 숨겨져 있음 (아래와 같이)

![Untitled](Domain_Nam%204a3cf/Untitled%2026.png)

이는 다음과 같이 나눠져있음

![Untitled](Domain_Nam%204a3cf/Untitled%2027.png)

그리고 이들 각각을 담당하는 DNS server들이 존재

![Untitled](Domain_Nam%204a3cf/Untitled%2028.png)

root 는 Top-level을

Top-level은 Second-level을

Second-level은 sub를

담당하는 서버목록과 IP address를 각각 알고 있어야한다

(직속 하위 파트만 알고 있음)

![Untitled](Domain_Nam%204a3cf/Untitled%2029.png)

그렇다면 blog.example.com. 이라는 IP address를 알아가는 과정을 보면 (sub를 담당하는 DNS server까지 접근해야함 

즉 전달 전달을 통해서 sub DNS server 까지 전달됨

![Untitled](Domain_Nam%204a3cf/Untitled%2030.png)

....

![Untitled](Domain_Nam%204a3cf/Untitled%2031.png)

![Untitled](Domain_Nam%204a3cf/Untitled%2032.png)

![Untitled](Domain_Nam%204a3cf/Untitled%2033.png)

### 도메인 이름 등록 과정과 원리

![Untitled](Domain_Nam%204a3cf/Untitled%2034.png)

Registrant 서버를 [`example.com`](http://example.com) 으로 등록하고 싶다면?

우선, 

1. ICANN이라는 비영리 단체가 있음 
- . domain (root 도메인)을 관리 [`a.root-server.net`](http://a.root-server.net)

2. 그 아래에는 Registry 기관/기업이 존재
- .com. domain을 관리하는 Top-level domain 서버가 존재

3. 그리고 그것을 도와주는 Register 등록대행자가 존재

![Untitled](Domain_Nam%204a3cf/Untitled%2035.png)

등록하고자한다면

다음과 같은 과정이 진행되는데 

수수료가 청구됨

![Untitled](Domain_Nam%204a3cf/Untitled%2036.png)

![Untitled](Domain_Nam%204a3cf/Untitled%2037.png)

루트 네임서버는 Top-level domain name server의 주소를 기억함

아래를 보면 com 네임서버는 a.gtld-servers.net에 존재한다 라는 걸 알 수 있음

![Untitled](Domain_Nam%204a3cf/Untitled%2038.png)

![Untitled](Domain_Nam%204a3cf/Untitled%2039.png)

실제로 도메인을 운영하기 위해서는

**top-level domain에 IP주소를 등록할 수 없고,**

스스로 서버를 마련해서 그곳에 name-server를 설치해야됨

여기선 그게 [`a.iana-servers.net`](http://a.iana-servers.net) 이라 하자

(실제론 Register등록대행자에서 무료로 풀어놓은 것도 있음)

![Untitled](Domain_Nam%204a3cf/Untitled%2040.png)

그리고 이제 등록자가 등록대행자에게 해당 서버 주소를 알려주면

아래와 같이 등록대행자는 등록소로 전달하고

등록소에서는 [example.com](http://example.com) 네임서버의 주소를 등록해줌.

![Untitled](Domain_Nam%204a3cf/Untitled%2041.png)

이로써 Top-level domain server 는 하위 서버를 알게된 것.

![Untitled](Domain_Nam%204a3cf/Untitled%2042.png)

그 다음 [`example.com`](http://example.com)의 주소가 93.184.216.34 라는 것을 알려주면 됨 

![Untitled](Domain_Nam%204a3cf/Untitled%2043.png)

![Untitled](Domain_Nam%204a3cf/Untitled%2044.png)

### 그러면 접근은 어떻게?

처음엔 ISP에서 Root domain server 주소가 있는 DNS server를 설치해놓는다.

그곳이 168.126.63.1 이라 하자

그곳에 [example.com](http://example.com) 을 요청을 보내면 

![Untitled](Domain_Nam%204a3cf/Untitled%2045.png)

해당 DNS server에는 존재하지 않으므로 Root name server로 보냄 

![Untitled](Domain_Nam%204a3cf/Untitled%2046.png)

다시 .com을 관리하는 서버로 가보라고 알려주고

DNS server는 다시 .com. 관리하는 Top-level domain server로 요청

![Untitled](Domain_Nam%204a3cf/Untitled%2047.png)

여기에 주소가 있으므로 주소를 알려주고

그 주소로 접근

![Untitled](Domain_Nam%204a3cf/Untitled%2048.png)

결국 그 IP 주소를 전달

![Untitled](Domain_Nam%204a3cf/Untitled%2049.png)

그것들 다시 Client에 전달

![Untitled](Domain_Nam%204a3cf/Untitled%2050.png)

결국 그곳에 접속하게 됨

![Untitled](Domain_Nam%204a3cf/Untitled%2051.png)

### nslookup

![Untitled](Domain_Nam%204a3cf/Untitled%2052.png)

[example.com](http://example.com) 의 주소는 93.184.216.34 이고

도메인 조회시 dns server에 의뢰하는데 그 서버 주소는 

[pcns.bora.net](http://pcns.bora.net) (61.41.153.2)

![Untitled](Domain_Nam%204a3cf/Untitled%2053.png)

### [Freenom.com](http://freenom.com) 에서 도메인 확인

쓸수있는 도메인 확인 및 기간 설정 

[Freenom - A Name for Everyone](https://www.freenom.com/en/index.html?lang=en)

아래에서 등록대행자로 보면 됨

![Untitled](Domain_Nam%204a3cf/Untitled%2054.png)