# Delegate Pattern

1. Delegate Pattern <br>
Delegate Pattern은 delegate, 즉 위임자를 갖고 있는 객체가 다른 객체에게 자신의 일을 위임하는 형태의 디자인 패턴이다. <br>

<br>

2. Example <br>
우리는 파티를 준비하려고 한다.<br>
파티를 하기 위해서는 음식과 노래가 필요하다. <br>
파티 책임자는 파티 준비자들에게 음식과 노래를 준비할 것을 주문(위임)한다.<br>
파티 준비자는 그들의 주문에 따르고, 각자 음식과 노래를 준비한다. <br>
![Alt text](https://velog.velcdn.com/images%2Fzooneon%2Fpost%2F05116dc9-6449-47f9-adb7-4587f5ff4ebc%2Fimage.png)
PrepareParty 프로토콜에는 파티를 준비하기 위한 일들을 작성한다. <br>
![Alt text](https://velog.velcdn.com/images%2Fzooneon%2Fpost%2Fa392c8b8-e622-4552-a4e3-f99e8463d718%2Fimage.png)
책임자 역할을 할 PartyDirector 클래스에는 일을 위임할 delegate 변수와 일을 시키는 order() 함수를 만들어준다. <br>
delegate 변수의 자료형으로 PrepareParty 프로토콜을 사용하므로써 이 delegate 변수, 즉 위임자가 파티를 준비하기 위한 일들을 시킬 수 있다.<br>
order() 함수는 delegate변수를 이용하여 음식과 노래를 준비하는 일을 시킬 것이다. <br>
![Alt text](https://velog.velcdn.com/images%2Fzooneon%2Fpost%2F06e9e587-ab4e-46cb-856c-b22ef59c6541%2Fimage.png)
파티를 준비해 줄 두명의 친구들을 만들었다. <br>
두 클래스의 특징을 살펴보면 클래스명의 뒤에 프로토콜을 명시하여 PrepareParty 프로토콜을 준수하도록 한다. <br>
이를 통해 두 클래스는 파티를 준비하기 위한 일들을 처리한다는 보장을 받는다. <br>
그리고 이니셜라이저 부분을 살펴보면 중요한 코드를 발견할 수 있다. <br>
![Alt text](https://velog.velcdn.com/images%2Fzooneon%2Fpost%2F9c8ca380-4b4b-457a-9c11-58b54c1b973d%2Fimage.png)<br>
이 코드를 우리의 예시를 통해 설명해보자면, <br>
파티 책임자가 시키는 일을 자신이 처리하겠다고 명시하는 것이다.<br>
즉, 위임자(여기서는 매개변수로 받은 director)의 delegate 변수를 자신으로 설정함으로써,<br>
자신이 위임자 일을 대신 처리하겠다는 의미이다. <br>
한 마디로 위임자의 delegate 변수와 자신을 연결해주는 코드이다.<br>
의미를 이해했다면 이 코드가 어떻게 가능한지 알아보자. <br>
우리는 delegate 변수를 만들 때 자료형으로 PrepareParty 프로토콜을 설정하였다. <br>
그리고 클래스를 만들 때 PrepareParty 프로토콜을 채택하였는데, 이러면 프로토콜로 형변환이 가능해진다. <br>
즉, 둘은 같은 자료형이므로 저런 코드가 가능해진다. <br>
![Alt text](https://velog.velcdn.com/images%2Fzooneon%2Fpost%2F6804c97d-2dfb-4a90-9110-34bce3d9ac00%2Fimage.png)
객체를 만들어 코드를 실행시켰다. <br>
파티 책임자로 zooneon을 생성하였고, 파티 준비를 도와줄 두 명의 파티준비자를 각각 생성했다. <br>
파티 책임자인 zooneon이 일을 주문하면 준비자들은 각각의 일을 처리한다. <br>
여기서 중요한 점은 zooneon이 파티를 준비시키기만 했고 어떤 음식, 어떤 노래를 준비할 지는 명시하지 않았다. <br>
어떤 것들을 준비할 지는 일을 위임받은 준비자들이 각자의 방식으로 처리한다. <br>
여기서 delegate패턴의 장점이 나오는데, <br>
조금 더 직관적인 프로젝트 예시를 보고 마지막에 정리하자. <br>
<br>

3. Project Example <br>
우리가 볼 예시는 버튼을 클릭하여 UI를 변경하는 간단한 코드이다. <br>
![Alt text](https://velog.velcdn.com/images%2Fzooneon%2Fpost%2F567fe2c7-500f-4e7d-9b9d-7ad276c8fc41%2Fimage.png)
우선 결과를 보면 이러하다. <br>
자! 이제 코드를 뜯어보자.<br>
![Alt text](https://velog.velcdn.com/images%2Fzooneon%2Fpost%2F1023ca4f-958e-4cbc-a0a4-d2ce57517b53%2Fimage.png)
changeUI()함수를 갖는 ChangeUIDelegate 프로토콜을 먼저 만들어 주었다. <br>
그리고 delegate 변수를 선언해주는데, 이 변수의 자료형은 ChangeUIDelegate 프로토콜로 선언했다.<br>
이로써 delegate 변수는 일을 위임할 준비가 되었다. <br>
clickButtonTapped() 메서드에는 Second View에서 Click 버튼을 누를 경우 앞서 선언한 delegate변수를 통해 위임 받은 객체에서 delegate()를 실행하도록 하였다.<br>
![Alt text](https://velog.velcdn.com/images%2Fzooneon%2Fpost%2Ff612cc07-2720-4708-8e54-01af0a276f14%2Fimage.png)
First View의 Next 버튼에는 nextButtonTapped() 메서드를 만들어주었다. <br>
nextButtonTapped() 메서드에는 Second View를 찾아서 보여주고 Second View의 delegate 변수와 연결해주는 코드가있다. <br>
앞서 설명했듯이, FirstViewController가 ChangeUIDelegate프로토콜을 채택했기 때문에 형변환이 가능하여 self를 사용하여 연결해주었다. <br>
ChangeUIDelegate를 채택한 FristViewController에는 위임자가 메소드를 호출하였을 때 (위의 경우에는 Second View에서 Click버튼을 누른 경우) 실행할 changeUI()함수를 작성해주어야한다.<br>
이렇게 작성한 함수를 통해 Second View에서 Click 버튼을 눌어 일을 시키면 First View에서 그 일을 대신 수행하는 것이다. <br>
여기서 Second View의 위임자는 일을 시키기만 할 뿐, 어떤 일을 하는지에 대한 구체적인 내용은 모른다.<br>
이게 Delegate 패턴의 장점이다. <br>
<br>

4. Delegate Pattern을 사용하는 이유 <br>
    위에 예제들에서 위임자는 그저 일을 시킬 뿐, 일을 어떻게 처리하는지는 모른다. <br>
    일을 처리하는 방법은 그 일을 수행하는 객체에 구현되어있다. <br>
    이렇게 작성하면 코드를 재사용하고, 유지보수하기 쉬워진다. <br>
    어떤 일을 해야하는지를 정해놓기만 하고, 상황에 맞는 코드를 작성하면된다. <br>
    예를 들어 우리가 어떤 작업을 처리해야 하는데, 동일한 작업임에도 불구하고 객체마다 다른 내용을 처리해야한다고 생각해보자. <br>
    이럴 경우 동일한 작업에 대해서는 함수를 전달하기만 하고, 각각의 내용은 전달받은 객체에서 처리하기만 하면 된다. <br>
    또한 작업을 전달할 때 공통된 부분을 제외하고 처리해야하는 부분만 전달하여 처리할 수도 있다. <br>


출처 : https://velog.io/@zooneon/Delegate-%ED%8C%A8%ED%84%B4%EC%9D%B4%EB%9E%80-%EB%AC%B4%EC%97%87%EC%9D%BC%EA%B9%8Cß