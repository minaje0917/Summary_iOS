# lazy var 를 알아보자<br>

1. lazy var란? <br>
    lazy variables는 처음에 변수가 요청되었을 때만 사용자가 지정한 함수를 사용하여 생성된다. <br>

    예시
    ```swift
        import UIKit

        struct InterviewCandidate {

            var isiOS: Bool?
            
            lazy var iOSDeveloper: String = {
                return "I am an iOS Developer"
            }()
            
            lazy var androidDeveloper: String = {
                return "I am an android Developer"
            }()
        }

        var person = InterviewCandidate()
        person.isiOS = true

        if person.isiOS! {
            print(person.androidDeveloper) // I am an android Developer
            // 지금 iOSDeveloper는 nil.
        } else {
            print(person.iOSDeveloper) // I am an iOS Developer
            // 지금 androidDeveloper는 nil.
        }
    ```

2. lazy 변수를 사용하면 얻는 이점
    1. lazy property와 관련된 클로저는 오직 그 프로퍼티를 읽을 때만 실행된다.<br>
    따라서 그 프로퍼티가 잘 사용되지 않는다면 불필요한 할당과 실행을 방지할 수 있다. <br>
    2. lazy property를 stored property의 값으로 체울 수 있다.<br>
    3. lazy 프로퍼티의 클로저안에 self를 사용할 수 있다.<br>

3. lazy rules
    * 사용자는 let과 함께 lazy를 사용할 수 없다.
    * computed propety와 함께 사용될 수 없다. 왜냐하면 computed propety는 computation 블록 안의 코드가 모두 실행되고난 다음에 값을 반환하기 때문이다.
    * lazy를 오직 struct나 class의 맴버로만 사용될 수 있다.
    * lazy 변수는 자동으로 초기화되지 않기 떄문에 thread safe하지 않다.
    * lazy 변수는 처음 request될 때 초기화되고 그 다음에는 그 값을 계속 저장합니다. 따라서 처음 그 값을 계속 유지한다.ㄴ 