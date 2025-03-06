---
생성일자: Invalid date
작성자: 안정흠
주차: 2주차
---
## KeyPath

SwiftUI 에서 List에서 사용해보고, Combine에서도 `assign` 메서드에서 사용을 했었던 KeyPath를 알아보자

  

Swift4!! 에 도입된 기능!!

객체의 프로퍼티나 서브스크립트에 대한 경로를 type-safe하게 참조하는 기능

  

컴파일 타임에 프로퍼티에 접근하거나 수정할 수있고, 코드 안전성과 가독성을 높여준다.

```Swift
\<\#typename#>.<\#path#>
```

KeyPath는 역슬래쉬 타입이름.프로퍼티 와 같은 형태로 사용된다.

```Swift
struct A { 
    var value: Int = 10 
}
class Person {
    var name: String = "NAME"
}

let a1 = A()
print(a1[keyPath: \.value])

let a2 = A()
let path = \A.value 
print(a2[keyPath: path]) // 10

let person = Person()
print(person[keyPath: \.name])
```

  

**KeyPath의 특징**

- 타입 안정성 - 컴파일 타임에 타입검사가 이뤄져 런타임 오류를 줄일 수 있다.
- 읽기, 쓰기 가능 - 아무렇게나 다 가능!! 이건 아니고, KeyPath로 사용한 해당 객체의 프로퍼티가 변경이 가능하면 KeyPath가 `WriteableKeyPath` 타입으로 저장되고, 아니면 그냥 읽기만 가능한 기본 `KeyPath` 타입으로 저장된다.
- 여러 타입이 있지만, 그냥 사용할 객체의 KeyPath 타입 생략하고 넣어주면 알아서 컴파일러가 추론해준다. 하지만 알긴 해야겠죠
    - `KeyPath` - 읽기만 가능
    - `WritableKeyPath` - 읽고 쓰기 가능
    - `ReferenceWritableKeyPath` - 읽고 쓰기 (참조타입에서)

```Swift
struct A { 
    var value: Int = 10 
}
var a = A()
// 직접 타입을 이렇게 지정할수도 있음
// <KeyPath를 사용할 객체, 반환할 타입>
let writablePath: WritableKeyPath<A, Int> = \A.value 
a[keyPath: writablePath] = 99
print(a[keyPath: \.value])
```

위 코드처럼 타입을 명시해서 사용할 수 있기는 한디.. 객체의 프로퍼티가 수정 불가능할때는 오류가 날것임.  
KeyPath가 불가능을 가능으로 만드는것은 아니다.  

  

이에 대한 자세한 설명은 링크에 블로그 글을 참고!! 정말 상세히 정리해주셨음 (나는 그냥 간단요약만..)

[https://0urtrees.tistory.com/362](https://0urtrees.tistory.com/362)

[https://eunjin3786.tistory.com/590](https://eunjin3786.tistory.com/590)

### KeyPath를 다양하게 사용하는 예제

타입이 Hashable인 경우에는 subscript를 keyPath에서도 사용가능

```Swift
let temp = ["a", "b", "c"]
print(temp[keyPath: \[String].[1]])
```

optional chaining, forced unwrapping을 사용가능.

```Swift
let temp = ["a", "b", "c"]
print("Count: \(temp[keyPath: \[String].first?.count)")
```

클로저에서도 KeyPath 사용가능 (EX - (Type) → Value 인 경우)

```Swift
struct Task {
    var description: String
    var completed: Bool
}
var toDoList = [
    Task(description: "Practice ping-pong.", completed: false),
    Task(description: "Buy a pirate costume.", completed: true),
    Task(description: "Visit Boston in the Fall.", completed: false),
]
let descriptions = toDoList.filter(\.completed).map(\.description)
print(descriptions)
```

### 문제점

**KeyPath는 Static member를 참조할 수 없다!!**

  

KeyPath를 알아보다 KVC, KVO라는것도 알게됐는데, 이것도 뭔가 비슷하게 KeyPath를 사용하는거 같아서 정리해봤다.

## KVC (Key Value Coding)

```Swift
class A: NSObject {
    @objc var value: Int = 0
}

let a = A()
a.setValue(5, forKey: "value")
if let value = a.value(forKey: "value") as? Int {
    print(value) // 5
}
```

문자열 키를 사용해서 객체 프로퍼티에 접근하고 수정할 수 있음.

런타임에 프로퍼티 이름을 동적으로 결정해야 할 때 유용하다.

  

KVC는 Obj-C 런타임에 의존하므로 NSObject를 상속해야하고, 프로퍼티 앞에 @objc 를 붙여서 사용

주로 Notification, UserDefaults에서 자주 사용해봤을것이다.

  

하지만 Swift에서는 타입 안정성과 컴파일 타임 검사를 선호하기에.. 이런 메커니즘은 최소화 하는걸 권장.. 한다는데요..

## KVO (Key Value Observing)

```Swift
class A: NSObject {
    @objc dynamic var value: Int = 0
}

let a = A()
var observation: NSKeyValueObservation? = a
    .observe(\.value, options: [.new, .old]) { old, new in
    if let newValue = new.newValue {
        print("\(newValue) 로 변경")
    }
}
a.value = 5 // 5 로 변경
observation?.invalidate() // 옵저버를 해제
observation = nil // 메모리 해제
```

KVO는 객체의 특정 프로퍼티 변경을 관찰하고, 변경이 발생할 때 통지를 받는 매커니즘.

  

KVO 역시 Obj-C 런타임에 의존하고, NSObject를 상속하고 프로퍼티에 `@objc dynamic` 키워드가 붙어야한다.

  

KVC와 다르게 `dynamic` 이 붙는 이유는 동적으로 프로퍼티의 변경을 관찰하고 반응할 수 있게 하기 위한 키워드라 보면 된다.

  

  

NotificationCenter에 Observer를 만드는것과 유사하다고 생각된다.

비슷한 매커니즘으로 NotificationCenter, Delegate 패턴이 있는데 이 차이는 표로 정리

![[스크린샷_2025-02-22_16.16.31.png]]

  

Delegate패턴은 **UI이벤트 처리, 데이터소스 위임등 특정 객체에게 동작을 위임할때 사용하고,**

Notification은 **로그인 상태변경, 네트워크 상태변경 등 여러 객체가 이벤트를 동시에 받아야할 때 사용하고,**

KVO는 **모델 값 변경 감지와 같이 속성이 변경될 때 자동으로 감지해야할때 사용하는것이 좋다.**

# 결론!

**KeyPath 와 KVC/KVO는 밀접한 연관이 있지만, 차이점을 정리해보자**

- KVC/KVO는 Obj-C 런타임에 의존함 (그래서 NSObject, @objc 등 키워드를 사용해야 쓸 수 있음)
- KeyPath는 Swift 기능으로 위와같은 의존성 없음!! 그냥 사용 가능!
- KVC는 문자열을 사용해 프로퍼티에 접근하므로 런타임 오류 가능성 있음!!
- KeyPath는 컴파일 타임에 타입 검사를 수행하므로 더 안전!!
- KVC/KVO는 런타임에 동적으로 프로퍼티에 접근 또는 관찰하는데 사용됨
- KeyPath는 컴파일 타임에 프로퍼티 경로를 지정해 안전하고 효율적인 코드를 작성하는데 중점을 둔다!!

## Combine에서 말하는 Subscription이란?

1주차 정리때 너무 잘못 생각하고 있었다.

  

**Subscriber는**

- Publisher에 데이터를 수신하는 역할
- Publisher를 구독해 데이터 스트림을 받아 처리함

  

**Subscription은**

- Publisher와 Subscriber간의 연결 담당
- Publisher가 데이터를 생성하고 이를 Subscriber가 수신하는 과정에서 데이터의 흐름을 제어함.
- Subscriber는 Subscription을 통해 구독 수명을 관리할 수 있음.

  

**AnyCancellable은**

- sink를 하면 반환됨.
- AnyCancellable이 Subscription이다!! 는 아니고,  
    Subscription을 관리하고 취소할 수 있는 타입소거형(Type-erased) 취소 객체임.  
    

  

**요약**

Subscription은 Publisher와 Subscriber를 연결하는 중개인 같은 느낌

AnyCancellable은 그 Subscription의 메모리를 가지고있고 그걸 취소해 release 할 수 있음.

## NotificationCenter의 Observer의 Publisher는 왜 Observer를 삭제해도 스트림이 살아있고 Completion이 되지 않는가?

> [!important] notificationCenter는 **이벤트 기반의 무한 스트림 퍼블리셔**이기 때문에 정상적으로 끝났다! 라는 개념 자체가 없다!

먼저 Completion이 호출되지 않는 이유는 간단하다 Observer의 Publisher가 만들어질때

해당 Publisher는 Infinite Stream이란걸 전제로 만들었기 때문에 Completion을 보내는 이벤트가 존재하지 않는다.

  

근데 왜 Infinite Stream이 되는가?

  

이것도 당연한거였다. NotificationCenter의 Observer는 계속해서 (메모리가 해제되기 전까지) 변경사항을 알려야하는 컨셉의 API니까!

  

정도로 이해했습니다…

# Combine 2주차 - Operator

[https://tanaschita.com/20221121-cheatsheet-combine-operators/](https://tanaschita.com/20221121-cheatsheet-combine-operators/)

[https://github.com/JustHm/Timer-CloneApp](https://github.com/JustHm/Timer-CloneApp)

![[/CombineOperatorsCheatSheet-Compact 2.pdf|CombineOperatorsCheatSheet-Compact 2.pdf]]

# RxSwift to Combine Cheatsheet

[https://github.com/CombineCommunity/rxswift-to-combine-cheatsheet](https://github.com/CombineCommunity/rxswift-to-combine-cheatsheet)

## Basics

|   |   |   |
|---|---|---|
||RxSwift|Combine|
|Deployment Target|iOS 8.0+|iOS 13.0+|
|Platforms supported|iOS, macOS, tvOS, watchOS, Linux|iOS, macOS, tvOS, watchOS, UIKit for Mac ¹|
|Spec|Reactive Extensions (ReactiveX)|Reactive Streams (+ adjustments)|
|Framework Consumption|Third-party|First-party (built-in)|
|Maintained by|Open-Source / Community|Apple|
|UI Bindings|RxCocoa|SwiftUI ²|

## Core Components

|   |   |   |
|---|---|---|
|RxSwift|Combine|Notes|
|AnyObserver|AnySubscriber||
|BehaviorRelay|❌|Simple wrapper around BehaviorSubject, could be easily recreated in Combine|
|BehaviorSubject|CurrentValueSubject|This seems to be the type that holds @State under the hood|
|Completable|❌||
|CompositeDisposable|❌||
|ConnectableObservableType|ConnectablePublisher||
|Disposable|Cancellable||
|DisposeBag|A collection of AnyCancellables|Call anyCancellable.store(in: &collection), where collection can be an array, a set, or any other RangeReplaceableCollection|
|Driver|ObservableObject|Both guarantee no failure, but Driver guarantees delivery on Main Thread. In Combine, SwiftUI recreates the entire view hierarachy on the Main Thread, instead.|
|Maybe|Optional.Publisher||
|Observable|Publisher||
|Observer|Subscriber||
|PublishRelay|❌|Simple wrapper around PublishSubject, could be easily recreated in Combine|
|PublishSubject|PassthroughSubject||
|ReplaySubject|❌||
|ScheduledDisposable|❌||
|SchedulerType|Scheduler||
|SerialDisposable|❌||
|Signal|❌||
|Single|Deferred + Future|Future has to be wrapped in a Deferred, or its greedy as opposed to Single's laziness|
|SubjectType|Subject||
|TestScheduler|❌|There doesn't seem to be an existing testing scheduler for Combine code|

## Operators

|   |   |   |   |
|---|---|---|---|
|RxSwift|Combine|Notes|기능 설명|
|amb()|❌|||
|asObservable()|eraseToAnyPublisher()|||
|asObserver()|❌|||
|bind(to:)|`assign(to:on:)`|Assign uses a KeyPath which is really nice and useful. RxSwift needs a Binder / ObserverType to bind to.|특정 변수에 데이터 바인딩 시킴!|
|buffer|buffer|||
|catchError|catch||에러 캐치|
|catchErrorJustReturn|replaceError(with:)||에러발생시 값 변경|
|combineLatest|combineLatest, tryCombineLatest||조합 오퍼레이터|
|compactMap|compactMap, tryCompactMap||array에 nil 제거|
|concat|append, prepend||이어 붙이기|
|concatMap|❌|||
|create|❌|Apple removed AnyPublisher with a closure in Xcode 11 beta 3 :-(||
|debounce|debounce|||
|debug|print||디버깅용 프린트|
|deferred|Deferred|||
|delay|delay||말그대로 delay|
|delaySubscription|❌|||
|dematerialize|❌|||
|distinctUntilChanged|removeDuplicates, tryRemoveDuplicates|||
|do|handleEvents|||
|elementAt|output(at:)|||
|empty|Empty(completeImmediately: true)|||
|enumerated|❌|||
|error|Fail|||
|filter|filter, tryFilter|||
|first|first, tryFirst|||
|flatMap|flatMap|||
|flatMapFirst|❌|||
|flatMapLatest|switchToLatest|||
|from(optional:)|Optional.Publisher(_ output:)|||
|groupBy|❌|||
|ifEmpty(default:)|replaceEmpty(with:)|||
|ifEmpty(switchTo:)|❌|Could be achieved with composition - replaceEmpty(with: publisher).switchToLatest()||
|ignoreElements|ignoreOutput|||
|interval|❌|||
|just|Just|||
|map|map, tryMap|||
|materialize|❌|||
|merge|merge, tryMerge|||
|merge(maxConcurrent:)|flatMap(maxPublishers:)|||
|multicast|multicast|||
|never|Empty(completeImmediately: false)|||
|observeOn|receive(on:)|||
|of|Sequence.publisher|`publisher` property on any `Sequence` or you can use `Publishers.Sequence(sequence:)` directly||
|publish|makeConnectable|||
|range|❌|||
|reduce|reduce, tryReduce|||
|refCount|autoconnect|||
|repeatElement|❌|||
|retry, retry(3)|retry, retry(3)|||
|retryWhen|❌|||
|sample|❌|||
|scan|scan, tryScan|||
|share|share|There’s no replay or scope in Combine. Could be “faked” with multicast.||
|skip(3)|dropFirst(3)|||
|skipUntil|drop(untilOutputFrom:)|||
|skipWhile|drop(while:), tryDrop(while:)|||
|startWith|prepend|||
|subscribe|sink|||
|subscribeOn|subscribe(on:)|RxSwift uses Schedulers. Combine uses RunLoop, DispatchQueue, and OperationQueue.||
|take(1)|prefix(1)|||
|takeLast|last|||
|takeUntil|prefix(untilOutputFrom:)|||
|throttle|throttle|||
|timeout|timeout|||
|timer|Timer.publish|||
|toArray()|collect()|||
|window|collect(Publishers.TimeGroupingStrategy)|Combine has a TimeGroupingStrategy.byTimeOrCount that could be used as a window.||
|withLatestFrom|❌|||
|zip|zip|||

[https://eunjin3786.tistory.com/67](https://eunjin3786.tistory.com/67)