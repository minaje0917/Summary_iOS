# MVC Desgin Patten

1. MVC Design Patten이란? <br>
    MVC는 Model - View - Controller의 약자이다.<br>
    MVC는 Model, View, Controller 3개의 component로 나뉜다.<br>
    ![Alt text](https://sochubert.github.io/assets/images/posts/Model-View-ControlMVC-design-pattern.png)<br>
    출처 : https://www.researchgate.net/figure/Model-View-ControlMVC-design-pattern_fig8_330140206<br>
    Model : 화면에 필요한 데이터와 Business Logic을 관리한다<br>
    View : Model이 가진 데이터를 화면으로 보여준다<br>
    Controller : Model과 View 사이의 브릿지 역할을 한다. <br>

2. MVC Design Patten의 하는 일<br>
    View에서 input events를 보내면 Controller는 이것을 받아서 Model에게 요청을 보낸다 <br>
    Model에서 Data나 logic이 있어서 이를 처리해 Controller에 Data를 보낸다.<br> 
    마지막으로 Controller는 이를 받아 해석하고 View에게 관련 부분을 보내고 View에서 User Interface를 처리한다. <br>
    정리 : Model 과 View는 다이렉트로 절대 소통하지 못하고, Controller를 통해서 통신해야만 한다. <br>

3. MVC Design Patten이 중요한 이유<br>
    예를 들어 한국어로 어플을 내었는데, 그것이 유명해져서 중국어, 영어 등으로도 출시해야한다고 가정하자. <br>
    MVC Design Patten을 적용해 앱을 만들었다면, Controller이나 View는 전혀 건드리지 않아도된다.<br> 
    오직 Model부분만 건드리면 간단하게 추가가 가능해진다.<br>
    그래서 MVC에서는  Reusing code에 아주 강력하다 <br>
    게다가 다른 개발자들이 코드를 쉽게 이해 가능하다는 장점도 있다.<br>

4. 예제<br>
Github : https://github.com/minaje0917/Learn_MVC