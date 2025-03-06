- [[#📋 학습 목표]]
- [[#🔥 6주차 개념 설명]]
    - [[#🍏 프로퍼티 (Property)]]
- [[#📚 6주차 실습]]
    - [[#문제 1. 프로퍼티 실습]]
- [[#📌 추가적으로 더 공부해 봤어요! ]]
- [[#❓ 이런 질문이 있어요!]]

# 📋 학습 목표

---

- `Swift`의 프로퍼티 개념에 대해 이해하고 실습해볼 수 있다.

# 🔥 6주차 개념 설명

---

## 🍏 프로퍼티 (Property)

> [!important] _**Properties**_ **associate values with a particular class, structure, or enumeration.**
> 
> _==프로퍼티==_==는 값과 특정 클래스, 구조체, 또는 열거형을 연결합니다.==
> 
> **Stored properties store constant and variable values as part of an instance, whereas computed properties calculate (rather than store) a value. Computed properties are provided by classes, structures, and enumerations. Stored properties are provided only by classes and structures.**
> 
> ==저장 프로퍼티 (Stored properties)는 인스턴스의 일부로 상수와 변수 값을 저장하는 반면에 연산 프로퍼티 (computed properties)는 값을 저장하는 대신에 계산합니다. 연산 프로퍼티 (Computed properties)는 클래스, 구조체, 그리고 열거형에 의해 제공됩니다. 저장 프로퍼티는 클래스와 구조체에 의해서만 제공됩니다.==
> 
>   
> 
> **Stored and computed properties are usually associated with instances of a particular type. However, properties can also be associated with the type itself. Such properties are known as type properties.**
> 
> ==저장 프로퍼티와 연산 프로퍼티는 대게 특정 타입의 인스턴스와 연결됩니다. 그러나 프로퍼티는 타입 자체와도 연결될 수 있습니다. 이러한 프로퍼티를 타입 프로퍼티라 합니다.==
> 
> [🍎 공식 문서 (The Swift Programming Language, Properties)](https://docs.swift.org/swift-book/documentation/the-swift-programming-language/properties)
> 
> [🍏 공식 문서 번역본 (The Swift Programming Language (한국어), 프로퍼티)](https://bbiguduk.gitbook.io/swift/language-guide-1/properties)

> `**프로퍼티**`**란 무엇일까요?**
> 
> 우리가 지금까지 선언해왔던 변수와 상수들? 이 말도 틀린 말은 아닙니다. `프로퍼티`의 범주에 들어가니까요!
> 
> `Swift`의 프로퍼티는 총 3가지의 형태로 존재합니다.
> 
> - **저장 프로퍼티 (Stored properties)**
> - **연산 프로퍼티 (Computed properties)**
> - **타입 프로퍼티 (Type properties)**
> 
> 이번 워크북에서는 각 프로퍼티를 하나씩 살펴보며 익혀보도록 하겠습니다.

### 🔴 **저장 프로퍼티 (Stored properties)**

> 특정 클래스 또는 구조체의 인스턴스의 부분으로 저장된 상수 또는 변수를 의미합니다.
> 
> 조금 더 직관적으로 이야기하자면 **클래스와 구조체에서만 사용할 수 있고, 값을 저장하기 위해 선언되는 상수/변수**를 의미해요!
> 
> 저장 프로퍼티는 `var` 키워드를 사용하는 _저장 프로퍼티 변수 (variable stored properties)_ 또는 `let` 키워드를 사용하는 _저장 프로퍼티 상수 (constant stored properties)_로 사용이 가능합니다.

```Swift
struct FixedLengthRange {
    var firstValue: Int
    let length: Int
}
var rangeOfThreeItems = FixedLengthRange(firstValue: 0, length: 3)
// the range represents integer values 0, 1, and 2
rangeOfThreeItems.firstValue = 6
// the range now represents integer values 6, 7, and 8
```

> 구조체 `FixedLengthRange`는 저장 프로퍼티 상수인 `length`, 저장 프로퍼티 변수인 `firstValue`를 가지고 있습니다.
> 
> `length`는 상수이기 때문에 한번 초기화된 이후에는 변경할 수 없지만 `firstValue` 는 변수이기 때문에 변경이 가능하죠!
> 
> 그러나 `rangeOfThreeItems` 을 상수로 선언한다면 어떨까요?

```Swift
struct FixedLengthRange {
    var firstValue: Int
    let length: Int
}
let rangeOfThreeItems = FixedLengthRange(firstValue: 0, length: 3)
// the range represents integer values 0, 1, and 2
rangeOfThreeItems.firstValue = 6
// this will report an error, even though firstValue is a variable property
```

> `rangeOfThreeItems` 가 `let` 키워드를 사용하여 상수로 선언되어 있기 때문에 `firstValue` 가 프로퍼티 변수지만 변경은 불가능합니다.
> 
> 이는 구조체가 값 타입이기 때문인데요!
> 
> 값 타입의 인스턴스가 상수로 선언되면 인스턴스의 모든 프로퍼티에 대해 수정할 수 없습니다.
> 
> 그러나 클래스는 참조 타입이므로 약간 다르게 동작합니다.
> 
> 참조 타입의 인스턴스를 상수로 할당하면 인스턴스의 프로퍼티 변수는 변경이 가능합니다.

```Swift
class DataImporter {
    var filename = "data.txt"
}

class DataManager {
    lazy var importer = DataImporter()
    var data = [String]()
}

let manager = DataManager()
manager.data.append("Some data")
manager.data.append("Some more data")
```

> 위 코드에서 `DataManager` 클래스는 `String` 값의 빈 배열로 초기화 되는 `data` 라는 저장된 프로퍼티를 가지고 있어요.
> 
> `DataManager` 클래스의 역할이 파일로부터 데이터를 가져오는 것이라고 할 때, 이 기능이 `DataImporter`로부터 제공되고 초기화되는 데 시간이 많이 걸린다고 가정해봅시다.
> 
> `DataManager` 인스턴스는 파일로부터 데이터를 가져올 필요 없이 데이터를 관리할 수 있으므로 `DataManager` 가 생성될 때 새로운 `DataImporter` 인스턴스를 생성할 필요가 없습니다.
> 
> 대신에 `DataImporter` 인스턴스를 처음 사용하는 경우에 생성하는 것이 더 합리적이겠죠! 이런 경우에 `lazy`를 사용하는 것입니다.
> 
> `lazy` 수식어가 붙어 선언된 프로퍼티는 사용되기 전까지 초기화되지 않습니다. 이외의 프로퍼티들은 초기화 구문이 불리는 순간 모든 프로퍼티가 초기화되어야 하는데 말이죠!
> 
> 이러한 프로퍼티를 **지연 저장 프로퍼티(Lazy Stored Property)** 라고 부릅니다.

### 🔴 **연산 프로퍼티 (Computed properties)**

> 연산 프로퍼티는 클래스, 구조체, 열거형에서 사용되며 저장 프로퍼티와 달리 직접 값을 저장하지 않고, 다른 `저장 프로퍼티`의 값을 읽어 저장하거나 연산을 수행합니다!
> 
> 예시를 함께 볼까요?

```Swift
var name: Type {
    get {           // getter (다른 저장 연산프로퍼티의 값을 얻거나 연산하여 리턴할 때 사용)
        statements
        return expr
    }
    set(name) {     // setter (다른 저장프로퍼티에 값을 저장할 때 사용)
        statements
    }
}
```

> 연산 프로퍼티는 어떠한 값을 저장하는 것이 아니기 때문에 타입 추론을 통해 형식을 아는 것은 불가능합니다.
> 
> 따라서 선언 시 반드시  **타입 어노테이션을 통해 자료형을 명시**해야 해요!
> 
> 이후 선언된 자료형 뒤에 {} 를 붙이는 것이 연산 프로퍼티의 사용법이라고 할 수 있습니다.
> 
> 그렇다면 어떤 타입의 값을 받아서 다른 저장 프로퍼티에 저장할 것인지, 어떤 타입의 값을 리턴할 것인지를 명시해야겠죠?
> 
> 이를 위해 `get`과 `set`를 활용합니다.

```Swift
 class Person {
    var name: String = "짐깅"
 
    var alias: String {
        get {
            return name
        }
        set(name) {
            self.name = name
        }
    }
}
```

> `get` 은 값을 받아오는 부분입니다. 어떤 저장 프로퍼티의 값을 연산해서 `return`할 지 결정하기 때문에 `return` 구문은 항상 존재해야 해요!
> 
> `set` 은 값을 설정하는 부분으로, 받아온 값을 저장 프로퍼티에 어떻게 할당할 것인지를 결정합니다.
> 
> 위 예시에서는 `alias` 라는 연산 프로퍼티를 다루고 있어요.
> 
> `alias` 는 `name`이라는 저장 프로퍼티의 값을 읽어와서 그대로 할당해주고 있습니다. 연산하는 과정도 함께 볼까요?

```Swift
class Person {
    var name: String = "햄"
 
    var alias: String {
        get {
            return self.name + "은 UMC의 멋진 iOS 7기 챌린저다"
        }
        set(name) {
            self.name = name + "은 6주차도 멋지게 해냈다!"
        }
    }
}
 
```

> 위 코드에서는 이름을 담은 저장 프로퍼티의 값을 `get`으로 가져와서 다른 `String` 값과 합친 후 `return`해주고 있어요.
> 
> 이후 `set`에서 `name` 프로퍼티에 다른 `String` 값과 기존 `name`의 값을 합친 새로운 값을 저장해주고 있습니다.

```Swift
let ham: Person = .init()
 
// get에 접근
print(ham.alias)             // 햄은 UMC의 멋진 iOS 7기 챌린저다
 
// set에 접근
ham.alias = "체리"
print(ham.name)              // 체리는 6주차도 멋지게 해냈다!
```

> 연산 프로퍼티인 `alias` 의 값을 읽으면, `alias`의 `get`이 실행되어 "`짐깅은 UMC의 멋진 iOS 7기 챌린저다`" 라는 값이 출력됩니다.
> 
> 이후 연산 프로퍼티인 `alias` 에 값을 쓰면, "체리"라는 값이 `set`의 파라미터로 넘어가 `set` 함수가 실행되는 것입니다!
> 
> 이제 연산 프로퍼티의 동작 원리에 대해 감이 잡히셨을까요?

### 🔴 **타입 프로퍼티 (Type properties)**

> 타입 프로퍼티는 클래스, 구조체, 열거형에서 사용됩니다.
> 
> 저장 타입 프로퍼티와 연산 타입 프로퍼티가 존재하고, 저장 타입 프로퍼티의 경우 선언할 때 항상 초기화를 시켜주어야 합니다!
> 
> `static`을 이용해 선언하며, 자동으로 `lazy`로 작동하기 때문에 `lazy`를 직접 명시할 필요가 없습니다.

```Swift
class Human {
    let name: String = "수"     // 저장 프로퍼티
    var alias: String {             // 연산 프로퍼티
        return name + "은 UMC의 멋진 iOS 7기 챌린저다"
    }
}


class Human {
    static let name: String = "아진"     // 저장 타입 프로퍼티
    static var alias: String {             // 연산 타입 프로퍼티
        return name + "은 UMC의 멋진 iOS 7기 챌린저다"
    }
}
```

> 두 클래스 중 위의 클래스는 저장 프로퍼티와 연산 프로퍼티를 나타내는 클래스입니다.
> 
> 아래의 클래스는 각각 저장 타입 프로퍼티와 연산 타입 프로퍼티를 나타내고 있어요. `static`만 붙여주면 된다니 굉장히 간단하죠?
> 
> 만약 아래의 저장 타입 프로퍼티를 초기화해주지 않는다면 어떨까요?

```Swift
class Human {
    static let name: String     // error! 'static var' declaration requires an initializer expression or getter/setter specifier
    static var alias: String {           
        return name + "은 UMC의 멋진 iOS 7기 챌린저다"
    }
}
```

> `static var` 은 초기값을 가지거나 연산 타입 프로퍼티로 선언되어야 한다는 오류가 발생하네요.
> 
> 이런 오류는 왜 발생하는 걸까요?
> 
> 그 이유는 `static`으로 선언되는 저장 타입 프로퍼티는 초기화 시 값을 할당할 `initializer`가 존재하지 않기 때문입니다.
> 
> 타입 프로퍼티는 인스턴스가 생성 된다고 매번 해당 인스턴스의 멤버로 생성되는 것이 아닙니다!
> 
> 언제 메모리에 올라가면, 그 뒤로는 생성되지 않으며 이후에는 언제든지 이 타입 프로퍼티에 접근할 수 있는 것입니다. 전역 변수 같은 느낌이겠죠?
> 
> 그렇다면 이런 타입 프로퍼티에는 어떻게 접근할까요?

```Swift
let human: Human = .init()

Human.name // 접근 가능
human.name // error! 접근 불가능
```

> 타입 프로퍼티는 타입과 이름을 통해서만 접근이 가능합니다.
> 
> 인스턴스가 생성된다고 해서 타입 프로퍼티가 매번 생성되는 것이 아니기 때문에 인스턴스를 통해 접근이 불가능한 것입니다!
> 
> 타입 프로퍼티는 싱글톤 등 개발에서도 유용하게 쓰이는 부분이 많으니 익숙해지는 것을 추천드립니다 😄

# 📚 6주차 실습

---

## 문제 1. 프로퍼티 실습

> [!important]
> 
> 1. 저장 프로퍼티를 사용하여 사각형의 너비 `width`와 높이 `height`를 저장하는 `Rectangle` 클래스를 선언하고 두 저장 프로퍼티를 이용해 사각형의 너비와 높이를 각각 출력해주세요.
> 2. 1번에서 구현한 `Rectangle` 클래스에서 사각형의 면적을 계산하는 `area`라는 연산 프로퍼티를 선언해주세요. 이후 `width` 와 `height` 를 이용해 면적을 계산하고 출력해주세요.
> 3. 1, 2번에서 구현한 `Rectangle` 클래스에서 모든 사각형이 사용할 수 있도록 `cm`라는 값을 가진 `unit`을 추가해주세요. 모든 `Rectangle` 인스턴스가 이 값을 공유할 수 있도록 타입 프로퍼티로 선언해주세요.

- 정답은 아래 코드 칸에 넣어주세요!
    
    ```Swift
    // 1. "사각형의 너비: \(rectangle.width) cm, 높이: \(rectangle.height) cm"와 같이 출력되도록 작성해주세요!
    
    // 2. "사각형의 면적: \(rectangle.area) cm²"와 같이 출력되도록 작성해주세요!
    
    // 3. "사각형의 면적: \(rectangle.area) \(Rectangle.unit)²" 형식으로 출력되도록 작성해주세요!
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