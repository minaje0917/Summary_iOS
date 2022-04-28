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

3. Socket<br>
한번 연결에 성공하면, 연결이 계속 유지됨(임의로 끊거나 네트워크 사정상 끊기는 것 제외)<br>
따라서, 연속적(실시간)으로 데이터를 받아야하는 경우 사용 (실시간 스트리밍 서버)<br>
또한 양방향 통신이라, Client가 Server에게 데이터를 요청할 수 있고,<br>
Server가 Client에게 데이터를 요청할 수도 있다.<br>

4. HTTP <br>
Client에서 데이터가 필요할 때마다 Server에게 요청하고,<br>
Server는 그 데이터를 응답하고 바로 연결이 종료되는 방식이다. <br> 
이처럼 HTTP통신은 단방향 통신이라, Client만 Server에게 데이터를 요청할 수 있고,<br>
Server는 Client에게 데이터를 요청할 수 없다.<br> 
보통 실시간 서비스를 제외하곤 HTTP형식을 사용한다. <br>
장점 - Server의 부하를 줄여줌! <br>
계속 연결을 맺는 것이 아닌 원하는 요청에 대한 데이터만 던져주고 끊기므로,<br>
Server가 다른 접속들도 원활히 처리할 수 있게됨 <br>

5. HTTP의 구조 <br>
    1. 종류 <br>
        - 라인 : 응답 / 요청 여부, 메세지 전송방식, 상태 정보 <br>
        - 헤더 : 메세지 본문에 대한 메타 정보 <br>
        - 바디 : 보내고자 하는 메세지(데이터) <br>
        * 실제 HTTP 메세지
            ![Alt TEXT](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FK8jQK%2FbtqDF1UBLfv%2FvYeBQuwic6BxWEYc6DGNy1%2Fimg.png)
            출처 : https://ios-development.tistory.com/58?category=894545 <br>
            첫 줄 : 무조건 라인 (GET 방식인 경우는 바디 포함) <br>
            이후 ~'/n'까지 : 헤더<br>
            마지막 줄 : 바디 (GET 방식인 경우는 존재 x) <br>
    2. 라인 <br>
    메세지의 가장 기본 내용인 응답/요청 여부, 메세지 전송 방식, 상태 등이 작성된다.<br> 매우 정형화되어 있고 무조건 한 줄로 작성된다.  <br>        
        ``` 
        POST /userAccount/login HTTP/1.1
        ```
        보통 이런식이다. <br>
        가장 처음에 POST/GET 등의 전송메서드 정의하며 시작한다. <br>
        바로 뒤에 요청에 대한 경로가 나오고, 마지막으로 요청형식에 대한 버전이 나온다. <br>
    3. 헤더 <br>
    메세지 본문에 대한 메타 정보가 들어가있는 부분으로 필요한 만큼 여러 줄로 작성된다. <br>
    길이가 유동적이므로 바디와 구분짓기 위해 한 줄의 공백이 삽입된다. <br>
        ```
        Host: swiftapi.rubypaper.co.kr:2029.
        Content-Type: application/json
        ``` 
        Host란 Key에는, 도메인 및 포트번호가 Value로 오고, <br>
        Content-Type이란 Key에는 메세지 바디의 타입을 나타낸다. <br>
    4. 바디 <br>
    실제로 보내고자 하는 메세지 본문 내용이 들어가는 부분으로 길이가 유동적이다. <br>
    들어가는 메세지 형식은, 헤더의 Content-Type에서 설정한 Type과 일치해야 한다. <br>
    