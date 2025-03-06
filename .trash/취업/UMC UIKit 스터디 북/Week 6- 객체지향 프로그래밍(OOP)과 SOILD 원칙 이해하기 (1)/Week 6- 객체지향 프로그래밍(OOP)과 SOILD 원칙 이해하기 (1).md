- [[#📋 학습 목표]]
- [[#✋ 잠깐! 스터디 인증샷 찍으셨나요?]]
- [[#🔥 6주차 개념 설명]]
    - [[#0️⃣ 5주차까지 우리는 이렇게 달려왔어요!]]
    - [[#1️⃣ 좋은 설계란 무엇일까요?]]
    - [[#2️⃣ 객체지향 프로그래밍(OOP)이란 무엇일까요?]]
    - [[#3️⃣ SOILD 원칙이란 무엇일까요?]]
- [[#🔥 6주차 개념 점검]]
- [[#💻 6주차 과제]]
    - [[#1. 세부 화면 레이아웃을 구현해주세요!]]
    - [[#2. OOP와 SOLID 원칙을 적용해 리팩토링을 진행해주세요!]]
    - [[#3. OOP에 맞추어 리팩토링을 진행하셨다면 리팩토링 과정을 설명해주세요!]]
    - [[#4. SOLID 원칙에 맞추어 리팩토링을 진행하셨다면 리팩토링 과정을 설명해주세요!]]
    - [[#5. 과제가 완성 되었다면 깃허브 링크와 시연 영상을 첨부해주세요!]]
- [[#🤔 6주차 트러블 슈팅]]
- [[#📌 이번 주차에는 이런 내용을 학습했어요!]]
    - [[#🍎 학습한 내용 제목]]
- [[#❓ 이런 질문이 있어요!]]

## 📋 학습 목표

---

- `좋은 설계`란 무엇인지 생각해보고, `객체지향 프로그래밍(OOP)`과 `SOILD` 원칙의 필요성을 이해할 수 있다.
- 객체지향 프로그래밍(`OOP`)에 대해 이해하고, `OOP`의 4가지 원칙을 생각해볼 수 있다.
- `SOILD` 원칙에 대해 이해하고, 기존 코드를 `SOILD` 원칙에 맞추어 리팩토링할 수 있다.

  

## ✋ 잠깐! 스터디 인증샷 찍으셨나요?

---

> [!important] 스터디 시작 전 ==**스터디 인증샷을 촬영**==해주세요!
> 
> 스터디는 대면이 원칙이며, 비대면 스터디의 경우에도 최대한 카메라를 킨 후 진행해주세요.
> 
> 아래 임베드 블록에 인증샷을 임베드해 주시면 됩니다 🫶

[](https://www.notion.soundefined)

  

## 🔥 6주차 개념 설명

---

### 0️⃣ 5주차까지 우리는 이렇게 달려왔어요!

> 우리는 1주차부터 5주차까지 iOS의 기본적인 컴포넌트를 구현하는 방법과 기본적인 화면 설계 방식을 학습했습니다. iOS 개발자로서의 첫 발을 내딛으신 것을 축하드려요! 🥳
> 
> 특히 1주차에는 `MVC` 패턴을 이용해 애플리케이션을 세 컴포넌트로 분리해 개발하는 구조를 학습했는데 기억하시나요?
> 
> 이 `MVC` 패턴을 이용해 코드의 `모듈화`를 촉진하고 `유지보수성`, `재사용성`을 높일 수 있다고 말씀드렸습니다.
> 
> `유지보수성`? `재사용성`? 그럴듯한 말들이지만 사실 한번 들었을 때 정확히 어떤 말인지, 어떤 의미인지 이해하기는 쉽지 않으셨을 겁니다.
> 
> `유지보수성` 과 `재사용성` 은 무엇인지, 왜 우리는 `유지보수성`, `재사용성`을 높여야 하는지 처음부터 찬찬히 다시 한 번 생각해볼까요?

### 1️⃣ 좋은 설계란 무엇일까요?

제목부터 철학적이죠? 사실 정말 어려운 질문입니다. 좋은 설계는 무엇이며 왜 좋은 설계를 해야 하는 걸까요?

> 🙋 : 저는 그냥 `CollectionView`, `TableView`를 짜는 데도 벅차고 힘든데 … 좋은 설계를 생각하는 것보다는 구현이 우선적으로 이루어져야 하지 않을까요? 일단 잘 실행되어야 좋은 코드고 설계라고 생각해요.
> 
> 🙋‍♀️ : 어려운 아키텍쳐와 라이브러리를 도입하다 보면 좋은 설계가 나오지 않을까요? `RxSwift`, `MVVM`, `Tuist`, `클린 아키텍쳐` … 이것저것 하다보면 자연스럽게 좋은 설계가 될거예요!
> 
> 🙋‍♂️ : 무엇보다 코드가 짧아야 하지 않을까요? 재사용성도 유지보수성도 코드가 짧으면 높아진다고 생각해요.

이런 생각이 드셨다면 … 사실 정말 당연한 생각들입니다. 저도 iOS를 처음 배울 때 왕왕 했던 생각들이예요!

그렇지만 이번 주차에서는 이런 생각들은 잠깐 접어두고 본질적인 부분부터 함께 이해해보도록 할까요?

우리는 이제 막 iOS 개발의 첫발을 내딛은 개발자입니다. iOS 개발자는 어떤 목표를 가지고 있는 사람일까요? 어떤 목표를 가지고 있길래 개발자는 평생 공부해야 한다는 말이 나오는 걸까요? 그냥 구현만 잘 하면 되는 게 아닐까요?

사람마다 다를 수도 있겠지만 결국 iOS 개발자는, 곧 클라이언트 개발자는 ==**근본적으로 프로덕트를 잘 만들어야 하는 사람**==입니다.

프로덕트를 잘 만든다는 건 어떤 의미일까요? 결국 코드를 잘 짠다는 말일겁니다. 우리는 코드로 프로덕트를 만드는 사람이니까요.

고품질의 프로덕트를 위해서는 구현은 물론이고 고품질의 코드가 필요합니다. 쉬운 이해를 위해 **[카카오뱅크 iOS 플랫폼의 모듈화, 왜 필요했을까요?](https://tech.kakaobank.com/posts/2308-ios-modular-architecture-kwdc2023/)** 아티클의 앞부분을 함께 읽어보도록 할게요.

카카오뱅크 앱은 2017년 모바일 은행 서비스를 출시한 후 2000만이 넘는 고객을 보유한 거대한 금융 플랫폼이 되었습니다.

이러한 비즈니스의 성장과 함께 애플리케이션의 코드 양 또한 함께 기하급수적으로 증가했다고 하네요!

20년도에는 109만 라인, 21년도에는 123만 라인, 22년도에는 158만 라인의 코드로 점점 증가하던 카카오뱅크의 23년 상반기 코드 라인 수는 ==**39만 줄이 증가한 197만 라인**==입니다.

이렇게 코드의 양이 기하급수적으로 증가하면서 어떤 일이 일어났을까요?

  

![[Assets/image 12.png|image 12.png]]

![[스크린샷_2024-09-28_오전_2.21.11.png]]

![[Assets/image 1 4.png|image 1 4.png]]

프로젝트 규모가 증가하면서 개발자의 수도 증가했고, 이로 인해 코드의 규모 또한 증가되었습니다.

프로젝트를 실행하는 데 걸리는 빌드 시간 또한 증가했고, 이로 인한 전체 개발 시간 또한 증가했겠네요! 근무 시간 또한 증가했다고 하니 야근도 잦았을 것 같습니다 …

유지보수에 드는 시간이 증가한다는 건 `유지보수성`이 그만큼 떨어졌다는 말과 동일하게 이해해볼 수 있겠습니다.

복잡한 만큼 결합되어 있는 코드들도 무궁무진하겠죠! 코드의 `결합도` 또한 높을 겁니다. 한 코드를 수정하면 다른 코드도 수정되어야 하고, 이런 코드 때문에 유지보수가 더 어려운 부분도 있겠죠.

결국 악순환의 반복입니다. 구현을 우선으로 한 코드는 프로젝트에서 이런 악순환을 초래하고, 결국 개발하는 우리는 매일매일 야근의 늪에 빠지게 되겠죠!

이렇게 ==**기술적인 문제가 해결되지 않아 악순환이 반복되는 것을 기술 부채가 쌓인다**==고 합니다.

물론 마감 기한은 정해져 있고, 그런 부분에서 기술 부채를 반드시 허용하지 않아야 한다는 말은 너무 이상만 추구하는 자세일 겁니다. 책임질 수 있는 한도 내에서 기술 부채를 유연하게 허용하고, 이후 그런 기술 부채를 해결할 줄도 알아야겠죠.

만약 해결되지 않는다면 … 매일 울면서 회사에서 야근하는 모습이 상상되시나요? 그런 일이 일어나지 않도록 초기에 예방하는 습관을 들여보도록 합시다.

위에서 살펴본 카카오뱅크의 문제는 결국 근본적으로 `유지보수성`과 `확장성`의 부족에 기반합니다.

코드가 너무 많고 코드 간 결합도도 높아 코드 하나를 수정하면 다른 코드도 수정해야 하니 `유지보수`에도, `확장`에도 적합한 코드가 아니었겠죠!

그렇다면 고품질의 프로덕트를 설계하기 위한 고품질의 코드는 결국 `유지보수성`과 `확장성`이 높아야 한다! 고 이야기해볼 수 있겠네요.

결국 좋은 설계란 `유지보수성`과 `확장성`이 뛰어난 설계라고 생각하시면 좋을 것 같습니다.

이번 주차에서는 `유지보수성`과 `확장성`을 코드 설계에 적용할 수 있도록 객체지향 프로그래밍과 `SOLID` 원칙에 대해 학습해보도록 하겠습니다.

### 2️⃣ 객체지향 프로그래밍(OOP)이란 무엇일까요?

![[Assets/image 2 4.png|image 2 4.png]]

  

0주차에서 Swift는 객체지향형 언어라는 내용을 학습했는데 기억하시나요?

`객체지향`이라는 용어는 사실 iOS 개발 분야를 제외하고도 개발을 한번이라도 접해보셨다면 어디선가 한 번 정도는 들어보셨을텐데요!

객체지향 프로그래밍에 대해 이해하기 위해서는 먼저 절차지향 프로그래밍에 대해 이해해보면 좋습니다.

> **💻 절차지향 프로그래밍**
> 
> 프로그램을 명령의 순서와 절차로 보는 방식입니다.
> 
> 프로그램의 순서와 흐름을 먼저 세우고 그에 맞게 자료 구조나 함수들을 구현합니다.
> 
> **순차적인 처리를 중요시하고 프로그램 전체가 유기적으로 연결**되도록 설계하는 방식으로 이해하시면 좋을 것 같습니다!
> 
> 데이터와 함수를 별도의 개체로 취급한다는 특징이 있습니다.
> 
> 절차지향 프로그래밍을 따르는 대표적인 언어로는 `C`가 있어요!

> **💻 객체지향 프로그래밍**
> 
> 현실 세계의 객체를 모델링해 프로그램을 구성하는 방식입니다.
> 
> 절차지향과는 다르게 데이터에 맞게 자료 구조를 먼저 설계한 후 이에 맞게 프로그램의 순서와 흐름을 설계합니다.
> 
> 객체 사이의 데이터 전달과 같은 상호작용을 통해 프로그램을 설계하는 방식이예요!
> 
> 데이터와 함수를 하나의 객체로 묶고 역할과 책임을 부여해 프로그램이 객체 간 상호작용에 따라 유기적으로 동작하도록 합니다.
> 
> 객체지향 프로그래밍을 따르는 대표적인 언어로는 `Java`, `Python` 등이 있어요!

두 방식의 차이는 `프로그램을 어떻게 바라보고 구성하는가` 에 기반합니다.

절차지향 프로그래밍은 **단계를 순차적으로 따라가며 문제를 해결**하고, 객체지향 프로그래밍은 **현실 세계의 객체들이 각각의 역할과 책임을 가지고 서로 상호작용하며 문제를 해결**합니다.

물론 객체지향 프로그래밍이 항상 더 좋은 방법이라는 건 아닙니다. 두 방식을 모두 이해하고 상황에 맞게 적절히 선택하는 게 중요하겠죠! 간단한 예시를 통해 두 방법의 차이를 조금 더 깊이 이해해보도록 하겠습니다.

```Swift
// 계좌 잔액 (전역 변수)
var accountBalance = 0

// 잔액 확인
func checkBalance(balance: Int) {
    print("현재 잔액은 \(balance)원 입니다.")
}

// 입금 (값을 반환)
func deposit(amount: Int, balance: Int) -> Int {
		print("\(amount)원을 입금했습니다.")
    return balance + amount
}

// 출금 (값을 반환)
func withdraw(amount: Int, balance: Int) -> Int {
    if balance >= amount {
		    print("\(amount)원을 출금했습니다.")
        return balance - amount
    } else {
        print("잔액이 부족합니다.")
        return balance
    }
}

checkBalance(balance: accountBalance)   // 현재 잔액은 0원 입니다.
accountBalance = deposit(amount: 50000, balance: accountBalance)   // 50000원을 입금했습니다.
checkBalance(balance: accountBalance)   // 현재 잔액은 50000원 입니다.
accountBalance = withdraw(amount: 20000, balance: accountBalance)  // 20000원을 출금했습니다.
checkBalance(balance: accountBalance)   // 현재 잔액은 30000원 입니다.
```

  

```Swift
class BankAccount {
    // 계좌 잔액 (상태)
    private var balance: Int = 0
    
    // 잔액 확인
    func checkBalance() {
        print("현재 잔액은 \(balance)원 입니다.")
    }
    
    // 입금 (상태 변경)
    func deposit(amount: Int) {
        balance += amount
        print("\(amount)원을 입금했습니다.")
    }
    
    // 출금 (상태 변경)
    func withdraw(amount: Int) {
        if balance >= amount {
            balance -= amount
            print("\(amount)원을 출금했습니다.")
        } else {
            print("잔액이 부족합니다.")
        }
    }
}

let myAccount = BankAccount()

myAccount.checkBalance()   // 현재 잔액은 0원 입니다.
myAccount.deposit(amount: 50000)   // 50000원을 입금했습니다.
myAccount.checkBalance()   // 현재 잔액은 50000원 입니다.
myAccount.withdraw(amount: 20000)   // 20000원을 출금했습니다.
myAccount.checkBalance()   // 현재 잔액은 30000원 입니다.
```

계좌의 잔액을 확인하고 입금, 출금의 기능을 수행하는 코드를 예시로 가져왔는데요!

왼쪽은 절차지향 방식, 오른쪽은 객체지향 방식을 사용한 코드입니다. 약간의 차이가 느껴지시나요?

`절차지향` 방식의 코드는 **전역 변수를 활용**하고, **기능이 함수 단위로 분리**되어 있습니다. **변수인 계좌와 기능인 함수들이 아예 별개**라는 점에 집중해 주시면 좋을 것 같습니다!

`객체지향` 방식의 코드는 **계좌 데이터와 기능을 모두 클래스를 이용해 묶어**두었습니다. **객체 내에 상태와 행위가 모두 존재**한다는 점에 집중해주시면 좋을 것 같습니다!

물론 위의 예시는 매우 간단한 로직만을 다루었기 때문에 두 방식 다 괜찮아보이는데? 절차지향 나쁘지 않은데? 라는 생각이 드실 수 있으실 것 같아요.

그렇다면 **절차지향 방식의 단점**은 무엇일까요?

> 절차지향형 프로그래밍은 **프로그램의 순서와 흐름을 먼저 세우고 그에 맞게 자료 구조나 함수들을 구현**한다고 말씀드렸는데요!
> 
> 순서와 흐름에 초점을 맞추기 때문에 순차적으로 흐름을 파악하는 데에는 객체지향형 프로그래밍보다 수월하다는 점이 장점입니다.
> 
> ==**그러나 로직이 복잡해진다면**== 어떨까요? 예시를 들어보겠습니다.
> 
> 만약 **관리해야 하는 계좌의 유형이 늘어난다면** 어떨까요?
> 
> 계좌 유형에 따라 입출금 로직도 달라진다면 **각 계좌에 따라 함수도 따로 지정**해야 하고, **새로운 계좌나 로직이 수정될 때마다 모든 변수가 수정**되어야 할 겁니다.
> 
> 따라서 ==**코드의 유지보수가 어려워진다는 문제점이 발생**==하게 되겠죠!

객체지향 방식에서는 위와 같은 문제를 클래스를 이용해 해결합니다. 계좌의 상태와 동작을 모두 한 객체로 묶어 관리한다고 보시면 편하실 것 같은데요!

```Swift
class BankAccount {
    var balance: Int
    
    init(initialBalance: Int) {
        self.balance = initialBalance
    }
    
    func deposit(amount: Int) {
        balance += amount
        print("\(amount)원을 입금했습니다.")
    }
    
    func withdraw(amount: Int) {
        if balance >= amount {
            balance -= amount
            print("\(amount)원을 출금했습니다.")
        } else {
            print("잔액이 부족합니다.")
        }
    }
    
    func checkBalance() {
        print("현재 잔액은 \(balance)원 입니다.")
    }
}

class InterestAccount: BankAccount {
    let interestRate: Double = 0.05
    
    override func deposit(amount: Int) {
        let interest = Int(Double(amount) * interestRate)
        balance += amount + interest
        print("\(amount)원을 입금하고 \(interest)원의 이자가 추가되었습니다.")
    }
}

let standardAccount = BankAccount(initialBalance: 50000)
let interestAccount = InterestAccount(initialBalance: 75000)

standardAccount.deposit(amount: 10000)
interestAccount.deposit(amount: 10000)
standardAccount.checkBalance()
interestAccount.checkBalance()
```

`BankAccount` 라는 클래스에서 기본적인 계좌의 데이터와 입, 출금 등의 동작을 모두 관리하고 있는 것을 확인할 수 있습니다.

위에서 말했던 것처럼 관리해야 하는 계좌의 유형이 늘어났을 때를 가정해볼게요!

`InterestAccount` 라는 이자 지급 계좌의 유형이 추가되었다고 생각해볼까요?

왼쪽 코드에서는 `InterestAccount` 가 `BankAccount`를 상속받고 있습니다. 이는 곧 `InterestAccount` 가 `BankAccount` 의 기능을 모두 사용할 수 있다는 것을 의미하는데요!

기본적인 출금 기능과 잔액 확인 기능은 모두 유지하되 입금 기능에 약간의 변화가 생겼습니다. 입금 시 5%의 이자율에 따라 추가로 금액이 입금되어야 한다네요! 부럽습니다.

이 때 객체지향 방식에서는 절차지향 방식처럼 따로 함수를 구현하는 것이 아니라 기존 `deposit()` 메소드를 `override` 해 기존의 입금 기능을 확장합니다.

이를 통해 입금 시 단순히 금액이 더해지는 일반 계좌와 입금 시 금액에 이자가 더해지는 이자 지급 계좌가 나누어지게 되었네요!

  

> 객체지향 프로그래밍은 **상속을 통해 코드의 중복을 피하고 각 유형에 맞게 기능을 확장**할 수 있습니다.
> 
> 이러한 특징 때문에 코드의 `유지보수성`과 `확장성`에 유리한 설계라고 볼 수 있는거죠!
> 
> 이제 객체지향 프로그래밍이 무엇인지 감이 오시나요? 이제 객체지향 프로그래밍의 특징에 대해 알아보도록 하겠습니다.

객체지향 프로그래밍의 특징은 크게 `추상화`와 `캡슐화`, `상속`과 `다형성` 4가지로 나뉩니다.

하나씩 알아보도록 할게요!

1️⃣ **추상화 (Abstraction)**

```Swift
class Person {
    private var name: String
    private var age: Int

    init(name: String, age: Int) {
        self.name = name
        self.age = age
    }

    func introduce() {
        print("7기 iOS 챌린저 여러분 안녕하세요, 저는 \(name)이고 \(age)살입니다.")
    }
}

let person = Person(name: "짐깅", age: 23)

person.introduce() // 7기 iOS 챌린저 여러분 안녕하세요, 저는 짐깅이고 23살입니다.
```

객체들이 공통적으로 필요로 하는 속성이나 동작을 하나로 추출해내는 것을 의미합니다.

아까 객체지향에서는 현실 세계의 객체를 모델링한다고 말씀드렸습니다.

이렇게 사물을 객체로 보고 필요한 공통적인 특성만 다루어 객체의 책임과 목적에만 집중할 수 있도록 해주는 것입니다.

이러한 추상화를 통해 코드의 복잡성을 낮추고 가독성을 높일 수 있겠죠?

  

2️⃣ **캡슐화 (Encapsulation)**

```Swift
class Person {
    // 내부 속성은 private으로 선언하여 외부에서 접근 불가능하도록 설정
    private var name: String
    private var age: Int

    init(name: String, age: Int) {
        self.name = name
        self.age = age
    }

    // 외부에서 접근 가능한 메서드를 통해 속성에 접근
    func introduce() {
        print("7기 iOS 챌린저 여러분 안녕하세요, 저는 \(name)이고 \(age)살입니다.")
    }

    // 외부에서 속성에 직접 접근하지 못하도록 설정
    func haveBirthday() {
        age += 1
        print("\(name)이 생일을 맞이해 \(age)살이 되었습니다.")
    }
}

// 외부에서 Person 클래스의 인스턴스 생성
let person = Person(name: "짐깅", age: 22)

// 외부에서는 private으로 선언된 속성에 직접 접근하지 못함
person.name // Error!

// 외부에서는 공개된 메서드를 통해 속성에 접근
person.introduce() // 7기 iOS 챌린저 여러분 안녕하세요, 저는 짐깅이고 22살입니다.
person.haveBirthday() // 짐깅이 생일을 맞이해 23살이 되었습니다.
```

객체의 내부 구현 로직을 외부에 드러내지 않고 내부에서만 처리하는 것을 의미합니다.

객체의 상태를 보호하고 안정성을 유지하기 위한 방법인데요!

Swift에서는 캡슐화를 위해 속성과 메서드에 대한 접근 제어자(`Access Control`)를 지원합니다.

왼쪽 예제에서 `name`과 `age` 속성은 `private`으로 선언되어 외부에서 직접 접근이 불가능한 것을 확인할 수 있는데요!

속성에 직접 접근이 불가능한 대신 `introduce()`와 `haveBirthday()` 메서드를 통해 속성에 접근하도록 합니다.

속성을 직접 변경할 수 없도록 설정해 객체의 내부 상태를 외부로부터 보호합니다.

  

3️⃣ **다형성 (Polymorphism)**

```Swift
class Student: Person {
    private var school: String
    private var grade: Int

    init(name: String, age: Int, school: String, grade: Int) {
        self.school = school
        self.grade = grade
        
        super.init(name: name, age: age)  // 부모 클래스의 생성자 호출
    }
    
    func introduce(generation: Int) {
        print("\(generation)기 iOS 챌린저 여러분 안녕하세요, 저는 \(name)이고 \(age)살입니다.")
    }
    
    // haveBirthday 메서드 override (부모 클래스의 로직 확장)
    override func haveBirthday() {
        super.haveBirthday()
        
        grade += 1
        print("생일을 맞아 \(school) \(grade)학년으로 올라갔습니다.")
    }
}
```

`Person` 클래스의 `introduce()` 메서드가 `overload` 되어 함수의 이름은 같지만 파라미터를 다르게 받아오고 있네요!

Swift에서는 `overloading` 을 허용하기 때문에 함수 이름과 파라미터, 리턴 타입 등을 고려해 함수를 식별합니다.

타입이나 리턴 값이 달라도 동일한 기능을 하는 함수를 하나로 묶기에 적합하겠죠!

또 `Person` 클래스의 `haveBirthday()` 메서드는 `override` 되어 원래 많아진 나이를 출력하던 로직에서 확장해 올라간 학년도 함께 출력하고 있습니다.

이렇게 원래 있던 메서드를 `override` 하면 기능을 재정의할 수 있습니다. 코드 중복을 줄일 수 있다는 점에서 재사용성이 높아지겠죠!

이렇게 다양한 타입을 정의하면서도 일관적인 코드를 유지할 수 있게 해주는 것을 다형성이라고 할 수 있겠습니다.

4️⃣ **상속 (Inheritance)**

```Swift
class Student: Person {
    private var school: String
    private var grade: Int

    init(name: String, age: Int, school: String, grade: Int) {
        self.school = school
        self.grade = grade
        
        super.init(name: name, age: age)  // 부모 클래스의 생성자 호출
    }

    // Student 클래스에만 있는 새로운 메서드
    func introduceStudent() {
        introduce()
        
        print("\(name)은 \(school) \(grade)학년입니다.")
    }

    override func haveBirthday() {
        super.haveBirthday()
        
        grade += 1
        print("생일을 맞아 \(school) \(grade)학년으로 올라갔습니다.")
    }
}

let student = Student(name: "짐깅", age: 22, school: "UMC대학교", grade: 3)

student.introduceStudent() //  짐깅은 UMC대학교 3학년입니다.
student.haveBirthday()      // 생일을 맞아 UMC대학교 4학년으로 올라갔습니다.
```

`Student` 클래스는 위의 `Person` 클래스를 상속받고 있습니다.

이 말인 즉 `Person` 클래스에서 정의된 `name`과 `age` 속성 및 `introduce`, `haveBirthday` 메서드를 상속받아 그대로 사용할 수 있다는 이야기가 됩니다!

상위 클래스인 `Person`의 속성과 메서드를 하위 클래스인 `Student`가 상속받아 그대로 사용할 수 있으니 코드의 길이가 줄어들고 가독성도 높아질 것입니다.

다형성과 약간 헷갈리실 수 있지만 코드의 재사용 측면이 아닌 기능의 확장 개념으로 생각하시면 둘의 차이를 금방 이해하실 수 있을 거예요!

  

### 3️⃣ SOILD 원칙이란 무엇일까요?

> 우리는 주차 초반에 좋은 설계란 `유지보수성`과 `확장성`이 뛰어난 설계라고 정의내렸죠!
> 
> `유지보수성`과 `확장성`에 열린 설계를 위해 객체지향 프로그래밍과 4가지 특징에 대해 학습했습니다.
> 
> 이번에는 유지보수와 확장에 열린 객체 설계를 위한 5가지 원칙에 대해 살펴볼텐데요! 이름도 유명한 `SOLID` 원칙입니다.
> 
> `SOLID` 원칙은 `Clean Code`, `Clean Architecture` 등의 저서를 출판한 로버트 C. 마틴이 제시한 객체지향 설계에 대한 5가지 원칙입니다.
> 
> 어떤 원칙이 있는지 하나씩 살펴보기 전에 원칙들을 이해하기 위한 두가지 개념을 먼저 살펴보도록 할까요?

💻 **결합도(Coupling)**

> 결합도는 요소 간 상호 의존 정도를 나타냅니다.
> 
> 어느정도 관련이 있는지를 나타내는 척도라고 이해하시면 좋을 것 같습니다!
> 
> 결합도가 높아지면 의존성이 커지기 때문에 코드 수정 시 다른 모듈에 영향을 끼칠 수 있습니다.
> 
> 오류가 발생했을 때도 영향을 끼칠 수 있기 때문에 결합도는 낮을수록 좋습니다!

💻 **응집도(Cohesion)**

> 응집도는 내부 요소들 간의 기능적 연관성을 나타내는 척도입니다.
> 
> 요소가 얼마나 독립적으로 존재하는지를 생각해보시면 좋을 것 같습니다!
> 
> 응집도가 높으면 수정이나 오류가 발생했을 때 하나의 요소 내에서 처리가 가능해지고, 유지보수에 용이해진다는 장점이 있습니다.
> 
> 결합도와는 반대로 높은 것이 더 좋겠죠?

1️⃣ **단일 책임 원칙 (Single Responsibility Principle, SRP)**

```Swift
class 7thChallenger {
		var name: String
		
    init(name: String) {
        self.name = name
    }
    
    private func android() {
        print("\(name)은 Android 파트를 공부하고 있어요")
    }
    
    private func iOS() {
        print("\(name)은 iOS 파트를 공부하고 있어요")
    }
    
    private func web() {
        print("\(name)은 Web 파트를 공부하고 있어요")
    }
}

let zimging = 7thChallenger(name: "짐깅")
```

==**하나의 객체는 하나의 책임만을 가져야 한다!**== 는 원칙입니다.

여기에서 `책임`이라는 말은 하나의 `기능` 정도로 이해하시면 좋을 것 같습니다.

왼쪽 코드를 함께 보면서 생각해볼까요?

7기에 새로 UMC에 들어온 열정있는 챌린저를 클래스로 만들어 보았습니다. 이제 이 클래스를 객체로 생각해볼까요?

한 챌린저가 안드로이드, iOS, 웹 스터디에 모두 참여하네요 …?

iOS만 들어도 죽을 것 같은데 안드로이드와 웹까지 참여한다니 정말 능력있는 챌린저인 것 같습니다.

물론 이렇게 계속 가면 이 챌린저는 얼마 안가 과로로 UMC를 떠나게 되겠죠?

한 객체에 너무 많은 책임을 수행하도록 구현한 경우입니다.

이 경우 어떻게 책임을 분리하면 좋을까요?

한 챌린저는 하나의 스터디만 참여할 수 있도록 클래스를 분리해주었습니다.

`7thChallenger` 로 묶여있던 클래스가 각각 `7thAndroidChallenger`, `7thiOSChallenger`, `7thWebChallenger` 로 분류되었네요!

이후 이 클래스들을 모아 `7thUMC`라는 클래스의 프로퍼티로 선언한 후 `study()` 라는 메서드를 통해 각자의 책임을 수행할 수 있도록 설계해주었습니다.

코드가 길어져서 더 복잡해졌다고 느끼실 수 있을 것 같습니다.

1️⃣ 그러나 각 클래스가 각자의 역할에만 집중할 수 있고

2️⃣ 각 클래스가 자신에게 맞는 책임을 가지고 있으니

`SRP` 를 준수한다고 볼 수 있겠죠?

이렇게 `SRP` 를 지키면 코드의 유지보수가 쉬워지고 각 클래스의 역할이 명확해진다는 장점이 있습니다.

```Swift
class 7thAndroidChallenger {
		var name: String
		
    init(name: String) {
        self.name = name
    }
    
    private func androidStudy() {
        print("\(name)은 Android 파트를 공부하고 있어요")
    }
}

class 7thiOSChallenger {
		var name: String
		
    init(name: String) {
        self.name = name
    }
    
    private func iOSStudy() {
        print("\(name)은 iOS 파트를 공부하고 있어요")
    }
}

class 7thWebChallenger {
		var name: String
		
    init(name: String) {
        self.name = name
    }
    
    private func webStudy() {
        print("\(name)은 Web 파트를 공부하고 있어요")
    }
}

class 7thUMC {
    private let androidChallenger: 7thAndroidChallenger
    private let iOSChallenger: 7thiOSChallenger
    private let webChallenger: 7thWebChallenger

    init(androidChallenger: 7thAndroidChallenger, iOSChallenger: 7thiOSChallenger, webChallenger: 7thWebChallenger) {
        self.androidChallenger = androidChallenger
        self.iOSChallenger = iOSChallenger
        self.webChallenger = webChallenger
    }

    func study() {
        androidChallenger.androidStudy()
        iOSChallenger.iOSStudy()
        webChallenger.webStudy()
    }
}
```

2️⃣ **개방-폐쇄 원칙 (Open-Closed Principle, OCP)**

```Swift
class Challenger {
    var name: String {
        return "7th UMC"
    }
    
    func study() -> String {
        return "none"
    }
}

class Tori: Challenger {
    override var name: String {
        return "토리"
    }
    
    override func study() -> String {
        return "Android"
    }
}

class Cherry: Challenger {
    override var name: String {
        return "체리"
    }
    
    override func study() -> String {
        return "iOS"
    }
}

class Dio: Challenger {
    override var name: String {
        return "디오"
    }
    
    override func study() -> String {
        return "Web"
    }
}

// 새로운 챌린저가 추가되어도 수정할 필요 없음
class ChallengerClassifier {
    func validate(challenger: Challenger) {
        print("\(challenger.name)는 \(challenger.study())를 공부하고 있습니다.")
    }
}

// 사용 예시
let classifier = ChallengerClassifier()

let tori = Tori()
let cherry = Cherry()
let dio = Dio()

classifier.validate(challenger: tori)  // "토리는 Android를 공부하고 있습니다."
classifier.validate(challenger: cherry)   // "체리는 iOS를 공부하고 있습니다."
classifier.validate(challenger: dio) // "디오는 Web를 공부하고 있습니다."
```

==**확장에는 열려있으나 변경에는 닫혀있어야 한다!**== 는 원칙입니다.

`확장에 열려있다`는 말은 기능을 확장할 때 불필요한 리소스 소모 없이 확장이 가능해야 한다는 뜻, `변경에 닫혀있다`는 말은 기능을 확장할 때 기존 코드를 최대한 수정하지 않고 확장해야 한다는 뜻입니다.

기존 코드를 최대한 수정하지 않고 확장한다는 말은 곧 연쇄적인 수정을 방지한다는 뜻입니다.

이러한 OCP를 잘 지키기 위해서는 `추상화`를 활용하면 좋은데요!

코드 예시를 함께 보도록 하겠습니다.

왼쪽처럼 구현해준다면 새로운 챌린저가 생기더라도 새로운 챌린저에 대한 객체만 만들어주면 되기 때문에 기존의 코드를 수정하지 않고 확장할 수 있습니다.

`OCP`를 잘 지키기 위해서는 새로운 기능이나 케이스가 추가될 때마다 기존의 코드를 수정해야 하는지에 대해 생각해보면 좋습니다.

변경될 것과 변경되지 않을 것을 엄격히 구분하고, 두 부분의 구분점에서 추상화를 정의해주세요.

구현체보다는 정의된 추상화에 의존하도록 코드를 작성하시면 좋습니다.

3️⃣ **리스코프 치환 원칙 (Liskov Substitution Principle, LSP)**

```Swift
class PartLeader {
    func work() -> String {
        print("안녕 나 파트장 나 일하는 중!")
        return "워크북"
    }
}

class AndroidPartLeader: PartLeader {
    override func work() {
        print("안녕 나 안드 파트장 근데 워크북은 안 줄거지롱")
        // Error: Method does not override any method from its superclass
    }
}

func 7thUMC(partLeader: PartLeader) {
		let workbook = partLeader.work()
		print(workbook)
}

let tori = AndroidPartLeader()
7thUMC(partLeader: tori)
//Error: Expressions are not allowed at the top level
```

==**서브 타입이 기반 타입의 역할을 완벽히 수행할 수 있어야 한다!**== 는 원칙입니다.

조금 더 이해가 쉽도록 설명하기 위해 서브 타입은 자식 클래스, 기반 타입은 부모 클래스에 빗대어 설명해 보겠습니다.

자식 클래스는 최소한 부모 클래스에서 가능한 행위는 수행이 보장되어야 하며, 자식 클래스가 부모 클래스의 동작을 바꿀 수 없습니다.

`LSP`의 존재 의의는 다형성에 기반합니다.

다형성을 실현하기 위해서는 클래스를 상속시켜 타입을 통합할 수 있게 하고, 이후 자식 클래스의 객체가 부모 클래스 타입으로 형변환되더라도 동작에 문제가 없도록 설계되어야 합니다.

`LSP` 를 잘 지키기 위해서는 부모 클래스의 인스턴스를 사용하는 위치에 자식 클래스의 인스턴스를 대신 사용했을 때 코드가 원래 의도대로 작동하는 지를 생각해보면 좋습니다.

왼쪽 예시에서는 `AndroidPartLeader` 클래스에서 부모 클래스인 `PartLeader` 의 형식을 어기고 값을 반환하고 있지 않은 모습을 확인할 수 있습니다.

서브 타입은 언제나 기반 타입으로 교체될 수 있어야 하기 때문에 `LSP`를 위반한 사례라고 볼 수 있겠죠!

오른쪽 코드에서는 `AndroidPartLeader` 가 `PartLeader` 가 제시한 반환 타입을 충실히 `override`하고 있는 모습을 확인할 수 있네요!

이 경우 `LSP`를 잘 지킨 사례라고 볼 수 있겠습니다.

단, 상속 시에는 강한 결합도가 생기기 때문에 항상 주의하면서 코드를 작성해야 합니다.

```Swift
class PartLeader {
    func work() -> String {
        print("안녕 나 파트장 나 일하는 중!")
        return "워크북"
    }
}

class AndroidPartLeader: PartLeader {
    override func work() -> String {
        print("안녕 나 안드 파트장 나 일하는 중!")
        return "안드로이드 워크북"
    }
}

func 7thUMC(partLeader: PartLeader) {
		let workbook = partLeader.work()
		print(workbook)
}

let tori = AndroidPartLeader()
7thUMC(partLeader: tori)
```

4️⃣ **인터페이스 분리 원칙 (Interface Segregation Principle, ISP)**

```Swift
protocol ChallengerWorkBook {
    func androidWorkbook()
    func iOSWorkbook()
    func webWorkbook()
}

class Challenger: ChallengerWorkBook {
    func androidWorkbook() {
        print("iOS 챌린저인데 Android 워크북 하는 중...")
    }

    func iOSWorkbook() {
        print("iOS 워크북 하는 중...")
    }

    func webWorkbook() {
        print("iOS 챌린저인데 Web 워크북 하는 중...")
    }
}
```

==**클라이언트가 자신이 사용하지 않는 인터페이스에 불필요하게 의존하지 않아야 한다!**== 는 원칙입니다.

막상 프로토콜이나 클래스를 상속받았을 때 상속받은 모든 메서드를 사용할 필요가 없는 상황이라면 어떨까요?

이를 불필요한 인터페이스에 의존한다는 표현을 사용합니다. 이런 불필요한 의존은 보통 해롭게 여겨지는데요. 그 이유는 무엇일까요?

> 그 이유는
> 
> 1️⃣ 불필요한 빌드나 문제를 유발하고
> 
> 2️⃣ 인터페이스가 거대해지는 경우 SRP를 위반하는 경우가 생길 수 있기 때문
> 
> 입니다.

왼쪽 예시에서 `Challenger`는 `ChallengerWorkBook`이라는 프로토콜을 준수하고 있습니다.

근데 `ChallengerWorkBook` 에 안드로이드와 iOS, 웹의 워크북이 모두 들어가 있기 때문에 `Challenger` 클래스에서는 모든 워크북 함수를 구현해야 합니다. 불필요한 부분이죠!

그래서 왼쪽 코드는 `ISP`를 위반한 사례가 됩니다.

그래서 이런 경우에는 프로토콜을 분리해 필요한 것만 채택해 사용할 수 있도록 하는 것이 좋습니다.

오른쪽 코드에서는 파트별로 프로토콜을 분리해 필요한 파트만 구현할 수 있도록 했습니다. `ISP`를 준수하고 있죠?

`SRP`와 약간 헷갈리는 부분이 있으실 것 같은데요! 차이점을 설명해보겠습니다.

> `SRP`는 클래스의 단일 책임 원리, `ISP`는 인터페이스의 단일 책임 원리라는 점에서 차이점이 있습니다.
> 
> 인터페이스는 클래스와 다르게 여러 개의 역할을 가질 수 있습니다.
> 
> 그러므로 관련 있는 기능끼리 하나의 인터페이스에 모으면서 크기가 불필요하게 커지지는 않도록 크기를 제한하는게 이상적이겠죠!
> 
>   

```Swift
protocol Android {
    func androidWorkbook()
}

protocol iOS {
    func iOSWorkbook()
}

protocol Web {
    func webWorkbook()
}

class androidChallenger: Android {
    func androidWorkbook() {
        print("Android 워크북 하는 중...")
    }
}

class iOSChallenger: iOS {
    func iOSWorkbook() {
        print("iOS 워크북 하는 중...")
    }
}

class webChallenger: Web {
    func webWorkbook() {
        print("Web 워크북 하는 중...")
    }
}
```

5️⃣ **의존성 역전 원칙 (Dependency Inversion Principle, DIP)**

```Swift
class Challenger {
    func doWorkbook() {
        print("챌린저는 워크북 하는 중!")
    }
}

class PartLeader {
    let challenger: Challenger
    
    init(challenger: Challenger) {
        self.challenger = challenger
    }
    
    func deployment() {
		    print("파트장은 워크북 배포 완료!")
        challenger.doWorkbook()
    }
}

let challenger = Challenger()
let partLeader = PartLeader(challenger: challenger)

partLeader.deployment()
```

==**상위 레벨의 모듈은 하위 레벨의 모듈에 의존해서는 안된다!**== 는 원칙입니다.

왼쪽 코드는 `PartLeader` 클래스가 `Challenger` 클래스에 직접적으로 의존하도록 설계되어 있습니다.

물론 iOS 챌린저들은 항상 워크북을 잘 해내시겠지만 … 불의의 일로 인해 워크북을 제대로 수행하지 못하는 상황이 온다면 왼쪽 코드에서는 제대로 일을 완수하지 못할 겁니다.

`Challenger` 클래스는 변동성이 큰 요소이기 때문에 `Challenger` 클래스에 의존하는 것은 지양해야 합니다. 안정적인 추상 인터페이스를 구현하기 힘든 설계이기 때문이예요!

`DIP`를 위반하게 되면 하위 요소의 구체적인 내용에 의존하게 되면서 하위 요소의 변화가 있을 때마다 상위 요소의 코드를 자주 수정하게 되는 불상사가 발생합니다. 아찔하죠?

이 코드를 어떻게 고쳐볼 수 있을까요?

이 경우에는 `protocol`을 이용해 `DIP`를 준수할 수 있습니다.

`PartLeader` 클래스 내에 있는 `challenger` 변수는 굳이 `zimging`이 아니더라도 다른 클래스도 인스턴스로 받을 수 있습니다.

`zimging`이 워크북을 제대로 수행하지 않아도 `PartLeader` 의 코드를 수정할 필요가 없겠죠!

`PartLeader` 클래스는 `Challenger` 프로토콜에 의존하므로 `Challenger` 프로토콜을 준수하는 어떤 클래스의 인스턴스라도 `PartLeader` 클래스에 전달이 가능합니다.

이렇게 `DIP`를 준수하면 코드의 유연성과 확장성이 향상될 수 있겠죠!

```Swift
protocol Challenger {
		func doWorkbook()
}

class PartLeader {
    let challenger: Challenger
    
    init(challenger: Challenger) {
        self.challenger = challenger
    }
    
    func deployment() {
		    print("파트장은 워크북 배포 완료!")
        challenger.doWorkbook()
    }
}

class zimging: Challenger {
    func doWorkbook() {
        print("챌린저는 워크북 하는 중!")
    }
}

let challenger: Challenger = zimging()
let partLeader = PartLeader(challenger: challenger)

partLeader.deployment()
```

## 🔥 6주차 개념 점검

---

> [!important] **좋은 설계란 무엇일까요? 그리고 왜 우리는 좋은 설계를 해야 할까요?**

- **여기에 답을 적어주세요!**
    
    유지보수와 확장성이 좋은 코드, 기술 부채를 덜 쌓이게 하기 위해
    

> [!important] **절차지향 프로그래밍과 객체지향 프로그래밍의 차이는 무엇에 기반할까요?**

- **여기에 답을 적어주세요!**
    
    절차지향 프로그래밍은 **단계를 순차적으로 따라가며 문제를 해결**하고, 객체지향 프로그래밍은 **현실 세계의 객체들이 각각의 역할과 책임을 가지고 서로 상호작용하며 문제를 해결**합니다.
    

> [!important] **아래 코드는 객체지향 프로그래밍의 특징 중 어떤 특징에 기반한 코드일까요?**
> 
> ```Swift
> class Person {
>     // 내부 속성은 private으로 선언하여 외부에서 접근 불가능하도록 설정
>     private var name: String
>     private var age: Int
> 
>     init(name: String, age: Int) {
>         self.name = name
>         self.age = age
>     }
> 
>     // 외부에서 접근 가능한 메서드를 통해 속성에 접근
>     func introduce() {
>         print("7기 iOS 챌린저 여러분 안녕하세요, 저는 \(name)이고 \(age)살입니다.")
>     }
> 
>     // 외부에서 속성에 직접 접근하지 못하도록 하는 메서드
>     func haveBirthday() {
>         age += 1
>         print("\(name)이 생일을 맞이해 \(age)살이 되었습니다.")
>     }
> }
> ```

- **여기에 답을 적어주세요!**
    
    캡슐화
    

> [!important] `ISP`와 `SRP`의 차이점은 무엇일까요?

- **여기에 답을 적어주세요!**
    
    `SRP`는 클래스의 단일 책임 원리, `ISP`는 인터페이스의 단일 책임 원리라는 점에서 차이점이 있습니다. 인터페이스는 클래스와 다르게 여러 개의 역할을 가질 수 있습니다.
    

## 💻 6주차 과제

---

> [!important] **화면 구현에 필요한 레이아웃과 리소스는 아래 피그마를 참고해주세요!**
> 
>   
>   
>   
> 모르는 부분은 **최대한 자신의 힘(구글링 등 자료 검색)으로 해결하신 후 팀원들과 파트장에게 질문**해보시는 것을 추천드립니다.
> 
> ==**생성형 AI의 무분별한 사용은 성장을 저해할 수 있습니다.**==
> 
> ==**충분한 생각을 거친 후의 개념 또는 오류 코드에 대한 질문은 좋지만 코드 자체를 AI에게 부탁하거나, 시도해보지 않고 오류를 질문하는 것은 최대한 지양해주세요.**==
> 
> **코드를 작성할 때 이유를 생각할 수 있는 iOS 개발자**가 되시길 바라겠습니다 🔥  
>   
> 
> [https://embed.figma.com/design/47IuhJxc7LFTwOYWtDgTdi/iOS-%EC%9B%8C%ED%81%AC%EB%B6%81?node-id=1773-396&t=japgdVZ8N4UlLo8p-1&embed-host=notion](https://embed.figma.com/design/47IuhJxc7LFTwOYWtDgTdi/iOS-%EC%9B%8C%ED%81%AC%EB%B6%81?node-id=1773-396&t=japgdVZ8N4UlLo8p-1&embed-host=notion)

### 1. 세부 화면 레이아웃을 구현해주세요!

> [!important] **실습 체크리스트**
> 
> - [x] **제공된 피그마 링크로 접속해** ==**제공된 메인 화면의 레이아웃을 구현**==**합니다.**
>     - [x] **단, 레이아웃은** ==**반드시**== ==`**SnapKit**`====**을 이용**==**해 구현합니다.**
>     - [x] **피그마에 명시된 레이아웃에 맞게** ==**크기와 간격을 정확히 반영**==**합니다.**
>     - [x] **세부 화면 상단의 뒤로가기 버튼은** `**UINavigationController**`**를 이용해 구현해주세요!**
>     - [x] **옷 정보 사진 아래의 다른 색상 옷 리스트는** `**UICollectionView**`**를 이용해 구현되어야 합니다.**
>         - [x] 가로 스크롤이 가능하도록 구현해주세요!
>         - [x] 세로 스크롤은 불가능하도록 구현해주세요!
>     - [x] **구매 버튼을 클릭했을 때** ==`**Modal**`== ==**방식으로 아래에서 시트가 올라오도록 구현**==**해주세요!**
>         - [x] 시트 상단의 ==**X 버튼을 눌렀을 때 위에서 아래로 시트가 내려가도록 구현**==해주세요!
>     - [x] **판매 버튼은** `**UIButton**`**으로 구현하되** ==**눌렀을 때의 액션은 따로 구현하지 않으셔도 됩니다.**==
>         - [x] 마찬가지로 세부 화면의 `빠른배송`, `일반배송` 버튼도 구현만 진행해주세요!
>     - [x] `**S**`**,** `**M**`**,** `**L**`**,** `**XL**`**,** `**XXL**` **등** ==**사이즈 버튼은 하나씩만 선택되도록 구현**==**해주세요!**
>         - [x] `XL` 사이즈가 선택된 상태에서 `S` 사이즈가 선택되면 `XL` 사이즈의 선택은 해제되는지 확인해주세요!

### 2. OOP와 SOLID 원칙을 적용해 리팩토링을 진행해주세요!

> [!important] **실습 체크리스트**
> 
> - [x] 1~6주차까지 구현한 화면 중 하나의 화면을 자유롭게 선택한 후 `OOP`가 적용되도록 리팩토링을 진행합니다.
>     - [x] 단, 6주차를 선택했을 경우 처음부터 코드를 `OOP`에 맞게 작성한 것이 아님이 증명되어야 합니다.
>         - [x] 깃허브 커밋 기록 등 검사 시 리팩토링의 흔적을 확인할 수 있도록 구현해주세요!
>     - [x] 리팩토링 이후 제공된 양식(3번)에 맞추어 어떤 부분을 보완했는지, 어떻게 리팩토링을 진행했는지 자세히 작성합니다.
> - [x] 1~6주차까지 구현한 화면 중 하나의 화면을 자유롭게 선택한 후 `SOLID` 원칙 중 하나가 적용되도록 리팩토링을 진행합니다.
>     - [x] 단, 6주차를 선택했을 경우 처음부터 코드를 `SOLID` 원칙에 맞게 작성한 것이 아님이 증명되어야 합니다.
>         - [x] 깃허브 커밋 기록 등 검사 시 리팩토링의 흔적을 확인할 수 있도록 구현해주세요!
>     - [x] 원칙은 `SOLID` 원칙 중 하나 이상을 자유롭게 선택해주시면 됩니다.
>     - [x] 리팩토링 이후 제공된 양식(3번)에 맞추어 어떤 부분을 보완했는지, 어떻게 리팩토링을 진행했는지 자세히 작성합니다.

### 3. OOP에 맞추어 리팩토링을 진행하셨다면 리팩토링 과정을 설명해주세요!

### 💻 저는 이 화면을 리팩토링하기로 했어요

---

> [!important] 어떤 화면을 리팩토링 하기로 했는지 이유와 함께 설명해주세요!
> 
> 가장 초반에 만들었던 Login화면을 리팩토링 하기로 했습니다 - 가장 처음 만들어서 엉망진창이고, 주차가 쌓이면서 다양한 기능이 쌓여 정리할 필요 느낌

### 💻 리팩토링 과정 중에는 이런 부분에 신경써봤어요

---

> [!important] 어떤 부분이 문제였고, 그 부분을 어떻게 리팩토링하려고 노력했는지 자세히 작성해주세요! 코드도 함께 첨부해주시면 좋습니다.

- 수정사항
    
    로그인 버튼의 경우 비슷한 프로퍼티가 많았지만 각각 정의되어있었음, 간편로그인은 카카오나 애플 말고도 많이 있으니 리팩토링하여 추후에 기능추가가 용이할거라고 생각
    
    ![[CleanShot_2024-11-16_at_22.26.202x.png]]
    

### 4. SOLID 원칙에 맞추어 리팩토링을 진행하셨다면 리팩토링 과정을 설명해주세요!

### 💻 저는 이 화면을 리팩토링하기로 했어요

---

> [!important] 어떤 화면을 리팩토링 하기로 했는지 이유와 함께 설명해주세요!
> 
> myView 화면에서 프로필 이름이 view 클라스에서 유저디폴트에서 불러와 지는것을 발견하여 viewController로 옮겨보기로 함

### 💻 리팩토링 과정 중에는 이런 부분에 신경써봤어요

---

> [!important] 어떤 부분이 문제였고, 어떤 원칙을 선택해 리팩토링 했는지도 자세히 작성해주세요! 코드도 함께 첨부해주시면 좋습니다.

![[CleanShot_2024-11-16_at_22.59.432x.png]]

### 5. 과제가 완성 되었다면 깃허브 링크와 시연 영상을 첨부해주세요!

> [!important] **시연 영상 체크리스트**
> 
> - [x] `AutoLayout`이 잘 적용되어 있음을 확인할 수 있나요?
>     - [x] `iPhone 15 Pro`, `iPhone 13 mini` 시뮬레이터에서 테스트한 내용이 모두 들어가게 영상을 업로드해주세요.
> 
>   
> ==**체크리스트 항목을 모두 만족하는 영상만 업로드**==해주시길 바랍니다.

> **깃허브 링크 임베드**

> [!info] GitHub - TUK-UMC/7th_UMC_iOS at 쿠트_김의택  
> 7th UMC iOS.  
> [https://github.com/TUK-UMC/7th_UMC_iOS/tree/%EC%BF%A0%ED%8A%B8_%EA%B9%80%EC%9D%98%ED%83%9D](https://github.com/TUK-UMC/7th_UMC_iOS/tree/%EC%BF%A0%ED%8A%B8_%EA%B9%80%EC%9D%98%ED%83%9D)  

  

> **시연 영상 업로드** ==(영상 개수 제한 X)==

![[Assets/13mini 3.mp4|13mini 3.mp4]]

![[_iPhone_16_Pro.mp4]]

## 🤔 6주차 트러블 슈팅

---

## 📌 이번 주차에는 이런 내용을 학습했어요!

---

==워크북을 진행하며 스스로 공부해본 내용을 이곳에 자유 양식으로 정리해 보세요!  
주차마다 하나씩은 작성해주셔야 합니다.  
==

### 🍎 학습한 내용 제목

### **📑 학습 내용**

> [!info] swift - 컬렉션뷰 버튼 토글하기!  
> 망딕이 구현해야 할 것은 다음과 같다 지역 버튼은 최대 1개까지 선택이 가능하다 클릭된 버튼 : 빨간색, 클릭되지 않은 버튼 : 회색 회색 버튼을 클릭 - 다른 빨간색 버튼이 있다면 회색으로 바꾸고, 클릭된 버튼을 빨간색으로 변경!  
> [https://leemyungjic.tistory.com/15](https://leemyungjic.tistory.com/15)  

> [!info] [iOS]  
> 안녕하세요!  
> [https://medium.com/@tellingme/ios-cf47100945f8](https://medium.com/@tellingme/ios-cf47100945f8)  

### **📚 참고 자료**

## ❓ 이런 질문이 있어요!

---

워크북을 진행하면서 궁금했던 점 또는 해결하지 못한 부분을 미리 작성하고 스터디에서 함께 논의해 보세요!  
해결하지 못한 질문이나 궁금한 점이 있다면 언제든지 편하게 DM 주세요 🙋‍♀️  

  

---

Copyright © 2024 Lee Youjin All rights reserved.

Copyright © 2024 Jeong Euichan All rights reserved.