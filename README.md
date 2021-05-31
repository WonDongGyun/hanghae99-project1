# hanghae99-project1

[**[GameTree에 오신 여러분을 환영합니다!]**](https://tristy.tistory.com/)  
  
  
프로젝트 개요
-------------  
<ul style="list-style-type: disc;" data-ke-list-type="disc">
<li><b>진행 날짜 - 2021.03.01 ~ 2021.03.04</b></li>
<li><b>목적 - 처음으로 배정된 팀원들과, 사전과제에서 공부한 지식을 바탕으로 프로젝트를 완성하기</b></li>
<li><b>필수 포함 사항</b></li>
</ul>
<p><b>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;ㄴ <span style="color: #333333;">쿠키/세션 방식으로 로그인을 구현하고 &rarr; JWT 인증 방식으로 바꿔보기</span></b></p>
<p><b>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;ㄴ Jinja2 템플릿 엔진을 이용한 서버사이드 렌더링</b><b></b></p>
<p>&nbsp;</p>
<hr contenteditable="false" data-ke-type="horizontalRule" data-ke-style="style7" />  
  

<br/>
<br/>

  
사용한 패키지
-------------  
- beautifulsoup4  
  > HTML과 XML문서를 파싱하기위한 파이썬 패키지 
- requests  
  > HTTP 요청을 간단하고 인간 친화적으로 만드는 파이썬 패키지
- pymongo  
  > 비관계형 데이터베이스인 MongoDB를 파이썬에서 사용할 수 있게 해주는 패키지
- Flask  
  > 웹 어플리케이션 개발을 위한 웹 프레임워크인 Flask를 사용할 수 있게 해주는 패키지
- Flask-JWT-Extended  
  > Flask에서 Jwt 인증방식을 사용할 수 있게 해주는 패키지
  

<br/>
<br/>

  
사용한 기술
-------------
1. BluePrint
2. jinja
3. jwt
4. ssr
5. animate CSS


<br/>
<br/>



BluePrint
-------------

<br/>

블루 프린트는 다음과 같은 장점이 있습니다.

- 어플리케이션을 블루프린트의 집합으로 고려합니다. 따라서 어플리케이션 객체를 인스턴스화 하고, 브루프린트의 묶음으로 만들 수 있습니다.  
- URL과 서브도메인의 파라미터 또한 블루프린트의 공통 뷰 인자가 됩니다.  
- 블루프린트를 사용해 다양한 유틸리티를 제공합니다. 어플리케이션과 뷰 함수를 구현하지 않아도 됩니다.  

<br/>

쉽게 말하면, 하나의 .py 파일에 모든 api를 만들기에는 코드가 너무 복잡해집니다.  
따라서 블루프린트라는 기능을 사용해서 경로를 묶고, 코드를 분리해서 좀 더 편리한 작업 환경을 만들 수 있습니다.  

<p align="center"> <img src=https://user-images.githubusercontent.com/52685665/112305146-b3fa7d00-8ce1-11eb-9b29-db8c5566b153.png> </p>

<br/>

예를 들어, 위 그림에서 login, register, write, main, mypage 기능을 담당하는 api들을 블루프린터를 사용해 분리하였습니다.  
이처럼 파일 구조를 잡아두면, 협업을 할 때 편하게 작업 구역을 나눌 수 있습니다.  

<br/>

만약, templates/login 에 존재하는 login.py의 기능을 사용하고 싶다면, 밑의 코드처럼 이미 선언된 블루프린터를 가져오면 됩니다.  

<br/>

``` python
from templates.login.login import login_blueprint
app.register_blueprint(login_blueprint)
```

<br/>

login.py에서 블루프린터로 설정해서, 다른 파일에서 참조하게 만들려면 밑의 코드처럼 선언해주시면 됩니다.  

<br/>

``` python
from flask import Flask, Blueprint
login_blueprint = Blueprint('login', __name__)

@login_blueprint.route('/login', methods=['POST'])
```

<br/>

<p align="center"> <img src=https://user-images.githubusercontent.com/52685665/112305989-a98cb300-8ce2-11eb-872c-3866b05f85e0.png> </p>

<br/>
<br/>


Jinja && SSR  && include
-------------

<br/>

SSR(Server Side Rendering)

<br/>

``` bash
완성된 페이지의 형태로 응답되기 때문에 검색엔진에 최적화되어 있습니다.  
전통적인 웹 어플리케이션의 경우 SSR 방식을 사용합니다.  

클라이언트 사이드 랜더링의 경우 서버는 Json 파일만 보내고 자바 스크립트가 Html을 그리는 역할을 담당하기에 초기 구동속도가 느립니다.  
SSR을 사용하면 첫 랜더링된 Html 파일을 클라이언트에게 전달해주기 때문에 초기 로딩 속도를 많이 줄일 수 있습니다.
```  

<br/>

Jinja는 Python 프로그래밍 언어를 위한 웹 템플릿 엔진입니다. Jinja에서 이런 SSR 방식의 기능을 구현할 수 있습니다.  
밑의 코드는 이 프로젝트에서 main 화면의 Card를 jinja SSR 방식을 사용해서 만든 코드입니다.  
{% 구문을 사용해서 html 파일에서 python을 사용할 수 있습니다.  

<br/>

<p align="center"> <img src=https://user-images.githubusercontent.com/52685665/112314065-ed37ea80-8ceb-11eb-8f03-29b23781b183.png> </p>

<br/>

Jinja에서는 include와 extends를 지원합니다.  
이 프로젝트는 include 기능을 활용하여 만들어 졌습니다.  
  
include 혹은 extends를 활용하면, html에서 공통적인 부분만 따로 분리하여 다른 html로 만들고 가져다 사용할 수 있습니다.  
예를 들어, main.html에서 상단 부분에 include를 선언해 사진과 같은 엄청난 양의 html 코드를 가져다 사용했습니다.  

<br/>

``` python
{% include './common/head.html' %}
``` 

<br/>

<p align="center"> <img src=https://user-images.githubusercontent.com/52685665/112315131-2755bc00-8ced-11eb-832b-61ccd52c1039.png> </p>

<br/>
<br/>

animate.css
-------------

<br/>

시간은 얼마 안남았는데, 쉽고 빠르게 애니메이션 CSS를 적용하려면 어떻게 해야할까요?  
그런 사람들을 위해 animate.css가 있습니다!!  

<br/>

[공식 홈페이지](https://animate.style/)

<br/>
<br/>

jwt
-------------

<br/>

JWT(Json Web Tokens)는 서버가 session을 저장하고 관리할 필요가 없이, client에게 token을 발급하고 clien가 준 token이  
맞는지만 확인합니다. 맞다면 권한을 할당해줍니다.  
  
사용자 인증에 필요한 모든 정보는 토큰 자체에 포함하기 때문에 별도의 인증 저장소가 필요없습니다.  
  
또한 토큰을 기반으로 하는 다른 인증 시스템에도 접근 가능합니다. 예를 들어 google, facebook 등이 있습니다.  
token 기반이기 때문에 secret key를 통해 token을 hash 암호화 하여 몇 분 마다 새로 바꾸도록 코딩하는 것이 좋습니다.  
  
이 프로젝트에서는 flask_jwt_extended를 활용한 간단한 jwt 로그인 방식을 사용하였습니다.  

<br/>

<p align="center"> <img src=https://user-images.githubusercontent.com/52685665/112317048-07bf9300-8cef-11eb-8cea-85d7b37dce1d.png> </p>

<br/>
<br/>






프로젝트 소감
-------------
<p>&nbsp;</p>
<h2 data-ke-size="size26"><span style="background-color: #c0d1e7;"><b>😀 배운점</b></span></h2>
<p><b>flask로 서버를 만들고 pymongo로 데이터베이스를 만들어서 웹사이트를 만드는게 처음이라서 걱정이 많았는데, 생각보다 훨씬 더 잘 만들어져서 기분이 좋습니다. 서버 사이드 렌더링이 뭔지 정확하게 감이 안잡힌 상태로 기능을 만들었다가, 막판에 jinja를 사용해서 서버 사이드 렌더링 작업을 한 것, blueprint와 jinja import를 사용해서 열심히 파일 구조 만들고 파일 정리한 것, css 애니메이션 효과를 어떻게 쉽게 줄 수 있을까 고민하던 차에 찾아낸 animate.css 등....</b></p>
<p>&nbsp;</p>
<p><b>배운 것이 너무 많아서 적을 수가 없네요. 앞으로의 프로젝트에서는 또 어떤 것을 배울지 너무 기대가 됩니다!</b></p>
<p>&nbsp;</p>
<h2 data-ke-size="size26"><span style="background-color: #c0d1e7;"><b>😙&nbsp;느낀점</b></span></h2>
<p><b>딱 한번 프로젝트 했을 뿐인데 요만큼만 알았던 제가 Lv Up을 한게 느껴집니다.(우오오!!)</b></p>
<p><b>정말 새벽까지 열심히 만들었기에 더 그런 느낌이 듭니다.</b></p>
<p><b><span style="color: #333333;">다음에는 위의 지식을 활용해서 더 다양한 기능을 넣은 웹사이트를 만들어 봐야겠어요!</span></b></p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<h2 data-ke-size="size26"><span style="background-color: #c0d1e7;"><b>😭 아쉬웠던 점</b></span></h2>
<p><b>바보같이 로그인 api의 코드를 다른 걸로 바꾸고 사용하는 바람에 불필요하게 api 접근을 하게 만들어버렸습니다. 그리고 서버 사이드 렌더링 개념을 정확하게 숙지 하지 않은 상태에서 기능을 구현해버리는 바람에 막판에 재작업을 해버렸습니다....</b></p>
<p><b>다음에는 절대 이런 실수 안 할 것 같네요. 정말 고생 너무 했어요 이것 때문에 ㅠㅠ</b></p>
