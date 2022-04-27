# REST Api

1. API <br>
API : Application Programming Interface의 약자 <br>
응용프로그램에서 사용가능하도록, 운영체제 또는 프로그래밍 언어가 제공하는 기능을 이용해 이를 제어할 수 있도록 만든 인터페이스. <br>

2. REST API <br>
REST(REpresentational State Tranfer)는 HTTP를 기반으로 필요한 자원에 접근하기 위한 방식을 정해놓은 아키텍처이다. <br>
여기서 자원이란 저장된 데이터, 모든 파일, 서비스를 모두 포함한다. <br>

    > REST의 4가지 속성 <br>
        1. 서버에 존재하는 모든 자원은 각 자원당 클라이언트가 바로 접근이 가능한 고유의 URI가 존재한다. <br>
        2. 클라이언트의 요청에 따라 필요한 정보들을 제공하기 때문에 서버에는 세션을 보관할 필요가 없다. <br>
        이를 통해 서비스에 자유도가 높아지고 보다 유연한 아키텍처의 적응이 가능해진다. <br>
        3. HTTP 메소드를 이용한다. 모든 자원은 HTTP의 인터페이스인 GET, POST, PUT, DELETE메소드를 통해 접근된다. <br>
        4. 서비스 내 하나의 자원은 연관된 자원과 연결되어 표현이 가능해야 한다 <br>
        정리 : REST는 HTTP URI를 통해 자원을 명시하고, HTTP Method(GET, POST, PUT, DELETE)를 통해 자원에 접근한다. <br>

3. RESTful <br>
RESTful은 일반적으로 REST라는 아키텍처를 구현한 서비스를 나타내기 위해 사용되는 용어이다. <br>
