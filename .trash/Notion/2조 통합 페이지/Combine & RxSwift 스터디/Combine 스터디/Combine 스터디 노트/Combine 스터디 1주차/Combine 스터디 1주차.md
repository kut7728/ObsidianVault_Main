---
생성일자: Invalid date
작성자: 안정흠
주차: 1주차
---
![[Combine_스터디_Chapter_1_2.pdf]]

## Combine? 사용이유?

> 이벤트 처리 연산자를 결합해 비동기 이벤트 처리를 사용자 정의합니다.
> 
> - apple docs combine 소개글

Combine은 비동기 이벤트 처리를 위한 선언정, 반응형 프레임워크.  
비동기 프로그래밍의 기존 문제를 해결하는것이 목표.  
3가지 주요 타입으로 구성되어 있다.  
**publisher(이벤트 발행) -> operator(이벤트 처리, 조작) -> subscriber(구독)**

시스템 레벨에 통합되어 있고, 재사용성이 좋다.  
비동기 코드에서도 비즈니스 로직에만 집중할 수 있다.  
delegate, closure 등의 방식으로 처리하지 않으니 덜 복잡하고 실수할 가능성이 낮다.  

Timer, NotificationCenter, URLSession등은 이미 Combine을 사용할 수 있게 Publisher가 존재한다.

## Publisher

시간의 흐름에 따라 element를 보내는(emit) 역할 (방출이라고도 함)

### 이벤트 종류

- Output
- Completion - Successfult completion
- Failure - completion with an error

### 특징

- 3가지 이벤트로 모든 종류의 동적 데이터 표현가능
- delegate, completion callback(closure) 등을 주입할 필요없음
- Publisher는 에러 핸들링이 내장되어있음
- Publisher는 2개의 제네릭을 기반으로 구성되어있음
    - Publisher.Output - Value emit
    - Publisher.Failure - 에러 전달, 에러가 발생할 일 없으면 Never 타입으로 정의하면 됌

`Publisher<Int, Never>`와 같이 타입이 선언되면 Output은 Int, Failure는 Never인것.

## Operators

map, filter, reduce 등의 고차함수를 사용해 같거나 새로운 Publisher를 반환하는 메소드.  
Operator들을 체이닝 해서 사용할 수 있기 때문에 유용하다  

### 장점

- Operator들은 독립적이고 조합가능
- 항상 Input&Output을 가지기 때문에 shared state를 피할 수 있음 (data race)
- 비동기 코드가 끼어들어 변경될일이 없음 (독립적인 stream)

## Subscribers

Publisher를 구독해, Publisher로부터 value나 completion event를 전달받아 작업을 처리함.  
Publisher는 명시적으로 Subscriber 가 있어야 값을 발행한다.  

### 기본 내장 Subscribers

- sink - output value, completion을 받을 수 있는 클로저를 제공
- assign - output을 key path를 통해 data model의 property나 UI control에 바로 바인딩 할 수 있음
    - RxSwift의 drive or bind 같은것

### Subscription (잘못된 설명)

### 장점

- Subscription은 비동기 이벤트들의 체인을 커스텀 코드, 에러 핸들링과 함께 한방에 선언 가능
- Full-Combine이면, 앱 전체의 로직을 subscription들로 표현 가능
- Subscription이 한번 선언되고 나면 콜백을 호출할 필요없이 시스템이 다 알아서 해줌

### 메모리 관리

Cancellable 프로토콜을 사용해 메모리를 관리함.  
Subscriber는 Cancellable을 준수하고 있다.  

1. 오브젝트를 메모리에서 해제
2. 모든 subscription은 취소
3. 리소스를 메모리로부터 해제

ViewController 같은 오브젝트에 Subscription을 bind해 dismiss 시 메모리 해제를 할 수있게 만들 수 있음

그 외에도 `[AnyCancellable]` 타입의 프로퍼티를 만들어 Subscription들을 여기에 담아두고, `[AnyCancellable]`이 메모리에서 해제될 때 자동으로 cancel 된다.

![[스크린샷_2025-02-16_22.20.44.png]]

---

여기까지는 Combine의 개념과 주요 3가지 타입의 개념을 알아보았고,  
여기부터 주요 3 타입의 코드를 보면서 이해해보자.  

## Publisher & Subscriber 사용예제

### Notification center 사용

```Swift
// "noti" 라는 이름의 Notification Center observer 생성
let notification = Notification.Name("noti")
// "noti" 라는 이름의 observer의 알림을 관찰하기 위한 publisher 생성
let publisher = NotificationCenter.default.publisher(for: notification, object: nil)
// 생성한 notification center 객체에서 따온 publisher 구독
let subscription = publisher.sink { _ in
	print("Notifivation received from a publisher!")
	// "noti" 에서 새로운 메시지가 발행되면 다음 구문이 출력됌
}
// "noti"에 메시지 보냄
let center = NotificationCenter.default
center.post(name: notification, object: nil)
// 이 구문이 끝난 후 subscription에서 발행된 값을 receive

// 구독 취소 (이 시점 후부터 다시 보내(emit)도 구독은 동작안함 )
subscription.cancel()
```

주석으로 대부분 설명이 되어있지만 cancel만 따로 조금 알아보자면,  
주로 [AnyCancellable] (RxSwift 에서는 DisposeBag)타입을 만들어 구독 후 체이닝으로  
`store(in: &bag)` 과 같은 식으로 저장하는데, subscription에서 직접 `cancel()`을 호출해서 구독을 해제할 수 있다.

직접 호출하지 않을시 deinit 될 때까지 구독유지

### 기본 타입에서 사용

```Swift
var cancelBag = [AnyCancellable]()
let integer = (0...4)

integer.publisher
    .sink { element in
       print("Received \\(element)")
    }
    .store(in: &cancelBag)
```

Swift 기본 타입 역시 publisher를 생성할 수 있다.  
위 코드를 실행해보면 ClosedRange의 element가 차례대로 출력된다.  

마지막에 위에서 설명한대로 `store(in:)`함수에 cancelBag이란 변수를 참조로 주입한게 보이는데,  
이것은 여러개의 subscription을 한곳에서 관리하는 방법 중 하나다.  

---

## 번외

잠시 Publisher를 구독할 때 사용한 sink를 살펴보자.

1. `.sink(receiveValue:)`
2. `.sink(receiveCompletion:, receiveValue:)`

기본적으로 2 개의 sink를 사용할 수 있는데,  
1번의 경우, 스트림에 보내진 값이 있을때 이를 받아서 처리할 클로저를 정의한다.  
2번의 경우, publisher가 complete 됐을때 호출되며 1번과 같이 이를 처리할 클로저를 정의한다.  

```Swift
integer.publisher
	.sink(
		receiveCompletion: {_ in print("Complete")},
		receiveValue: { element in
			print("Received \\(element)")
		}
	)
    .store(in: &cancelBag)
```

completion의 동작을 보고싶으면 이 코드로 바꿔서 실행해보면 된다. (모두 방출하고 마지막에 complete 뜸)

그렇다면 Notification 예제에서 `.cancel()`로 메모리를 해제했고, publisher에 연결된 subscription의 연결이 끊겼으니 completion 즉 완료했습니다~ 라고 떠야겠지? **(X)**

Completion의 경우 completion이 호출되는 경우가 2가지 있다.

1. Publisher가 정상완료 되었을때 `.finished`
2. Error가 방출되었을때

1번의 경우, Just, Future, Publisher.Sequence 등 정해진 값들만 방출하는경우 모두 방출 후 Completion이 호출된다.  
2번의 경우, 에러가 방출되면 그 이후에 completion이 방출됨.  

두 케이스 모두 completion이 방출되면 스트림이 즉시 종료되기 때문에, 그 이후에 어떤값을 방출하려해도 동작 안한다. (새로 만들어야함)

아 진짜 하나만 더 추가하자면, error가 방출되면 그 이후 completion이 방출되고 스트림이 종료되긴하는데  
만약에라도 "에러가 방출되어도 나는 유지하고 싶어요" 라면 몇가지 방법이 있다.  

1. retry(\_:) - 오류가 생겨도 입력받은 횟수만큼 다시 반복함
2. catch(\_:) - 오류가 방출되면 catch에 들어오게 되고 여기서 새로운 스트림을 생성해 반환해주면 유지 가능
3. replaceError(with:) - 오류가 방출되면 이를 기본값으로 변환해 내려줄 수 있는 클로저를 정의해 유지 가능

자세한 사용법은 나중에 Operator 챕터에서 알아보자

> 추가로 NotificationCenter로 생성한 publisher는 completion이 절대 호출안됨  
> infinite stream이기 때문  
> (removeObserver 해도 안됨 그건 그냥 NotiCenter에 observer를 지우는 동작만 하는거지 Combine으로 부터 생성된 publisher에 completion을 보내지 않음)  

---

**구독시 모든 이벤트에 대한 대응을 하고싶다면**

```Swift
publisher
    .handleEvents(
		receiveSubscription: {}, //???????????????
	    receiveOutput: {},
		receiveCompletion: {},
		receiveCancel: {},
	    receiveRequest: {} // ???????????????
)
```

handleEvents 라는 subscription을 사용하면 cancel 시 호출할 클로저를 정의할 수 있고, 뿐만 아니라 모든 Publisher에서 보내는 이벤트 종류의 동작을 정의할 수 있다.

---

```Swift
// 메모리 해제 (이 시점 후부터 다시 보내도 구독은 동작안함 )
subscription.cancel()
// cancel() 호출 후 subscription이 nil인지 확인
print(subscription == nil)// false
//(subscription 자체는 nil이 아님, 단지 구독이 취소된 것)
subscription?.cancel()
subscription = nil
print(subscription == nil) // true (이제 완전히 해제됨)
```

`cancel()`로 subscription을 종료하면 구독 중지 및 스트림도 사라지는 줄 알고 있었는데 그게아니다.

![[스크린샷_2025-02-16_22.15.32.png]]

GPT야 알려줘서 고마워..

**당연하게도 Subscription, Publisher Custom 가능 (이건 기본 개념 사용법을 익힌 후 알아보자)**

---

# 더 알아봐야할것

1. subscription 이 정확히 어떤것인가 (객체?, 스트림&구독 메모리?, 전체적인 흐름?)
2. handleEvents operator 에 들어가는 파라미터가 언제 불려지는것인가
3. 왜 notificationcenter observer는 삭제해도 publisher 스트림이 살아있는가