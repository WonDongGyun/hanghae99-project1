# hanghae99-project1

-   **진행 날짜 - 2021.03.01 ~ 2021.03.04**
-   **목적 - 처음으로 배정된 팀원들과, 사전과제에서 공부한 지식을 바탕으로 프로젝트를 완성하기**
-   **필수 포함 사항**

**         ㄴ 쿠키/세션 방식으로 로그인을 구현하고 → JWT 인증 방식으로 바꿔보기**

**         ㄴ Jinja2 템플릿 엔진을 이용한 서버사이드 렌더링**

---

**드디어 항해 99를 시작하게 되었습니다!**

첫 번째 주에 수행하는 과제는 처음으로 배정된 팀원들과 사전과제에서 공부한 지식을 바탕으로 필수 포함 사항을 지키며 프로젝트를 완성하는 것입니다.

문제는 저를 포함한 팀원 모두가 파이썬으로 웹개발을 해본 경험이 없었다는 거였죠. 물론 다른 조 분들도 마찬가지였습니다.

처음에 뭘 해야할지 감이 안잡혔지만 팀원분께서 "**모두 취미로 게임을 하니 게임 추천 사이트는 어떻겠냐**"는 제안을 해주셔서 주제는 빠르게 잡을 수 있었습니다.

[##_Image|kage@ct4Gge/btqZpV0GYVk/k3WPgZScTb5iuqqlebz3kK/img.png|alignCenter|data-filename="KakaoTalk_20210301_164343219.png" data-origin-width="1396" data-origin-height="1600" width="700" height="NaN" data-ke-mobilestyle="widthContent"|그래서 열심히 만들었다! 다행히도 팀원분이 포토샵을 잘 다루시더라구요~||_##]

주제를 잡았다면 **화면 설계도 (와이어 프레임)**를 만들어야겠죠?

팀원 분이 열심히 포토샵으로 만들어 주셨고, 저와 다른 팀원분이 열심히 검토하고 첨삭을 진행했습니다. 프로젝트 기간이 짧고, 팀원 모두가 파이썬 프로젝트가 처음이라 복잡한 기능을 넣는것보다 필수 포함 사항을 넣으며 있어(?) 보이게 화면 설계도를 만들었답니다.

화면 설계도를 만든 다음에는 역할 분담을 했습니다.

1명은 로그인 화면과 회원가입 화면을, 1명은 크롤링을 해서 카드로 만드는 메인화면을 만들기로 했고, 저는 글쓰기 기능과 파일 구조 잡기 및 정리 역할을 맡았습니다.

[##_Image|kage@clhDEU/btqZpT2RYYI/NtUgdMXHadatuENTOK41Ek/img.png|alignCenter|data-origin-width="0" data-origin-height="0" data-ke-mobilestyle="widthContent"|flask에 존재하는 강력한 기능중 하나인 BluePrint||_##]

파일 정리는 필수 포함 사항에 없었지만, 제가 꼭 해야겠다고 생각했던 이유는 다음과 같습니다.

1\. 깃허브로 형상관리를 하는데 있어서 충돌을 최소화 할 수 있다.

2\. 작업자들이 작업영역을 명확히 알 수 있다.

3\. 아름다운 프로젝트를 만들 수 있다!

그래서 찾던 와중 파이썬 Flask에서는 BluePrint라는 강력한 기능을 지원한다는 것을 알게 되었고, 바로 저희 프로젝트에 적용해서 구조를 잡았습니다.

## 🤔 **BluePrint가 뭔데?**

**" route() 함수를 구조적으로 다룰 수 있고 큰 application을 단순화할 수 있는 기능 "**

app.py에 모든 api를 담는것은 같은 작업자로 하여금 관리하기 힘들게 만듭니다.

그래서 app.py에는 단순한 기능만 넣어놓고 로그인, 메인화면 등에서 작동하는 api는 각각의 .py 파일로 분리해서 하위 디렉토리에다가 넣었습니다

[##_Image|kage@4cwR9/btqZywk1yT0/pxsxWm9HWACekygtUPyBK0/img.png|alignCenter|data-origin-width="0" data-origin-height="0" width="651" height="NaN" data-ke-mobilestyle="widthContent"|mypage 화면에서만 사용되는 mypage.py||_##]

이렇게 BluePrint를 사용해서 api를 나눠버렸기에 깃허브 형상관리도 원할할 수 있었고, 팀원들간 작업 일정을 쉽게 공유할 수 있었습니다.

## 🤔 **Jinja - include, extends?**

**" 파일 구조를 잡았으니까 추가로 HTML도 정리해봅시다! "**

BluePrint로 파일구조를 잡다가 문득, HTML도 정리를 할 수 있지 않을까란 생각이 들어서 구글을 뒤져보았습니다. 

jinja에서는 include와 extends 기능을 지원합니다.

**" include - html 파일에서 다른 html 파일을 가져오는 기능 지원 "**

****" extends - include와 기능은 비슷해 보이지만 부모 html(template)를 만들고****

****그 안에 block을 지정해둬서 자식 html이 해당 block 부분을 필요하다면 갈아 치울 수 있다"****

재가 만들때는 extends를 모른 상태로 include를 알아내서 구조를 잡아버리는 바람에 extends를 사용하지 못했는데요, 

include 보다 extends가 각 페이지별 코드의 양이 훨씬 줄어들기 때문에 더 좋답니다.

[##_Image|kage@crE9v8/btqZvNUXN7w/CPOJwKfVqBJGLgvlpGqZkK/img.png|alignCenter|data-origin-width="0" data-origin-height="0" width="513" height="NaN" data-ke-mobilestyle="widthContent"|main.html에서 include를 사용하여 밑의 head.html의 meta 태그, link 태그 등을 사용하는 모습||_##][##_Image|kage@dJyPSt/btqZn0PfKmh/p4VKxUWOBp3LyPZ1nIvsx0/img.png|alignCenter|data-origin-width="0" data-origin-height="0" width="489" height="NaN" data-ke-mobilestyle="widthContent"|||_##]

## 🤔 **JWT가 뭐지???**

**" JWT (Json Web Token) - JSON 웹 서명은 임의 데이터 서명을위한 IETF 제안 표준입니다." **

[##_Image|kage@wYTCN/btqZBeEu3u5/uaV8a6TAWMKIgD4eo8dovk/img.png|alignCenter|data-origin-width="0" data-origin-height="0" data-ke-mobilestyle="widthContent"|이 부분이 제일 어려웠고, 제일 나를 많이 괴롭혔다.||_##]

JWT는 Json 토큰을 만들어서 인증하는 방식을 말합니다.

처음에 다른 팀원분이 로그인 기능을 만들어 주셨는데, 사용하기 조금 불편해서 flask jwt extended를 사용해서 jwt 인증 로그인을 만들었습니다.

**" 그런 짓은 하지 말아야 했는데 난 그 사실을 몰랐어 "**

그런데 문제는 flask jwt extended를 사용하니까 flask에서 쿠키로 접근해서 가지고 올 수 있는 방법이 없었습니다...

그러다 보니 html에 접속할때마다 api 호출을 해야하니, 불필요한 호출이 많이 일어났죠. 원래 팀원분이 만들어 주셨던 jwt 로그인 방식을 사용했다면 flask에서 쿠키를 호출해서 jwt.decode를 사용할 수 있었을텐데, flask jwt extended는 그런 기능을 지원해주지 않았습니다. (못찾은 것일 수도 있어요 ㅠㅠ)

[##_Image|kage@A9XyK/btqZBdlhA2s/6IVgLlMhPXk8UBpbWAQFq1/img.png|alignCenter|data-origin-width="0" data-origin-height="0" data-ke-mobilestyle="widthContent"|flask jwt extended는 jwt_required()를 무조건 사용해야 하고 복호화 하기 위해서는 get_jwt_identity()를 사용해야 한다.||_##]

그러니까 혹시라도 flask jwt extended를 사용하시려는 분은 import jwt를 해서 jwt incode, decode를 사용하시길 바랍니다.

## 🤔 **SSR ???**

" **SSR (Server Side Rendering) - 사용자가 웹페이지 접근시 서버에 페이지에 대한 요청을 하고, 서버에서는 수많은 리소스들이 어떻게 보여질지 렌더링해서 반환합니다** "

그렇다면 jinja로 서버 사이드 렌더링을 도대체 어떻게 해야하는걸까?

아무리 검색해도 답을 찾을 수 없었다. 그래서 일단은 ajax로 필요한 데이터를 가지고와서 jquery로 html에서 데이터가 필요한 곳에 넣는 작업을 하였다.

**" 모르면 당해야지 "**

[##_Image|kage@dacrTJ/btqZvNnagNh/nkXenMz90u1h83HxVVFCB0/img.png|alignCenter|data-origin-width="0" data-origin-height="0" width="700" height="NaN" data-ke-mobilestyle="widthContent"|ajax로 호출할때마다 엄청난 양의 데이터를 jquery를 사용해서 뿌린다. 완전 비효율적이다.||_##]

정말 모르면 당해야한다. 위의 코드를 보면 우리가 main.html에 접근할 때마다 ajax가 api에 접근해서 대량의 데이터를 가지고 오고, html에 뿌려준다.엄청난 시간이 걸리게 된다!!!!!

[##_Image|kage@FKOmg/btqZqpURBwE/kTVUdDHNQp8og3gEk6YHC0/img.png|alignCenter|data-origin-width="0" data-origin-height="0" width="652" height="NaN" data-ke-mobilestyle="widthContent"|ajax를 사용하지 않고도, flask에서 return render_template를 사용해 html로 바로 데이터를 넘길 수 있다.||_##]

하지만 jinja로 서버 사이드 렌더링을 하게되면?

ajax로 api 호출을 하지 않아도 이렇게 이쁘게 한번에 데이터를 뿌려준다. 2번 작업하는 것을 한번으로 줄였으니

이 얼마나 아름다운 코드인가...

## 🤔 **CSS Animation을 어떻게 줘야할까?**

파일 구조도 다잡고 웹페이지도 디자인에 따라서 잘 만든것 같은데 뭔가 부족한것 같았습니다. 그래서 저희 웹사이트에 별건 없지만 애니메이션을 넣으려고 했습니다. 하지만 css상으로 구현하기에는 시간도 너무 오래걸리고 코드량도 많아질 것 같아서 다른 방법을 선택했습니다.

## " Animate CSS "

[##_Image|kage@bbo5f2/btqZoxMQ5o7/fiBoLTYskECAvSjUszwfT1/img.png|alignCenter|data-origin-width="0" data-origin-height="0" data-ke-mobilestyle="widthContent"|animate.css의 공식사이트||_##]

Animate.css를 사용하면 html class에 몇자 적는 것으로 간단하게 애니메이션 기능을 넣어줄 수 있답니다.

이 방법을 사용해서 큰 시간을 들이지 않고도 버튼이나 모달 창에 애니메이션 효과를 줄 수 있었죠.

---

## **😀 완성!!!**

[##_Image|kage@di4KkE/btqZrfRYZxe/VLRJiI8dYjcHyelm7hKOB0/img.png|alignCenter|data-filename="KakaoTalk_20210304_231949595.png" data-origin-width="280" data-origin-height="160" data-ke-mobilestyle="widthContent"|Game Tree 이미지||_##]

-   **팀 번호 -** 24조
-   **팀원 수 -** 3명
-   **제목 -** Game Tree
-   **주소 -** [http://gametree.shop  ](http://%20http://gametree.shop)
-   **깃허브 -** [https://github.com/kbyunghoon/hanghae99-project1/](https://github.com/kbyunghoon/hanghae99-project1/)
-   **영상 -** [https://www.youtube.com/watch?v=XyuV\_e9DRi4&ab\_channel=Hoonlee](https://www.youtube.com/watch?v=XyuV_e9DRi4&ab_channel=Hoonlee%20)  
-   **설명** 

게임을 좋아하는 사람들을 위한 게임 정보 공유 사이트입니다.  
한눈에 쉽고 빠르게 게임에 대한 정보들을 확인할 수 있으며 크롤링을 통해 유저가 게임제목만 입력해도 정보를 공유할 수 있도록 했습니다.  
빠르고 간단하게 정보를 공유할 수 있도록 최소한의 정보로 로그인을 할 수 있고 로그인을 하지않아도 게임정보를 확인하고 추천할 수 있습니다

-   **SSR (Server Sids Rendering)의 장점**

1.  완성된 페이지의 형태로 응답되기때문에 검색엔진에 최적화 가능한 점이 가장 큰 장점입니다. 빈 html을 전달하는 클라이언트 랜더링은 검색 엔진에 잘 잡히지않지만 이미 서버에서 랜더링된 html 파일을 보내주기때문에 검색엔진에 잘 잡힙니다. 전통적인 웹 어플리케이션은 서버 사이드 렌더링 방식을 사용합니다.
2.  클라이언트 사이드 랜더링의 경우 서버는 json파일만 보내고 자바 스트립트가 html을 그리는 역활을 당담하기때문에 초기 구동속도가 느립니다. 하지만 서버 사이드 랜더링 방식은 첫 랜더링된 html 파일을 클라이언트에게 전달해주기때문에 초기 로딩 속도를 많이 줄여줄수 있습니다

-   **JWT 방식 설명 및 장점**

1.  서버가 session을 저장하고 관리할 필요가 없다. client에게 token을 발급하고 client가 준 token이 올바른지만 확인하고 맞는 경우 권한을 줍니다.따라서 사용자 인증에 필요한 모든 정보는 토큰 자체에 포함하기때문에 별도의 인증 저장소가 필요없습니다. session의 경우 서버에 session id를 저장하여 관리합니다. 서버가 많은 경우 session 데이터베이스를 따로 만드는데 session 데이터베이스를 관리하는 과정이 복잡하고 db에 부하가 올수 있습니다.
2.  토큰을 기반으로 하는 다른 인증 시스템에 접근이 가능하다. google, facebook도 jwt인증 방식을 사용합니다. 페이스북,네이버등의 서비스를 통해 로그인할때 토큰에서 사용자의 정보를 선택적으로 가져올 수 있습니다.token 기반이기 때문에 secret key를 통해 token을 hash하여 암호화 하기때문에 secret key는 최대 한시간에서 몇분 마다 새로 바꾸도록 코딩하는게 좋습니다. token의 보안에 대해서 생각을 해야합니다.
3.  많은 프로그래밍 언어에서 지원됩니다.

## **😀 완성된 화면 **

[##_Image|kage@evZcwo/btqZqpN7erc/5xK0rhFX73YZbe374IVaIk/img.png|alignCenter|data-origin-width="0" data-origin-height="0" data-ke-mobilestyle="widthContent"|[Game Tree] main.html||_##]

[##_Image|kage@mKyYA/btqZoyE3cDa/pkshsP9wShPffHUCQzHyDK/img.png|alignCenter|data-origin-width="0" data-origin-height="0" data-ke-mobilestyle="widthContent"|[Game Tree] login.html||_##]

[##_Image|kage@2XYRQ/btqZpfL2fhW/4UhZjfE57GP2ZaEH7LgCKk/img.png|alignCenter|data-origin-width="0" data-origin-height="0" data-ke-mobilestyle="widthContent"|[Game Tree] register.html||_##]

회원가입을 할 수 있는 페이지입니다. 아이디와 비밀번호를 맞게 생성하시려면 규칙에 따라서 만들어주셔야 합니다.

[##_Image|kage@coOKmK/btqZn0V6Adb/bXm8Jj2MkJ31czmNuJT4k0/img.png|alignCenter|data-origin-width="0" data-origin-height="0" data-ke-mobilestyle="widthContent"|animate css를 사용해서 통통 튀기게 구현했습니다||_##]

로그인시, 로그아웃 버튼과 이름이 출력되게 했으며, 통통 튀는 애니메이션을 넣었습니다.  그리고 저 이름을 클릭하면

회원정보 수정 페이지로 넘어간답니다.

[##_Image|kage@bCgZkY/btqZtAn5lVu/TT19nJ7JCFnObuUiikh1t1/img.png|alignCenter|data-origin-width="0" data-origin-height="0" data-ke-mobilestyle="widthContent"|로그인하면 html 화면에 글쓰기 버튼이 생깁니다.||_##]

추천하기 버튼을 누르면 해당 게임 Card를 추천하고 앞에서부터 추천이 많은 순으로 게임 Card를 정렬해 줍니다!

또한 게임 이름을 클릭하면 그 게임의 공식사이트로 갈 수 있습니다.

[##_Image|kage@xSvRG/btqZyu1VMcM/kIBObVlSmLTjsA2Ji4E7k0/img.png|alignCenter|data-origin-width="0" data-origin-height="0" data-ke-mobilestyle="widthContent"|글쓰기 버튼을 누르면 짜잔! 게임 소개하기 버튼이 나타납니다!||_##]

게임 소개하기 버튼을 누르면 이렇게 게임 제목과 소개글을 작성할 수 있고, 네이버에서 크롤링해서 각종 태그 및 정보를 가지고 옵니다. 네이버에서 크롤링하다보니 롤이라고 검색하던 리그오브레전드라고 검색하던 똑같은 결과값을 보여줘서 편하더라고요. 팀원분의 아이디어가 돋보이는 부분이랍니다.

[##_Image|kage@KmdWm/btqZBdyQEiA/yazsCh5SjzPY0amjMkcw3k/img.png|alignCenter|data-origin-width="0" data-origin-height="0" data-ke-mobilestyle="widthContent"|작성이 완료되면 톱니바퀴가 돌아가고, ajax 호출이 끝나면 이쁜 팝업이 뜹니다. 짜쟌~||_##]

부트스트랩의 디자인을 살짝 바꿔서 모달창을 만들었습니다. 이러니까 뭔가 있어보이는 페이지 같네요.

[##_Image|kage@UTL8r/btqZtAaxtrk/sQb89uDHDKfkhK7Bp7Smwk/img.png|alignCenter|data-origin-width="0" data-origin-height="0" data-ke-mobilestyle="widthContent"|[Game Tree] mypage.html||_##]

수정하기 버튼을 누르면 비밀번호를 수정할 수 있는 페이지로 갈 수 있습니다.

---

## **😀 배운점**

**flask로 서버를 만들고 pymongo로 데이터베이스를 만들어서 웹사이트를 만드는게 처음이라서 걱정이 많았는데, 생각보다 훨씬 더 잘 만들어져서 기분이 좋습니다. 서버 사이드 렌더링이 뭔지 정확하게 감이 안잡힌 상태로 기능을 만들었다가, 막판에 jinja를 사용해서 서버 사이드 렌더링 작업을 한 것, blueprint와 jinja import를 사용해서 열심히 파일 구조 만들고 파일 정리한 것, css 애니메이션 효과를 어떻게 쉽게 줄 수 있을까 고민하던 차에 찾아낸 animate.css 등....**

**배운 것이 너무 많아서 적을 수가 없네요. 앞으로의 프로젝트에서는 또 어떤 것을 배울지 너무 기대가 됩니다!**

## **😙 느낀점**

**딱 한번 프로젝트 했을 뿐인데 요만큼만 알았던 제가 Lv Up을 한게 느껴집니다.(우오오!!)**

**정말 새벽까지 열심히 만들었기에 더 그런 느낌이 듭니다.**

**다음에는 위의 지식을 활용해서 더 다양한 기능을 넣은 웹사이트를 만들어 봐야겠어요!**

## **😭 아쉬웠던 점**

**바보같이 로그인 api의 코드를 다른 걸로 바꾸고 사용하는 바람에 불필요하게 api 접근을 하게 만들어버렸습니다. 그리고 서버 사이드 렌더링 개념을 정확하게 숙지 하지 않은 상태에서 기능을 구현해버리는 바람에 막판에 재작업을 해버렸습니다....**

**다음에는 절대 이런 실수 안 할 것 같네요. 정말 고생 너무 했어요 이것 때문에 ㅠㅠ**
