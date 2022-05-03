# JSON

1. What is JSON <br>
JavaScript Object Notation 의 약자. <br>
객체 속성을 표현하기 위한 방법으로 사용하기 시작한 데이터 구조<br>
JSON의 정의 : 간결하고 쉽게 데이터를 나타내는 방법 중 하나 <br>
 <br>

2. JSON 객체 <br>
"Key" : Value 로 이루어진 데이터의 집합. <br>
Dictionary와 같은 성격이다. <br>
중괄호 { 로 시작해서 중괄호 } 로 끝남. <br>
이 중괄호 사이 Key-Value가 쌍을 이루어 들어가는 것이다. <br>
이때, Key-Value는 : (colon)을 이용해서 다음과 같이 표현. <br>
    ``` JSON 
    {
        "name" : "minaje"
    }
    ```
    만약 Key-Value를 더 추가하고 싶다면, ,(comma)를 이용해서 추가하면 된다. <br>
    ``` JSON
    {
        "name" : "minaje"
        "age" : 18
    }
    ```
    JSON은 Dictionary 성격을 가지고 있기 때문에, Swift에서 이 JSON 객체를 다룰 땐 Dictionary 개열의 자료형을 사용. <br>
    하지만 Dictionary와 달리 Key-Value 쌍이 순서대로 안 되어있어도 상관 없다. <br>
    
    * Key-Value의 타입. <br>
    Key-Value 타입은 미리 지정된 타입만 쓸 수 있다. <br>
    ![Alt text](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FboZJzk%2FbtqO0gnq43c%2FI0SmTMLwBJqXFjMb5q6I4k%2Fimg.png) 
    Value 타입으로 JSON 객체 타입이 된다는 게 무슨 말이냐면.<br>
        ``` JSON
        {
            "name" : "minaje"
            "age" : 18
            "dad" : {
                "name" : "dad"
                "age" : 50
            }
        }
        ```
        이런 식으로 사용되는 것이 JSON 객체이다. <br>
<br>

3. JSON 배열 <br>
JSON 객체가 '사람 한 명'에 대한 정보를 저장하기에는 더할 나위 없이 좋지만. <br>
'여러 명의 사람의 정보'를 데이터로 만들고 싶다면, JSON 배열이 가장 좋다. <br>
JSON 배열은 대괄호[로 시작해 대괄호]로 끝난다. <br>
이 대괄호 사이에 원하는 아이템을 넣어주면 된다. <br>
    ``` JSON
    [
        {
            "name" : "minaje"
            "age" : 18
        }
    ]
    ```
    2명 이상의 데이터를 다루고 싶다면, ,(comma)를 이용해서 나열하면된다. <br>
    ``` JSON
    [
        {
            "name" : "minaje"
            "age" : 18
        },
        {
            "name" : "minjae"
            "age" : 19
        }
    ]
    ```
    이때, 배열 안에 들어가는 아이템의 타입은 매우 다양하다. <br>
    ![Alt text](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcBPO8U%2FbtqOYuM2b5e%2FrdK6nxbs8VHKV4Q26A3ZT1%2Fimg.png) <br>
    배열의 아이템으로 또 JSON 배열이 들어갈 수 있다. <br>
    ``` JSON
    // 정수
    [1, 3, 5, 7, 9]
    
    // 문자열
    ["a", "b", "c", "d", "e"]
    
    //하위에 JSON 배열이 포함된 경우
    [
        ["a", "b", "c", "d", "e"],
        ["A", "B", "C", "D", "E"],
        ["가", "나", "다", "라", "마"]
    ]
    
    //하위에 JSON 객체를 나열한 경우
    [
        {"name" : "Sodeul"},
        {"name" : "Sossam"}
    ]
    ``` 
    물론 JSON 배열을 다룰 때 Swift는 Array 개열의 자료형을 사용. <br>
    배열인 만큼 Index가 중요하기 때문에, JSON Object처럼 순서가 뒤바뀔 일이 없다. <br> 

참고 - https://babbab2.tistory.com/69