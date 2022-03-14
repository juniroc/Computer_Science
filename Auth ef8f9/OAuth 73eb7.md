# OAuth

구글, Facebook, Twitter 등 을 이용해 본인 인증하는 것. (페이지 관리자는 해당 민감 정보를 가지고 있을 필요가 없다)

개인정보 같이 본인인증에 관련된 데이터는 중소기업이나 작은 페이지 자체에서 가지고 있으면, 문제가 발생할 수 있음. 그렇기 때문에 OAuth를 이용하는 경우가 많음(중소/스타트업 등)  

사용자가 나의 페이지에 접근한 경우

![Untitled](OAuth%2073eb7/Untitled.png)

![Untitled](OAuth%2073eb7/Untitled%201.png)

(구글이나 페북 등에서) **사용자의 정보를 가지고있다가 사용자의 인증 및 구글 페북 등에 접근을** **안전하게 상호작용하도록 도움**

유저 요청 **accessToken**을 발급을 통해 상호작용 

![Untitled](OAuth%2073eb7/Untitled%202.png)

회원들의 아이디와 비밀번호를 처음부터 보관하지않고 회원을 식별할 수 있는 기능을 제공

### **Federate Identity (라고도 불림)**

![Untitled](OAuth%2073eb7/Untitled%203.png)

PHP 또는 JS를 통해 구현이 가능

![Untitled](OAuth%2073eb7/Untitled.png)

위 그림은 OAuth 관점에서 보면

![Untitled](OAuth%2073eb7/Untitled%204.png)

이와 같이 볼 수 있는데 **Their는 Resource server 와 Authorization Server 두개로 구성 (이후는 그냥 Resource Server 하나로 표현)**

클라이언트는 Resource Server의 승인을 사전에 받아놔야함

![Untitled](OAuth%2073eb7/Untitled%205.png)

아이디와 비밀번호 그리고 

ArURIS : Resource server가 Authorized Code를 부여하는데 그것을 전달 받을 주소

이후 Resource server는 저 주소가 아닌 다른 주소로 올 경우 거절함.

이후 Resource Server에 OAuth 등록을 하면 다음과 같은 정보가 Resource Server에 등록됨

Redirect URL 에 해당되는 부분은 구현해놓고 준비하면 됨 (나중에 다룸) 

![Untitled](OAuth%2073eb7/Untitled%206.png)

만약 Resource owner가 Client 서버에서 Resource Server에 있는 기능(아래에선 scope= B,C)을 (ex, google calendar 등) 이용할 경우 Client는 다음과 같은 것을 Resource Owner에게 전달함. 

![Untitled](OAuth%2073eb7/Untitled%207.png)

그리고 로그인을 하면 Resource Owner는 Resource Server에게 기능 요청 전달

 

![Untitled](OAuth%2073eb7/Untitled%208.png)

이때 만약 Redirect_uri가 Resource server에 등록된 redirect_URL과 다르면 거절하고 종료

같다면 아래와 같은 내용 전송

![Untitled](OAuth%2073eb7/Untitled%209.png)

그리고 allow를 누를 경우

Resource server는 다음과 같은 기능을 허용했다고 저장

![Untitled](OAuth%2073eb7/Untitled%2010.png)

그리고 바로 Access Token을 발급하지 않고 Authorization Code를 전송함

![Untitled](OAuth%2073eb7/Untitled%2011.png)

다음과 같이 auth_code 3을 받게 되면 Resource Owner는 자신이 느끼지 못하게 아래의 auth_code 3 이 부여된 링크로 이동하게 됨. 

그러면 Client는 Auth_code 3을 갖게됨.

![Untitled](OAuth%2073eb7/Untitled%2012.png)

Client는 auth_code 를 받았으므로 

Resource Owner를 통하지 않고 Resource Server로 접속한다 

(아래와 같은 방법으로) auth_code와 Client_secret이라는 것이 추가된 방법 이용

![Untitled](OAuth%2073eb7/Untitled%2013.png)

이후 위 사진에서 본 것처럼 링크에 제공된 정보(client_id, client_secret, auth_code, redirect URL 일치여부 등)를 통해 판단 후 접근 토큰을 부여

![Untitled](OAuth%2073eb7/Untitled%2014.png)

Access Token을 부여했으면 auth_code를 다시 제거함

![Untitled](OAuth%2073eb7/Untitled%2015.png)

그리고 access Token을 발급함 

![Untitled](OAuth%2073eb7/Untitled%2016.png)

Resource Server를 이용하려면 API를 이용해야함

![Untitled](OAuth%2073eb7/Untitled%2017.png)

![Untitled](OAuth%2073eb7/Untitled%2018.png)

(윗 내용은 추후 개발단계에서 자세히 다룰 것)

---

### Refresh Token

Access_token도 (일정시간이 지나면) 수명이 끝나는데, 이를 다시 발급받는 방법 (쉽게)

![Untitled](OAuth%2073eb7/Untitled%2019.png)

---

[https://developers.google.com/identity/protocols/oauth2/scopes](https://developers.google.com/identity/protocols/oauth2/scopes)

![Untitled](OAuth%2073eb7/Untitled%2020.png)

[WEB4 - Express-Session-Auth](https://opentutorials.org/module/3648)