# Codable


1. What is Codable <br>
Swift4에 새롭게 추가된 프로토콜로, JSON 데이터를 간편하고 쉽게 Encoding/Decoding 할 수 있게된다.<br>
Codable을 사용하면 직접 다루거나 라이브러리를 사용하는 것보다 간편하게 JSON 데이터를 다룰 수 있다. <br>
![Alt text](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fcd5Lbp%2FbtqOH8O793R%2FShTtajem0k4u3CkArIt3o1%2Fimg.png) <br>
Codable은 Decodable 과 Encodable로 이루어져 있다고 typealias로 정의되어 있다. <br>
    * What is Decodable and Encodable <br>
        ``` swift
        protocol Decodable

        protocol Encodable
        ```

        
