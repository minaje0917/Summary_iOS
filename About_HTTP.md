<h1> HTTP 통신 </h1>


1. what is TCP/IP?     
간단하게 인터넷으로 통신하는데 가장 기반이 되는 프로토콜이다.   
대다수의 많은 프로그램들이 TCP를 기반으로한 IP위에서 동작을 하기 때문에 흔히들 묶어서 TCP/IP로 표현한다.    
하지만 TCP와 IP는 계층이 나눠져있으며 역활과 책임이 명확히 다르다.      
    1. IP     
    IP는 Internet Protocol의 약자로써 네트워크상에서 다른 컴퓨터와 구별할 수 있도록 할당되는 주소입니다.     
    그래서 이 주소를 통해 패킷이라는 단위로 데이터를 전송합니다.    
    하지만 IP만 이용해서 통신을 하면 1 2 3 4 5 6 -> 2 6 3 4 1 1 처럼 도착하니 신뢰성과 연결성을 보장하지 못한다.     
    때문에 TCP위에서 IP를 사용한다.     
          
    2. TCP    
    TCP는 Transmission Control Protocol의 약자로써 전송제어 프로토콜 정도로 변역할 수 있습니다.   
    앞서 설명한대로 TCP는 IP와 함께 스이며 데이터의 누락, 순서 등 신뢰성과 속도를 보장하기 위해 사용됩니다.    
    TCP와 IP는 UDP와 달리 연결지향 프로토콜이며 서버와 클라이언트가 통신하는동안 연결을 맺고 있는 상태를 유지합니다.    



2. what is HTTP?   
대량의 정보가 흐르는 곳이라면 언제나 효율적인 교류를 위한 규칙이 존재한다.    
    ``` 
    HTTP란 한 마디로 HTML문서를 주고 받는데 쓰이는 통신프로토콜이며,    
    TCP와 UDP를 사용하여 통신하며 80번 포트를 사용하는 통신프로토콜이다.
    ```
    TCP위에서 동작하지만 TCP와 달리 무상태성 혹은 비연결성이다.     
    때문에 쿠키나 세션을 이용하여 클라이언트의 상태를 관리할 수 있다.
    
3. HTTP의 특징     
* HTTP 메세지는 서버와 클라리언트에 의해 해석된다.
* TCP/IP 를 이용하는 응용프로토콜이다.
* HTTP는 연결상태를 유지하지 않은 비연결성 프로토콜입니다. 클라이언트가 이전에 요청한 내용을 기억하고 있지 않는다 라는 것.    
* 비연결성의 단점을 해결하기 위한 cookie와 Session이 등장했다.
* 비연결성 프로토콜이기 때문에 요청/응답 방식으로 등작한다.
* 도메인 + 자원위치(URL),도메인 + 자원의 식별자(URI)를 통해서 요청을하고, 서버가 요청에 따른 HTML 문서응답을 해줌    
        
4. HTTP 통신과정     
① 클라이언트가 서버에 HTTP Request(요청)을 한다.     
② 서버가 사용자의 요청을 받고 HTTP Response(응답)을 한다.

    1. HTTP Request(요청) 메세지     
    요청은 웹브라우저의 URL을 통해 어느 웹사이트(도메인)의 어느경로에 있는 페이지에 요청할지 나타내는 행위이다. 요청 메세지의 세부사항은 아래와 같다.   
        ``` 
        Request-Line
        *(( general-header | request-header | entity-header ) CRLF)
        CRLF
        [ message-body ]
        ```
        ① Request-Line     
        Request-Line, URL정보, 요청방식(Method), HTTP 버전 제공 정보의 규칙입니다.      
        아래 그림에서는 Request URL, Request Method를 나타내고 있습니다.     
        ![Alt text](https://velog.velcdn.com/images%2Fdoomchit_3%2Fpost%2Ffed43472-01f3-4778-b43e-c206a6606860%2Fhttp-rere4.PNG)     
             
        ②  *(( general-header | request-header | entity-header ) CRLF)     
        헤더정보, 헤더에는 요청하는 클라이언트 PC, 브라우저정보, 사용자언어환경, 쿠키등의 다양한 클라이언트 환경에 대한 정보를 가지고 있다.     
        때문에 헤더영역에 존재하는 데이너틑 보안에 취약하다.     
        ![Alt text](https://velog.velcdn.com/images%2Fdoomchit_3%2Fpost%2F529a78f6-b86f-43dc-8a54-232ee2ff78c4%2Fhttp-rere5.PNG)
              
       ③ CRLF     
       줄바꿈 명령.     
             
       ④ [ message-body ]     
       HTTP 본문영역, 주로 클라이언트가 입력한 데이터를 저장하는 영역이다.     
       입력폼에 입력한 각종 데이터가 Method 방식에 따라 서버로 전달할 때 보안이 강화된 방식으로 message-body에 넣어 전달한다.     
               
    2. HTTP Response(응답) 메세지     
    응답은 HTTP Request를 통해 요청된 정보에 대해 웹서버가 클라이언트에 보내는 응답형식 및 결과를 나타냅니다.     
        ```
        Status-Line
        *(( general-header | response-header | entity-header ) CRLF )
        CRLF
        [ message-body ]
        ````
        ① Status-Line      
        응답 상태정보 표시 라인, HTTP버전정보와 세자리 숫자값(200)과 상태코드 값을 통해 응답결과 및 상태정보를 나타냅니다.    
        ![Alt text](https://velog.velcdn.com/images%2Fdoomchit_3%2Fpost%2F89dbacfc-2a0b-407d-ab1f-7d8509ae78c2%2Fhttp-rere6.PNG)      
             
        ② 응답 헤더정보 제공      
        헤더정보, 각종 서버 및 웹사이트 관련 환경정보를 제공한다.     
        ![Alt text](https://velog.velcdn.com/images%2Fdoomchit_3%2Fpost%2F3f11e3b4-97b0-4e70-af27-84e568c83327%2Fhttp-rere7.PNG)     
                
        ③ [ message-body ]     
        HTTP본문영역, 주로 서버에서 사용자에게 전달되는 HTML소스 및 포함된 데이터를 저장하는 영역이다.    
             
5. HTTP Method      
Method는 클라이언트가 웹서버에게 사용자의 요청의 목적/종류를 알리는 수단이다.      
* GET : 정보검색 ex) 게시판 리스트 불러오기
* POST : 실행 / 저장 ex) 회원가입 / 로그인
* 







자료 참고 : https://velog.io/@doomchit_3/Internet-HTTP-%EA%B0%9C%EB%85%90%EC%B0%A8%EB%A0%B7-IMBETPY     
https://mysterico.tistory.com/29