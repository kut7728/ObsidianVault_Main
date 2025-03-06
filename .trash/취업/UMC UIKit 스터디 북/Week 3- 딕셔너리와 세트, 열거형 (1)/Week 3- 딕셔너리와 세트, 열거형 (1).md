- [[#📋 학습 목표]]
- [[#🔥 3주차 개념 설명]]
    - [[#😃 딕셔너리]]
    - [[#😃 세트]]
    - [[#😃 열거형(Enum)]]
- [[#📚 3주차 실습]]
    - [[#문제 1. 딕셔너리 실습]]
    - [[#문제 2. Set 실습]]
    - [[#문제 3. Enum 실습]]
- [[#📌 추가적으로 더 공부해 봤어요! ]]
- [[#❓ 이런 질문이 있어요!]]

  

# 📋 학습 목표

> **딕셔너리**  
>   
> **세트**  
>   
> **열거형**

# 🔥 3주차 개념 설명

---

### 😃 딕셔너리

> Swift에서 키(key)와 값(value)을 하나의 쌍으로 저장하는 컬렉션 타입 입니다. 각 키는 고유해야 하며, 해당 키에 대응하는 값이 존재합니다. 딕셔너리는 데이터를 키로 검색할 수 있어, 특정 값을 효율적으로 찾을 수 있습니다.

  

![[Assets/image 15.png|image 15.png]]

  

- **키 - 값 쌍**
    - 각각의 항목은 고유한 키와 그 키에 해당하는 값으로 이루어져 있습니다.
- **키의 고유성**
    - 딕셔너리 내의 키는 고유해야 합니다. 같은 키로 두 개 이상의 값을 가질 수 없습니다.
- **순서 없음**
    - 딕셔너리는 항목의 저장 순서를 보장하지 않습니다. 따라서 순서가 중요한 경우 배열과 같은 다른 컬렉션을 사용해야 합니다.

  

### 🔴 딕셔너리 선언 및 초기화

딕셔너리는 `[KeyType : ValueType]` 형태로 선언합니다. `KeyType` 은 키의 자료형을 의미하며, `ValueType` 은 값의 자료형을 나타냅니다. 딕셔너리를 선언할 때는 키와 값을 `:` 으로 구분하며, 여러 쌍을 `,` 로 구분하여 입력합니다.

  

빈 딕셔너리 생성을 위해 아래와 같이 작성하면 됩니다.

```Swift
var emptyDictionary: [String: Int] = [:] // String 키로, Int를 값으로 갖는 빈 딕셔너리
```

  

초기값을 선언하고자 할 경우, 아래와 같이 작성하면 됩니다.

```Swift
var studentScore: [String: Int] = ["Jeong": 100, "Marco": 80]
```

  

### 🔴 딕셔너리 기본 사용

딕셔너리에서 값에 접근하려면 키를 사용합니다. 키를 사용하여 값에 접근하면 **옵셔널(Optional)** 값으로 반환되는데, 해당 키가 존재하지 않을 수 있기 때문입니다. ==**옵셔널에 대한 설명은 추후 문법 워크북을 통해 배우게 될 것입니다.**==

```Swift
let score = studentScore["Jeong"]
print(score)
```

![[스크린샷_2024-09-12_오후_8.43.02.png]]

### 🔴 딕셔너리 추가 및 수정

딕셔너리에 새로운 키-값 쌍을 추가하거나, 기존 키의 값을 수정할 수 있습니다.

```Swift
// 값 추가
studentScore["Ming"] = 88
```

```Swift
// 값 수정
studentScore["Jeong"] = 80 // Jeong의 점수를 80으로 수정
```

```Swift
// 값 제거
studentScore["Jeong"] = nil
```

  

### 🔴 딕셔너리 반복문

딕셔너리는 for-in 반복문을 사용하여 각 키-값 쌍을 반복할 수 있습니다. 반복문을 통해 딕셔너리의 모든 항목을 순회하며 각 키와 값을 가져올 수 있습니다.

```Swift
for (name, score) in studentScore {
    print("\(name)의 점수 \(score)")
}
```

![[스크린샷_2024-09-12_오후_8.48.12.png]]

### 🔴 딕셔너리의 주요 메서드

- `update(_:forKey:)`
    
    - 딕셔너리에서 값의 추가나 수정을 할 때, `updateValue(_:forKey:)` 메서드를 사용할 수 있습니다. 이 메서드는 새로 추가되거나 업데이트된 값을 반환합니다.
    
    ```Swift
    if let oldValue = studentScore.updateValue(95, forKey: "Bob") {
        print("Bob의 이전 점수는 \(oldValue)점입니다.")
    } else {
        print("Bob의 점수가 새로 추가되었습니다.") // Bob의 점수가 없었으므로, 새롭게 추가됩니다.
    }
    ```
    
    ![[스크린샷_2024-09-12_오후_8.54.24.png]]
    
- `removeValue(forKey:)` 메서드
    
    - 딕셔너리에서 특정 키를 사용하여 값을 삭제할 때는 `removeValue(forKey:)` 메서드를 사용할 수 있습니다. 삭제된 값은 반환되며, 키가 존재하지 않을 경우 `nil` 을 반환합니다.
    
    ```Swift
    if let value = studentScore.removeValue(forKey: "Jeong") {
        print("Jeong의 점수 \(value)가 삭제 되었습니다.")
    } else {
        print("Jeong의 점수를 찾을 수 없습니다.")
    }
    ```
    
    ![[스크린샷_2024-09-12_오후_8.57.28.png]]
    

### 🔴 복잡한 데이터 딕셔너리 사용

딕셔너리의 키와 값으로 기본 자료형 외에도 복잡한 데이터 타입을 사용할 수 있습니다.

```Swift
var classGrades: [Int: [String: Int]] = [
    1: ["Jeong": 85, "Ming": 90],
    2: ["Marco": 95, "Bob": 88]
]
```

### 😃 세트

> `Set` 은 Swift에서 제공하는 컬렉션 타입 중 하나로 **순서가 없고 고육한 값을 저장**하는 데이터 구조입니다. **중복되지 않는 값**을 저장해야 할 때 매우 유용하며, 배열과는 달리 동일한 값을 여러 번 저장할 수 있습니다, 또한 `Set` 은 값의 `순서를 보장하지 않기` 때문에 배열과 달리 인덱스를 사용하여 접근할 수 없고, 값의 유일성에 중점을 둡니다.

  

- **중복된 값이 없음**
    - `Set` 은 모든 값이 고유해야 합니다. 동일한 값이 중복으로 저장될 수 없습니다.
- **순서가 없음**
    - 값이 특정 순서대로 저장되지 않으며, 추가된 순서와 관계없이 임의의 순서로 저장됩니다.
- **빠른 검색**
    - 값의 순서와 관계없이, `Set` 에서 값을 검색하는 작업이 매우 빠릅니다.

  

### 🔴 Set 선언 및 초기화

빈 Set을 선언할 때는 Set<Element>로 타입을 명시해줘야 합니다. `Set` 은 ==**타입을 명시하지 않으면 배열로 추론됩니다.**==

```Swift
var empySet: Set<String>() // String 타입의 빈 Set 선언
```

  

초기값을 가진 Set 선언은 아래 코드와 같습니다.

```Swift
var fruits: Set<String> = ["Apple", "Banana"]
```

  

### 🔴 Set의 주요 메서드와 사용법

`insert(_:)` 메서드를 사용하여 Set에 값을 추가할 수 있습니다.

```Swift
var colors: Set = ["Red", "Green", "Blue"]
colors.insert("Yellow")  // "Yellow" 추가
print(colors)
```

  

`remove(_:)` 메서드를 사용해 특정 값을 제거할 수 있습니다. 값이 존재하지 않을 경우 `nil`을 반환합니다.

```Swift
colors.remove("Green")  // "Green" 제거
print(colors)
```

  

### 🔴 Set의 집합 연산

Set은 집합 연산을 수행할 수 있는 강력한 기능을 제공합니다. 이 기능을 사용하면 두 개의 Set 간에 교집합, 합집합, 차집합 등을 계산할 수 있습니다.

  

`교집합` , 두 Set간의 공통된 값을 찾을 때 사용합니다.

```Swift
let setA: Set = [1, 2, 3, 4, 5]
let setB: Set = [4, 5, 6, 7, 8]

let intersection = setA.intersection(setB)
print(intersection)  // 출력: [4, 5]
```

  

`합집합`, 두 Set 간의 모든 값을 결합하여 중복을 제거한 값을 반환합니다.

```Swift
let unionSet = setA.union(setB)
print(unionSet)  // 출력: [1, 2, 3, 4, 5, 6, 7, 8]
```

  

`차집합`, 한 Set에서 다른 Set에 있는 값을 제외한 나머지 값을 반환합니다.

```Swift
let subtractingSet = setA.subtracting(setB)
print(subtractingSet)  // 출력: [1, 2, 3]
```

  

`대칭 차집합`, 두 Set 간의 교집합을 제외한 값을 반환합니다.

```Swift
let symmetricDifferenceSet = setA.symmetricDifference(setB)
print(symmetricDifferenceSet)  // 출력: [1, 2, 3, 6, 7, 8]
```

  

  

Set은 배열과 달리 값의 순서를 유지하지 않으므로, 값 검색, 삽입, 삭제 등의 연산이 매우 빠르게 이루어집니다. 특히 많은 양의 데이터에서 중복을 제거하거나 특정 값을 빠르게 검색해야 할 때 유용합니다.

그렇기 때문에 실제로 `선택된 항목 관리`, `중복된 단어 필터링` 등등 다양하게 쓰입니다.

### 😃 열거형(Enum)

> 열거형 `enum` 은 ==**연관된 값의 그룹을 정의**==하고, 코드에서 이러한 값들을 보다 구조화된 방식으로 사용하도록 돕는 자료형입니다. Swift의 열거형은 단순한 값의 그룹을 정의하는 것 이상으로, 각 값에 추가 정보를 저장하거나 메서드를 정의하는 등 강력한 기능을 제공합니다.

> 열거형 내의 각 값은 **열거형 케이스** 또는 **멤버**라고 하며, 이 값들은 고유하며 특정한 의미를 가집니다.

  

- **타입 안정성**
    - 열거형은 정해진 값만 사용하도록 강제하여 타입 안전성을 제공합니다.
- **추가 기능**
    - 각 케이스에 연관된 값을 저장하거나 메서드를 추가하여 열거형을 확장할 수 있습니다.

  

### 🔴 열거형 선언

열거형은 `enum` 키워드를 사용하여 선언합니다. 각 케이스는 열거형 내부에 하나의 값으로 나열됩니다.

```Swift
enum CompassDirection {
	case north
	case south
	case east
	case west
}
```

  

위에 열거형에 정의된 케이스는 아래 코드와 같이 사용할 수 있습니다.

```Swift
var direction: CompassDirection = .north
```

  

### 🔴 열거형의 원시값

열거형의 각 케이스에 **원시값**을 지정할 수 있습니다. 원시값은 각 케이스와 연관된 값으로, 문자열, 정수, 실수 등을 사용할 수 있습니다.

```Swift
enum Weekday: Int {
    case monday = 1
    case tuesday
    case wednesday
    case thursday
    case friday
    case saturday
    case sunday
}
```

  

열거형 값에 해당하는 원시값을 가져오려면 `rawValue` 속성을 사용합니다.

```Swift
let today: Weekday = .friday
print("오늘은 \(today.rawValue)번째 요일입니다.")
```

  

### 🔴 열거형의 연관값

Swift 열거형은 각 케이스에 연관된 값을 저장할 수 있습니다. 열거형의 각 케이스가 각각 다른 형태의 데이터를 가질 수 있습니다.

```Swift
enum Barcode {
    case upc(Int, Int, Int, Int)
    case qrCode(String)
}
```

  

연관 값이 있는 열거형 케이스는 값을 함께 저장하며, 이를 사용할 때는 각 케이스에 맞는 값을 지정해줘야 합니다.

```Swift
var productBarcode: Barcode = .upc(8, 1111, 5555, 2)
productBarcode = .qrCode("ABCDE")

print(productBarcode)
```

  

### 🔴 열거형의 메서드 정의

Swift의 열거형은 메서드를 가질 수 있습니다. 즉, 열거형의 각 케이스에 대해 특정한 동작을 수행하는 함수를 정의할 수 있습니다.

```Swift
enum LightSwitch {
	case on
	case off
	
	mutating func toggle() {
		self = (self == .on) ? .off : .on
	}
}
```

```Swift
var light: LightSwitch = .off
light.toggle()
print(light)
```

  

### 🔴 열거형의 Iterator

Swift에서 열거형 자체는 반복할 수 있는 타입이 아닙니다. 기본적으로 열거형은 배열이나 딕셔너리처럼 `for-in` 구문을 사용하여 각 케이스를 순회할 수 없습니다. 그러나 열거형에 CaseIterable 프로토콜을 채택하면, 열거형의 모든 케이스를 `반복 가능` 하게 만들 수 있습니다.

  

```Swift
enum Beverage: CaseIterable {
    case coffee
    case tea
    case juice
}
```

Beverage 열거형은 `CaseIterable` 프로토콜을 채택했기 때문에 `allCases` 라는 자동 생성된 배열을 사용할 수 있습니다. 프로토콜의 개념에 대한 설명은 추후 문법 워크북을 통해 학습하게 될 겁니다.

```Swift
for beverage in Beverage.allCases {
    print(beverage)
}
```

  

열거형은 앱의 다양한 상태를 관리하는 데 매우 유용합니다. 로그인 상태 관리, 네트워크 요청 상태 관리, UI 상태 관리 등 상태가 명확하게 정의된 값을 갖도록 하여, 코드의 가독성을 높이고 오류 발생을 방지할 수 있습니다.

# 📚 3주차 실습

---

### 문제 1. 딕셔너리 실습

학생들의 이름과 그들의 점수를 관리하는 프로그램 작성

1. 학생들의 이름(Alice, Bob, Min)을 키로, 점수를 값으로 가지는 딕셔너리를 선언하세요
2. 학생 “Alice”의 점수를 95점으로 수정하세요
3. “Bob”의 점수를 삭제하고, 남은 학생들의 점수를 출력하세요

  

위 세가지 문제에 대해 아래 코드 칸에 넣으시면 됩니다!

```Swift
// 1. 학생들의 점수 딕셔너리 선언



// 2. “Alice”의 점수를 95점으로 수정



// 3. “Bob”의 점수를 삭제하고, 남은 학생들의 점수를 출력
```

  

결과 사진을 넣어주세요!

[![](https://www.notion.so)](https://www.notion.so)

### 문제 2. Set 실습

Set를 사용하여 중복되지 않는 과일 목록을 관리하는 프로그램 작성

1. Set를 사용하여 “Apple”, “Banana”, “Orange”를 추가하는 과일 목록을 선언
2. “Banana”가 이미 존재하는지 확인하고, 존재하면 “Mango”를 추가하세요
3. 세트에 있는 모든 과일을 반복문으로 출력하세요

```Swift
// 1. 과일 목록 세트 선언


// 2. “Banana”가 이미 존재하는지 확인하고, 존재하면 “Mango”를 추가하세요


// 3. 세트에 있는 모든 과일을 반복문으로 출력하세요
```

  

결과 사진을 넣어주세요!

[![](https://www.notion.so)](https://www.notion.so)

### 문제 3. Enum 실습

아래 코드에서 **3번의 코드**와 **결과화면**을 보고 ==**1번과 2번을 완성**==하세요

==**단, 케이스 success와 failure에 대한 연관 값은 String 자료형입니다.**==

- **결과 화면**

![[스크린샷_2024-09-12_오후_10.41.10.png]]

  

- **코드 작성 칸**

```Swift
// 1. 네트워크 요청 상태 열거형 정의



// 2. 네트워크 요청 상태를 나타내는 변수 선언



// 3. switch문으로 상태에 맞는 출력 작성
switch currentState {
case .idle:
    print("현재 대기 상태입니다.")
case .requesting:
    print("요청 중입니다...")
case .success(let success):
    print("요청 성공: \(success)")
case .failure(let error):
    print("요청 실패: \(error)")
}
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