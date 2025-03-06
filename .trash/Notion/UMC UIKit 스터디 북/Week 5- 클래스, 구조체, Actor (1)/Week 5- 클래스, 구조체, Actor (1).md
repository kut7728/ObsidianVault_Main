- [[#📋 학습 목표]]
- [[#🔥 5주차 개념 설명]]
    - [[#😃 Class 이해하기]]
    - [[#🧐 Struct 이해하기]]
    - [[#😁 Actor 이해하기]]
- [[#📚 5주차 실습]]
    - [[#문제 1. 은행 계좌 관리 시스템 - Class 구현]]
    - [[#문제 2. 차량관리 시스템 - Struct 구현]]
    - [[#문제 3. 비동기 주문 처리 시스템]]
- [[#📌 추가적으로 더 공부해 봤어요! ]]
- [[#❓ 이런 질문이 있어요!]]

## 📋 학습 목표

---

> **클래스 이해하기**  
>   
> **구조체 이해하기**  
>   
> **Actor 이해하기**  

## 🔥 5주차 개념 설명

---

### 😃 Class 이해하기

> Swift에서 클래스를 이해하는 것은 객체 지향 프로그래밍의 기본을 다지는 중요한 단계입니다. ==**클래스는 관련된 속성과 메소드를 하나의 청사진으로 묶어 데이터와 기능을 캡슐화하고, 객체 지향적인 설계 패턴을 효과적으로 사용할 수 있게 해줍니다.**== 클래스는 코드의 재사용성을 높이고, 복잡한 시스템을 구조적으로 관리할 수 있도록 해주는 중요한 개념입니다.

  

### 1. 클래스 기본 개념

> 클래스는 객체 지향 프로그래밍에서 핵심적인 개념으로, 관련된 속성과 메서드를 하나의 청사진으로 묶어주는 역할을 합니다. Swift에서 클래스는 사용자 정의 타입의 일종으로, 데이터를 캡슐화하고 기능을 구현하며, 복잡한 프로그램을 구조적으로 설계할 수 있게 해줍니다.

### 🔴 클래스 정의 및 선언

Swift에서 클래스를 정의하려면 `class` 키워드를 사용합니다. 클래스 정의는 속성과 메서드를 포함할 수 있으며, 이를 통해 객체의 상태와 동작을 정의합니다.

```Swift
class 클래스이름 {
    // 속성 정의
    var 속성1: 타입 = 초기값
    var 속성2: 타입 = 초기값
    
    // 메서드 정의
    func 메서드이름() {
        // 메서드 구현 내용
    }
}
```

```Swift
class UMC {
	var name: String
	var count: Int
	
	init(name: String, count: Int) {
		self.name = name
		self.count = count
	}
	
	func message() {
		print("안녕하세요! UMC입니다")
	}
}
```

  

### 🔴 클래스 인스턴스 생성

클래스를 정의한 후에는 해당 클래스를 기반으로 인스턴스를 생성하여 사용할 수 있습니다. 클래스 인스턴스를 생성하려면 클래스 이름을 사용하고, 이니셜라이저를 호출하면 됩니다.

```Swift
let umc = UMC(name: "ChungAng", count: 40)
```

  

### 🔴 클래스의 속성

클래스의 속설은 객체의 상태를 나타내는 변수 또는 상수를 의미합니다. 속성은 클래스 내부에 정의되며 `var` , `let` 키워드를 사용하여 선언합니다.

  

- **저장 속성**
    - 값을 저장하고 관리하는 속성입니다. 위 코드에서 `name` 과 `age` 는 UMC 클래스의 저장 속성입니다.
- **계산 속성**
    
    - 실제로 값을 저장하지 않고, 다른 속성이나 연산을 통해 값을 계산하여 변환하는 속성입니다.
    - 아래의 코드에서 `diameter` 는 계산 속성으로, `radius` 의 값을 기반으로 지름을 계산하여 반환합니다.
    
    ```Swift
    class Circle {
    	var radius: Double
    	var diameter: Double {
    		return radius * 2
    	}
    		
    	init(radius: Double) {
    		self.radius = radius
    	}
    }
    ```
    

  

### 🔴 클래스의 메서드

클래스의 메서드는 특정 작업을 수행하는 함수입니다. 메서드는 클래스 내부에서 정의되며, 클래스 인스턴스를 통해 호출할 수 있습니다.

  

- **인스턴스 메서드**
    - 위 코드에서 `message` 메서드는 `UMC` 인스턴스의 속성을 사용하여 인사 메시지를 출력합니다.
- **타입 메서드**
    
    - 클래스 자체와 연관된 작업을 수행하며, `static` 또는 `class`키워드를 사용하여 선언합니다.
    
    ```Swift
    class Math {
    	class func square(_ number: Int) -> Int {
    			return number * number
    		}
    	}
    
    let result = Math.square(5)
    print(result)
    
    // result 값 : 25
    ```
    

### 2. 클래스 초기화

> 클래스 초기화는 객체를 생성할 때 그 ==**객체의 초기 상태를 설정하는 과정**==입니다. Swift에서는 클래스의 각 속성에 초기 값을 할당하거나, 이니셜라이저를 통해 인스턴스를 초기화합니다. 이니셜라이저는 클래스의 인스턴스가 생성될 때 호출되며, 속성에 기본 값을 설정하고 필요한 초기 설정을 수행합니다.

  

### 🔴 기본 이니셜라이저

Swift에서는 클래스의 모든 저장 속성에 기본 값을 제공하면, 자동으로 기본 이니셜라이저가 제공됩니다. 이 ==**기본 이니셜라이저는 매개변수가 없는 형태로, 객체를 생성할 때 기본 값을 사용하여 인스턴스를 초기화**==합니다.

```Swift
class Animal {
	var name: String = "Dog"
	var age: Int = 0
}

let animal = Animal() // 기본 이니셜라이저 사용
print(animal.name) // "Dog"
print(animal.age) // 0
```

  

### 🔴  커스텀 이니셜라이저 작성

원하는 방식으로 객체를 초기화하려면 커스텀 이니셜라이저를 정의할 수 있습니다. 커스텀 이니셜라이저는 `init` 키워드를 사용하여 정의하며, 필요한 매개변수를 받아 객체를 초기화합니다.

```Swift
class Person {
	var name: String
	var age: Int
	
	init(name: String, age: Int) {
			self.name = name
			self.age = age
		}
	}
```

```Swift
let person = Person(name: "Jeong", age: 28)
print(person.name) // "Jeong"
print(person.age) // 28
```

  

### 🔴  초기화 실패

객체를 초기화할 때 특정 조건을 만족하지 못하면 초기화에 실패할 수 있습니다. 이 경우, 실패 가능한 이니셜라이저를 사용할 수 있습니다. 실패 가능한 이니셜라이저는 `init?` 형식으로 정의되며, 초기화에 실패하면 `nil` 을 반환합니다.

```Swift
class Vehicle {
    var model: String
    
    init?(model: String) {
        if model.isEmpty {
            return nil // 초기화 실패
        }
        self.model = model
    }
}
```

```Swift
/* 초기화 성공 */
if let car = Vehicle(model: "KiA") {
	print("초기화 성공했습니다.") // 이 문장이 출력됩니다.
} else {
	print("초기화 실패")
}

/* 초기화 실패 */
if let invalidCar = Vehicle(model: "") {
	print("초기화 성공했습니다")
} else {
	print("초기화 실패") // 이 문장이 출력됩니다.
}
```

  

### 🔴  이니셜라이저 위임

이니셜라이저 위임은 클래스의 이니셜라이저에서 다른 이니셜라이저를 호출하여 속성을 초기화하는 과정입니다. Swift에서는 클래스 내부에서 다른 이니셜라이저를 호출하여 코드의 중복성을 줄이고, 보다 명확한 초기화 과정을 구성할 수 있습니다.

  

- **자기 자신에게 위임**
    
    - 동일한 클래스 내에서 다른 이니셜라이저를 호출합니다.
    
    ```Swift
    	class Rectangle {
    		var width: Double
    		var height: Double
    		
    		init(width: Double, height: Double) {
    			self.width = width
    			self.height = height
    		}
    		
    		init() {
    			self.init(width: 0, height: 0)
    		}
    }
    ```
    
      
    
- **상속 계층에서 위임**
    
    - 서브클래스의 이니셜라이저가 부모 클래스의 이니셜라이저를 호출하여 속성을 초기화합니다.
    
    ```Swift
    class Animal {
        var name: String
        
        init(name: String) {
            self.name = name
        }
    }
    
    class Dog: Animal {
        var breed: String
        
        init(name: String, breed: String) {
            self.breed = breed
            super.init(name: name)
        }
    }
    ```
    

  

### 🔴  이니셜라이저 상속

Swift의 클래스에서는 기본적으로 부모 클래스의 이니셜라이저가 상속되지 않습니다. 그러나 특정 조건에서 부모 클래스의 이니셜라이저를 상속받을 수 있습니다. ==**서브클래스가 모든 속성에 기본 값을 제공하거나, 부모 클래스의 모든 지정 이니셜라이저를 구현한 경우 부모 클래스의 편의 이니셜라이저를 상속받을 수 있습니다.**==

```Swift
class Parent {
	var name: String
	
	init(name: String) {
		self.name = name
	}
}

class Child: Parent {
	var age: Int
	
	init(name: String. age: Int) {
		self.age = age
		super.init(name: name)
	}
}
```

```Swift
let child = Child(name: "Jeong", age: 28)
```

  

### 🔴  편의 이니셜라이저

Swift에서 `**convenience init**` **는** 클래스에 추가적인 초기화 메서드를 정의할 때 사용됩니다. 주로 지정된 이니셜라이저를 호출하여 초기화 과정을 단순화하거나 편리한 방법을 제공하기 위해 사용됩니다.

  

편의 이니셜라이저 사용을 통해 ==**동일한 초기화 과정을 반복하지 않고, 다른 이니셜라이저를 호출하여 코드를 단순화할 수 있습니다.**==

  

> [!important]
> 
> - `convenience init` 은 반드시 같은 클래스 내의 다른 이니셜라이저를 호출해야 하며, 최종적으로는 지정된 이니셜라이저를 호출해야 합니다.
> - `convenience init` 에서 `self.init` 을 사용하여 지정된 이니셜라이저를 호출해야 합니다.

```Swift
class Person {
	var name: String
	var age: Int
	
	init(name: String, age: Int) {
		self.name = name
		self.age = age
	}
	
	convenience init(name: String) {
		self.init(name: name, age: 28)
	}
	
	convenience init() {
		self.init(name: "Jeong", age: 28)
	}
```

```Swift
let personA = Person(name: "Jeong", age: 28) // 지정 이니셜러이저 사용
let personB = Person(name: "Jeong") // 편의 이니셜라이저 사용 (나이 생략)
let personC = Person() // 편의 이니셜라이저 사용 (이름과 나이 모두 생략)
```

  

### 3. 클래스와 상속

> 상속은 객체 지향 프로그래밍에서 코드 재사용성을 높이고 클래스 간의 계층 구조를 정의항는 중요한 개념입니다. Swift에서는 한 클래스가 다른 클래스의 속성과 메서드를 물려받아 사용할 수 있으며, 이를 통해 기존 클래스의 기능을 확장하거나 변경할 수 있습니다. 상속을 통해 공통 기능을 부모 클래스에 정의하고, 자식 클래스에서 이를 재사용하거나 덮어쓸 수 있습니다.

  

### 🔴 클래스 상속

부모 클래스를 정의하고 이를 기반으로 자식 클래스를 정의할 수 있습니다. 서브클래스는 부모 클래스의 모든 속성과 메서드를 상속받으며 새로운 기능을 추가하거나 기존의 기능을 재정의할 수 있습니다.

```Swift
class 부모 클래스 {

}

class 자식 클래스: 부모 클래스 {

}
```

```Swift
class Vehicle {
    var speed = 0
    
    func description() -> String {
        return "\(speed) km/h"
    }
}

class Car: Vehicle {
    var gear = 1
    
    func changeGear(to gear: Int) {
        self.gear = gear
    }
    
    // 부모 클래스의 메서드를 재정의하여 추가적인 정보를 제공
    override func description() -> String {
        return super.description() + " 현재 기어 :  \(gear)"
    }
}
```

```Swift
let car = Car()
car.speed = 120
car.changeGear(to: 3)
print(car.description()) // 결과를 직접 출력시켜보시기 바라겠습니다.
```

  

### 🔴 상속 방지

상속을 방지하고 특정 클래스가 상속될 수 없도록 만들기 위해 `final` 키워드를 사용할 수 있습니다. `final` 키워드를 클래스 선언 앞에 사용하면 해당 클래스는 더 이상 상속될 수 없습니다.

```Swift
final class Animal {
	var name: String
	
	init(name: String) {
		self.name = name
	}
}
```

  

### 🔴 메서드, 속성 재정의

서브클래스에서 부모 클래스의 속성이나 메서드를 재정의할 수 있습니다. 재정의는 서브클래스에서 부모 클래스의 기본 구현을 변경하거나 확장할 수 있게 해줍니다. Swift에서는 재정의하려는 메서드, 속성, 서브스크립트 앞에 `Override` 키워드를 사용하여 재정의할 수 있음을 명시해야 합니다.

```Swift
class Animal {
	var sound: String {
			return "sound"
		}
		
		func makeSound() -> String {
			return sound
		}
}

class Dog: Animal {
	override var sound: String {
		return "Dog sound"
	}
	
	override func makeSound() -> String {
		return "소리: " + super.makeSound()
	}
}
```

```Swift
let dog = Dog()
print(dog.makeSound()) // 소리: Dog sound
```

  

### 🔴 부모 클래스의 멤버 접근

`super` 키워드는 서브클래스에서 부모 클래스의 메서드나 속성에 접근할 때 사용됩니다. 주로 메서드를 재정의할 때 부모 클래스의 기본 동작을 호출하고 추가적인 동작을 정의하고자 할 때 사용합니다.

```Swift
class Shape {
	func draw() {
		print("원을 그려봐요")
	}
}

class Circle: Shape {
	override func draw() {
			super.draw()
			print("네모를 그려봐요")
		}
	}
```

```Swift
let circle = Circle()
circle.draw()
// 원을 그려봐요
// 네모를 그려봐요
```

  

### 4. 클래스와 접근 제어

> 접근 제어는 코드 내에서 클래스, 속성, 메서드, 함수, 이니셜라이저 등에 대한 접근 권한을 제한하여 모듈성과 데이터 은닉을 강화하는 중요한 개념입니다. Swift는 다양한 접근 수준을 제공하여 클래스와 그 멤버들이 어디에서 어떻게 사용될 수 있는지 제어할 수 있습니다. 올바른 접근 제어를 사용하면 코드의 가독성을 높이고, 외부에서의 부적절한 사용을 방지할 수 있습니다.

  

### 🔴 접근 제어자

- **open**
    - 모듈 외부에서 접근 가능하며, 클래스와 메서드는 상속 및 재정의가 가능합니다. 주로 프레임워크에서 사용됩니다.
- **public**
    - 모듈 외부에서 접근 가능하지만, 클래스는 상속 및 재정의가 불가능합니다. 주로 라이브러리나 프레임워크의 API를 제공할 때 사용됩니다.
- **internal**
    - 같은 모듈 내에서만 접근 가능하며, 모듈 외부에서는 접근할 수 없습니다. 기본 접근 제어 수준으로, 명시하지 않으면 **internal**로 설정됩니다.
- **fileprivate**
    - 같은 파일 내에서만 접근 가능합니다. 다른 파일에서는 접근할 수 없습니다.
- **private**
    - 같은 선언 내에서만 접근 가능하며, 다른 범위에서는 접근할 수 없습니다.

```Swift
public class Car {
	public var brand: String
	internal var model: String
	fileprivate var year: Int
	private var engineNumber: String
	
	public init(brand: String, model: String, year: Int, engineNumber: String) {
        self.brand = brand
        self.model = model
        self.year = year
        self.engineNumber = engineNumber
  }
  
  public func startEngine() {
        print("Engine started")
    }
    
    fileprivate func updateYear(_ year: Int) {
        self.year = year
    }
    
    private func checkEngineNumber() -> Bool {
        // 엔진 번호를 확인하는 내부 로직
        return engineNumber == "1234"
    }
}
```

  

### 🔴 공개 수준

- **open**
    - 모듈 외부에서 접근 가능
    - 클래스와 메서드는 상속 및 재정의 가능
    - 외부에서 자유롭게 상속을 허용해야 할 때 사용
- **public**
    - 모듈 외부에서 접근 가능
    - 상속 및 재정의 불가능
    - 외부에서 접근 가능하지만, 기능 확장을 제한고자 할 때 사용
- **internal**
    - 같은 모듈 내에서만 가능
    - 모듈 외부에서 접근 불가
    - 기본 접근 수준이며, 대부분의 코드에서 사용
- **fileprivate**
    - 같은 파일 내에서만 접근 가능
    - 파일 내의 다른 클래스나 구조체와 데이터를 공유할 때 유용
- **private**
    - 같은 선언 범위 내에서만 접근 가능
    - 데이터와 메서드를 완전히 감추고, 외부 접근을 차단하고자 할 때 사용

### 5. 클래스의 확장

> 클래스의 확장은 기==**존 클래스, 구조체, 열거형, 프로토콜에 새로운 기능을 추가하는 강력한 기능**==입니다. 확장을 사용하면 ==**원래 소스 코드를 수정하지 않고도 기존 타입에 메서드, 속성, 이니셜라이저, 서브스크립트, 프로토콜 준수 등을 추가**==할 수 있습니다. 확장은 타입의 기본 기능을 확장하거나 새로운 기능을 모듈화하여 코드의 가독성과 재사용성을 높일 수 있습니다.

  

### 🔴 클래스 확장을 통한 기능 추가

클래스 확장을 사용하여 기존 클래스에 새로운 메서드, 계산 속성, 서브스크립트, 탙입 메서드 등을 추가할 수 있습니다. 이때, 확장에서 저장 속성을 추가할 수는 없으며, 계산 속성만 추가할 수 있습니다.

```Swift
class Rectangle {
	var width: Double
	var height: Double
	
	init(width: Double, height: Double {
			self.width = width
			self.height = height
		}
}

extension Rectangle {
	var area: Double {
			return width * height
		}
		
		func description() -> String {
			return "width: \(width), height: \(height)"
		}
}
```

```Swift
let rect = Rectangle(width: 10, height: 10)
print("Area: \(rect.area)) // 직접 확인 해주시기 바랍니다.
print(rect.description()) // 직접 확인 해주시기 바랍니다.
```

  

### 🔴 프로토콜 준수와 클래스 확장

클래스 확장은 특정 클래스가 새로운 프로토콜을 준수하도록 만들거나, 이미 준수하고 있는 프로토콜의 요구사항을 구현하는 데 사용할 수 있습니다. 기존 클래스의 소스 코드를 수정하지 않고도 프로토콜 준수를 쉽게 구현할 수 있습니다.

  

```Swift
protocol Printable {
	func printDetail()
}
```

```Swift
class Book {
	var title: String
	var author: String
	
	init(title: String, author: String) {
			self.title = title
			self.author = author
	}
}

extension Book: Printable {
	func printDetail() {
			print("hello")
	}
}
```

```Swift
let book = Book(title: "swift", author: "Jeong")
book.printDetail() // hello 출력
```

  

> [!important]
> 
> ### 클래스 확장의 장점
> 
> 1. **기능 분리**
>     1. 클래스 확장은 기능을 논리적으로 분리하여 코드를 더 명확하고 가독성 있게 만들 수 있습니다.
> 2. **코드 재사용성**
>     1. 확장은 클래스에 새로운 기능을 추가할 수 있어, 코드 재사용성을 높이고 중복 코드를 줄일 수 있습니다.
> 3. **유연한 프로토콜 준수**
>     1. 기존 클래스에 프로토콜을 쉽게 준수시킬 수 있어, 클래스를 여러 곳에서 일관되게 사용할 수 있습니다.
> 4. **원본 코드 수정 불필요**
>     1. 클래스의 원본 소스 코드를 수정하지 않고도 새로운 기능을 추가할 수 있습니다.

> [!important]
> 
> ### 클래스 확장의 제한사항
> 
> 1. **저장 속성 추가 불가**
>     1. 확장에서 새로운 저장 속성을 추가할 수 없습니다. 하지만 계산 속성이나 메서드만 추가할 수 있습니다.
> 2. **오버라이딩 불가**
>     1. 확장에서 기존 클래스의 메서드를 재정의할 수 없습니다. 서브클래싱을 통해서만 메서드 오버라이딩 가능합니다,
> 3. **접근 제어자 준수**
>     1. 확장에서는 기존 클래스의 접근 제어를 준수해야 합니다.

  

  

### 6. 클래스와 메모리 관리

> Swift에서는 메모리 관리를 위해 ==**자동 참조 카운트(ARC)**==를 사용합니다. ARC는 객체의 생명 주기를 추적하고 필요하지 않은 객체를 자동으로 메모리에서 해제하여 메모리 누수를 방지합니다. 그러나 클래스 인스턴스 간의 강한 참조 순환 문제가 발생할 수 있으며, 이를 방지하기 위해 **약한 참조**와 **미소유 참조** 같은 기법을 사용합니다.

  

### 🔴 참조 카운트 이해

`참조 카운트` 는 객체가 현재 몇 개의 변수나 상수에 의해 참조되고 있는지를 나타내는 값입니다. 객체의 참조 카운트는 인스턴스가 생성되거나 참조될 때 증가하고, 참조가 해제될 때 감소합니다.

참조 카운트가 0이되면 해당 객체는 해제됩니다.

```Swift
class Person {
    let name: String
    
    init(name: String) {
        self.name = name
        print("\(name) 이니셜")
    }
    
    deinit {
        print("\(name) 디이니셜")
    }
}
```

```Swift

var person1: Person? = Person(name: "Alice") // 참조 카운트: 1
var person2 = person1                         // 참조 카운트: 2

person1 = nil                                 // 참조 카운트: 1
person2 = nil                                 // 참조 카운트: 0, 메모리 해제됨
```

  

### 🔴 강함 참조 순환

강한 참조 순환은 두 객체가 서로 강하게 참조하여 서로의 참조 카운트를 0으로 만들 수 없게 되어 메모리에서 해제되지 않는 현상을 말합니다. 이것은 `메모리 누수` 를 일으키는 주 원인이기도 해요!

```Swift
class Person {
    let name: String
    var apartment: Apartment? // Person은 Apartment를 강하게 참조
    
    init(name: String) {
        self.name = name
    }
    
    deinit {
        print("\(name) 이니셜")
    }
}

class Apartment {
    let unit: String
    var tenant: Person? // Apartment도 Person을 강하게 참조
    
    init(unit: String) {
        self.unit = unit
    }
    
    deinit {
        print("Apartment \(unit) 디이니셜")
    }
}
```

```Swift
var alice: Person? = Person(name: "Alice")
var bob: Apartment? = Apartment(unit: "Bob")

alice!.apartment = bob
bob!.tenant = alice

alice = nil  // Person 인스턴스의 참조 카운트가 1로 남아 있음
bob = nil // Apartment 인스턴스의 참조 카운트가 1로 남아 있음

// alice와 bob은 서로 강하게 참조하고 있기 때문에 메모리에서 해제되지 않음
```

  

### 🔴 약한 참조와 미소유 참조

강한 참조 순환 문제를 해결하기 우해 약한 참조(weak)와 미소유 참조(unowned)를 사용할 수 있습니다. 객체의 참조 카운트를 증가시키지 않으므로 강한 참조 순환을 방지할 수 있습니다.

  

> [!important]
> 
> ### 약한 참조(weak)
> 
> 약한 참조는 참조 카운트를 증가시키지 않는 참조입니다. 객체가 해제되면 자동으로 `nil` 로 설정되며, 항상 옵셔널로 선언해야 합니다.
> 
> ```Swift
> class Person {
>     let name: String
>     var apartment: Apartment?
>     
>     init(name: String) {
>         self.name = name
>     }
>     
>     deinit {
>         print("\(name) 이니셜")
>     }
> }
> 
> class Apartment {
>     let unit: String
>     weak var tenant: Person? // 약한 참조 사용
>     
>     init(unit: String) {
>         self.unit = unit
>     }
>     
>     deinit {
>         print("Apartment \(unit) 디이니셜")
>     }
> }
> 
> var alice: Person? = Person(name: "Alice")
> var bob: Apartment? = Apartment(unit: "Bob")
> 
> alice!.apartment = unit4A
> bob!.tenant = alice
> 
> alice = nil  // Person 인스턴스 해제됨
> bob = nil // Apartment 인스턴스 해제됨
> ```

> [!important]
> 
> ### 미소유 참조(unowned)
> 
> 미소유 참조는 참조 카운트를 증가시키지 않지만, 옵셔널이 아닌 비옵셔널로 선언할 수 있습니다. 객체가 해제되었을 때도 `nil` 이 되지 않고 접근하면 런타인 오류가 발생합니다.
> 
> ```Swift
> class Customer {
>     let name: String
>     var card: CreditCard?
>     
>     init(name: String) {
>         self.name = name
>     }
>     
>     deinit {
>         print("\(name) is being deinitialized")
>     }
> }
> 
> class CreditCard {
>     let number: Int
>     unowned var customer: Customer // 미소유 참조 사용
>     
>     init(number: Int, customer: Customer) {
>         self.number = number
>         self.customer = customer
>     }
>     
>     deinit {
>         print("CreditCard #\(number) is being deinitialized")
>     }
> }
> 
> var john: Customer? = Customer(name: "John")
> john!.card = CreditCard(number: 1234, customer: john!)
> 
> john = nil // Customer와 CreditCard 인스턴스 모두 해제됨
> ```

  

### 🔴 메모리 누수 방지 기법

1. **약한 참조(**`**weak**`**)와 미소유 참조(**`**unowned**`**) 사용**
    1. 객체 간의 참조 관계를 설정할 때, 강한 참조 순환이 발생할 수 있는 경우 약한 참조나 미소유 참조를 사용하여 참조 카운트를 증가시키지 않도록 합니다.
2. **클로저의 캡처 리스트 사용**
    
    1. 클로저가 객체를 강하게 참조하여 강한 참조 순환을 일으킬 수 있습니다. 이것을 방지하기 위해 클로저의 캡쳐 리스트에 `[weak self]` 또는 `[unowned self]` 를 사용하여 클로저가 객체를 약하게 참조하도록 합니다.
    
    ```Swift
    class ViewController {
        var message = "Hello, World!"
        
        lazy var greeting: () -> String = { [unowned self] in
            return self.message
        }
        
        deinit {
            print("ViewController 디이니셜라이저")
        }
    }
    
    var vc: ViewController? = ViewController()
    print(vc?.greeting()) // "Hello, World!"
    vc = nil // ViewController 해제됨
    ```
    

  

### 7. 클래스의 고급 기능

> Swift 클래스는 기본적인 속성과 메서드뿐만 아니라 다양한 고급 기능을 제공합니다. 클래스 타입 메서드와 속성, `Self` 키워드, 서브스크립트 등을 활용하면 클래스를 효율적으로 설계할 수 있습니다.

  

### 🔴 클래스 타입 메서드와 속성

클래스는 인스턴스 메서드와 속성 외에도 `타입 메서드` 와 `타입 속성` 을 가질 수 있습니다. 타입 메서드와 속성은 클래스의 인스턴스가 아닌 클래스 자체에 속하며, 특정 클래스의 모든 인스턴스에서 공통적으로 사용됩니다.

  

- **클래스 타입 메서드**
    
    - 타입 메서드는 클래스 자체와 관련된 작업을 수행하며 `static` `class` 키워드를 사용하여 선언합니다. `class` 키워드를 사용하면 서브클래스에서 재정의할 수 있는 타입 메서드를 정의할 수 있습니다.
    
    ```Swift
    class Math {
    		static func square(_ number: Int) -> Int {
    				return number * number
    		}
    			
    		class func cube(_ number: Int) -> Int {
    			return number * number * number
    		}
    }
    
    print(Math.square(4)) // 16
    print(Math.cube(4))	// 64
    ```
    
      
    
- **클래스 타입 속성**
    
    - 타입 속성은 클래스의 모든 인스턴스에서 공유되는 속성입니다. `static` 또는 `class` 키워드를 사용하며, 초기값을 설정해야 합니다. `let` 또는 `var` 로 선언할 수 있으며, `class` 키워드는 서브클래스에서 재정의가 가능한 타입 속성을 정의할 때 사용합니다.
    
    ```Swift
    class Configuration {
        static let timeout: Int = 30
        static var retries: Int = 3
    }
    
    print(Configuration.timeout) // 30
    print(Configuration.retries)     // 3
    
    Configuration.retries = 5
    print(Configuration.retries)     // 5
    ```
    
      
    

### 🔴 Self 키워드 활용

`self` 키워드는 클래스, 구조체, 열거형에서 자신을 참조하는 데 사용됩니다. `self` 는 인스턴스 자신을 가리키고, `self` 는 현재 타입을 가리킵니다.

  

- **인스턴스 메서드에서 self 사용**
    
    - `self` 키워드는 인스턴스 메서드 내에서 인스턴스 자신의 속성이나 메서드를 참조할 때 사용됩니다.
    
    ```Swift
    class Person {
        var name: String
        
        init(name: String) {
            self.name = name
        }
        
        func greet() {
            print("Hello, my name is \(self.name).") // self는 생략 가능
        }
    }
    
    let person = Person(name: "Jeong")
    person.greet() // "Hello, my name is Jeong."
    ```
    
      
    
- **타입 메서드에서 Self 사용**
    
    - 타입 메서드에서 `self` 는 현재 클래스 타입 자체를 의미합니다.
    
    ```Swift
    class Vehicle {
        var speed: Int
        
        init(speed: Int) {
            self.speed = speed
        }
        
        class func make() -> Self {
            return self.init(speed: 0)
        }
    }
    
    class Car: Vehicle {
        var model: String
        
        init(speed: Int, model: String) {
            self.model = model
            super.init(speed: speed)
        }
        
        override class func make() -> Self {
            return self.init(speed: 0, model: "KIA")
        }
    }
    
    let car = Car.make() // Car 인스턴스 생성
    print(car.model) // "KIA"
    ```
    
      
    

### 🔴 서브스크립트 구현

서브스크립트는 배열, 딕셔너리 등에서 사용하는 `[index]` 또는 `[key]` 형태의 구문을 사용자 정의 클래스나 구조체에서도 사용할 수 있도록 하는 기능입니다. 서브스크립트를 사용하여 객체의 내부 데이터를 간결하게 접근하고 수정할 수 있습니다.

  

- **서브스크립트 정의**
    
    - 서브스크립트는 `subscript` 키워드를 사용하여 정의하며, 매개변수와 반환 타입을 지정합니다. 읽기 전용 또는 읽기-쓰기 서브스크립트로 정의합니다.
    
    ```Swift
    /* 읽기 전용 서브스크립트 예시 */
    
    class Week {
        private var days = ["Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday"]
        
        subscript(index: Int) -> String {
            return days[index]
        }
    }
    
    let week = Week()
    print(week[0])
    print(week[6])
    ```
    
    ```Swift
    /* 읽기-쓰기 서브스크립트 예시 */
    
    class NumberList {
        private var numbers: [Int] = []
        
        subscript(index: Int) -> Int {
            get {
                return numbers[index]
            }
            set(newValue) {
                numbers[index] = newValue
            }
        }
        
        func addNumber(_ number: Int) {
            numbers.append(number)
        }
    }
    
    var list = NumberList()
    list.addNumber(10)
    list.addNumber(20)
    print(list[0]) // 10
    print(list[1]) // 20
    
    list[0] = 100
    print(list[0]) // 100
    ```
    

### 🧐 Struct 이해하기

> Swift에서 구조체는 객체 지향 프로그래밍의 핵심적인 데이터 타입 중 하나로, 클래스와 유사하게 여러 속성과 메서드를 하나의 청사진으로 묶어줍니다. 구==**조체는 값 타입으로 인스턴스가 생성될 때 해당 데이터가 복사되어 전달**==됩니다. 이로 인해, 구==**조체는 코드의 안전성을 높이고 예상치 못한 데이터 변경을 방지하는 데 유용**==합니다.

  

### 1. 구조체의 기본 개념

> 구조체(Struct)는 여러 속성과 메서드를 하나의 데이터 타입으로 묶어주는 Swift의 주요 데이터 타입 중 하나입니다. ==**구조체는 값 타입**==으로, ==**인스턴스 간 데이터가 독립적으로 존재**==하며, 데이터를 복사하여 전달하는 방식으로 작동합니다. 이러한 특성 덕분에 ==**구조체는 코드의 안전성을 높이고, 불변 데이터를 효과적으로 관리**==할 수 있습니다

  

### 🔴 클래스 타입 메서드와 속성

`struct` 키워드를 사용하여 정의하며, 내부에 속성과 메서드를 포함할 수 있습니다.

```Swift
struct 구조체이름 {
    // 속성 정의
    var 속성1: 데이터타입
    var 속성2: 데이터타입
    
    // 메서드 정의
    func 메서드이름() {
        // 메서드 구현
    }
}
```

```Swift
struct Rectangle {
    var width: Double
    var height: Double
    
    func area() -> Double {
        return width * height
    }
}
```

  

### 🔴 구조체 인스턴스 생성

구조체는 선언된 속성에 초기 값을 설정하거나, 이니셜라이저를 통해 인스턴스를 생성할 수 있습니다. 구조체는 Swift에서 기본적으로 자동으로 생성된 멤버와이즈 이니셜라이저를 제공합니다.

```Swift
struct Person {
    var name: String
    var age: Int
}

let personA = Person(name: "Jeong", age: 28) // 멤버와이즈 이니셜라이저 사용
print(personA.name) // "Jeong"
print(personA.age)  // 28
```

  

### 🔴 구조체와 클래스의 차이점

구조체와 클래스는 모두 속성과 메서드를 하나의 타입으로 묶어 데이터를 정의할 수 있지만, 근본적인 차이점이 있습니다.

- **구조체**
    
    - 값 타입, 인스턴스를 다른 변수나 상수에 할당하거나 함수에 전달할 때 값이 복사됩니다.
    - 각 인스턴스는 독립적인 메모리 공간을 가지며, 한 인스턴스의 변경이 다른 인스턴스에 영향을 미치지 않습니다.
    - 데이터 모델링, 불변 데이터 처리에 적합합니다.
    
    ```Swift
    struct Point {
        var x: Int
        var y: Int
    }
    
    var point1 = Point(x: 10, y: 20)
    var point2 = point1 // point1을 복사하여 point2 생성
    point2.x = 50       // point2의 x 값을 변경
    
    print(point1.x) // 10 (point1은 영향받지 않음)
    print(point2.x) // 50
    ```
    
      
    
- **클래스(참조 타입)**
    
    - 클래스는 참조 타입으로, 인스턴스를 다른 변수나 상수에 할당하거나 함수에 전달할 때 메모리 주소를 참조하게 됩니다.
    - 여러 참조가 동일한 인스턴스를 가리키며, 한 곳에서 변경된 내용이 다른 모든 참조에도 영향을 미칩니다.
    - 객체 간의 관계를 표현하거나, 상태가 변할 수 있는 복잡한 데이터 모델링에 적합합니다.
    
    ```Swift
    class Person {
        var name: String
        init(name: String) {
            self.name = name
        }
    }
    
    var personA = Person(name: "Jeong")
    var personB = person1 // personA의 참조를 personB에 할당
    personB.name = "Bob"  // personB의 name 값을 변경
    
    print(personA.name) // "Bob" (personA도 동일한 인스턴스를 참조)
    print(personB.name) // "Bob"
    ```
    
      
    
- **구조체의 사용 시기**
    - 단일 값을 기반으로 여러 관련 속성을 묶어야 할 때 (좌표, 크기, 범위 등)
    - 데이터가 독립적으로 존재해야 하며, 다른 인스턴스에 영향을 주지 않아야 할 때
    - 상속이 필요하지 않고, ==**단순한 데이터 모델링이 필요할 때**==

### 2. 구조체의 속성과 메서드

> 구조체는 다양한 속성과 메서드를 포함하여 데이터와 기능을 정의할 수 있습니다. 속성은 구조체가 보유하는 데이터나 상태를 나타내며, 메서드는 구조체가 수행할 수 있는 동작을 정의합니다. 구조체의 속성에는 값을 저장하는 ==**저장 속성**==과 특정 값을 계산하여 반환하는 ==**계산 속성**==이 있습니다. 또한, 구조체의 메서드는 데이터를 처리하고 특정 기능을 수행하기 위한 함수를 정의합니다.

  

### 🔴 저장 속성

저장 속성은 구조체 내부에 데이터를 저장하고 관리하는 속성입니다. 저장 속성은 초기화 시 값을 설정하거나, 이후에 값을 변경할 수 있습니다. `var` 로 선언하면 변경 가능한 속성이 되고, `let` 으로 선언하면 초기화 후 값을 변경할 수 없는 상수 속성이 됩니다.

```Swift
struct Car {
    var brand: String
    var model: String
    let year: Int
}
```

```Swift
var car1 = Car(brand: "Toyota", model: "Corolla", year: 2020)
print(car1.brand) // "Toyota"
print(car1.year)  // 2020

car1.brand = "Honda" // 변경 가능
car1.year = 2021   // 오류 발생: 'year'는 상수 저장 속성이므로 변경할 수 없음
```

  

### 🔴 계산 속성

계산 속성은 실제 값을 저장하지 않고, 특정 값을 계산하여 반환하는 속성입니다. 계산 속성은 `get` 블록을 사용하여 값을 반환하고, 필요한 경우 `set` 블록을 사용하여 값을 설정할 수 있습니다. 동적인 값 계산이나 간접적인 데이터 접근이 가능합니다.

```Swift
struct Rectangle {
    var width: Double
    var height: Double
    
    // 계산 속성: 면적을 계산하여 반환
    var area: Double {
        return width * height
    }
    
    // 계산 속성: 둘레를 계산하고 설정 가능
    var perimeter: Double {
        get {
            return 2 * (width + height)
        }
        set {
            width = newValue / 4
            height = newValue / 4
        }
    }
}
```

```Swift
var rect = Rectangle(width: 5, height: 10)
print(rect.area)      // 50.0
print(rect.perimeter) // 30.0

rect.perimeter = 40
print(rect.width)  // 10.0
print(rect.height) // 10.0
```

  

### 🔴 메서드의 정의와 사용

메서드는 구조체 내부에 정의된 함수로, 구조체의 속성을 활용하거나 특정 작업을 수행하기 위해 사용됩니다. 메서드는 ==**인스턴스 메서드**==와 ==**타입 메서드**==로 나뉩니다.

- **인스턴스 메서드**
    
    - 인스턴스 메서드는 구조체의 인스턴스와 연관된 메서드로, 구조체의 속성에 접근하거나 변경할 수 있습니다. `mutating` 키워드를 사용하여 메서드 내에서 구조체의 속성을 변경할 수 있습니다.
    
    ```Swift
    struct Counter {
        var count = 0
        
        // 구조체의 속성을 변경하는 메서드
        mutating func increment() {
            count += 1
        }
        
        // 지정된 값만큼 증가시키는 메서드
        mutating func increment(by amount: Int) {
            count += amount
        }
        
        // 카운트를 초기화하는 메서드
        mutating func reset() {
            count = 0
        }
    }
    ```
    
    ```Swift
    var counter = Counter()
    counter.increment()
    print(counter.count) // 1
    
    counter.increment(by: 5)
    print(counter.count) // 6
    
    counter.reset()
    print(counter.count) // 0
    ```
    
      
    
- **타입 메서드**
    
    - 타입 메서드는 특정 구조체 인스턴스가 아닌, 구조체 자체와 관련된 작업을 수행합니다. 타입 메서드는 `static` 키워드를 사용하여 정의하며, 구조체 내의 타입 속성에 접근하거나 특정 타입과 관련된 작업을 수행할 수 있습니다.
    
    ```Swift
    struct Math {
        static func square(_ number: Int) -> Int {
            return number * number
        }
        
        static func cube(_ number: Int) -> Int {
            return number * number * number
        }
    }
    ```
    
    ```Swift
    let squareValue = Math.square(4)
    let cubeValue = Math.cube(3)
    
    print(squareValue) // 16
    print(cubeValue)   // 27
    ```
    

### 3. 구조체의 초기화

> 구조체의 초기화는 구조체의 인스턴스를 생성할 때 각 속성에 초기 값을 할당하여 올바른 상태로 만드는 과정입니다. Swift에서 구조체는 기본적으로 ==**자동 이니셜라이저**==(initializer)를 제공하지만, 필요에 따라 ==**사용자 정의 이니셜라이저**==를 구현할 수도 있습니다.

  

### 🔴 기본 이니셜라이저

구조체는 모든 저장 속성에 기본 값을 제공하거나 이니셜라이저를 명시하지 않을 경우, 자동으로 기본 이니셜라이저와 멤버와이즈 이니셜라이저를 생성합니다. 기본 이니셜라이저는 매개변수가 없는 형태로, 저장 속성에 정의된 기본 값을 사용하여 인스턴스를 초기화합니다.

```Swift
struct Point {
    var x = 0.0
    var y = 0.0
}

let point = Point()
print(point.x) // 0.0
print(point.y) // 0.0
```

```Swift
struct Person {
    var name: String
    var age: Int
}

let person1 = Person(name: "Jeong", age: 28)
print(person1.name) // "Jeong"
print(person1.age)  // 28
```

  

### 🔴 커스텀 이니셜라이저

구조체의 각 속성을 원하는 방식으로 초기화하려면 커스텀 이니셜라이저를 정의할 수 있습니다. 커스텀 이니셜라이저는 `init` 키워드를 사용하여 정의하며, 특정 조건에 따라 속성의 초기 값을 설정하거나 추가적인 초기화 작업을 수행할 수 있습니다.

```Swift
struct Rectangle {
    var width: Double
    var height: Double
    
    // 커스텀 이니셜라이저 정의
    init(width: Double, height: Double) {
        self.width = width
        self.height = height
    }
    
    // 특정 조건을 만족하는 커스텀 이니셜라이저
    init(squareSide: Double) {
        self.width = squareSide
        self.height = squareSide
    }
}
```

```Swift
let rect1 = Rectangle(width: 5.0, height: 10.0)
print(rect1.width)  // 5.0
print(rect1.height) // 10.0

let square = Rectangle(squareSide: 5.0)
print(square.width)  // 5.0
print(square.height) // 5.0
```

  

### 🔴 이니셜라이저 위임

Swift의 구조체에서는 하나의 이니셜라이저가 다른 이니셜라이저에게 초기화 작업을 위임할 수 있습니다. `이니셜라이저 위임` 이라고 하며, 코드의 중복을 줄이고 초기화 로직을 중앙화하는 데 유용합니다.

```Swift
struct Size {
    var width: Double
    var height: Double
    
    // 전체 크기를 지정하는 이니셜라이저
    init(width: Double, height: Double) {
        self.width = width
        self.height = height
    }
    
    // 정사각형 크기를 지정하는 이니셜라이저
    init(squareSide: Double) {
        self.init(width: squareSide, height: squareSide) // 다른 이니셜라이저에게 초기화 작업 위임
    }
}
```

```Swift
let size1 = Size(width: 10.0, height: 5.0)
print(size1.width)  // 10.0
print(size1.height) // 5.0

let squareSize = Size(squareSide: 7.0)
print(squareSize.width)  // 7.0
print(squareSize.height) // 7.0
```

### 4. 값 타입으로서의 구조체

> 값 타입은 인스턴스가 다른 변수나 상수에 할당되거나 함수에 전달될 때, 그 값이 복사되는 방식으로 동작합니다. 클래스와 같은 참조 타입(reference type)과는 다른 동작 방식으로, 데이터의 안전성과 불변성을 높이는 데 유용합니다.

  

### 🔴 구조체의 복사 동작

구조체는 값 타입이므로, 인스턴스가 다른 변수나 상수에 할당될 때마다 값이 복사됩니다. 이로 인해 구조체의 복사 동작은 데이터의 안전성을 높이고, 원본 데이터의 변경으로 인한 부작용을 방지할 수 있습니다.

```Swift
struct Book {
    var title: String
    var author: String
}

var book1 = Book(title: "Swift Programming", author: "John Doe")
var book2 = book1 // book1의 값이 book2로 복사됨

book2.title = "Advanced Swift"
print(book1.title) // "Swift Programming" (book1은 영향을 받지 않음)
print(book2.title) // "Advanced Swift"
```

  

### 🔴 구조체의 불변성 이해

구조체의 인스턴스를 상수로 선언하면, 해당 인스턴스의 모든 속성은 불변이 됩니다. 값 타입의 특성과 결합되어 불변 데이터 구조를 쉽게 구현할 수 있도록 도와줍니다. 불변성은 데이터의 안정성과 예측 가능성을 높여줍니다.

```Swift
struct User {
    var name: String
    var age: Int
}

let user = User(name: "Alice", age: 30)
// user.name = "Bob" // 오류 발생: 'user'는 상수로 선언되어 속성 변경 불가

var mutableUser = User(name: "John", age: 25)
mutableUser.name = "Jack" // 가변 변수로 선언된 인스턴스는 속성 변경 가능
```

  

- `**mutating**` **키워드**
    
    - 구조체 메서드에서 mutating 키워드를 사용하지 않으면, 메서드 내에서 속성을 변경할 수 없습니다. `mutating` 키워드는 메서드가 구조체의 속성을 변경할 수 있도록 허용하며, 가변 메서드를 정의할 수 있습니다.
    
    ```Swift
    struct Counter {
        var count = 0
        
        mutating func increment() {
            count += 1
        }
    }
    
    var counter = Counter()
    counter.increment()
    print(counter.count) // 1
    ```
    

### 5. 구조체와 프로토콜

> 구조체는 Swift에서 매우 유연하게 사용될 수 있습니다. 프로토콜을 채택하여 특정 동작이나 속성에 대한 요구 사항을 준수하도록 할 수 있습니다.

  

### 🔴 프로토콜 채택

구조체가 프로토콜을 채택한다는 것은 해당 구조체가 프로토콜에서 정의된 요구 사항을 준수한다는 의미입니다. 프로토콜을 통해 속성, 메서드, 서브스크립트 등을 요구할 수 있습니다.

```Swift
protocol Describable {
    var description: String { get }
    func describe()
}
```

```Swift
struct Person: Describable {
    var name: String
    var age: Int
    
    var description: String {
        return "Name: \(name), Age: \(age)"
    }
    
    func describe() {
        print(description)
    }
}

let person = Person(name: "Jeong", age: 28)
person.describe() // Name: Jeong, age: 28
```

  

### 🔴 구조체와 프로토콜의 상호작용

프로토콜은 구조체가 서로 다른 타입 간의 공통된 동작을 정의할 수 있도록 도와줍니다. 다형성을 지원하며, 다양한 타입의 구조체가 동일한 인터페이스를 통해 작동할 수 있습니다.

```Swift
Protocol Drivable {
	func drive()
}

struct Car: Driable {
	func drive() {
			print("Driving a car")
	}
}

struct Bicycle: Driable {
	func dirve() {
			print("Riding a bicycle")
	}
}
```

```Swift
let car = Car()
let bike = Bicycle()

let vehicles: [Drivable] = [car, bike]

for vehicle in vehicles {
	vehicle.drive()
}
```

  

### 🔴 프로토콜 준수와 확장을 통한 기능 추가

`프로토콜 확장` 을 통해 프로토콜을 준수하는 모든 타입에 대해 기본 동작을 정의할 수 있습니다. 프로토콜 확장은 프로토콜의 기본 구현을 제공하거나, 공통된 기능을 확장하여 타입에 기능을 추가할 수 있습니다.

```Swift
protocol Playable {
    func play()
}

extension Playable {
    func pause() {
        print("Paused")
    }
}

struct MusicPlayer: Playable {
    func play() {
        print("Playing music")
    }
}

struct VideoPlayer: Playable {
    func play() {
        print("Playing video")
    }
}
```

```Swift
let musicPlayer = MusicPlayer()
let videoPlayer = VideoPlayer()

musicPlayer.play() // "Playing music"
musicPlayer.pause() // "Paused"

videoPlayer.play() // "Playing video"
videoPlayer.pause() // "Paused"
```

### 6. 구조체와 메모리 관리

> 구조체는 값 타입으로 인스턴스가 생성될 때마다 독립적인 메모리 공간을 차지하며, 다른 변수나 상수에 할당되거나, 함수에 전달될 때 값이 복사됩니다. 참조 타입인 클래스와는 다른 메모리 관리 방식을 가지며, 메모리 사용과 데이터 안정성 측면에서 중요한 차이점을 만듭니다.

  

### 🔴 값 타입의 메모리 관리 원리

구조체는 값 타입으로 인스턴스가 다른 변수나 상수에 할당되거나 함수에 전달될 때 값이 복사됩니다. 복사는 얕은 복사가 아닌 깊은 복사가 수행되어 독립적인 메모리 공간을 차지합니다. 그러므로 각 인스턴스는 독립적으로 존재하며, 하나의 인스턴스에 대한 변경이 다른 인스턴스에 영향을 미치지 않습니다.

```Swift
struct Point {
    var x: Int
    var y: Int
}

var point1 = Point(x: 10, y: 20)
var point2 = point1 // point1의 값이 point2에 복사됨

point2.x = 50 // point2의 x 값을 변경
print(point1.x) // 10 (point1은 영향을 받지 않음)
print(point2.x) // 50 (point2만 변경됨)
```

  

### 🔴 구조체와 ARC 차이점

구조체는 값 타입으로, 클래스와 같은 참조 타입에서 사용하는 `ARC`를 적용받지 않습니다.

ARC에 대한 설명은 클래스 설명에 있었습니다. 그러므로 자세한 설명은 생략하도록 하겠습니다.

  

- **구조체**
    - 값 타입으로, 다른 변수에 할당되거나 함수에 전달될 때 값이 복사됩니다.
    - ARC가 적용되지 않으므로, 참조 카운트가 증가하거나 감소하는 메모리 관리가 필요하지 않습니다.
    - 메모리 관리는 값이 복사되거나 해제될 때 자동으로 이루어지며, 참조 순환 문제가 발생하지 않습니다.
- **클래스**
    - 참조 타입으로, 객체의 참조가 변수나 상수에 할당될 때 참조 카운트가 증가하고, 해제될 때 참조 카운트가 감소합니다.
    - ARC를 통해 메모리 관리가 이루어지며, 객체의 생명 주기를 추적합니다.

  

|   |   |   |
|---|---|---|
|특성|**구조체**|**클래스**|
|**메모리 관리 방식**|값이 복사될 때 독립적인 메모리 공간 할당|ARC를 통해 참조 카운트로 메모리 관리|
|**메모리 할당 시점**|할당 및 변경 시 값이 복사되어 새로운 메모리 할당|참조 카운트가 0이 되면 메모리 해제|
|**참조 순환 문제**|발생하지 않음|강한 참조 순환으로 메모리 누수 발생 가능|
|**사용 예**|간단한 데이터 모델링, 불변 데이터 관리|객체 간의 관계 표현, 상태가 변할 수 있는 데이터 관리|

### 😁 Actor 이해하기

> Swift의 Actor는 ==**동시성프로그래밍**==에서 데이터 경쟁 문제를 방지하기 위해 도입된 새로운 타입입니다. Actor는 여러 스레드에서 접근할 때 데이터를 안전하게 보호하며, 객체의 상태를 일관되게 관리할 수 있도록 도와줍니더. 기존의 클래스와 유사하지만 상탤르 격리하여 동시 접근으로 인한 오류를 방지합니다. Swift 5.5부터 제공되는 Actor는 비동기 프로그래밍의 안정성과 효율성을 높이기 위한 중요한 개념입니다. ==**꼭!!! 집중해서 학습해주시길 바라겠습니다.**==

> [!important] Actor에 대한 내용은 엄청 깊습니다. 그렇기 때문에 전부 자세히 설명하진 않겠습니다.
> 
>   
> UIkit에서 활용힐 수 있는 기초적인 부분에 한해서만 개념을 정리했습니다. UIkit에서 Actor가 어떻게 사용되는지에 대해 꼭 이해하고 있기를 바랍니다!!  
>   
> Actor에 대해 아주 기초적인 내용을 학습 후 실제로 사용하게 될 시점은  
> **1. 사용자 요청이 동시에 처리되는 사용자 세션 관리**  
> **2. API 호출을 통해 데이터를 가져오고 이를 처리하여 UI에 반영하는 작업**  
> **3. 데이터 로딩 후 UI 업데이트 작업**  
>   
>   
> ==**Actor에 대해 학습을 했으니, 추후 정규 워크북에 자주 사용해보면서 익힐 수 있도록 하겠습니다.**==

  

### 1. Actor의 기본 개념

> 여러 스레드에서 객체의 상태에 안전하게 접근할 수 있도록 설계되었습니다. Actor는 상태를 격리하여 데이터 경쟁(race condition)을 방지하고, 동시 접근으로 인한 예기치 않은 동작을 방지합니다.

  

### 🔴 Actor란 무엇인가?

**Actor**는 Swift 5.5부터 도입된 동시성 타입으로, 클래스와 유사하게 참조 타입입니다. 하지만 중요한 차이점은 Actor는 내부 상태에 대한 `단일 접근 보장(single access guarantee)`을 제공한다는 것입니다. 이는 여러 스레드가 동시에 Actor의 속성이나 메서드에 접근하려고 할 때, 한 번에 하나의 스레드만 접근할 수 있도록 보장합니다. 덕분에 동시성 프로그래밍에서 흔히 발생하는 데이터 경쟁 문제를 차단할 수 있습니다.

  

### Actor의 특징

- **참조 타입**
    - Actor는 클래스처럼 참조 타입으로, 변수나 상수에 할당될 때 참조가 전달됩니다.
- **단일 접근 보장**
    - 여러 스레드가 동시에 접근할 때, Actor는 한 번에 하나의 스레드만 접근할 수 있도록 보장합니다.
- **비동기적 상태 접근**
    - Actor의 속성이나 메서드에 접근할 때는 `await` 키워드를 사용하여 비동기적으로 접근해야 합니다.

  

Actor로 정의되어, `value` 속성에 대해 단일 접근이 보장됩니다. `increment()` 메서드를 통해 `value`를 안전하게 증가시킬 수 있습니다.

```Swift
actor Counter {
    var value = 0
    
    func increment() {
        value += 1
    }
}
```

  

### 🔴 Actor의 동작 원리

Actor는 상태와 메서드를 안전하게 관리하기 위해 내부적으로 `Serial Queue` 를 사용합니다. Actor 내부의 속성과 메서드에 대한 접근이 한 번에 하나의 스레드에서만 이루어지도록 보장합니다. Actor는 여러 스레드가 동시에 접근하더라도 내부적으로 큐를 통해 요청을 순차적어로 처리하므로, 동시성 문제를 방지할 수 있습니다.

  

### 동작 원리

1. **단일 접근 보장**
    1. Actor의 상태에 접근할 때, 다른 스레드가 동시에 접근하려 해도 단일 스레드만 접근할 수 있습니다.
2. **비동기 접근**
    1. Actor의 메서드나 속성에 접근할 때는 `await` 키워드를 사요아형 비동기적으로 접근합니다.
3. **재진성입성**
    1. Actor의 메서드는 기본적으로 재진입성을 가집니다. 즉, Actor가 하나의 작업을 처리하는 동안, 다른 작업이 들어오면 이전 작업이 잠시 중단되고 새 작업이 처리될 수 있습니다.

```Swift
actor Counter {
    var value = 0
    
    func increment() {
        value += 1
    }
    
    func getValue() -> Int {
        return value
    }
}
```

```Swift
let counter = Counter()

Task {
    await counter.increment()
    let currentValue = await counter.getValue()
    print("Current value: \(currentValue)") // "Current value: 1"
}
```

  

### 🔴 Actor와 클래스의 차이점

Actor는 클래스와 유사하게 참조 타입이며, 인스턴스 메서드와 속성을 가지 수 있습니다.

  

### 데이터 접근 방식의 차이

- **클래스**
    - 클래스는 동시성 제어가 없으므로, 여러 스레드가 동시에 동일한 속성이나 메서드에 접근할 수 있습니다. 이로 인해 데이터 경쟁 문제가 발생할 수 있습니다.
- **Actor**
    - Actor는 내부적으로 `Serial Queue`를 사용하여 동시성 제어를 자동으로 수행합니다.
    - 여러 스레드에 접근하더라도, 한 번에 하나의 스레드만 Actor의 상태에 접근할 수 있도록 보장합니다.
    - 비동기적으로 상태를 보호하며, 데이터 경쟁을 방지합니다.

  

```Swift
class UnsafeCounter {
    var value = 0
    
    func increment() {
        value += 1
    }
}

let counter = UnsafeCounter()
DispatchQueue.global().async {
    for _ in 0..<1000 {
        counter.increment() // 여러 스레드에서 동시에 접근, 데이터 경쟁 발생
    }
}

/* 여러 스레드에서 동시에 호출될 수 있어, 예상치 못한 결과가 발생할 수 있습니다. */
```

```Swift
actor SafeCounter {
    var value = 0
    
    func increment() {
        value += 1
    }
    
    func getValue() -> Int {
        return value
    }
}

let counter = SafeCounter()
Task {
    for _ in 0..<1000 {
        await counter.increment() // 안전한 접근, 데이터 경쟁 방지
    }
}

/* 단일 접근이 보장되어, 여러 스레드에서 동시에 접근하더라도 안전하게 동작합니다. */
```

  

### 동시성 처리 방식

- **클래스**
    - 여러 스레드에서 동시 접근할 수 있으며, 동기화 메커니즘 없이 동작할 경우, 비정상적인 상태에 빠질 수 있습니다.
    - 동시성 문제를 해결하기 위해 수동으로 `DispatchQueue`나 `NSLock`을 사용해야 합니다.
- **Actor**
    
    - 동시성 처리가 자동으로 이루어지며, 비동기 접근을 통해 데이터 경쟁을 방지합니다.
    - `await` 키워드를 통해 비동기 메서드 호출이 가능하며, 데이터 접근이 안전하게 이루어집니다.
    
      
    

### 재진입성

- **클래스(Class)**:
    - 기본적으로 재진입성을 가지지 않으며, 여러 스레드에서 메서드가 중첩 호출될 경우 비정상적인 동작을 할 수 있습니다.
- **Actor**:
    - 기본적으로 재진입성을 가지며, 비동기 작업이 효율적으로 관리됩니다. 그러나 재진입성이 필요하지 않거나, 이를 방지해야 하는 경우 개발자가 직접 제어할 수 있습니다.

### 2. Actor의 정의와 사용

> Actor는 동시성 프로그래밍을 안전하게 처리하기 위해 설계된 참조 타입으로, 여러 스레드에서 객체의 상태를 안전하게 보호하며 데이터 경쟁을 방지합니다.

### 🔴 Actor 정의 방법

Actor는 `actor` 키워드를 사용하여 정의합니다. Actor는 클래스와 유사하게 속성, 메서드, 이니셜라이저를 가질 수 있으며, 객체의 상태를 안전하게 관리하기 위해 내부적으로 단일 스레드 접근을 보장합니다. Actor 내부의 모든 속성은 `actor-isolated` 속성으로 처리되며, 외부에서 접근할 때는 비동기적으로 접근해야 합니다.

```Swift
actor BankAccount {
    var balance: Int
    
    init(balance: Int) {
        self.balance = balance
    }
    
    func deposit(amount: Int) {
        balance += amount
    }
    
    func withdraw(amount: Int) {
        if amount <= balance {
            balance -= amount
        }
    }
    
    func getBalance() -> Int {
        return balance
    }
}
```

  

### 🔴 Actor 인스턴스 생성 및 사용

Actor의 인스턴스를 생성하고, 그 인스턴스에 정의된 메서드를 호출할 때는 비동기적으로 접근해야 합니다. `await` 키워드를 사용하여 Actor의 속성이나 메서드에 접근할 수 있으며, Actor 내부의 작업이 안전하게 처리됩니다.

```Swift
let bankAccount = BankAccount(balance: 1000)

Task {
    await bankAccount.deposit(amount: 500) // 비동기 메서드 호출
    let currentBalance = await bankAccount.getBalance()
    print("Current balance: \(currentBalance)") // "Current balance: 1500"
}
```

  

### 🔴 비동기 함수와 Actor

Actor는 비동기 함수와 결합하여 동시성 프로그래밍을 더욱 강력하게 만들 수 있습니다. 비동기 함수는 `async` 키워드를 사용하여 정의하며, Actor 내의 메서드도 비동기 함수로 정의할 수 있습니다.

```Swift
actor DataFetcher {
    func fetchData() async -> String {
        // 비동기 작업 예시
        return "Fetched Data"
    }
    
    func processData() async -> String {
        let data = await fetchData()
        return "Processed: \(data)"
    }
}
```

```Swift
let fetcher = DataFetcher()

Task {
    let result = await fetcher.processData()
    print(result) // "Processed: Fetched Data"
}
```

  

### 3. UI 업데이트

> 비동기적으로 데이터를 처리하고 UI를 업데이트할 때, Actor를 결합하여 데이터 처리와 UI 업데이트를 분리할 수 있습니다. 비동기 작업이 UI 스레드와 충돌하지 않고 안전하게 실행되도록 할 수 있습니다.

```Swift
actor DataFetcher {
    func fetchData() async -> String {
        try? await Task.sleep(nanoseconds: 1_000_000_000) // 1초 지연
        return "hello!!"
    }
}
```

```Swift
import UIKit

class ViewController: UIViewController {
    private let dataFetcher = DataFetcher()
    private let label = UILabel()

    override func viewDidLoad() {
        super.viewDidLoad()
				self.view.backgroundColor = .white
        setupUI()
        loadData()
    }

    private func setupUI() {
        label.text = "Loading..."
        label.textAlignment = .center
        label.font = UIFont.systemFont(ofSize: 20)
        label.frame = view.bounds
        view.addSubview(label)
    }

    private func loadData() {
        Task {
            let data = await dataFetcher.fetchData()
            
            await MainActor.run {
                updateUI(with: data)
            }
        }
    }

    private func updateUI(with data: String) {
        label.text = data
    }
}
```

**데이터 로딩 중**

![[스크린샷_2024-09-29_오후_2.54.20.png]]

**데이터 로딩 후**

![[스크린샷_2024-09-29_오후_2.54.22.png]]

## 📚 5주차 실습

---

### 문제 1. 은행 계좌 관리 시스템 - Class 구현

- 요구사항
    - **클래스 이름:** `**BankAccount**`
        - 은행 계좌를 나타내는 클래스입니다.
    - **속성 (Properties)**
        - `accountNumber` (String): 계좌 번호를 저장합니다. 계좌 번호는 계좌 생성 시 설정되며, 이후 변경할 수 없습니다.
        - `balance` (Double): 계좌의 현재 잔액을 저장합니다. 외부에서 잔액을 변경할 수 없도록 `private(set)` 접근 제어자를 사용하세요.
    - **초기화 메서드 (Initializer)**
        - `init(accountNumber: String, initialBalance: Double)`: 계좌 번호와 초기 잔액을 입력받아 계좌를 생성합니다.
        - 초기 잔액은 0 이상이어야 하며, 음수일 경우 0으로 설정하세요.
    - **메서드 (Methods)**
        - `deposit(amount: Double)`: 입금 메서드로, `amount`만큼 잔액을 증가시킵니다. 입금 후 입금된 금액과 현재 잔액을 출력합니다.
        - `withdraw(amount: Double)`: 출금 메서드로, `amount`만큼 잔액을 감소시킵니다. 출금 금액이 잔액보다 많을 경우 "Insufficient funds" 메시지를 출력하고 출금을 하지 않습니다. 출금 후 출금된 금액과 현재 잔액을 출력합니다.
- 정답은 아캐 코드 칸에 넣어주세요!
    
    ```Swift
    class BankAccount {
    /* 요구사항에 맞춰 구현해주세요! */
    }
    ```
    
    ```Swift
    /* 코드 시나리오, 위 클래스 구현 후 실행 시켜주세요! */
    
    let account = BankAccount(accountNumber: "123-456", initialBalance: 100.0)
    
    account.deposit(amount: 50.0) // 출력: "Deposited 50.0. Current balance: 150.0"
    account.withdraw(amount: 30.0) // 출력: "Withdrew 30.0. Current balance: 120.0"
    account.withdraw(amount: 200.0) // 출력: "Insufficient funds. Current balance: 120.0"
    ```
    
      
    

### 문제 2. 차량관리 시스템 - Struct 구현

- 요구사항
    - **구조체 이름:** `**Car**`
        - 차량의 정보를 관리하는 구조체입니다.
    - **속성 (Properties)**
        - `make` (String): 차량의 제조사 이름을 저장합니다.
        - `model` (String): 차량의 모델명을 저장합니다.
        - `year` (Int): 차량의 연식을 저장합니다.
        - `mileage` (Double): 차량의 현재 주행거리를 저장합니다.
        - `isRunning` (Bool): 차량의 상태를 나타내는 불리언 값입니다. 차량이 작동 중일 때 `true`, 그렇지 않으면 `false`입니다.
    - **초기화 메서드 (Initializer)**
        - `init(make:model:year:mileage:isRunning:)`: 제조사, 모델, 연식, 주행거리, 작동 상태를 입력받아 새로운 차량 인스턴스를 생성합니다.
    - **메서드 (Methods)**
        - `start()`: `isRunning` 속성을 `true`로 변경하고, "차 시동 걸림." 메시지를 출력합니다. 차량이 이미 작동 중인 경우, "차 이미 시동 중." 메시지를 출력합니다.
        - `stop()`: `isRunning` 속성을 `false`로 변경하고, "차 시동 꺼짐." 메시지를 출력합니다. 차량이 이미 정지된 상태라면, "차 이미 꺼짐." 메시지를 출력합니다.
        - `drive(distance:)`: 주행거리를 나타내는 `distance` 값을 입력받아, 차량이 작동 중일 때만 `mileage`에 주행거리를 추가하고, "이동거리 {y} km. 현재 mileage: {x} km" 메시지를 출력합니다. 차량이 작동 중이 아닐 때는 "이동 불가능. 차 시동 꺼짐." 메시지를 출력합니다.
- 정답은 아래 코드 칸에 넣어주세요!
    
    ```Swift
    struct Car {
    /* 요구사항에 맞춰 구현해주세요! */
    }
    ```
    
    ```Swift
    /* 코드 시나리오, 위 클래스 구현 후 실행 시켜주세요! */
    
    var myCar = Car(make: "한국", model: "KIA", year: 2024, mileage: 15000.0, isRunning: false)
    
    myCar.start() // 출력: "차 시동 걸림."
    myCar.drive(distance: 100) // 출력: "이동거리 100 km. 현재 mileage: 15100 km"
    myCar.stop() // 출력: "차 시동 꺼짐."
    myCar.drive(distance: 50) // 출력: "이동 불가능. 차 시동 꺼짐."
    myCar.start() // 출력: "Car started."
    myCar.start() // 출력: "차 이미 시동 중."
    ```
    

### 문제 3. 비동기 주문 처리 시스템

- 요구사항
    - **주문 추가**
        - `addOrder(_ order: String)` 메서드를 사용하여 `Pizza`, `Burger`, `Pasta`를 순차적으로 주문에 추가합니다.
    - **주문 처리**
        - `processOrder()` 메서드를 사용하여 추가된 주문을 처리합니다. 순서대로 첫 번째 주문 `Pizza`, 두 번째 주문 `Burger`를 처리한 후, 처리된 주문에 대한 메시지가 출력되어야 합니다.
    - **남은 주문 확인**
        - `printAllOrders()` 메서드를 사용하여 현재 남아있는 주문을 확인합니다.
        - 첫 번째 확인에서는 `Pasta`가 남아있어야 하고, 마지막 확인에서는 남은 주문이 없어야 합니다.
- 정답은 아래 코드 칸에 넣어주세요!
    
    ```Swift
    actor OrderProcessor {
    		private var orders: [String] = []
    	
    	// 주문 추가 메서드
    	func addOrder(_ order: String) {
    			orders.append(order)
    			print("추가된 주문: \(order)")
    	}
    
    	// 주문 처리 메서드
    	func processOrder() {
    		if orders.isEmpty {
    				print("처리할 주문 없음")
    		} else {
    				let order = orders.removeFirst()
    				print("처리된 주문: \(order)")
    		}
    	}
    
    	// 현재 남아있는 주문 출력 메서드
    	func printAllOrder() {
    		if orders.isEmpty {
    				print("남아 있는 주문 없음")
    		} else {
    				print("남아 있는 주문: \(orders.joined(separator: ", "))")
    		}
    	}
    }
    ```
    
    ```Swift
    let orderProcessor = OrderProcessor()
    
    /*  요구 사항에 맞춰 구현해주세요 */
    /* 힌트 : Task와 await 활용하기 */
    ```
    
    ![[스크린샷_2024-09-29_오후_4.24.29.png]]
    
      
    
      
    

## 📌 추가적으로 더 공부해 봤어요!

---

==추가적으로 과제를 하면서 스스로 공부해본 내용이 있다면 이곳에 자유 양식으로 정리해 보세요!==

## ❓ 이런 질문이 있어요!

---

워크북을 진행하면서 궁금했던 점 또는 해결하지 못한 부분을 미리 작성하고 스터디에서 함께 논의해 보세요!  
해결하지 못한 질문이나 궁금한 점이 있다면 언제든지 편하게 DM 주세요 🙋‍♀️  

  

---

Copyright © 2024 Lee Youjin All rights reserved.

Copyright © 2024 Jeong Euichan All rights reserved.