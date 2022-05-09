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

            let sodeul: Human = .init(name: "Sodeul", age: 26)
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
            서버에서 name과 age가 담긴 JSON 데이터를 준다고 생각해보자. <br>
            ``` swift
            let data = """
            {
                "name" : "Sodeul",
                "age" : 26
            }
            """.data(using: .utf8)!
            ```
            지금은 서버와 작업하는 것이 아니므로 data라는 변수를 서버가 준 JSON 데이터라 생각하자. <br>
            그럼 나는 이 data를 Human이라는 구조체 변수에 Decoding을 하고싶다면 <br>
            ``` swift
            let sodeul = try? JSONDecoder().decode(Human.self, from: data)
            ```
            이렇게 써주면 파싱이 완료된다. <br>
            결과값을 보면 <br>
            ![Alt text](https://blog.kakaocdn.net/dn/bLiz8a/btqOtZNzBYa/qgK0oFloUCDYfUTYX74ovK/img.png) <br>
            Sodeul이라는 객체에 JSON Data 값이 잘 파싱되어있다. <br>
            decode 함수 원형부터 살펴보자. <br>
            ![Alt text](https://blog.kakaocdn.net/dn/m3IbW/btqOuGNICzc/EMDAmjsL3yvlPAJEdQejW1/img.png) <br>
            Encode와 마찬가지로 Generic T는 Decodable을 준수하고 있어야하고, <br>
            Decoding 중 실패할 수 있기때문에 try문을 써줘야한다. <br>
            또한 type 파라미터는 T.Type을 받기 때문에, <br>
            우리가 파싱하고자 하는 클래스 Human의 Type을 써줘야해서 Human.self를 써줘야한다. <br>

            * 파싱이 되는 과정 <br>
            Human 타입의 구조체를 하나 만들고, <br>
            JSON Data의 Key 값과 동일한 이름의 구조체 변수에 value에 값을 파싱한다. <br>
            그리고 파싱된 구조체를 리턴한다. <br>
            좀 더 쉽게 설명하자면, <br>
            ![Alt text](https://blog.kakaocdn.net/dn/NhLQZ/btqOH9AywVs/JXqxxkhcjFRskNVR7tMgg1/img.png)
            이런 식으로 JSON Data의 "Key"값(name,age)가 구조체 변수 이름(name,age)와 동일하면, <br>
            그 변수의 값(name,age)에 Value("Sodeul",26)을 파싱한다. <br>
            따라서 JSON Data의 Key 값은 Codable을 따르는 타입(Human 구조체)의 맴버 이름과 1대1 매칭 되어야만 문제 없이 사용할 수 있다. <br>
            그럼 서버에서 주는 Key값에 무조건 맞춰서 변수명을 사용해야하나? <br>
            Decodable의 특징을 정리해주겠다. <br>

    2. Coding Key <br>
    만약 서버에선 Name 이라는 Key를 사용한다고 치자. <br>
        ``` swift
        struct Human: Codable {
            var name: String
        }
        let data = """
        {
            "Name" : "Sodeul",
        }
        """.data(using .utf8)!
        ```
        근데 변수명은 대문자로 시작하지 않으니까..  <br>
        우리가 name이라고 이름을 바꿔버리면 1대1 매칭이 되지 않기 때문에 <br>
        Decoding Fail로 간주되어, nil로 떨어진다. <br>
        따라서 Key값에 대응하는 이름을 바꿔주고 싶다면, Coding Key라는 프로토콜을 이용해서 <br>
        Key의 이름이 바뀌었다는 걸 명시해줘야한다. <br>
        Coding Key를 준수하는 타입에 enum으로 다음과 같이 명시해줘야한다. <br>
        ``` swift
        struct Human: Codable {
            var name: String

            enum CodingKeys: String, CodingKey {
                case name = "Name"
            }
        }
        ```
    3. 특정 Key-Value가 없이 오는 경우 <br>
        만약 서버에서 데이터를 주는데, <br>
        ``` swift
        struct Human: Codable {
            var name: String
        }

        let data = """
        {
        }
        """.data(using: .utf8)!
        ```
        이렇게 data에 name이라는 Key-Value가 누락되어 아무것도 안 와버려면 <br>
        Codable은 에러가 난다. <br>
        이럴 경우를 대비해서 2가지 처리를 할 수 있다. <br>
        1. Key가 없을 경우를 대비해 직접 Decoding 함수를 작성한다. <br>
        


참고 : https://babbab2.tistory.com/61