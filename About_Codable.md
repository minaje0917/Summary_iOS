# Codable


1. What is Codable <br>
Swift4에 새롭게 추가된 프로토콜로, <br>
JSON 데이터를 간편하고 쉽게 Encoding/Decoding 할 수 있게된다.<br>
Codable을 사용하면 직접 다루거나 라이브러리를 사용하는 것보다 간편하게 JSON 데이터를 다룰 수 있다. <br>
![Alt text](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fcd5Lbp%2FbtqOH8O793R%2FShTtajem0k4u3CkArIt3o1%2Fimg.png) <br>
Codable은 Decodable 과 Encodable로 이루어져 있다고 typealias로 정의되어 있다. <br>
    * What is Decodable and Encodable <br>
        ``` swift
        protocol Decodable

        protocol Encodable
        ```
        Encodable & Decodable 프로토콜을 준수하는 프로토콜이다. <br>
        Struct, Class, Enum 모두 Codable을 채택할 수 있다. <br>
<br>

2. Codable을 이용한 Encoding <br>
    1. What is Encoding <br>
        내가 원하는 struct, class, enum 등등의 인스턴스를 JSON 형태의 Data로 만들어주는 것. <br>
        
        * Example <br>
        Encoding 할 데이터를 Struct로 하나 만들고 sodeul이라는 구조체 변수를 생성했다. <br>
            ``` swift
            struct Human: Codable {
                var name: String
                var age: Int
            }

            let sodeul: Human = .init(name: "minaje", age: 18)
            ```
            여기서 중요한 것은 Codable을 이용해서 Encoding 하고 싶을 경우, <br>
            반드시 Codable이라는 Protocol을 준수하고 있어야한다. <br>
            이제 sodeul이라는 구조체 변수를 Encoding 해보겠다.
            ``` swift
            let data = try? JSONEncoder().encode(sodeul)
            ```
            이렇게 한 줄로 끝난다. <br>
            JSONEncoder 클래스에다가 encode 메서드를 호출해주는데, <br>
            이때 codable을 준수하는 구조체 타입인 sodeul을 넣어주면 <br>
            JSON 데이터를 알아서 만들어준다. <br>

            이 encode 함수를 좀 더 자세히 보자면 <br>
            ![Alt text](https://blog.kakaocdn.net/dn/wBuPQ/btqOvR8YEuy/OjkDcMEtHwVMRRgflczNC1/img.png) <br>
            Generic으로 선언되어 있는데, 이 T는 Encodable이라는 프로토콜을 준수하고 있어야만 <br>
            이 encode라는 메서드를 사용할 수 있다. <br>
            우리는 Codable(Encadable + Decodable)을 사용했기 때문에 <br>
            이 encode라는 메소드를 사용할 수 있다. <br>
            또한 throws라고 되어있는 것처럼, Encoding 중 에러가 발생할 수 있기 때문에 <br>
            반드시 try와 같이 써주어야한다. <br>
            만약, Codable 프로토콜을 채택하지 않고 사용하려 한다면 에러가 발생한다. <br>
<br>

3. Codable을 이용한 Decoding
    1. What is Decoding <br>
        JSON 형태의 Data를 struct, class, enum 등의 인스턴스에 자동으로 파싱해주는 것. 
        <br>
        * Example <br>
        Codable을 준수하는 구조체가 있다. <br>
            ``` swift 
            struct Human: Codable {
                var name: String
                var age: Int
            }
            ```
            
