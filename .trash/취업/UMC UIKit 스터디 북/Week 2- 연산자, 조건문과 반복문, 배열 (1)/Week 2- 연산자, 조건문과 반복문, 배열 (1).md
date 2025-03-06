- [[#📋 학습 목표]]
- [[#🔥 2주차 개념 설명]]
    - [[#🍏 연산자]]
    - [[#🍏 조건문]]
    - [[#🍏 반복문]]
    - [[#🍏 배열]]
- [[#📚 2주차 실습]]
    - [[#문제 1. 연산자 실습]]
    - [[#문제 2. 조건문 실습]]
    - [[#문제 3. 반복문 실습]]
- [[#📌 추가적으로 더 공부해 봤어요! ]]
- [[#❓ 이런 질문이 있어요!]]

# 📋 학습 목표

---

- 연산자, 조건문, 반복문의 개념을 알고 실습을 통해 응용해 볼 수 있다.
- 배열의 개념을 이해하고 여러 가지 배열을 직접 입출력해볼 수 있다.

# 🔥 2주차 개념 설명

---

## 🍏 연산자

> [!important] **An** _**operator**_ **is a special symbol or phrase that you use to check, change, or combine values.**<br><br>_==연산자 (operator)==_ ==는 값을 체크, 변경, 또는 결합하기 위해 사용하는 기호 또는 구 입니다.==<br><br><br>[🍎 공식 문서 (The Swift Programming Language, Basic Operators)](https://docs.swift.org/swift-book/documentation/the-swift-programming-language/basicoperators/)<br><br>[🍏 공식 문서 번역본 (The Swift Programming Language (한국어), 기본 연산자)](https://bbiguduk.gitbook.io/swift/language-guide-1/basic-operators)

Swift에서 사용하는 연산자는 C언어를 기반으로 만들어졌습니다.

**몇 개의 항목에 동작하느냐**에 따라 ==**단항(unary), 이항(binary), 삼항(ternary)**== **연산자**로 나뉩니다.

하나씩 살펴볼까요?

### **🔴 단항(unary) 연산자**

> [!important] _**Unary**_ **operators operate on a single target (such as** `**-a**`**). Unary** _**prefix**_ **operators appear immediately before their target (such as** `**!b**`**), and unary** _**postfix**_ **operators appear immediately after their target (such as** `**c!**`**).**<br><br><br>_==단항 (Unary)==_ ==연산자는== ==`-a`== ==처럼 단일 항목에 동작합니다. 단항== _==접두사==_ ==연산자는== ==`!b`== ==처럼 항목 바로 직전에 위치하고 단항== _==접미사==_ ==연산자는== ==`c!`== ==처럼 항목 바로 다음에 위치합니다.==

> ==**단일 숫자(또는 항목)에 대해서만 동작하는 연산자**==라고 이해하시면 됩니다.
> 
> 기본적인 예시로는 **논리적 NOT 연산자(**`**!**`**)**가 있어요!

### **🔴 이항(binary) 연산자**

> [!important] _**Binary**_ **operators operate on two targets (such as** `**2 + 3**`**) and are** _**infix**_ **because they appear in between their two targets.**<br><br><br>_==이항 (Binary)==_ ==연산자는== ==`2 + 3`== ==처럼 2개의 항목에 동작하고 2개의 항목 사이에 위치해야 하므로 위치는== _==고정==_ ==입니다.==

> ==**두 개의 숫자(또는 항목)에 대해서 동작하는 연산자**==라고 이해하시면 됩니다.
> 
> 대부분의 연산자가 이항 연산자에 속하는데요. 대표적인 예시로는 **대입 연산자(**`**=)**`**, 산술 연산자(**`**+**`**,** `**-**`**,** `*****`**,** `**/**`**), 범위 연산자(**`**…**`**), 비교 연산자(**`**==**`**,** `**<**`**,** `**>**`**)**가 있어요!

### **🔴 삼항(ternary) 연산자**

> [!important] _**Ternary**_ **operators operate on three targets. Like C, Swift has only one ternary operator, the ternary conditional operator (**`**a ? b : c**`**).**<br><br><br>_==삼항 (Ternary)==_ ==연산자는 3개의 항목에 동작합니다. C 처럼 Swift는 하나의 삼항 연산자만 있으며 삼항 조건 연산자 (====`a ? b : c`====)입니다.==

> ==**세 개의 숫자(또는 항목)에 대해서 동작하는 연산자**==라고 이해하시면 됩니다.
> 
> 삼항 연산자는 **삼항 조건 연산자(**`**a ? b : c**`**)**가 유일합니다.

이렇게 몇 개의 항목에 동작하느냐에 따라 연산자의 종류를 나눠볼 수 있어요.

---

이번에는 조금 더 구체적으로 개발 시 많이 쓰이는 연산자들 몇 가지를 알아보도록 하겠습니다!

`대입 연산자`와 `산술 연산자`, `비교 연산자`, `삼항 조건 연산자`, `범위 연산자`와 `논리 연산자`를 알아볼텐데요. 워크북에서 설명하지 않는 `Nil-결합 연산자`는 공식 문서를 참고해서 꼭 한 번 읽어보시고 적용해보시길 바랍니다!

### **🔴 대입 연산자 (Assignment Operator)**

> [!important] **The** _**assignment operator**_ **(**`**a = b**`**) initializes or updates the value of** `**a**` **with the value of** `**b**`**:**<br><br><br>_==대입 연산자 (assignment operator)==_ ==(====`a = b`====) 는== ==`b`== ==의 값으로 초기화 되거나 업데이트 됩니다:==
> 
>   
> 
> ```Swift
> let b = 10
> var a = 5
> a = b
> // a is now equal to 10
> ```

> 대입 연산자 `=` 를 이용해 전항 값에 후항 값을 할당할 수 있어요.
> 
> 단지 ==`**같다**`== ==**라는 개념이 아닌**== ==`**할당한다**`== ==**라는 개념**==으로 이해하시면 됩니다.
> 
> 다음과 같이 여러 개의 값을 동시에 할당할 수도 있어요!

```Swift
let (x, y) = (1, 2)
// x에는 1, y에는 2가 할당됩니다.
```

### **🔴 산술 연산자 (Arithmetic Operators)**

> [!important] **Swift supports the four standard** _**arithmetic operators**_ **for all number types:**
> 
> - **Addition (**`**+**`**)**
> - **Subtraction (**`**-**`**)**
> - **Multiplication (**`*****`**)**
> - **Division (**`**/**`**)**
> 
> ==Swift는 모든 숫자 타입에 대해 4개의 기본== _==산술 연산자 (arithmetic operators)==_ ==를 제공합니다:==
> 
> - ==덧셈 (====`+`====)==
> - ==뺄셈== ==**(**====`**-**`====**)**==
> - ==곱셈== ==**(**====`*****`====**)**==
> - ==나눗셈 (====`/`====)==
> 
> ```Swift
> 1 + 2       // equals 3
> 5 - 3       // equals 2
> 2 * 3       // equals 6
> 10.0 / 2.5  // equals 4.0
> ```

> 사칙연산의 경우 `+`, `-`, `*`, `/` 를 통해 간편하게 계산이 가능합니다.
> 
> 나머지 연산의 경우 `**%**` **연산자**를 통해 같은 형식으로 계산할 수 있어요!
> 
> 음수의 경우 `**-(자연수)**` **의 형식**으로 나타냅니다.

```Swift
var a = 1
a += 2
// a 값은 3
```

> `+=`, `-=` 연산자는 각각 ==**단항 덧셈 연산자, 단항 뺄셈 연산자**==라고 불러요.
> 
> 오직 한 값에 특정 정수를 빼거나 더하고 싶을 때만 사용합니다.
> 
> 복합 대입 연산자는 값을 반환하지 않기 때문에 `let b = a += 2` 와 같은 형식으로는 작성할 수 없습니다! 유의해서 사용해주세요.

### **🔴 비교 연산자 (Comparison Operators)**

> [!important] **Swift supports the following comparison operators:**
> 
> - **Equal to (**`**a == b**`**)**
> - **Not equal to (**`**a != b**`**)**
> - **Greater than (**`**a > b**`**)**
> - **Less than (**`**a < b**`**)**
> - **Greater than or equal to (**`**a >= b**`**)**
> - **Less than or equal to (**`**a <= b**`**)**
> 
> Swift는 아래의 비교 연산자 (comparison operators)를 제공합니다:
> 
> - 같음 (`a == b`)
> - 다름 (`a != b`)
> - 보다 큼 (`a > b`)
> - 보다 작음 (`a < b`)
> - 보다 크거나 같음 (`a >= b`)
> - 보다 작거나 같음 (`a <= b`)
> 
>   
> 
> ```Swift
> 1 == 1   // true because 1 is equal to 1
> 2 != 1   // true because 2 is not equal to 1
> 2 > 1    // true because 2 is greater than 1
> 1 < 2    // true because 1 is less than 2
> 1 >= 1   // true because 1 is greater than or equal to 1
> 2 <= 1   // false because 2 is not less than or equal to 1
> ```

### **🔴 삼항 조건 연산자 (Ternary Conditional Operator)**

> [!important] **The** _**ternary conditional operator**_ **is a special operator with three parts, which takes the form** `**question ? answer1 : answer2**`**. It’s a shortcut for evaluating one of two expressions based on whether** `**question**` **is true or false. If** `**question**` **is true, it evaluates** `**answer1**` **and returns its value; otherwise, it evaluates** `**answer2**` **and returns its value.**<br><br><br>_==삼항 조건 연산자 (ternary conditional operator)==_ ==는== ==`question ? answer1 : answer2`== ==형태의 3가지 부분으로 이루어진 특별한 연산자입니다.== ==`question`== ==이 참 또는 거짓인지에 따라 2개의 표현식 중 하나를 나타내는 식입니다.== ==`question`== ==이 참이라면== ==`answer1`== ==을 반환하고 반대면== ==`answer2`== ==를 반환합니다.==

### **🔴 범위 연산자 (Range Operators)**

> [!important] **The** _**closed range operator**_ **(**`**a...b**`**) defines a range that runs from** `**a**` **to** `**b**`**, and includes the values** `**a**` **and** `**b**`**. The value of** `**a**` **must not be greater than** `**b**`**.**<br><br><br>_==닫힌 범위 연산자 (closed range operator)==_ ==(====`a...b`====)는 값== ==`a`== ==와== ==`b`== ==가 포함된== ==`a`== ==부터== ==`b`== ==까지의 범위 실행을 정의합니다.== ==`a`== ==의 값은== ==`b`== ==보다 클 수 없습니다.==

```Swift
for index in 1...5 {
    print("\(index) times 5 is \(index * 5)")
}
// 1 times 5 is 5
// 2 times 5 is 10
// 3 times 5 is 15
// 4 times 5 is 20
// 5 times 5 is 25
```

### **🔴 논리 연산자 (Logical Operators)**

> [!important] _**Logical operators**_ **modify or combine the Boolean logic values** `**true**` **and** `**false**`**. Swift supports the three standard logical operators found in C-based languages:**<br><br><br>_==논리 연산자 (Logical operators)==_ ==는 부울 로직 값을== ==`true`== ==와== ==`false`== ==로 수정하거나 결합합니다. Swift는 C-기반 언어에서 볼 수 있는 3개의 표준 논리 연산자를 제공합니다:==

```Swift
!a // 논리적 NOT
a && b // 논리적 AND
a || b // 논리적 OR
```

## 🍏 조건문

### 🔴 `If`

> 가장 간단한 형식으로 `if` 구문은 단일 `if` 조건을 갖습니다.
> 
> 조건이 `true` 일 경우에만 구문을 실행합니다.

```Swift
var temperatureInFahrenheit = 30
if temperatureInFahrenheit <= 32 {
    print("It's very cold. Consider wearing a scarf.")
}
// Prints "It's very cold. Consider wearing a scarf."
```

> `if` 구문은 `if` 조건이 `false` 일 때 그밖의 다른 구문을 제공할 수 있습니다.
> 
> 이 구문은 `else` 키워드로 표기합니다.

```Swift
temperatureInFahrenheit = 40
if temperatureInFahrenheit <= 32 {
    print("It's very cold. Consider wearing a scarf.")
} else {
    print("It's not that cold. Wear a T-shirt.")
}
// Prints "It's not that cold. Wear a T-shirt."
```

> 2개의 중괄호 중 하나는 항상 실행됩니다.
> 
> 기온이 증가하여 화씨 `40` 도를 가지므로 `else` 구문이 실행 됩니다.

### 🔴 `Switch`

> `switch` 구문은 값을 고려하고 가능한 여러개의 일치 패턴과 비교합니다.
> 
> 그런 다음 첫번째로 일치하는 패턴을 기반으로 적절한 코드 블럭을 실행합니다.
> 
> `switch` 구문은 여러 가능한 상태에 응답하기 위해 `if` 구문의 대체 구문으로 제공합니다.

```Swift
let someCharacter: Character = "z"
switch someCharacter {
case "a":
    print("The first letter of the Latin alphabet")
case "z":
    print("The last letter of the Latin alphabet")
default:
    print("Some other character")
}
// Prints "The last letter of the Latin alphabet"
```

> 모든 `switch` 구문은 완벽해야 합니다.
> 
> 고려 중인 타입의 가능한 모든 값은 `switch` 케이스 중 하나와 일치해야 합니다.
> 
> 가능한 모든 값에 대한 케이스를 제공하는 것이 적절하지 않은 경우 명시적으로 해결되지 않은 모든 값을 포함하도록 기본 케이스를 정의할 수 있습니다.
> 
> 기본 케이스는 `default` 키워드로 나타내고 항상 마지막에 위치합니다.

## 🍏 반복문

### 🔴 `For-In`

> 배열에 아이템, 범위의 숫자, 또는 문자열에 문자와 같은 연속된 것들에 대해 `for`-`in` 루프를 사용하여 반복할 수 있습니다.

```Swift
let names = ["Anna", "Alex", "Brian", "Jack"]
for name in names {
    print("Hello, \(name)!")
}
// Hello, Anna!
// Hello, Alex!
// Hello, Brian!
// Hello, Jack!
```

> 숫자 범위에 대해 `for`-`in` 루프를 사용할 수도 있습니다.

```Swift
for index in 1...5 {
    print("\(index) times 5 is \(index * 5)")
}
// 1 times 5 is 5
// 2 times 5 is 10
// 3 times 5 is 15
// 4 times 5 is 20
// 5 times 5 is 25
```

### 🔴 `While`

> `while` 루프는 조건이 `false` 가 될 때까지 구문을 수행합니다.
> 
> 이러한 루프는 첫번째 반복이 시작되기 전에 반복 횟수를 가늠할 수 없을 때 가장 잘 사용됩니다.

```Swift
while <\#condition#> {
   <\#statements#>
}
```

## 🍏 배열

> [!important] **Swift provides three primary** _**collection types**_**, known as arrays, sets, and dictionaries, for storing collections of values. Arrays are ordered collections of values.**<br><br>==Swift는 콜렉션의 값을 저장하기 위한 배열 (array), 집합 (set), 딕셔너리 (dictionary)와 같은 3개의 원시적인== _==콜렉션 타입 (collection types)==_ ==을 제공합니다. 배열은 콜렉션 값에 순서를 가지고 있습니다.==

![[c969b958-8028-48dc-9574-aa3603663485.png]]

### 🔴 **빈 배열 생성 (Creating an Empty Array)**

```Swift
var someInts: [Int] = []
print("someInts is of type [Int] with \(someInts.count) items.")
// Prints "someInts is of type [Int] with 0 items."
```

> `someInts` 변수의 타입은 초기화 타입을 통해 `[Int]` 로 추론됩니다.
> 
> 함수 인수나 이미 타입이 명시 된 변수 또는 상수와 같은 타입 정보를 제공하는 경우 `[]` (빈 대괄호 쌍)으로 빈 배열을 생성할 수 있습니다!

### 🔴 **기본값 배열 생성 (Creating an Array with a Default Value)**

```Swift
var threeDoubles = Array(repeating: 0, count: 3)
// threeDoubles 배열은 [Int] 티입이며 [0, 0, 0]과 같습니다.
```

> Swift의 `Array` 타입은 같은 기본 값으로 설정하고 크기를 고정하여 배열을 생성하는 초기화도 제공합니다. 적합한 타입 (파라미터 명 `repeating`)의 기본값과 새로운 배열에 반복될 값의 횟수 (파라미터 명 `count`)를 초기화 시 전달합니다!

### 🔴 **배열을 더해 생성 (Creating Array by Adding Two Arrays Together)**

```Swift
var anotherThreeDoubles = Array(repeating: 2.5, count: 3)
// anotherThreeDoubles is of type [Double], and equals [2.5, 2.5, 2.5]

var sixDoubles = threeDoubles + anotherThreeDoubles
// sixDoubles is inferred as [Double], and equals [0.0, 0.0, 0.0, 2.5, 2.5, 2.5]
```

> 동등한 타입의 2개의 존재하는 배열을 덧셈 연산자 (`+`)를 통해 합쳐서 새로운 배열을 생성할 수 있습니다.
> 
> 새로운 배열의 타입은 합쳐진 2개의 배열의 타입으로부터 추론됩니다!

### 🔴 **배열 접근과 수정 (Accessing and Modifying an Array)**

> 배열의 아이템 갯수를 알기 위해서는 읽기 전용 프로퍼티인 `count`를 이용합니다.

```Swift
print("The shopping list contains \(shoppingList.count) items.")
// Prints "The shopping list contains 2 items."
```

> isEmpty 프로퍼티를 사용해 배열의 `count` 프로퍼티 값이 `0` 인지 아닌지 빠르게 판단할 수 있습니다.

```Swift
if shoppingList.isEmpty {
    print("The shopping list is empty.")
} else {
    print("The shopping list is not empty.")
}
// Prints "The shopping list is not empty."
```

> 배열의 `append(_:)` 메서드를 호출하여 배열의 끝에 새로운 아이템을 추가할 수 있습니다.

```Swift
shoppingList.append("Flour")
// shoppingList now contains 3 items, and someone is making pancakes
```

> 또한 하나 이상의 동등한 아이템의 배열은 덧셈 대입 연산자 (`+=`)를 통해 추가할 수 있습니다.

```Swift
shoppingList += ["Baking Powder"]
// shoppingList now contains 4 items
shoppingList += ["Chocolate Spread", "Cheese", "Butter"]
// shoppingList now contains 7 items
```

> _서브 스크립트 구문 (subscript syntax)_ 을 사용하여 배열의 값을 가져올 수 있습니다. 배열의 이름 뒤에 바로 대괄호를 붙이고 가져올 값의 인덱스를 넣어 해당 값을 가져올 수 있습니다.  
> 배열의 첫번째 인덱스는  
> `1` 이 아니라 `0` 으로 시작함을 유의해주세요!

```Swift
var firstItem = shoppingList[0]
// firstItem is equal to "Eggs"
```

> 배열의 마지막 아이템을 삭제하고 싶다면 배열 `count` 프로퍼티의 사용을 피하기 위해 `remove(at:)` 메서드 보다 `removeLast()` 메서드를 사용하는 것이 더 좋습니다.  
>   
> `remove(at:)` 메서드와 같이 `removeLast()` 메서드는 삭제된 아이템을 반환합니다.

```Swift
let apples = shoppingList.removeLast()
// the last item in the array has just been removed
// shoppingList now contains 5 items, and no apples
// the apples constant is now equal to the removed "Apples" string
```

### 🔴 **배열 반복 (Iterating Over an Array)**

> `For - in` 루프를 사용해 배열의 전체 값을 알 수 있습니다.

```Swift
for item in shoppingList {
    print(item)
}
// Six eggs
// Milk
// Flour
// Baking Powder
// Bananas
```

# 📚 2주차 실습

---

## 문제 1. 연산자 실습

1. 단항 연산자를 이용해 변수 `x`의 값을 5로 초기화한 후 1 증가시키고, 증가된 값을 출력하세요.
2. 이항 연산자를 이용해 변수 `a`와 `b`를 각각 10과 20으로 초기화한 뒤 더한 결과를 변수 `sum`에 저장하고, 그 결과를 출력하세요.
3. 삼항 연산자를 이용해 변수 `score`가 60 이상이면 "합격"을, 그렇지 않으면 "불합격"을 출력하세요. `score` 의 값은 임의로 지정해주세요.
4. 논리 연산자를 이용해 변수 `isMember`가 `true`이고 `points`가 100 이상이면 "할인 가능"을 출력하고, 그렇지 않으면 "할인 불가능"을 출력하세요.
5. 범위 연산자를 이용해 변수 `numbers`에 1부터 5까지의 숫자를 저장하고 숫자들을 출력하세요.
    
    ```Swift
    1, 2, 3, 4, 5
    ```
    

- 정답은 아래 코드 칸에 넣어주세요!
    
    ```Swift
    // 1. 단항 연산자: 변수 x의 값을 5로 초기화한 후 1 증가시키고, 증가된 값을 출력
    
    // 2. 이항 연산자: 변수 a와 b를 각각 10과 20으로 초기화한 뒤 더한 결과를 변수 sum에 저장하고, 그 결과를 출력
    
    // 3. 삼항 연산자: 변수 score가 60 이상이면 "합격", 그렇지 않으면 "불합격"을 출력
    
    // 4. 논리 연산자: 변수 isMember가 true이고 points가 100 이상이면 "할인 가능", 그렇지 않으면 "할인 불가능"을 출력
    
    // 5. 범위 연산자: 변수 numbers에 1부터 5까지의 숫자를 저장하고, 이 숫자들을 출력
    ```
    

## 문제 2. 조건문 실습

1. `**if**`**문**을 이용해 변수 `temperature`가 30 이상이면 "덥다"를 출력하고, 10 이상 30 미만이면 "적당하다"를 출력하며, 그렇지 않으면 "춥다"를 출력하세요. `temperature` 의 값은 임의로 지정해주세요.
2. `**switch**`**문**을 이용해 변수 `day`에 요일을 나타내는 정수(1부터 7까지, 1은 월요일)를 저장하고, 해당 요일에 따라 "주중" 또는 "주말"을 출력하세요. 예를 들어, 1부터 5까지는 "주중", 6과 7은 "주말"을 출력하세요. `day` 값은 임의로 지정해주세요.

- 정답은 아래 코드 칸에 넣어주세요!
    
    ```Swift
    // 1. if문: temperature가 30 이상이면 "덥다", 10 이상 30 미만이면 "적당하다", 그렇지 않으면 "춥다"를 출력
    
    
    // 2. switch문: day에 따른 요일을 출력하고, 1~5는 "주중", 6과 7은 "주말"을 출력
    ```
    

## 문제 3. 반복문 실습

1. `**for-in**`**문을 이용해** 배열 `fruits`에 "Apple", "Banana", "Cherry"를 저장하고, 각 과일의 이름을 출력하세요.
2. `**while**`**문을 이용해** 변수 `count`가 5가 될 때까지 "Count: n" 형식으로 숫자를 출력하세요. (`n`은 현재 숫자를 나타냅니다.)

```Swift
// 1. for-in문: 배열 fruits에 "Apple", "Banana", "Cherry"를 저장하고, 각 과일의 이름을 출력

// 2. while문: 변수 count가 5가 될 때까지 "Count: n" 형식으로 숫자를 출력
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