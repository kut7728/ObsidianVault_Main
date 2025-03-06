- [[#📋 학습 목표]]
- [[#🔥 4주차 개념 설명]]
    - [[#🍏 함수 (Functions)]]
    - [[#🍏 클로저 (Closures)]]
- [[#📚 4주차 실습]]
    - [[#문제 1. 함수 실습]]
    - [[#문제 2. 클로저 실습]]
- [[#📌 추가적으로 더 공부해 봤어요! ]]
- [[#❓ 이런 질문이 있어요!]]

# 📋 학습 목표

---

- `Swift`의 함수 개념에 대해 이해하고 실습해볼 수 있다.
- `Swift`의 클로저 개념에 대해 이해하고 실습해볼 수 있다.

# 🔥 4주차 개념 설명

---

## 🍏 함수 (Functions)

> [!important] _**Functions**_ **are self-contained chunks of code that perform a specific task. You give a function a name that identifies what it does, and this name is used to “call” the function to perform its task when needed.**<br><br>_==함수 (Functions)==_ ==는 특정 작업을 수행하는 코드 모음 형태입니다. 무슨 동작을 하는지 함수에 특정 이름을 부여할 수 있으며 작업을 수행하기 위해 함수를 "호출" 할 때 사용됩니다.<br><br>==
> 
> [🍎 공식 문서 (The Swift Programming Language, Functions)](https://docs.swift.org/swift-book/documentation/the-swift-programming-language/functions)
> 
> [🍏 공식 문서 번역본 (The Swift Programming Language (한국어), 함수)](https://bbiguduk.gitbook.io/swift/language-guide-1/functions)

> `Swift`가 `Objective-C`에 기반해 만들어진 언어인 동시에 함수형 프로그래밍 언어라고 했던 것을 기억하시나요?
> 
> `Swift`의 함수는 기본적으로 파라미터를 받아 반환 값을 전달하는 형식으로 이루어져 있습니다. 이 부분은 C언어와 유사한 부분인데요! 어떻게 함수를 사용하는지 함께 알아보도록 합시다.

### 🔴 함수 정의하고 호출하기

> 함수를 정의할 때 _`파라미터`_ 라고 알고 있는 함수가 입력으로 받는 하나 이상의 타입으로 된 값을 선택적으로 정의할 수 있습니다. 또한 _`반환 타입`_ 이라고 알고 있는 작업이 완료 되었을 때 함수가 다시 전달하는 값의 타입을 선택적으로 정의할 수 있습니다.
> 
> 위에서 설명했듯이 함수를 정의할 때는 파라미터와 반환 타입을 명시해야 합니다. 예시를 함께 살펴볼까요?

```Swift
func greet(person: String) -> String {
    let greeting = "Hello, " + person + "!"
    return greeting
}
```

> 위 `greet` 함수는 사람의 이름을 입력으로 받아 그 사람의 인사말을 반환합니다.
> 
> 이것을 수행하기 위해 `person` 이라 불리는 `String` 값인 하나의 파라미터와 인사말을 포함한 `String` 반환 타입을 정의해주고 있네요!
> 
> 위 함수를 호출하기 위해서는 어떻게 해야 할까요?

```Swift
print(greet(person: "Anna")) // Prints "Hello, Anna!"
print(greet(person: "Brian")) // Prints "Hello, Brian!"
```

> 파라미터에 `String` 타입의 인자를 넣어 함수를 실행하고, 반환 값으로 각각 `String` 타입의 값을 받아 `print`해주고 있는 것을 볼 수 있습니다.

### 🔴 함수 파라미터와 반환값 알아보기

> 함수의 필수 요소인 `파라미터`와 `반환값`에 대해 조금 더 알아보겠습니다.
> 
> `Swift`에서는 이름이 지정되지 않은 단일 파라미터가 있는 간단한 유틸리티 함수에서 파라미터 이름과 다른 파라미터 옵션이 있는 복잡한 함수에 이르기까지 모든 것을 정의할 수 있어요!
> 
> 예시를 함께 살펴보겠습니다.

```Swift
func sayHelloWorld() -> String {
    return "hello, world"
}

print(sayHelloWorld()) // Prints "hello, world"
```

> 위 함수는 파라미터가 없는 함수로, 빈 소괄호만을 명시해준 후 따로 입력 파라미터에 대한 정의를 요구하지 않습니다. 대신 반환 타입은 `String`이라고 명시해주고 있고, `“hello, world”`라는 `String` 타입의 값을 출력해주고 있네요!
> 
> 그렇다면 파라미터가 여러 개인 경우에는 어떻게 해야할까요?

```Swift
func greet(person: String, alreadyGreeted: Bool) -> String {
    if alreadyGreeted {
        return greetAgain(person: person)
    } else {
        return greet(person: person)
    }
}

print(greet(person: "Tim", alreadyGreeted: true)) // Prints "Hello again, Tim!"
```

> 위 함수는 사람의 이름과 이미 인사 여부를 파라미터로 받고 있고, 적절한 인사말을 반환하고 있습니다.
> 
> `person` 이라는 라벨을 가진 `String` 값과 `alreadyGreeted` 이라는 라벨을 가진 `Bool` 값을 소괄호 안에 콤마로 구분해주고 있네요!
> 
> 이후 `greet(person:alreadyGreeted:)` 함수로 전달한 뒤 호출해주고 있습니다.

- **🙋** `**greet(person:)**`**과** `**greet(person:alreadyGreeted:)**` **는 그럼 같은 함수인가요?**
    
    정답은 … **아닙니다!**
    
    두 함수 모두 `greet` 이라는 이름을 가지지만 `greet(person:alreadyGreeted:)` 함수는 2개의 인수를 가지고, `greet(person:)` 함수는 하나의 인수를 가지고 있습니다.
    
    두 함수의 파라미터가 다르기 때문에 이름은 같아도 두 함수는 다른 함수라는 것을 명심해주세요!
    

```Swift
func greet(person: String) {
    print("Hello, \(person)!")
}

greet(person: "Dave") // Prints "Hello, Dave!"
```

> 위 함수는 person이라는 값을 파라미터로 받고, 아무것도 반환하지 않고 있습니다. 반환값이 없는 함수인데요!
> 
> 반환값이 필요하지 않기 때문에 함수의 정의 부분에서 반환 화살표 (`->`) 또는 반환 타입을 포함하지 않고 있습니다.
> 
> ==**그러나 엄밀히 말하면 위**== ==`**greet(person:)**`== ==**함수에서는 반환값을 정의하지 않았지만 여전히 반환 값 자체는 가지고 있습니다.**==
> 
> 반환 타입이 정의되지 않은 함수는 `Void` 타입의 특별한 값을 반환합니다! `Void` 타입의 특별한 값은 `()` 로 쓰여진 빈 튜플로 구성되어 있기 때문에 우리는 반환 값이 없다고 인식하는 것입니다.

```Swift
func printAndCount(string: String) -> Int {
    print(string)
    return string.count
}
func printWithoutCounting(string: String) {
    let _ = printAndCount(string: string)
}

printAndCount(string: "hello, world")
printWithoutCounting(string: "hello, world")
```

> 위 두 `print` 문에서는 각각 어떤 값이 출력될까요? 잠깐 생각해보신 후 아래 토글을 열어주세요!

- **🧐 정답을 생각해보셨다면 토글을 열어주세요!**
    
    ```Swift
    printAndCount(string: "hello, world")
    // prints "hello, world" and returns a value of 12
    printWithoutCounting(string: "hello, world")
    // prints "hello, world" but does not return a value
    ```
    
    > 두 함수는 모두 `hello, world`라는 String 값을 출력하지만 위 `printAndCount` 함수에서는 12를 반환하고, 아래 `printWithoutCounting`에서는 값을 반환하고 있지 않습니다.
    > 
    > 함수의 반환값은 호출될 때 무시될 수 있습니다. `printAndCount` 함수에서는 값을 반환하고 있지만 `printWithoutCounting` 함수에서는 함수를 호출하되 반환값을 무시하고 있는 것입니다!
    > 
    > 반환값은 무시될 수 있지만 함수는 항상 값을 반환합니다. 정의된 반환 타입이 있는 함수의 경우 반환되는 값이 없으면 컴파일 에러가 발생할 수 있으니 유의해주세요!
    

## 🍏 클로저 (Closures)

> [!important] _**Closures**_ **are self-contained blocks of functionality that can be passed around and used in your code. Closures in Swift are similar to closures, anonymous functions, lambdas, and blocks in other programming languages.**<br><br><br>_==클로저 (Closures)==_ ==는 코드에서 주변에 전달과 사용할 수 있는 자체 포함된 기능 블럭입니다. Swift의 클로저는 다른 프로그래밍 언어에서 클로저, 익명 함수, 람다, 그리고 블럭과 유사합니다.==
> 
>   
> 
> **Closures can capture and store references to any constants and variables from the context in which they’re defined. This is known as** _**closing over**_ **those constants and variables. Swift handles all of the memory management of capturing for you.**  
>   
>   
> ==클로저는 정의된 컨텍스트에서 모든 상수와 변수에 대한 참조를 캡처하고 저장할 수 있습니다. 이러한 상수와 변수를== _==폐쇄 (closing over)==_ ==라고 합니다. Swift는 캡처의 모든 메모리 관리를 처리합니다.==
> 
> [🍎 공식 문서 (The Swift Programming Language, Closure)](https://docs.swift.org/swift-book/documentation/the-swift-programming-language/closures)
> 
> [🍏 공식 문서 번역본 (The Swift Programming Language (한국어), 클로저)](https://bbiguduk.gitbook.io/swift/language-guide-1/closures)

> 클로저는 `일급 객체`로서, 변수나 상수 등으로 저장 가능한 형태를 뜻합니다.
> 
> 일급 객체는 객체를 인자 값, 반환 값으로 사용 및 전달할 수 있어야 하고 데이터 구조 안에 저장할 수 있어야 합니다.
> 
> 위에서 살펴본 함수는 클로저의 한 케이스라고 볼 수 있는데요! 클로저가 함수보다 더 큰 범위라고 생각하시면 좋을 것 같습니다.
> 
> 조금 더 구분이 편하도록 설명해드리자면!
> 
> > `func` 키워드를 사용하고 + 이름이 있다 → 클로저이면서 함수
> > 
> > `func` 키워드를 사용하지 않고 + 이름이 없다 → 클로저
> 
> 편의 상 위의 경우를 함수, 밑의 경우를 클로저로 이해하시면 되겠습니다.

### 🔴 **클로저 표현식 (Closure Expressions)**

> 클로저와 함수의 차이를 살펴볼까요? 아래 코드를 같이 보겠습니다.

```Swift
func pay(user: String, amount: Int) {
    // code
}

let payment = { (user: String, amount: Int) in
    // code
}
```

> 두 코드는 같은 결과 값을 가집니다. 그러나 `pay()`는 함수, `payment`는 클로저라는 차이가 있죠!
> 
> 왜 클로저가 이름 없는 함수인지 약간 감이 잡히실까요?
> 
> 이제 클로저를 표현하는 다른 식들에 대해 조금 더 알아보겠습니다.

```Swift
{ <parameter> -> <return type> in
   <statements>
}
```

![[스크린샷_2024-09-28_오전_7.48.44.png]]

> 클로저는 기본적으로 위와 같은 형식을 가지고 있습니다. 파라미터와 반환 타입, 내용으로 구성되는데요!
> 
> 예시를 함께 보겠습니다.

```Swift
let closure = { (name: String) -> String in
    return "Hello, \(name)"
}
```

> 이 클로저를 사용하기 위해서는 어떤 코드를 작성해야 할까요?

```Swift
closure("Zimi")
closure(name: "Zimi")  //error!
```

> **🙋 어? 함수는 분명 파라미터의 이름도 같이 적어줬는데요 …?**
> 
> 맞습니다. 그러나 클로저에서는 따로 파라미터의 이름을 명시하지 않습니다!
> 
> 클로저를 사용하실 때는 파라미터의 이름 없이 인자 값만 입력해주시면 됩니다.

### 🔴 일급 객체로서 클로저 사용하기

> 클로저는 일급 객체로서, 변수와 상수처럼 사용할 수 있다고 설명드렸는데요!
> 
> 빠르게 예시를 한번 들어보도록 하겠습니다.

```Swift
let closure = { () -> () in
    return "Hello Zimging"
}
```

> 위 내용에서 파라미터와 반환 타입이 생략된 모습인데요! 이렇게도 클로저를 작성할 수 있습니다.
> 
> 위 방법은 대입과 동시에 클로저를 작성하는 방법입니다.

```Swift
let closure2 = closure
```

> 또 이렇게 클로저를 직접 새로운 변수나 상수에 대입하는 방법도 있습니다!
> 
> 클로저는 일급 객체인 만큼 함수의 파라미터로 사용할 수도, 반환 타입으로 사용될 수도 있는데요, 함께 알아볼까요?

```Swift
func doSomething(closure: () -> ()) {
    closure()
}

doSomething(closure: { () -> () in
    print("Hello!") // prints Hello!
})
```

> 위 `doSomething`이라는 함수는 함수를 파라미터로 전달받고 있어요.
> 
> 그런데 이렇게 함수가 아닌 클로저를 파라미터로 전달해줄 수도 있습니다!
> 
> 아래 클로저가 파라미터로 전달된 게 보이시나요?

### 🔴 클로저 호출하기

```Swift
let closure = { () -> String in
    return "Hello Zimging!"
}

closure()
```

> 위 `closure` 변수에는 클로저가 대입되어 있습니다.
> 
> 클로저가 대입된 변수 `closure`를 호출 구문 ()을 이용해 실행시키고 있는게 보이시나요?

### 🔴 **클로저의 경량 문법**

> 클로저의 경량 문법을 사용하면 ==**문법을 최적화해 클로저를 최대한 단순하게 쓸 수 있게**== 해줍니다.
> 
> 어떻게 단순하게 쓸 수 있다는 건지 알아볼까요?

```Swift
func doSomething(closure: (Int, Int, Int) -> Int) {
    closure(1, 2, 3)
}
```

> 위의 함수는 파라미터로 `Int` 타입의 변수를 세개 받아 `Int` 타입의 변수를 반환합니다.
> 
> 클로저의 파라미터로 1, 2, 3을 넘겨주고 있는 것을 확인할 수 있네요!
> 
> 직접 사용해볼까요?

```Swift
doSomething(closure: { (a: Int, b: Int, c: Int) -> Int in
    return a + b + c
})
```

> a, b, c를 하나하나 선언하고 타입까지 명시해주고 있네요.
> 
> 물론 필요한 과정이지만 조금 복잡해 보이기도 합니다. 이런 부분을 조금 더 단순하게 표현할 수 있을까요?

```Swift
doSomething(closure: { (a, b, c) in
    return a + b + c
})
```

> 위와 같이 타입을 생략한 채로 클로저를 경량화시켜 사용할 수 있습니다.
> 
> 놀랍게도 여기서 조금 더 클로저를 경량화시킬 수 있는데요!

```Swift
doSomething(closure: {  
    return $0 + $1 + $2
})
```

> `$0` 에서 0은 인덱스 주소로, `a`, `b`, `c`가 차례대로 `0`, `1`, `2`의 인덱스 값을 가집니다.
> 
> 파라미터 대신 $를 사용함으로써 파라미터에 순서대로 접근할 수 있는 것이죠!
> 
> 클로저를 사용하면 함수를 사용하지 않고도 아주 간단하게 코드를 작성할 수 있습니다.

# 📚 4주차 실습

---

## 문제 1. 함수 실습

> [!important]
> 
> 1. 음식점에서 총 주문 금액과 팁 금액을 입력받고, 팁을 포함한 최종 결제 금액을 계산해 반환하는 함수 `calculateTotalPrice` 를 작성한 뒤 반환된 값을 출력해주세요.
> 2. 특정 온도를 입력받아 그에 따라 "덥다", "춥다", "적당하다"라는 메시지를 출력하는 함수 `checkTemperature`를 작성해주세요.
> 3. 여행지에 대한 정보(도시 이름, 숙박 일수, 하루 예산)를 입력받아 여행 총 예산을 계산하여 출력하는 함수 `printTravelBudget`을 작성해주세요.
> 4. 오늘 날짜를 문자열 형식으로 반환하는 함수 `getCurrentDate`를 작성한 뒤 출력해주세요.
>     1. 오늘 날짜를 받아올 수 있는 `Date()` 를 이용해 작성해주세요! [🍎 참고자료](https://developer.apple.com/documentation/foundation/date)

- 정답은 아래 코드 칸에 넣어주세요!
    
    ```Swift
    // 1. "최종 결제 금액: (최종 결제 금액)원"과 같이 출력되도록 작성해주세요!
    
    // 2. "덥다", "춥다", "적당하다"와 같이 출력되도록 작성해주세요!
    
    // 3. "(여행지)에서의 총 여행 예산은 (총 예산)원입니다."와 같이 출력되도록 작성해주세요!
    
    // 4. "오늘 날짜: 2024-09-19"와 같이 오늘 날짜가 "YYYY-MM-DD" 형식으로 출력되도록 작성해주세요!
    ```
    

## 문제 2. 클로저 실습

> [!important]
> 
> 1. `Int` 변수를 파라미터로 받아 1부터 파라미터로 받은 변수까지 값을 누적시켜 더한 후 누적 값을 반환하는 `addValue` 클로저를 선언하고 출력해주세요.
>     1. 이 때 함수가 아닌 클로저로 선언해주세요!
> 2. `addValue` 클로저를 선언했다면, 클로저를 `$`를 이용해 경량화한 후 같은 결과를 출력하는지 확인해주세요!

- 정답은 아래 코드 칸에 넣어주세요!
    
    ```Swift
    // 1. Int 변수를 파라미터로 받는 addValue 클로저를 선언하고 출력해주세요! 값은 임의로 넣어주세요.
    
    // 2. 1번에서 선언한 addValue 클로저를 $를 이용해 경량화 시킨 코드를 아래 넣어주세요!
    ```
    

# 📌 추가적으로 더 공부해 봤어요!

---

==추가적으로 과제를 하면서 스스로 공부해본 내용이 있다면 이곳에 자유 양식으로 정리해 보세요!==

# ❓ 이런 질문이 있어요!

---

워크북을 진행하면서 궁금했던 점 또는 해결하지 못한 부분을 미리 작성하고 스터디에서 함께 논의해 보세요!  
해결하지 못한 질문이나 궁금한 점이 있다면 언제든지 편하게 DM 주세요 🙋‍♀️  

  

---

Copyright © 2024 Lee Youjin All rights reserved.

Copyright © 2024 Jeong Euichan All rights reserved.