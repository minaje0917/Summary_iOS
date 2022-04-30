# REST API

REST API(REpresentational State Tranfer)<br>
REST API : REST 아키텍쳐 스타일을 따르는 API <br>
REST : 분산 하이퍼미디어 시스템( 예 : 웹 )을 위한 아키텍쳐 스타일 <br>
아키텍쳐 스타일 : 제약조건의 집합 <br>
#### REST를 구성하는 스타일 
* client-server
* stateless
* cache
* uniform interface
* layerd system
* code-on-demand (optional) <br>


HTTP만 잘 따라도 uniform interface를 제외하고 잘 지킬 수 있다. <br>
#### uniform interface의 제약조건 
* identification of resources( 잘 지켜지고 있음 )
* manipulation of resources through representations( 잘 지켜지고 있음 )
* self-descriptive messages ( 안 지켜지고 있음 )
* hypermedia as the engline of application state (HATEOAS) ( 안 지켜지고 있음 ) <br>
self-descriptive messages : 메세지는 스스로를 설명해야한다.<br>
HATEOAS : 애플리케이션의 상태는 Hyperlink를 이용해 전이되어야한다. <br>

#### uniform interface가 필요한 이유 : 독립적 진화 
* 서버와 클라이언트가 각각 독립적으로 진화한다. 
* 서버의 기능이 변경되어도 클라이언트를 언데이트할 필요가 없다.

참고 | https://www.youtube.com/watch?v=RP_f5dMoHFc&ab_channel=naverd2