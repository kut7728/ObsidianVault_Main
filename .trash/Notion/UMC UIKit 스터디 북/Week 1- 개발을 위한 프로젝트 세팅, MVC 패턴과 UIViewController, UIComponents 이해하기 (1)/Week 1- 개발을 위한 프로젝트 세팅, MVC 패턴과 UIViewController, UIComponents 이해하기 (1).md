- [[#📋 학습 목표]]
- [[#🔥 1주차 개념 설명]]
    - [[#1️⃣ MVC 패턴 알기]]
    - [[#2️⃣ Xcode UI 커스터마이징 기초]]
    - [[#3️⃣ UIViewController 이해하기]]
    - [[#4️⃣ UIComponents 이해하기]]
- [[#🔥 1주차 개념 점검]]
- [[#📚 1주차 실습]]
    - [[#1. SceneDelegate 설정]]
    - [[#2. 분석]]
    - [[#3. 파일 및 폴더 생성 ]]
    - [[#4. Model 작성하기]]
    - [[#5. View 작성]]
    - [[#6. ViewController 버튼 액션 추가 및 모델 연결]]
    - [[#7. 최종 결과 화면 및 최종 코드]]
- [[#💻 1주차 과제]]
    - [[#1. 프로젝트 파일 생성]]
    - [[#2. 스토리보드 파일 삭제 및 SceneDelegate 설정]]
    - [[#3. 폴더 및 파일 생성]]
    - [[#4. 로그인 레이아웃 구현]]
    - [[#5. 과제가 완성 되었다면 깃허브 링크와 시연 영상을 첨부해주세요!]]
- [[#🤔 1주차 트러블 슈팅]]
- [[#📌 추가적으로 더 공부해 봤어요! ]]
- [[#❓ 이런 질문이 있어요!]]

- 스터디 사진
    
    ![[KakaoTalk_Photo_2024-10-23-10-57-25-1.png]]
    
      
    

## 📋 학습 목표

---

> **MVC 패턴 알기**  
>   
> **Xcode UI 커스터마이징 기초**  
>   
> **UIViewController 이해하기**  
>   
> **UIComponents 이해하기**  

  

## 🔥 1주차 개념 설명

---

### 1️⃣ MVC 패턴 알기

![[스크린샷_2024-09-04_오전_9.30.15.png]]

### MVC 패턴이란 무엇일까?

MVC패턴은 소프트웨어 디자인 패턴 중 하나입니다. 애플리케이션을 ==**세 가지 주요 컴포넌트로 분리하여 개발하는 구조**==입니다.

이 패턴을 사용하여 코드의 모듈화를 촉진하고, 유지 보수를 용이하게 하며, 재사용성을 높이는 데 목적이 있습니다.

  

### 1. Model(모델)

> 모델은 애플리케이션의 데이터와 비즈니스 로직을 관리합니다. 데이터를 정의하고 데이터를 가져오거나 수정하는 기능을 담당합니다.  
> ==**모델은 뷰나 컨트롤러에 적접적인 UI 정보를 제공하지 않으며, 단지 데이터와 관련된 작업만 처리합니다.**==

### 2. View(뷰)

> 뷰는 사용자 인터페이스(UI)를 담당합니다. 사용자가 볼 수 있는 화면을 구성하며, 모델에서 제공된 데이터를 사용자에게 표시하는 역할을 합니다. ==**뷰는 데이터가 어떻게 표시되는지에 대한 부분만 담당하며, 데이터의 변화를 직접 처리하지 않습니다.**==

### 3. Controller(컨트롤러)

> 컨트롤러는 모델과 뷰 서이에 중개자 역할을 합니다. 사용자의 입력을 받아 모델을 업데이트하고, 업데이트된 데이터를 다시 뷰에 반영하여 UI를 갱신하는 기능을 합니다. ==**컨트롤러는 사용자의 요청을 해석하고, 이를 처리하기 위해 필요한 모델과 뷰를 제어합니다.**==

  

# 그럼 왜 iOS 앱 개발에서 MVC를 알아야 하는가? 🧐

  

**UIkit은 MVC 패턴에 기반하여 설계되었습니다**. 즉 애플리케이션을 개발할 때 기본적으로 MVC 패턴을 따라야 UIkit 프레임워크를 효율적으로 사용할 수 있습니다.!

  

MVC 패턴을 통해 뷰와 컨트롤러를 명확히 분리하면 다양한 사용자 인터페이스 요구사항에 유연하게 대응할 수 있습니다. 앱을 개발할 때 UI가 변경되거나 새 기능이 추가될 때, 뷰와 컨트롤러 간의 명확한 역할 분리 덕분에 UI를 독립적으로 변경할 수 있습니다.

  

그럼 iOS에서 MVC가 어떻게 적용되고 있는지 예시를 볼까요??

  

### 1. Model(모델)

> 모델은 CoreData, Realm, 간단한 구조체 및 클래스 등으로 구현할 수 있습니다.

> 만약 `User` 구조체는 사용자의 이름과 나이를 담고 있다고 가정하면 아래 코드와 같이 `User` 정보를 관리합니다.

```Swift
import Foundation

struct UserData {
    var name: String
    var age: Int
    
    mutating func increaseAge() {
        self.age += 1
    }
}
```

> [!important] Structure와 Enumerations 는 Value Type으로 내부에서 메소드로 내부값을 변경 불가<br>→ 메소드에 mutating을 명시하여 변경 가능<br>

### 2. View(뷰)

> UIView, UILabel, UIButton 등등 UIComponent 들이 존재합니다. 컴포넌트에 대해서는 추후 설명할 예정입니다. 이러한 UI 요소를 사용하여 데이터를 화면에 표시하는 뷰입니다. 뷰는 데이터를 직접 다루지 않고, 단순히 데이터를 화면에 표시하는 역할만 합니다.

> `User` 모델을 정의했으니, 이제 `User` 모델을 뷰에 담아 표시해보도록 하겠습니다. 아래 코드를 참고해주세요!

```Swift
import UIKit

class UserView: UIView {

    let nameLabel: UILabel = {
        let label = UILabel()
        label.textAlignment = .center
        label.font = UIFont.systemFont(ofSize: 20)
        return label
    }()
    
    let ageLabel: UILabel = {
        let label = UILabel()
        label.textAlignment = .center
        label.font = UIFont.systemFont(ofSize: 17)
        return label
    }()
    
    let increaseAgeBtn: UIButton = {
        let btn = UIButton(type: .system)
        btn.setTitle("나이 증가", for: .normal)
        return btn
    }()
    
    override init(frame: CGRect) {
        super.init(frame: frame)
        
        let stackView = UIStackView(arrangedSubviews: [nameLabel, ageLabel, increaseAgeBtn])
        stackView.axis = .vertical
        stackView.spacing = 10
        stackView.translatesAutoresizingMaskIntoConstraints = false
        addSubview(stackView)
        
        NSLayoutConstraint.activate([
            stackView.centerXAnchor.constraint(equalTo: self.centerXAnchor),
            stackView.centerYAnchor.constraint(equalTo: self.centerYAnchor)
        ])
    }
    
    required init?(coder: NSCoder) {
        fatalError()
    }
}
```

  

  

### 3. Controller(컨트롤러)

> 컨트롤러는 `UIViewController` 를 사용하여 사용자의 입력을 처리하고, 모델과 뷰 간의 데이터 흐름을 관리합니다.

> 사용자가 버튼을 누르면 `User` 모델의 나이가 증가하고, 그에 따라 UI가 갱신됩니다.

```Swift
import UIKit

class ViewController: UIViewController {
    
    private lazy var user: UserData = {
        return UserData(name: "Jeong", age: 28)
    }()
    
    private lazy var userView: UserView = {
        let view = UserView()
        view.increaseAgeBtn.addTarget(self, action: \#selector(increaseBtnTapped), for: .touchUpInside)
        return view
    }()

    override func viewDidLoad() {
        super.viewDidLoad()
        self.view = userView
        self.view.backgroundColor = .white
        self.updateUserView()
    }
    
    private func updateUserView() {
        userView.nameLabel.text = "Name: \(user.name)"
        userView.ageLabel.text = "Age: \(user.age)"
    }

    @objc private func increaseBtnTapped() {
        user.increaseAge()
        updateUserView()
    }
}
```

  

### 실행화면

- 나이 증가 버튼 누르기 전 결과 화면

![[스크린샷_2024-09-04_오전_10.30.34.png]]

- 나이 증가 버튼 누른 후 결과 화면

![[스크린샷_2024-09-04_오전_10.31.02.png]]

> [!important] 위 코드 내부에서 사용되고 있는 키워드, UI Component 등등 자세한 설명은 앞으로 워크북을 공부하게 되면서 배우게 될 것입니다.

  

### 동작 과정

- ViewDidLoad() 메서드에서 `userView` 와 `user` 가 각각 처음으로 호출되어 뷰와 모델이 초기화됩니다.
- `userView` 는 사용자 인터페이스를 담당하며, “IncreaseAge” 버튼을 눌렀을 때 `increaseBtnTapped()` 메서드가 호출됩니다.
- 이 메서드는 `user`의 나이를 증가시키고, 변경된 데이터를 다시 뷰에 반영하여 UI를 업데이트 합니다.

  

**MVC 패턴을 지키면서 코드를 작성하는 것은 단순한 권장이 아니라, 더 다은 품질의 애플리케이션을 만들기 위한 필수적인 방법입니다.**

MVC 패턴을 제대로 이해하고 활용한다면, 프로젝트의 복잡도가 증가하더라도 유연하고 견고한 코드를 작성할 수 있을 것입니다.

==**반드시 MVC의 원칙을 지키면서 코드를 작성하는 습관을 들이세요! 앞으로의 워크북 진행과 UMC 프로젝트 진행에 있어 중요한 첫 걸음이 될 것입니다.**==

  

**이제 iOS 개발에서의 UI 커스터마이징 기초에 대해 살펴 보겠습니다. Xcode를 사용하여 어떻게 화면을 설계하고, 기본적인 UI 컴포넌트를 커스터마이징할 수 있는지 알아보겠습니다.**

### 2️⃣ Xcode UI 커스터마이징 기초

## iOS 화면 구조(View Hierarchy)

  

![[NavigationViews_2x_e69e98a2-aaac-477e-9e33-92e633e29cc7.png]]

  

iOS 앱에서 화면은 여러 레이어로 이루어져 있으며, 이들 레이어는 각각 다른 역할을 담당합니다.

**UIView 계층 구조**는 사용자가 화면에서 볼 수 있는 모든 인터페이스 요소들을 계층적으로 배치합니다.

기본적으로 최상위에는 Window가 있고, 그 아래에 다양한 뷰들이 배치됩니다. 이를 이해하면 복잡한 UI를 효과적으로 관리할 수 있습니다.

  

**위 사진에 Window, Tab bar View, Navigation VIewm Custom View hierachy로 이루어져 있습니다.**

**이것은 iOS 화면 계층 구조의 구성 요소입니다.**

1. Window(윈도우)
    1. iOS 앱의 최상위 레이어로, 모든 UI 요소는 이 ==**UIWindow**== 객체 안에 배치됩니다. 모든 화면은 Window위에 그려지며 앱의 시작점입니다.
2. Tab Bar View (탭 바 뷰)
    1. 화면 하단에 위치한 탭 바는 앱의 여러 주요 섹션으로 이동할 수 있는 **탭**을 제공합니다. 여러 화면을 쉽게 전환할 수 있도록 ==**UITabBarController**==를 사용하여 구현됩니다.
3. Navigation View(네비게이션 뷰)
    1. 주로 화면 상단에 위치하는 내비게이션 바는 화면 간 이동을 지원합니다. 상위 화면으로 돌아가기 위한 뒤로 가기 버튼이나 화면의 타이틀을 표시하며, ==**UINavigationController**==를 통해 계층적인 화면 전환을 관리합니다.
4. Custom View Hierarchy(커스텀 뷰 계층 구조)
    1. ==**실제로 사용자가 상호작용하는 화면의 콘텐츠가 표시되는 커스텀 뷰**==입니다. UIView 객체를 기반으로 구성되며 개발자가 자유롭게 설계하고 커스터마이징할 수 있습니다. 이 안에는 `UILabel`, `UIButton`, `UIImageView` 등등 같은 구체적인 UI 요소들이 포함됩니다.

  

## Xcode에서 UI 커스터마이징

> Xcode는 iOS 앱 개발의 핵심 도구로, UI를 커스터마이징하는 다양한 방법을 제공합니다.

  

> [!important] ==**❗️❗️❗️❗️❗️ 저희 워크북은 CodeBase로 하여 직접 코드 작성으로 하는 UI 커스터마이징을 할 것이기 때문에, 스토리보드 사용과 그에 대한 설명은 하지 않도록 하겠습니다. ❗️❗️❗️❗️❗️**==

  

### 1. 스토리보드와 Interface Builder

- 스토리보드는 Xcode의 시각적인 UI 구성 도구로, 앱의 여러 화면을 연결하여 전체적인 사용자 흐름을 디자인할 수 있습니다.
- **Object Library**에서 필요한 UI 요소( `UILabel`, `UIButton`, `UIImageView` 등등 ) 을 드래그하여 화면에 배치하고 **Attributes Inspector**에서 속성을 수정할 수 있습니다.
    
    ![[스크린샷_2024-09-04_오후_1.07.18.png]]
    

  

### 2. 코드를 통한 UI 생성 및 커스터마이징

> 코드를 사용하여 UI를 생성하고 커스터마이징 하는 것은 iOS 앱 개발에서 매우 유연하고 강력한 방법입니다. Interface Builder를 사용하지 않고 직접 코드를 작성해 UI를 구성하면, 화면 배치나 디자인을 더 세밀하게 제어할 수 있습니다. 또한, 코드 기반 UI는 **동적인 레이아웃**이나 **재사용 가능한 컴포넌트**를 만들 때 강력한 도구로 작용합니다.

> [!important] ==**[❗️](https://www.notion.so/34c3fbc69a634a7a9dd34df548f5785e?pvs=21)**== ==**위**====**에 언급했듯이 저희 워크북은 10주차가 끝날 때까지 스토리보드 사용 방식이 아닌, 코드를 통**====**한 UI 생성 및 커스터마이징을 할 것임을 알아주시기 바랍니다.**====**❗️**==

  

❗️❗️❗️ ==**코드로 UI를 생성하기 전, Xcode에서 프로젝트 파일 생성 후 꼭 해야할 단계가 있습니다**== ❗️❗️❗️

### ==1. storyboard 파일 삭제==

프로젝트 파일 생성 후, ==**Main.storyboard**== 파일과 ==**LaunchScreen.storyboard**== 파일을 삭제합니다.

![[스크린샷_2024-09-10_오후_5.28.59.png]]

### ==2. 해당 프로젝트 Info.plist 수정하기==

1. 프로젝트 파일을 클릭합니다.
2. TARGETS의 프로젝트 파일을 클릭합니다.
3. 상단의 Info 탭으로 들어갑니다.
4. 아래 사진에 보이듯이 `Main storyboard file base name` 클릭 후, 백스페이스로 지웁니다.
5. 아래 사진에 보이듯이 `Application Scene Manifest -> Scene Configuration -> Window Application Session Role -> Item 0 -> Storyboard Name` 클릭 후, 백스페이스로 지웁니다.

  

즉, `Main storyboard file base name` 파일과 `Storyboard Name` 파일을 삭제를 하시면 되겠습니다.

![[스크린샷_2024-09-10_오후_5.33.11.png]]

### ==3. SceneDelegate 설정==

SceneDelegate.swift 파일을 클릭하면 이렇게 화면이 보일겁니다. 여기서 기본으로 설정할 뷰 컨트롤러를 작성해야 실행할 수 있습니다.

![[스크린샷_2024-09-10_오후_5.50.01.png]]

아래 사진 속, `func scene(_ scene: UIScene, willConnectTo session: UISceneSession, options connectionOptions: UIScene.ConnectionOptions)` 메소드의 내부에 코드를 작성해야 합니다.

![[스크린샷_2024-09-10_오후_5.58.26.png]]

  

아래 사진 처럼 아래 코드를 작성해서 넣어주시면 되겠습니다.

![[스크린샷_2024-09-10_오후_6.04.14.png]]

```Swift
 guard let windowScene = (scene as? UIWindowScene) else { return }
        window = UIWindow(frame: windowScene.coordinateSpace.bounds)
        window?.windowScene = windowScene
        window?.rootViewController = ViewController() // 원하는 뷰 컨트롤러 파일의 이름을 작성하면 됩니다.
        window?.makeKeyAndVisible()
```

> [!important] 코드에 대한 자세한 설명과 **SceneDelegate**에 대한 설명은 워크북의 하단 개념 점검 문제를 푸시면서 스스로 학습 하시면 되겠습니다.!

  

### ==4. ViewController 실행==

아래 사진처럼 뷰 컨트롤러의 코드를 작성 후 실행해서 초록색 화면의 시뮬레이터가 제대로 등장하면 됩니다!

![[스크린샷_2024-09-10_오후_6.08.28.png]]

  

  

같은 UI 요소를 ==**스토리보드로 진행할 때(**====**)**==와 아래 **코드로 진행할 때**의 모습을 확인해주시기 바랍니다.

코드로 진행 하기 전, 위에 진행된 사전준비를 완료해주시기 바랍니다.

  

- **코드로 생성한 Button**

```Swift
class UIButtonCustomViewController: UIViewController {
    

    override func viewDidLoad() {
        super.viewDidLoad()
        self.view.backgroundColor = .white
        self.view.addSubview(button)
        button.centerXAnchor.constraint(equalTo: view.centerXAnchor).isActive = true
        button.centerYAnchor.constraint(equalTo: view.centerYAnchor).isActive = true
    }
    
    private lazy var button: UIButton = {
        let btn = UIButton()
        btn.setTitle("UIButton 입니다.", for: .normal)
        btn.setTitleColor(.black, for: .normal)
        btn.translatesAutoresizingMaskIntoConstraints = false
        return btn
    }()
}
```

  

- **결과 화면**
    
    ![[스크린샷_2024-09-10_오후_5.20.35.png]]
    

  

  

**스토리보드로 진행한 사진 속 UI**를 **코드 방식으로 전환**하면 위의 코드가 되고, 똑같은 뷰가 생성됩니다.

  

> [!important] iOS 화면 구조와 Xcode UI 커스터마이징을 이해하고 적용하는 것은 iOS 앱 개발의 중요한 기본입니다. 이를 통해 직관적이고 사용자가 만족하는 인터페이스를 설계할 수 있으며, 다양한 기기에서 안정적으로 동작하는 앱을 구현할 수 있습니다.

  

이제 이러한 UI 구성 요소를 화면에 올리고 사용자와 상호작용하는 과정에서 중요한 역할을 담당하는 **UIViewController**에 대해 알아보겠습니다.

  

**UIViewController**는 iOS 앱에서 화면을 관리하고, 데이터 흐름을 제어하며, 사용자 이벤트에 반응하는 핵심 클래스입니다. 본격적으로 **UIViewController**의 구조와 역할을 이해하고, 이를 활용한 앱 화면의 구성 방법을 살펴보겠습니다.

### 3️⃣ UIViewController 이해하기

# ==뷰 컨트롤러란?!==

> View Controller는 iOS 앱의 한 화면을 담당하는 클래스입니다. UIViewController 클래스를 기반으로 하며 하나의 뷰 컨트롤러는 하나의 뷰를 관리합니다.  
> 앱에서 뷰 컨트롤러는 사용자의 상호작용을 처리하고, 데이터를 보여주고, 다른 화면으로의 전환을 관리하는 중요한 역할을 합니다.  

> **뷰 컨트롤러는 MVC패턴에서 Controller에 해당하는 역할을 하며, 사용자가 화면에서 행하는 모든 동작과 입력을 받아들여 적절한 로직을 처리하고 화면에 데이터를 반영합니다.**

  

# ==뷰 컨트롤러의 역할?!==

## 1. UI 요소와 데이터 연결

뷰 컨트롤러는 ==**UI요소(뷰)와 데이터(모델)을 연결**==하는 중재자 역학을 합니다.

뷰 컨트롤러는 사용자 인터페이스(UI)에 표시되는 데이터를 준비하고 사용자의 상호작용에 따라 데이터를 변경하거나 처리한 후 그 결과를 화면에 다시 반영합니다.

> [!important] Example) 뷰 컨트롤러는 `UITableView` 에 데이터 소스를 제공하고, 그 데이터를 화면에 출력하는 방식으로 작동한다. 사용자가 스크롤하거나 셀을 클릭하면, 그에 따른 적절한 동작을 수행하도록 뷰 컨트롤러가 반응한다.

  

## 2. 화면 전환 관리

뷰 컨트롤러는 화면 간 전환을 관리합니다. 한 화면에서 다른 화면으로 이동할 때, iOS에서는 보통 **내비게이션 컨트롤러**나 **탭 바 컨트롤러** 등을 사용해 전환을 처리합니다. 이러한 전환을 뷰 컨트롤러가 담당하며, 화면 간의 데이터 전달도 뷰 컨트롤러가 처리합니다.

> [!important] Example) 사용자가 로그인 화면에서 로그인 버튼을 눌렀을 때. 뷰 컨트롤러는 다음 화면으로 전환하는 작업을 처리하고, 로그인 정보가 필요하면 그 데이터를 새로운 화면에 전달한다.

  

## 3. 라이프사이클 관리

뷰 컨트롤러는 화면의 **라이프사이클**을 관리합니다. iOS의 뷰 컨트롤러는 특정 시점에 따라 뷰를 로드하고 화면에 나타나거나 사라질 때마다 특정 메서드가 호출됩니다.

![[rendered2x-1683733157.png]]

  

![[생명주기_2.jpg]]

  

==**뷰 컨트롤러의 라이프사이클 메서드**==

1. **viewDidLoad()**
    1. 뷰가 메모리에 로드된 후 호출됩니다. 초기 UI 구성이나 데이터 로드를 위한 작업을 수행합니다.
2. **viewWillAppear()**
    1. 뷰가 화면에 나타나기 직전에 호출됩니다. 화면이 나타나기 전에 데이터 업데이트 또는 준비 작업을 수행할 수 있습니다.
3. **viewDidAppear()**
    1. 뷰가 화면에 완전히 나타난 후 호출됩니다.
4. **viewWillDisappear()**
    1. 뷰가 화면에서 사라지기 직전에 호출됩니다. 화면이 사라지기 전에 데이터 저장 등의 작업을 처리할 수 있습니다.
5. **viewDidDisappear()**
    1. 뷰가 화면에서 완전히 사라진 후 호출됩니다.

  

> [!important] ==**라이프사이클을 이해하고 관리하는 것은 iOS 앱 개발에서 아주 중요합니다.**==

  

라이프사이클을 관리하지 않으면 앱의 성능 저하, 메모리 낭비, 비정상적인 동작이 발생할 수 있습니다.

그렇기 때문에 `효율적인 메모리 관리` , `뷰가 나타나고 사라지는 시점에 적절한 로직 처리` , `사용자 상호작용 및 이벤트 처리` , `화면 전환의 상태 관리` , `비동기 작업과의 연동` , `앱 상태와의 연동` 를 위해서 라이프 사이클을 이해하고 있어야 하며, 적절히 관리할 줄 알아야 합니다.

  

# 컨텐츠(Content) 뷰 컨트롤러와 컨테이너(Container) 뷰 컨트롤러

> iOS 의 뷰 컨트롤러는 크게 **컨텐츠 뷰 컨트롤러**와 **컨테이너 뷰 컨트롤러**로 나눌 수 있습니다. 이 두 가지 유형의 뷰 컨트롤러는 화면 구조를 관리하는 방식에서 차이가 있으며, 서로 다른 역할을 합니다.  
> ==**콘텐츠 뷰 컨트롤러는 개별적인 콘텐츠를 화면에 표시하는 역할을 합니다.**==  
> ==**컨테이너 뷰 컨트롤러는 여러 콘텐츠 뷰 컨트롤러를 포함하고 이들 간의 전환과 배치를 관리하는 역할을 합니다.**==

  

![[VCPG-container-acting-as-root-view-controller2x.png]]

  

## ==컨텐츠 뷰 컨트롤러==

> ==**컨텐츠 뷰 컨트롤러**==는 일반적으로 사용자가 상호작용하는 단일 화면의 내용을 관리하는 뷰 컨트롤러입니다.  
> 주된 역할은 UI 요소들을 배치하고, 해당 화면에서 일어나는 사용자 상호작용을 처리하는 것입니다.  
> 즉, ==**컨텐츠 뷰 컨트롤러는 화면을 구성하는 각 뷰를 담당하며, 화면에 보이는 데이터와 로직을 처리합니다.**==

  

- **단일 화면** : 하나의 화면에 UI 및 데이터 처리를 담당합니다.
- **데이터 표시 및 처리** : 사용자가 상호작용하는 컨텐츠를 화면에 표시하고, 데이터 입력 및 결과를 처리합니다.
- **단일 흐름** : 대부분의 컨텐츠 뷰 컨트롤러는 자체적으로 완결된 로직을 가지고 있으며, 특정 화면에 국한된 동작을 수행합니다.

  

컨텐츠 뷰 컨트롤러가 어디에 쓰이는지 간단한 예시로 확인 해보도록 하겠습니다.

  

- **로그인 화면**
    - 텍스트 필드와 버튼이 포함된 화면으로, 사용자로부터 입력을 받는 역할을 하는 로그인 뷰 컨트롤러가 컨텐츠 뷰 컨트롤러입니다.
- **상세 정보 화면**
    - 특정 아이템의 세부 정보를 표시하는 화면으로 제품 정보나 프로필 화면을 담당하는 뷰 컨트롤러입니다.

  

로그인 화며이나 상세 정보 화면처럼 단일한 목적을 가진 화면에서 컨텐츠 뷰 컨트롤러를 사용하여 다양한 사용자 경험을 제공할 수 있습니다.

  

컨텐츠 뷰 컨트롤러는 로그인 화면이나 상세 정보 화면 외에도 `설정 화면`, `검색 화면`, `폼 입력 화면` 등과 같이 각각의 화면에서 다양한 방식으로 적용될 수 있습니다. 각 화면의 목적과 상호작용을 콘텐츠 뷰 컨트롤러를 통해 관리하며, 다양한 사용자 경험을 제공하는 직관적이고 일관된 UI를 설계할 수 있습니다.

  

위 예시에 있는 **로그인 화면에서의 콘텐츠 뷰 컨트롤러 예시를 보도록 하겠습니다.**

> [!important] ==**MVC에 맞추어 모델, 뷰, 컨트롤러를 분리하고 컨트롤러만 작성했습니다.**==
> 
> ==**실제로 빌드해서 완벽한 화면을 보이기 위해 모델과 뷰 파일을 작성해야 합니다!**==

```Swift
import UIKit

class LoginViewController: UIViewController {
    
    override func viewDidLoad() {
        super.viewDidLoad()
        
        self.view = loginView
    }
    
    private lazy var loginView: LoginView = {
        let loginView = LoginView()
        
        loginView.loginBtn.addTarget(self, action: \#selector(loginButtonTapped), for: .touchUpInside)
        return loginView
    }()
    
    @objc private func loginButtonTapped() {
        let loginUser = LoginUser(id: "qwer", pwd: 1234)
        print("loginUserData : \(loginUser)")
    }
}
```

  

LoginViewController는 LoginView를 사용하여 UI를 관리하고, 사용자의 입력을 처리합니다.

이 컨트롤러는 모델(LoginUser)과 뷰(LoginView) 사이에서 데이터를 주고 받으며, 사용자의 상호작용에 따른 로직을 실행합니다.

  

## ==컨테이너 뷰 컨트롤러==

> ==**컨테이너 뷰 컨트롤러**==는 하나 이상의 ==**컨텐츠 뷰 컨트롤러**==를 포함하고 관리하는 뷰 컨트롤러입니다. 여러 화면을 관리하거나 화면 전환을 관리하는 데 사용되며, _**화면 간 전환**_ 또는 _**화면 배열**_을 담당합니다.  
> 기본적으로 컨테이너 뷰 컨트롤러는 하위에 있는 컨텐츠 뷰 컨트롤러 간의 관계를 관리하고, 여러 화면을 하나로 결합하는 역할을 합니다.  

> 대표적으로 컨테이너 뷰 컨트롤러는 iOS에서 기본적으로 제공하는 `UINavigationController` , `UITabBarController`, `UIPageViewController` 등입니다.

### 주요 역할

- **화면전환** : 한 화면에서 다른 화면으로 이동할 때, 필요한 로직과 전환 효과를 관리합니다.
- **다중 뷰 관리** : 여러 개의 컨텐츠 뷰 컨트롤러를 한 곳에서 관리하며, 다양한 방법으로 배열하거나 전환할 수 있습니다.
- **데이터 및 상태 전달** : 화면 간 전환 시 데이터를 전달하거나, 이전 화면의 상태를 기억하여 다시 돌아왔을 때 복원할 수 있습니다.

  

### ==UINavigationController==

**계층적인 화면 전환을 관리하는 컨테이너 뷰 컨트롤러**입니다. 일반적으로 “뒤로 가기” 버튼을 제공하여 사용자가 이전 화면으로 돌아갈 수 있도록 합니다.

**Stack** 구조로 동작하며, 새로운 화면을 **Push** 할 때마다 스택에 추가되고, 뒤로 갈 때는 **Pop** 되어 이전 화면으로 돌아갑니다.

![[navigation_interface_2x_8f059f7f-2e2f-4c86-8468-7402b7b3cfe0.png]]

  

  

```Swift
let firstVC = UIViewController()
let navigationController = UINavigationController(rootViewController: firstVC)

// 화면 전환
let secondVC = UIViewController()
navigationController.pushViewController(secondVC, animated: true)
```

  

`UINavigationController` 는 계층적 탐색에서 강력한 도구로 사용됩니다. 이를 적절히 활용하면 사용자 친화적이고 유연한 화면 전환을 구현할 수 있다.

  

### ==UITabBarController==

**하단에 탭바를 표시하여, 여러 화면 간 전환을 관리**하는 컨테이너 뷰 컨트롤러입니다.

`UITabBarController` 는 사용자가 빠르게 화면 간 전환을 할 수 있도록 지원합니다. 또한 각 탭마다 개별적인 ViewController를 연결하여 관리합니다. 이를 통해 사용자는 각 탭을 선택함으로써 해당 화면으로 전환할 수 있게 됩니다.

사용 예시로, 앱의 메인 화면에서 홈, 프로필, 설정 등의 화면을 각각 다른 탭으로 제공할 때 자주 사용됩니다.

![[a4c30adf-176b-4020-ae69-f228edb9e621.png]]

  

```Swift
let firstVC = UIViewController()
firstVC.tabBarItem = UITabBarItem(tabBarSystemItem: .favorites, tag: 0)

let secondVC = UIViewController()
secondVC.tabBarItem = UITabBarItem(tabBarSystemItem: .contacts, tag: 1)

let tabBarController = UITabBarController()
tabBarController.viewControllers = [firstVC, secondVC]
```

  

`UITabBarController` 는 이러한 화면들을 논리적으로 분리하고 전환을 관리하는 역할을 합니다. 앱의 여러 주요 섹션을 탭 바를 통해 제공하면 사용자 경험이 더욱 직관적이고 간소화됩니다.

### ==UIPageViewController==

페이지 단위로 화면을 넘길 수 있는 컨테이너 뷰 컨트롤러로, **사용자가 좌우로 스와이프하여 화면 간에 자연스럽게 전환**할 수 있습니다. 각 페이지는 컨텐츠 뷰 컨트롤러로 구성되며, 사용자 인터페이스는 책을 넘기듯이 페이지를 전환하는 형태로 구현됩니다.

사용 예시로, 사진 앨범에서 이미지를 넘기거나, 전자책 앱에서 페이지를 넘기는 방식, 앱 첫 화면에서 제공하는 튜토리얼 등에서 자주 사용됩니다.

  

```Swift
let pageViewController = UIPageViewController(transitionStyle: .scroll, navigationOrientation: .horizontal)
```

  

  

컨테이너 뷰 컨트롤러들을 살펴보았습니다.

하나의 iOS 앱에서는 여러 개의 컨테이너 뷰 컨트롤러가 동시에 사용될 수 있습니다.

**UINavigationController**와 **UITabBarController**를 함께 사용하여 탭 바에서 다른 화면으로 전환할 때 내비게이션 흐름을 처리할 수 있습니다

```Swift
let firstVC = UIViewController()
let navController = UINavigationController(rootViewController: firstVC)

let secondVC = UIViewController()

let tabBarController = UITabBarController()
tabBarController.viewControllers = [navController, secondVC]
```

  

### 그럼 우리는 왜 컨테이너 뷰 컨트롤러를 사용해야 할까요?!

컨테이너 뷰 컨트롤러를 사용하면 앱의 화면 전환과 구성을 더 유연하고 효율적으로 관리할 수 있습니다. 여러 개의 뷰 컨트롤러 간 전환을 쉽고 직관적으로 처리할 수 있을 뿐만 아니라, 각 화면 간의 데이터 전달이나 상태 복원도 더욱 체계적으로 할 수 있습니다. 이를 통해 복잡한 UI를 단순하게 구현할 수 있으며, 사용자 경험을 향상시키는 데 기여합니다. `UINavigationController`, `UITabBarController` , `UIPageViewController` 와 같은 컨테이너 뷰 컨트롤러는 앱의 다양한 화면 구조를 효과적으로 구성하는 데 필수적인 도구입니다.

  

### 마지막으로..!

또한 각 화면에서 사용하는 다양한 UI 요소들, 즉 UIComponents는 뷰 컨트롤러와 긴밀하게 연결되어 있습니다. 버튼, 레이블, 텍스트 필드와 같은 컴포넌트들은 사용자와의 상호작용을 처리하고, 뷰 컨트롤러는 이러한 상호작용을 효과적으로 관리합니다. 그렇다면 이제 뷰 컨트롤러에서 사용하는 UIComponents가 무엇인지, 그리고 어떻게 커스터마이징하고 활용할 수 있는지 자세히 살펴보겠습니다.

### 4️⃣ UIComponents 이해하기

  

> [!important] 아래 컴포넌트들에 대해 ==**코드로 작성하면서 커스터마이징 하는 방법은 실습을 통해 배우게 될 것입니다.**== 그러니 이 단계에서 개념을 꼼꼼히 읽고 숙지 하시기 바랍니다. 또한, ==**애플 디벨로퍼 문서 링크도 첨부해드렸는데 아주 자세한 설명을 담고 있습니다.**== 이 내용을 꼭 읽어 주셨으면 합니다.

  

**UIComponents**는 iOS 앱에서 사용자 인터페이스의 핵심 요소로, 사용자와의 상호작용을 가능하게 하는 다양한 컨트롤들을 말합니다. 이 컴포넌트들은 사용자의 입력을 받아 처리하고, 앱의 데이터를 표시하는 중요한 역할을 합니다. UIkit 프레임워크 내에는 버튼, 레이블, 텍스트 필드, 슬라이더, 스위치 등 다양한 UI 요소가 포함되어 있으며, 각각의 컨포넌트는 특정한 기능과 사용 목적을 가집니다.

  

앞으로 워크북을 수행하면서 많은 Components들을 알게 되고, 커스터마이징을 하게 될 것입니다.

  

1주차 워크북에서 주로 많이 쓰이는 UIComponent들을 소개 하도록 하겠습니다.

### 주요 UIComponents

==**UIButton**==

- 사용자가 탭할 수 있는 버튼으로, 다양한 액션을 트리거하는 데 사용됩니다.
- 커스터마이징이 가능하여, 배경색, 텍스트, 아이콘 등을 설정할 수 있습니다.

![[Screenshot_2024-09-07_at_8.51.41_PM.png]]

> [!info] UIButton | Apple Developer Documentation  
> A control that executes your custom code in response to user interactions.  
> [https://developer.apple.com/documentation/uikit/uibutton/](https://developer.apple.com/documentation/uikit/uibutton/)  

  

==**UILabel**==

- 텍스트를 표시하는 데 사용되는 컴포넌트로, 사용자에게 정보를 제공합니다.
- 폰트, 색상, 정렬 방식 등을 설정하여 시각적으로 다양하게 표현할 수 있습니다.

![[Screenshot_2024-09-07_at_8.52.33_PM.png]]

> [!info] UILabel | Apple Developer Documentation  
> A view that displays one or more lines of informational text.  
> [https://developer.apple.com/documentation/uikit/uilabel/](https://developer.apple.com/documentation/uikit/uilabel/)  

  

==**UITextField**==

- 사용자로부터 텍스트 입력을 받는 필드로, 로그인 화면의 아이디나 패스워드 입력창 등에 사용됩니다.
- 키보드 유형, 보안 설정, 텍스트 검증 등을 커스터마이징할 수 있습니다.

![[Screenshot_2024-09-07_at_8.54.30_PM.png]]

> [!info] UITextField | Apple Developer Documentation  
> An object that displays an editable text area in your interface.  
> [https://developer.apple.com/documentation/uikit/uitextfield/](https://developer.apple.com/documentation/uikit/uitextfield/)  

  

==**UISlider**==

- 값의 범위를 조정할 때 사용되는 슬라이더로, 볼륨 조절이나 이미지 필터 적용 등에 활용됩니다.
- 최소값, 최댁값, 현재 값 등을 설정할 수 있으며, 시각적으로도 다양한 스타일을 적용할 수 있습니다.

![[Screenshot_2024-09-07_at_8.55.00_PM.png]]

> [!info] UISlider | Apple Developer Documentation  
> A control for selecting a single value from a continuous range of values.  
> [https://developer.apple.com/documentation/uikit/uislider/](https://developer.apple.com/documentation/uikit/uislider/)  

  

==**UISwitch**==

- 설정 화면에서 옵션을 켜고 끄는 스위치로 사용됩니다.
- On/Off 상태를 타나내며, 이벤트에 따라 다른 동작을 수행하도록 설정할 수 있습니다.

![[Screenshot_2024-09-07_at_9.25.58_PM.png]]

> [!info] UISwitch | Apple Developer Documentation  
> A control that offers a binary choice, such as on/off.  
> [https://developer.apple.com/documentation/uikit/uiswitch/](https://developer.apple.com/documentation/uikit/uiswitch/)  

  

==**UIImageView**==

- 이미지를 표시하는 뷰로, 앱 내에서 그래픽 컨텐츠를 보여줄 때 사용됩니다.
- 로컬 이미지나 네트워크에서 받은 이미지를 적재하여 표시할 수 있습니다.

> [!info] UIImageView | Apple Developer Documentation  
> A view that displays a single image or a sequence of animated images in your interface.  
> [https://developer.apple.com/documentation/uikit/uiimageview/](https://developer.apple.com/documentation/uikit/uiimageview/)  

  

==**UIPickerView**==

- 여러 선택지 중 하나를 선택할 수 있게 해주는 피커 뷰로, 날짜나 시간, 혹은 사용자 정의 데이터 선택에 사용됩니다.
- 각 컴포넌트는 데이터 소스를 통해 동적으로 데이터를 제공받을 수 있습니다.

![[Screenshot_2024-09-07_at_9.29.04_PM.png]]

> [!info] UIPickerView | Apple Developer Documentation  
> A view that uses a spinning-wheel or slot-machine metaphor to show one or more sets of values.  
> [https://developer.apple.com/documentation/uikit/uipickerview/](https://developer.apple.com/documentation/uikit/uipickerview/)  

  

### UIComponens의 중요성

==**UIComponents는 앱의 사용성을 직접적으로 좌우하는 요소입니다.**== 사용자는 이 컴포넌트들을 통해 앱과 상호작용하므로, 각 요소가 적절히 구성되어 있어야 효과적인 사용자 경험을 제공할 수 있습니다.

  

앞에 언급했듯이, ==**코드를 통해 UI를 생성하고 커스터마이징 기술**==을 배우게 될 것입니다. 이러한 **학습을 통해 여러분은 앱의 사용자 경험을 직접 설계하고, 실제 사용자의 요구에 맞춘 맞춤형 인터페이스를 제공**할 수 있게 됩니다.

  

하지만!! UI는 다양한 크기의 기기에서 일관된 레이아웃을 유지하는 것이 중요합니다.

각기 다른 화면 크기에서도 요소들이 균형 있게 배치되고 동작하도록 하기 위해서는 ==**Auto Layout**==이라는 개념을 활용해야 합니다. 이 개념에 대한 자세한 설명은 다음 주차에 이루어질 것입니다. 하지만 실습과 과제를 위해서 아주 짧게 설명하고자 해요!

  

## Auto Layout이란?

> Auto Layout이란 iOS에서 UI 요소들을 다양한 기기와 화면 크기에 맞게 유연하게 배치하기 위해 사용하는 강력한 도구입니다. 다양한 화면 크기와 방향(세로모드, 가로모드)에서도 UI 요소들이 일관되게 나타날 수 있도록 ==**Auto Layout은 제약을 사용하여 뷰들의 크기, 위치, 여백 등을 설정**==합니다.

> [!info] Auto Layout Guide: Anatomy of a Constraint  
> Describes the constraint-based system for laying out user interface elements.  
> [https://developer.apple.com/library/archive/documentation/UserExperience/Conceptual/AutolayoutPG/AnatomyofaConstraint.html](https://developer.apple.com/library/archive/documentation/UserExperience/Conceptual/AutolayoutPG/AnatomyofaConstraint.html)  

  

  

==**Auto Layout이 중요한 이유!!**==

1. 다양한 화면 크기에서 일관된 UI 유지
2. 동적 컨텐츠(텍스트 크기, 이미지 등등)에 따라 UI 요소 크기 자동 조정
3. 세로 및 가로 방향 전환에 따른 UI의 유연한 재배치

  

위의 설명에서 제약을 사용하여 뷰들의 크기, 위치, 여백을 설정한다 했습니다. 그럼 제약 조건을 설정하는 설정하는 기본적인 개념을 알아보도록 합시다.

  

![[attributes_2x.png]]

  

위 사진은 **Auto Layout**에서 사용하는 ==**기본 속성**==들을 보여주는 그림입니다.

이 속성들을 이해하면 Auto Layout이 어떻게 동작하는지 쉽게 알 수 있습니다.

### Top, Bottom, Left(Leading), Right(Trailing)

- ==**Top**==
    - 요소의 상단이 부모 뷰 또는 다른 요소와 어떻게 배치될지 설정합니다. 예를 들어, 어떤 요소가 화면의 상단에서 20pt 아래에 위치하도록 설정할 수 있습니다.
- ==**Bottom**==
    - 요소의 하단에 대해 같은 방식으로 제약을 설정합니다. 하단 여백을 설정하면 화면의 아래쪽에서부터 요소가 얼마나 떨어져 있는지 제어할 수 있습니다.
- ==**Left(Leading), Right(Trailing)**==
    - 요소의 왼쪽과 오른쪽을 다른 요소나 부모 뷰와의 관계에서 설정할 수 있습니다. 이를 통해 화면의 가로 방향에서 요소가 어디에 위치할지 결정합니다.
    - **Left**
        - 단순히 화면의 왼쪽을 의미합니다. 즉, 이 속성은 ==**항상 화면의 왼쪽을 기준으로 배치**==됩니다. 앱의 언어 설정이 무엇이든, 화면의 물리적인 왼쪽 위치와 관계를 맺습니다.
    - **Leading**
        - 텍스트의 읽기 방향을 기반으로 결정됩니다. 영어, 한글처럼 왼쪽에서 오른쪽으로 읽는 언어에서는 Leading이 화면의 왼쪽과 동일하지만, 아랍어나 히브리어처럼 오른쪽에서 왼쪽으로 읽는 언어에서는 Leading이 오른쪽을 가리킵니다. ==**즉, Leading은 언어의 텍스트 방향을 고려한 속성입니다.**==
    - **Right**
        - 단순히 화면의 오른쪽을 의미합니다. 이 속성은 항상 화면의 물리적인 오른쪽과의 관게를 정의합니다. 언어와 무관하게 물리적으로 오른쪽에 배치될 UI 요소에 사용됩니다.
    - **Trailing**
        - 텍스트의 읽기 방향을 기반으로 합니다. 즉, Trailing은 Leading과 마찬가지로 언어의 텍스트 방향에 맞춰 UI 요소를 배치하는 데 사용됩니다
- ==**Width & Height**==
    - Width(너비)와 Height(높이)는 요소의 크기를 결정하는 제약입니다. 너비와 높이는 고정할 수도 있고, 다른 요소와 비례하여 동적으로 설정할 수도 있습니다.
- ==**Center X & Center Y**==
    - Center X 와 Center Y는 요소를 수평 또는 수직 중앙에 배치할 때 사용됩니다. 예를 들어, 어떤 뷰가 부모 뷰의 중앙에 정확하게 위치하게 하고 싶을 때 Center X 와 Center Y를 함께 설정합니다.
- ==**Baseline**==
    - Baseline은 주로 텍스트와 관련된 속성입니다. 두 개의 레이블이 있을 때, 텍스트의 기준선이 서로 일치하도록 설정하여 레이블이 시각적으로 깔끔하게 정렬됩니다.

  

### Auto Layout으로 UI 구성하기

Auto Layout의 핵심은 각 속성을 적절히 조합하여 UI 요소들이 화면에서 어디에 배치되고, 크기가 어떻게 결정 되는지를 제어하는 것입니다. 실제 예시를 통해 익혀 보도록 하겠습니다.

  

- **간단한 버튼 배치**

아래 코드는 화면 중앙에 버튼을 배치하고, 버튼의 너비를 화면의 절반으로 설정하는 간단한 예시입니다.

```Swift
class AutoLayoutUI: UIViewController {

    override func viewDidLoad() {
        super.viewDidLoad()
        self.view.backgroundColor = .white
        setBtn()
    }
    

    private lazy var button: UIButton = {
        let btn = UIButton()
        btn.setTitle("버튼입니다.", for: .normal)
        btn.setTitleColor(.black, for: .normal)
        btn.translatesAutoresizingMaskIntoConstraints = false
        return btn
    }()
    
    private func setBtn() {
        self.view.addSubview(button)
        
        NSLayoutConstraint.activate([
            button.centerXAnchor.constraint(equalTo: view.centerXAnchor),
            button.centerYAnchor.constraint(equalTo: view.centerYAnchor),
            
            button.widthAnchor.constraint(equalTo: view.widthAnchor, multiplier: 0.5),
            button.heightAnchor.constraint(equalToConstant: 50)
        ])
    }
}
```

  

- **결과 화면**

**iPhone 15 Pro 화면**

![[스크린샷_2024-09-10_오후_3.26.17.png]]

  

**iPhone 11 화면**

![[스크린샷_2024-09-10_오후_4.58.00.png]]

  

그럼 위 코드를 분석 해볼까요?!

  

1. `translatesAutoresizingMaskIntoConstraints` 속성을 `false`로 설정하여 **자동 제약을 사용하지 않도록** 합니다. UIkit은 기본적으로 뷰가 프레임 기반 레이아웃을 사용하여 배치되도록 합니다. 하지만 Auto Layout을 사용할 때는 이 속성을 `false` 로 설정해야 수동으로 제약을 추가할 수 있습니다.

```Swift
btn.translatesAutoresizingMaskIntoConstraints = false
```

  

1. button을 현재 뷰에 서브뷰로 추가합니다. Auto Layout은 뷰 계층 구조에서 상위 뷰와의 관계를 기반으로 작동하기 때문에, 버튼을 반드시 상위 뷰에 추가해야 제약을 적용할 수 있습니다.

```Swift
view.addSubview(button)
```

  

1. `NSLayoutConstraint.activate()` 메소드는 배열 형태로 전달된 여러 제약 조건을 한 번에 활성화하는 메서드입니다. 이제 각 제약 조건을 살펴보겠습니다. 위에 업로드한 그림()을 참고하며 봐주시기 바랍니다.

```Swift
NSLayoutConstraint.activate([
            button.centerXAnchor.constraint(equalTo: view.centerXAnchor),
            button.centerYAnchor.constraint(equalTo: view.centerYAnchor),
            
            button.widthAnchor.constraint(equalTo: view.widthAnchor, multiplier: 0.5),
            button.heightAnchor.constraint(equalToConstant: 50)
        ])
```

  

- `button.centerXAnchor.constraint(equalTo: view.centerXAnchor)`
    - 이 제약은 버튼의 X축 중앙이 `view` 의 X축 중앙에 위치하도록 설정합니다. 즉, 버튼이 수평적으로 화면의 중앙에 위치합니다.
- `button.centerYAnchor.constraint(equalTo: view.centerYAnchor)`
    - 이 제약은 버튼의 Y축 중앙이 `view` 의 Y축 중앙에 위치하도록 설정합니다. 즉, 버튼이 수직적으로 화면의 중앙에 배치됩니다.
- `button.widthAnchor.constraint(equalTo: view.widthAnchor, multiplier: 0.5)`
    - 이 제약은 버튼의 너비가 `view` 의 너비가 50%가 되도록 설정합니다. 즉, 버튼은 화면 너비의 절반을 차지하게 됩니다. 화면 크기가 변해도 버튼의 너비는 항상 화면 크기의 50%로 유지합니다.
- `button.heightAnchor.constraint(equalToConstant: 50)`
    - 이 제약은 버튼의 높이를 고정된 값의 `50pt`로 설정합니다. 높이는 화면 크기나 다른 요소에 상관없이 항상 50pt로 고정됩니다.

  

> Auto Layout을 통해 다양한 기기와 화면 크기에 적응하는 UI를 만드는 방법을 알게 되었습니다. 중요한 것은 제약 조건을 사용해 각 UI 요소가 화면에 어떻게 배치도고, 크기가 결정되는지를 정확하게 규정하는 것입니다.

### 🔥 1주차 개념을 끝으로!!

iOS 앱 개발의 기본적인 뼈대를 이해하는데 첫 걸음을 내딛었습니다.

**MVC패턴**, **UIViewController**, **UIComponents**, 그리고 **Xcode UI 커스터마이징**에 대한 지식은 앱 개발 여정에서 근본적인 역할을 하게 될 것입니다.

중간중간 작성되어 있던 코드에 대한 실습과 더 세부적인 내용은 앞으로 워크북을 하나하나 학습을 통해 배우게 될 것입니다.

## 🔥 1주차 개념 점검

---

위 개념에 대해 열심히 읽고 이해를 했다면 이제 **아래의 문제를 꼬옥!! 풀어서 다음 스터디까지 작성해보세요!**

> [!important] iOS 앱에서 MVC 패턴을 사용하는 이유는 무엇일까요?!

- **여기에 답을 적어주세요!**
    
    코드의 모듈화를 촉진하고, 유지 보수를 용이하게 하며, 재사용성을 높이는 데 목적
    

> [!important] UIViewController의 라이프사이클 중 viewDidLoad(), viewWillAppear(), viewDidAppear() 각 메서드가 호출되는 시점과 그 기능을 설명하세요!

- **여기에 답을 적어주세요!**
    
    viewDidLoad() - 초기 UI구성과 데이터 로드 작업 수행
    
    viewWillAppear() - 뷰가 화면에 나타나기 직전에 호출
    
    viewDidAppear() - 뷰가 화면에 완전히 나타난 후 호출
    

> [!important] 코드를 사용하여 UIVIewController의 배경색을 변경하는 방법을 코드로 작성하세요.<br>==**(위 개념 설명에서 코드가 언급되어 있었습니다. 만약 코드를 이해하지 않고 그냥 넘겼다면 다시 올라가서 확인하고 오세요!)**==

- **여기에 답을 적어주세요!**
    
    `self.view.backgroundColor = .white`
    

> [!important] UIButton과 UILabel의 기본 속성 세 가지를 각각 나열하고, 각 속성이 어떤 기능을 하는지 설명하세요!

- **여기에 답을 적어주세요!**
    
    > UIBotton
    
    - `[func setTitle(String?, for: UIControl.State)](https://developer.apple.com/documentation/uikit/uibutton/1624018-settitle)` : 특정 버튼 상태에 표시될 버튼의 제목 지정
    - `[func setBackgroundImage(UIImage?, for: UIControl.State)](https://developer.apple.com/documentation/uikit/uibutton/1624016-setbackgroundimage)` : 특정 버튼 상태에 사용될 배경 이미지 지정
    - `[func setTitleColor(UIColor?, for: UIControl.State)](https://developer.apple.com/documentation/uikit/uibutton/1623993-settitlecolor)` : 버튼 상태에 따른 버튼 제목 색깔 지정
    
    > UILabel
    
    - `[var text: String?](https://developer.apple.com/documentation/uikit/uilabel/1620538-text)` : 뷰가 표시할 문자열
    - `[var font: UIFont!](https://developer.apple.com/documentation/uikit/uilabel/1620532-font)` : 문자열의 폰트
    - `[var textAlignment: NSTextAlignment](https://developer.apple.com/documentation/uikit/uilabel/1620541-textalignment)` : 문자열 정렬을 위한 속성

> [!important] iOS 13부터 SceneDelegate가 도입되면서, 앱의 생명주기 관리가 변경되었습니다. <br>SceneDelegate와 AppDelegate의 차이점을 설명하세요!<br>

- **여기에 답을 적어주세요!**
    
    아이패드의 Split View 등장이후 UI의 상태만을 관리해주는 SceneDelegate 등장
    
    AppDelegate 에서는 더이상 UI의 생명주기를 관리하지 않음, 앱의 전반적인 생명주기를 관리 (앱의 시작과 종료, 백그라운드 포그라운드 전환 등)
    
      
    
      
    

## 📚 1주차 실습

---

> 이제 실습을 진행해보도록 하겠습니다.
> 
> 실습 내용은 위에 배운 내용을 사용하여 **카운트 업, 다운 하는 앱**을 만들도록 하겠습니다.  
> 순서대로 진행하도록 하겠습니다. 순서를 지키면서 따라와 주시기 바랍니다.  

> 아래 피그마 링크에 들어 오셔서 디자인을 확인하시기 바랍니다.  
> ==**Option 키를 누르고, 프레임 위에 마우스를 올려 확인 하시면서 오토레이아웃 수치를 꼭!! 확인해주시기 바랍니다.**==

[https://www.figma.com/embed?embed_host=notion&url=https%3A%2F%2Fwww.figma.com%2Fdesign%2F47IuhJxc7LFTwOYWtDgTdi%2FiOS-%EC%9B%8C%ED%81%AC%EB%B6%81-KREAM-%ED%81%B4%EB%A1%A0%EC%BD%94%EB%94%A9%3Fnode-id%3D0-1%26t%3DewlSGg1sYHxXPfor-1](https://www.figma.com/embed?embed_host=notion&url=https%3A%2F%2Fwww.figma.com%2Fdesign%2F47IuhJxc7LFTwOYWtDgTdi%2FiOS-%EC%9B%8C%ED%81%AC%EB%B6%81-KREAM-%ED%81%B4%EB%A1%A0%EC%BD%94%EB%94%A9%3Fnode-id%3D0-1%26t%3DewlSGg1sYHxXPfor-1)

### 1. SceneDelegate 설정

위에 설명한 ==**프로젝트 사전 준비 내용(**==**Xcode에서 UI 커스터마이징 부분**==**)**==을 진행해주시기 바랍니다.

![[스크린샷_2024-09-13_오전_9.00.53.png]]

  

### 2. 분석

위 피그마 링크에 가서 디자인 된 것을 보면, UI를 구성하고 있는 것은 `숫자` , `증가 버튼` , `감소 버튼` 이렇게 있습니다.

증가, 감소를 통해 숫자가 바뀌는 거라는 것을 저희는 알고 있습니다.

Model에는 ==**카운트를 담당하는 변수**==와 ==**증가, 감소를 진행하는 함수**==를 가지고 있으면 되겠죠?!

View에는 카운트를 보여주는 ==**Text 라벨**==과 ==**위, 아래 클릭하는 버튼**==

ViewController에는 위 뷰를 연결시키면 끝!!

  

그럼 하나씩 진행해보도록 하겠습니다.

  

### 3. 파일 및 폴더 생성

뷰 컨트롤러를 담는 폴더 `ViewControllers` 와 모델을 담는 폴더 `Models`, 뷰를 담는 폴더 `Views` 를 생성해줍니다.

`ViewControllers` 폴더 내부에 ViewController.swift 파일을 넣어주시고,

`Models` 폴더 내부에 CountUpDownModel.swift 파일을 생성합니다.

`Views` 폴더 내부에는 CountUpDownView.swift 파일을 생성합니다.

- **CountUpDownModel.swift 파일을 생성**

파일을 생성하실 때, 아래 이미지 처럼 Swift File을 생성해주시면 되겠습니다.

![[스크린샷_2024-09-13_오전_9.48.24.png]]

  

- **CountUpDownView.swift**

뷰를 생성하실 때, 아래 이미지 처럼 Cocoa Touch Class 를 클릭하여 생성하시면 됩니다.

![[스크린샷_2024-09-13_오전_10.07.13.png]]

![[스크린샷_2024-09-13_오전_10.10.23.png]]

아래 사진 처럼 파일 및 폴더 구조가 완성되면 됩니다.

![[스크린샷_2024-09-13_오전_10.10.14.png]]

### 4. Model 작성하기

위에 언급했듯이, Model에는 ==**카운트를 담당하는 변수, 변수를 1 증가 시키는 함수, 변수를 1 감소시키는 함수**====를 작성하면 됩니다.==

  

- **카운트를 담당하는 변수 작성**
    
    - 구조체를 생성 후, Int 타입의 Count를 생성합니다.
    
    ```Swift
    struct CountUpDownModel {
        var count: Int = 0
    }
    ```
    
      
    
- **카운트를 증가, 감소 시키는 함수 작성**
    
    - `mutating` 키워드를 사용하여 증가 감소 함수를 작성합니다.
    
    ```Swift
    struct CountUpDownModel {
        var count: Int = 0
        
        // count 변수를 1 증가시킵니다.
        mutating func increaseCount() {
            self.count += 1
        }
        
        mutating func decreaseCount() {
            self.count -= 1
        }
    }
    ```
    
    > [!important] `mutating` 키워드는 구조체나 열거형 내에서 인스턴스의 프로퍼티를 수정하거나 자기 자신을 변경할 수 있게 하는 기능을 제공합니다. 기본적으로 구조체와 열거형은 값 타입이므로, 해당 타입의 메서드 내에서 인스턴스를 수정하려면 특별한 조치가 필요합니다. 그 때 사용하는 것이 `mutating` 입니다.
    

  

### 5. View 작성

카운트는 단순히 텍스트가 보이는 거니, UILabel로 생성하면 됩니다.

그리고 업, 다운 버튼은 액션을 하는 버튼이니 UIButton을 생성하면 됩니다.

그리고 피그마의 AutoLayout 수치에 맞춰 값을 넣어 뷰의 크기와 위치를 맞추면 끝!

  

- **View 초기화**
    
    - `init(frame:)` 이니셜라이저를 통해 코드에서 뷰를 생성할 수 있으며, 스토리보드를 사용할 경우에는 지원되지 않도록 `init(coder:)` 메서드에 `fatalError`를 추가합니다.
    
    ```Swift
    import UIKit
    
    class CountUpDownView: UIView {
    
        override init(frame: CGRect) {
            super.init(frame: frame)
            self.backgroundColor = .white
        }
        
        required init?(coder: NSCoder) {
            fatalError("init(coder:) has not been implemented")
        }
    }
    ```
    
      
    
- **ViewController에 뷰 연결**
    
    - 뷰 컨트롤러 파일로 넘어가서, 지금부터 작업할 뷰를 연결해줍니다.
    - ==**아래 코드는 ViewController 코드입니다.**==
    
    ```Swift
    import UIKit
    
    class ViewController: UIViewController {
    		lazy var counterView = CountUpDownView()
    
        override func viewDidLoad() {
            super.viewDidLoad()
            self.view = counterView
        }
    }
    ```
    
      
    
    아래 사진처럼 하얀색으로 나타나면 성공입니다!
    
    ![[스크린샷_2024-09-13_오후_1.40.15.png]]
    
      
    
    > [!important] ==**위 사진처럼 나타난다면, 다시 View 파일로 넘어와서**<br>**아래의 작업을 순서대로 진행해주시기 바랍니다.**<br>==
    

  

- **카운트를 나타내는 UILabel 생성**
    
    - 피그마에서 카운트 텍스트의 크기와 굵기를 확인해주세요
    - 42 사이즈에, bold를 사용하고 있습니다.
    - 또한, 폰트 색을 검은색으로 두고 있기 때문에 검은색으로 지정합니다.
    
    ```Swift
    // 카운트 표시 라벨
        public lazy var countLabel: UILabel = {
            let label = UILabel()
            
            label.font = UIFont.systemFont(ofSize: 42, weight: .bold)
            label.textColor = UIColor.black
            label.textAlignment = .center
            
            label.translatesAutoresizingMaskIntoConstraints = false
            
            return label
        }()
    ```
    
    - **왜 클로저를 이용해서 초기화를 할까?**
        
        당연히 직접적으로 `countLabel`에 속성을 부여하는 방법도 가능합니다. 그러나 코드를 작성하는 많은 방식들 중에서 다음과 같은 이유로 클로저를 사용해 프로퍼티 초기화를 하는 것이 더욱 선호되는 경우가 있습니다:
        
        ### 1. **가독성 및 코드 구조화**
        
        클로저를 사용함으로써 초기화 코드를 블록으로 감싸서 하나의 단위로 만들 수 있어 코드 구조를 더욱 깔끔하고 명확하게 합니다. 클로저 안에서 초기화 작업을 전부 처리하면 프로퍼티 초기화가 한 눈에 들어오기 때문에 유지보수와 가독성이 향상됩니다.
        
        ### 2. **Lazy Initialization**
        
        `lazy` 키워드를 사용할 때는 클로저 기반 초기화가 필요합니다. 이는 프로퍼티가 처음 액세스될 때 초기화되도록 하는 성능 최적화 방법입니다. 이럴 경우 클로저를 사용해 프로퍼티 초기화를 하는 것이 적절합니다.
        
        ### 직접 속성 부여와 클로저 사용의 차이
        
        클로저를 사용하지 않고 직접 `countLabel`에 속성을 부여할 수도 있습니다. 다만, 이는 `lazy` 키워드를 사용하지 않거나 단순히 전역 초기화 구문이 필요한 경우에만 가능합니다:
        
        ### 클로저 없이 초기화
        
        ```Swift
        public var countLabel: UILabel = {
            let label = UILabel()
            label.font = UIFont.systemFont(ofSize: 42, weight: .bold)
            label.textColor = .black
            label.textAlignment = .center
            label.translatesAutoresizingMaskIntoConstraints = false
            return label
        }()
        ```
        
        ### 클로저 안의 초기화와 직접 초기화의 차이
        
        둘 다 가능합니다만, `lazy`를 사용해야 하는 경우에는 클로저 사용이 필수적입니다. 단순 초기화는 이렇게 할 수 있습니다:
        
        ### 직접 초기화:
        
        ```Swift
        public var countLabel: UILabel = UILabel()
        
        init() {
            countLabel.font = UIFont.systemFont(ofSize: 42, weight: .bold)
            countLabel.textColor = UIColor.black
            countLabel.textAlignment = .center
            countLabel.translatesAutoresizingMaskIntoConstraints = false
        }
        ```
        
        ### 결론
        
        클로저를 사용하는 것은 코드의 가독성을 높이고 프로퍼티를 효율적으로 초기화하는 좋은 방법입니다. 이런 방식은 특히 `lazy` 초기화와 함께 사용할 때 유용합니다. 그러나 상황에 따라서는 직접 초기화도 충분히 가능합니다. 어떤 방법을 선택할지는 주로 코드의 복잡도, 메모리 사용 패턴, 가독성 등의 여러 요소에 따라 달라집니다.
        
    
      
    
- **카운트를 업, 다운 하는 UIButton 생성**
    - UIButton의 Configuration 속성을 사용하여 위 화살표, 아래 화살표, 텍스트를 구현합니다.
    - 화살표 이미지 같은 경우, 피그마에서 추출해서 사용해도 되고 SF Symbol에서 아무거나 사용하셔도 됩니다.
    - 아래 사진은 SF Symbol 앱의 사진입니다. 다운 받으셔서 사용하시면 됩니다. 코드에서 사용할 때는 기호의 이름을 그대로 복사해서 사용하시면 되겠습니다.
    - ==**피그마에서 버튼 이미지와 텍스트 사이의 간격을 보면 5의 간격을 가지고 있습니다.**==
    - ==**버튼의 텍스트는 가운데 정렬이고, 버튼의 이미지는 위로 올라가 있습니다.**==
        
        ![[스크린샷_2024-09-13_오후_1.11.07.png]]
        
        ```Swift
         // 버튼 내부 텍스트 폰트 지정 컨테이너
            private lazy var titleContainer: AttributeContainer = {
                var container = AttributeContainer()
                container.font = UIFont.systemFont(ofSize: 16, weight: .bold)
                container.foregroundColor = UIColor.black
                return container
            }()
            
            // 숫자 업 버튼
            public lazy var countUpButton: UIButton = {
                let btn = UIButton()
                
                var configuration = UIButton.Configuration.plain()
                
                configuration.image = UIImage(systemName: "arrowtriangle.up.fill")?.withRenderingMode(.alwaysOriginal).withTintColor(.black)
                configuration.imagePlacement = .top
                configuration.imagePadding = 5 
                
                configuration.attributedTitle = AttributedString("숫자 올리기", attributes: titleContainer)
                configuration.titleAlignment = .center
                
                btn.configuration = configuration
                btn.translatesAutoresizingMaskIntoConstraints = false
                
                return btn
            }()
            
            // 숫자 다운 버튼
            public lazy var countDownButton: UIButton = {
                let btn = UIButton()
                
                var configuration = UIButton.Configuration.plain()
                
                configuration.image = UIImage(systemName: "arrowtriangle.down.fill")?.withRenderingMode(.alwaysOriginal).withTintColor(.black)
                configuration.imagePlacement = .top
                configuration.imagePadding = 5
                
                configuration.attributedTitle = AttributedString("숫자 내리기", attributes: titleContainer)
                configuration.titleAlignment = .center
                
                btn.configuration = configuration
                btn.translatesAutoresizingMaskIntoConstraints = false
                
                return btn
            }()
        ```
        
          
        
- **카운트 텍스트 AutoLayout 설정하기**
    
    - 피그마에서 Option 키를 사용하여 프레임 위에 마우스를 올리면 UI 요소들의 AutoLayout 수치를 확인할 수 있습니다.
    - ==**상단으로부터 362,**== ==**왼쪽 111**====,== ==**오른쪽 110**== 만큼 공간을 가지고 있습니다.
    - 이 수치에 맞춰 텍스트의 AutoLayout을 지정하도록 하겠습니다.
    
    ![[IMG_6511.heic]]
    
      
    
    - AutoLayout을 설정하기 전에 UI 컴포넌트를 뷰에 추가하는 코드부터 작성하도록 합니다.
    - 추가를 했으면 `NSLayoutConstraint` 를 통해 ==**AutoLayout**==을 지정합니다.
    - 뷰를 추가하고 AutoLayout을 지정하는 함수를 작성합니다.
    - 함수 작성이 끝나면 `override init()` 초기화 부분에 함수를 추가해주세요
    
    ```Swift
    override init(frame: CGRect) {
            super.init(frame: frame)
            self.backgroundColor = .white
            self.addComponents()
        }
    
     private func addComponents() {
            self.addSubview(countLabel)
            
            NSLayoutConstraint.activate([
                countLabel.topAnchor.constraint(equalTo: self.topAnchor, constant: 362),
                countLabel.leftAnchor.constraint(equalTo: self.leftAnchor, constant: 111),
                countLabel.rightAnchor.constraint(equalTo: self.rightAnchor, constant: -110)
            ])
        }
    ```
    
    - ViewController로 넘어와서 아래 코드처럼 작성하고 실행시켜보세요!
    
    ```Swift
    import UIKit
    
    class ViewController: UIViewController {
    
        override func viewDidLoad() {
            super.viewDidLoad()
            self.view = counterView
        }
        
        private lazy var counterView: CountUpDownView = {
            let view = CountUpDownView()
            view.countLabel.text = "1"
            return view
        }()
    }
    ```
    
    ![[스크린샷_2024-09-13_오후_1.51.02.png]]
    
      
    
- **카운트 버튼 AutoLayout 설정하기**
    
    - 왼쪽은 감소 버튼 오른쪽은 증가 버튼이 위치하도록 `AutoLayout`을 설정하도록 합니다.
    - ==**양쪽 버튼의 위는 카운트 라벨의 아래로부터 17의 간격을 두고 있습니다.**==
    - ==**왼쪽 버튼(숫자 내리기 버튼)은 뷰의 왼쪽으로부터 93의 간격을 가지고 있습니다.**==
    - ==**왼쪽 버튼(숫자 내리기 버튼)은 오른쪽 버튼(숫자 올리기 버튼)의 왼쪽으로부터 7의 간격을 가지고 있습니다.**==
    - 아래 코드는 위 조건에 맞춰 작성한 코드입니다.
    
    ```Swift
     override init(frame: CGRect) {
            super.init(frame: frame)
            self.backgroundColor = .white
            self.addComponents()
        }
        
        required init?(coder: NSCoder) {
            fatalError("init(coder:) has not been implemented")
        }
    
    private func addComponents() {
            self.addSubview(countLabel)
            self.addSubview(countDownButton)
            self.addSubview(countUpButton)
            
            
            NSLayoutConstraint.activate([
                countLabel.topAnchor.constraint(equalTo: self.topAnchor, constant: 362),
                countLabel.leftAnchor.constraint(equalTo: self.leftAnchor, constant: 111),
                countLabel.rightAnchor.constraint(equalTo: self.rightAnchor, constant: -111),
                
                countDownButton.topAnchor.constraint(equalTo: countLabel.bottomAnchor, constant: 17),
                countDownButton.leftAnchor.constraint(equalTo: self.leftAnchor, constant: 93),
                
                countUpButton.topAnchor.constraint(equalTo: countLabel.bottomAnchor, constant: 17),
                countUpButton.leftAnchor.constraint(equalTo: countDownButton.rightAnchor, constant: 7)
                
            ])
        }
    ```
    
    ![[스크린샷_2024-09-13_오후_2.29.18.png]]
    

### 6. ViewController 버튼 액션 추가 및 모델 연결

이제 뷰가 원하는 모습을 가지고 나타납니다.

그럼 이제 저희가 해야할 일은 ==**버튼의 액션 추가, Count 모델 연결**== ==이 두가지를 하면 끝이 납니다!==

  

- **Count 모델 연결**
    
    - 아주 간단합니다. 카운트 초기 값은 1로 시작하니, 모델 데이터를 뷰 모델에 인스턴스하고 뷰의 텍스트에 텍스트로 지정하면 됩니다.
    - 뷰 컨트롤러로 넘어와주시기 바랍니다. 그럼 이제 아래 코드 처럼 모델을 뷰 컨트롤러에 넣어주면 됩니다.
    
    ```Swift
    import UIKit
    
    class ViewController: UIViewController {
        
        var data: CountUpDownModel = CountUpDownModel(count: 1)
    
        override func viewDidLoad() {
            super.viewDidLoad()
            self.view = counterView
        }
        
        private lazy var counterView: CountUpDownView = {
            let view = CountUpDownView()
            view.countLabel.text = String(data.count)
            return view
        }()
    }
    ```
    
    - 아래 실행 결과처럼 잘 나타나는 것을 알 수 있습니다.
    
    ![[스크린샷_2024-09-13_오후_2.51.45.png]]
    
- **Count 증가 감소 액션 추가**
    
    - 증가 버튼을 누르면 증가하도록
    - 감소 버튼을 누르면 감소하도록
    - 우리는 Model 파일을 만들 때 증가, 감소 함수를 작성했었습니다.
    - 이 함수를 버튼에 연결하여 버튼이 이 함수를 실행시키고, 버튼이 함수를 실행해서 count의 데이터가 바뀌면 ViewController가 뷰를 업데이트하여 바뀐 값을 보이도록 만들도록 하겠습니다.
    - ==**위 설명은 MVC 패턴이 적용되어 이 카운트 업, 다운 앱의 모델, 뷰, 뷰 컨트롤러가 작동하는 모습입니다.**==
    - 아래 코드 처럼 버튼에 직접 넣을 액션을 만들고, 바뀐 값을 뷰에 적용하도록 함수를 만들어 버튼의 액션에 넣어줍니다.
    
    ```Swift
     @objc func increaseCount() {
            self.data.increaseCount()
            self.updateCount()
        }
        
        @objc func decreaaseCount() {
            self.data.decreaseCount()
            self.updateCount()
        }
        
        private func updateCount() {
            self.counterView.countLabel.text = String(data.count)
        }
    ```
    
    - 그 후 위 버튼의 액션 함수 `@objc func increaseCount()` , `@objc func decreaaseCount()` 를 뷰의 버튼에 액션으로 넣어줍니다.
    - 아래 코드처럼 작성하면 됩니다.
    
    ```Swift
     private lazy var counterView: CountUpDownView = {
            let view = CountUpDownView()
            view.countLabel.text = String(data.count)
            view.countDownButton.addTarget(self, action: \#selector(decreaaseCount), for: .touchUpInside)
            view.countUpButton.addTarget(self, action: \#selector(increaseCount), for: .touchUpInside)
            return view
        }()
    ```
    
    - **메서드 선택자 \#selector 는 왜 사용한걸까?**
        
        메서드 선택자(`selector`)를 사용하는 주된 이유는 특정 이벤트가 발생했을 때 실행할 메서드를 지정하기 위해서입니다. Swift와 Objective-C에서 사용되는 이벤트 기반 프로그래밍 패턴에서는 UI 요소(버튼 등)의 **특정 이벤트(터치 등)에 대해 어떤 메서드를 호출할지를 명시적으로 지정**할 필요가 있습니다. 이를 위해 `#selector`를 사용하여 메서드 참조를 제공합니다.
        
        ### 메서드 선택자를 사용하는 이유
        
        1. **타입 안전성(Type Safety)**:
            - `#selector` 구문을 사용하면 컴파일 시점에 해당 메서드가 정확히 존재하는지 검증할 수 있습니다. 즉, 잘못된 메서드 이름을 지정하면 컴파일 오류가 발생합니다.
            - 예를 들어, `#selector(decreaseCount)`는 `decreaseCount` 메서드가 정확히 존재한다는 것을 보장합니다.
        2. **가독성**:
            - 메서드 선택자를 사용하면 어떤 이벤트에 어떤 메서드가 호출될지 명확하게 알 수 있습니다. 이는 코드의 가독성을 높여주며, 어떤 메서드가 호출될지 쉽게 추적할 수 있습니다.
        3. **동적인 메서드 바인딩**:
            - 선택자는 런타임에 메서드를 동적으로 호출할 수 있게 합니다. 이는 런타임에 메서드를 변경하거나 새로운 메서드를 바인딩할 수 있는 유연성을 제공합니다.
        4. **이벤트 처리와 콜백**:
            - UI 이벤트(버튼 누름 등)에 대해 특정 동작을 수행하려면, 해당 동작을 수행할 메서드와 이벤트를 명시적으로 연결해야 합니다. 이를 위해 선택자를 사용합니다.
        
        ### 메서드 선택자 없이 호출하는 방식
        
        만약 메서드 선택자 없이 직접 이벤트를 처리한다면, Swift에서 일반적인 이벤트 처리를 위한 방법은 없습니다. 메서드 선택자는 이벤트 처리 방식의 핵심 요소이며, 버튼 클릭 이벤트와 같은 UI 이벤트에서는 선택자를 사용하는 것이 일반적이고 표준적입니다. 선택자 없이 이벤트를 처리하려면 버튼의 상태를 반복적으로 폴링하거나, 다른 구조적인 방법으로 이벤트를 감지해야 하는데 이는 비효율적이고 비직관적입니다.
        
        따라서, 메서드 선택자를 사용하여 이벤트와 메서드를 명확하게 연결하고 이벤트 발생 시 어떤 메서드가 호출될지 정확히 지정하는 것이 매우 중요하며, 코드의 안정성과 유지 보수성을 높여줍니다.
        
    
      
    
    - 그럼 ViewController의 전체 코드는 아래와 같이 됩니다.
    
    ```Swift
    import UIKit
    
    class ViewController: UIViewController {
        
        var data: CountUpDownModel = CountUpDownModel(count: 1)
        
        override func viewDidLoad() {
            super.viewDidLoad()
            self.view = counterView
        }
        
        private lazy var counterView: CountUpDownView = {
            let view = CountUpDownView()
            view.countLabel.text = String(data.count)
            view.countDownButton.addTarget(self, action: \#selector(decreaseCount), for: .touchUpInside)
            view.countUpButton.addTarget(self, action: \#selector(increaseCount), for: .touchUpInside)
            return view
        }()
        
        @objc func increaseCount() {
            self.data.increaseCount()
            self.updateCount()
        }
        
        @objc func decreaseCount() {
            self.data.decreaseCount()
            self.updateCount()
        }
        
        private func updateCount() {
            self.counterView.countLabel.text = String(data.count)
        }
    }
    ```
    

### 7. 최종 결과 화면 및 최종 코드

- **결과 화면 사진**

![[스크린샷_2024-09-13_오후_3.16.32.png]]

  

- **결과 화면 영상**

![[Simulator_Screen_Recording_-_iPhone_15_-_2024-09-13_at_15.17.56.mp4]]

  

- **최종 결과 코드**
    
    - **Model**
    
    ```Swift
    import Foundation
    
    struct CountUpDownModel {
        var count: Int = 0
        
        mutating func increaseCount() {
            self.count += 1
        }
        
        mutating func decreaseCount() {
            self.count -= 1
        }
    }
    ```
    
      
    
    - **View**
    
    ```Swift
    import UIKit
    
    class CountUpDownView: UIView {
    
        override init(frame: CGRect) {
            super.init(frame: frame)
            self.backgroundColor = .white
            self.addComponents()
        }
        
        required init?(coder: NSCoder) {
            fatalError("init(coder:) has not been implemented")
        }
        
       
        
        // 카운트 표시 라벨
        public lazy var countLabel: UILabel = {
            let label = UILabel()
            
            label.font = UIFont.systemFont(ofSize: 42, weight: .bold)
            label.textColor = UIColor.black
            label.text = "1"
            label.textAlignment = .center
            
            label.translatesAutoresizingMaskIntoConstraints = false
            
            return label
        }()
        
        // 버튼 내부 텍스트 폰트 지정 컨테이너
        private lazy var titleContainer: AttributeContainer = {
            var container = AttributeContainer()
            container.font = UIFont.systemFont(ofSize: 16, weight: .bold)
            container.foregroundColor = UIColor.black
            return container
        }()
        
        // 숫자 업 버튼
        public lazy var countUpButton: UIButton = {
            let btn = UIButton()
            
            var configuration = UIButton.Configuration.plain()
            
            configuration.image = UIImage(systemName: "arrowtriangle.up.fill")?.withRenderingMode(.alwaysOriginal).withTintColor(.black)
            configuration.imagePlacement = .top
            configuration.imagePadding = 5
            
            configuration.attributedTitle = AttributedString("숫자 올리기", attributes: titleContainer)
            configuration.titleAlignment = .center
            
            btn.configuration = configuration
            btn.translatesAutoresizingMaskIntoConstraints = false
            
            return btn
        }()
        
        // 숫자 다운 버튼
        public lazy var countDownButton: UIButton = {
            let btn = UIButton()
            
            var configuration = UIButton.Configuration.plain()
            
            configuration.image = UIImage(systemName: "arrowtriangle.down.fill")?.withRenderingMode(.alwaysOriginal).withTintColor(.black)
            configuration.imagePlacement = .top
            configuration.imagePadding = 5
            
            configuration.attributedTitle = AttributedString("숫자 내리기", attributes: titleContainer)
            configuration.titleAlignment = .center
            
            btn.configuration = configuration
            btn.translatesAutoresizingMaskIntoConstraints = false
            
            return btn
        }()
        
        private func addComponents() {
            self.addSubview(countLabel)
            self.addSubview(countDownButton)
            self.addSubview(countUpButton)
            
            
            NSLayoutConstraint.activate([
                countLabel.topAnchor.constraint(equalTo: self.topAnchor, constant: 362),
                countLabel.leftAnchor.constraint(equalTo: self.leftAnchor, constant: 111),
                countLabel.rightAnchor.constraint(equalTo: self.rightAnchor, constant: -111),
                
                countDownButton.topAnchor.constraint(equalTo: countLabel.bottomAnchor, constant: 17),
                countDownButton.leftAnchor.constraint(equalTo: self.leftAnchor, constant: 93),
                
                countUpButton.topAnchor.constraint(equalTo: countLabel.bottomAnchor, constant: 17),
                countUpButton.leftAnchor.constraint(equalTo: countDownButton.rightAnchor, constant: 7)
                
            ])
        }
    }
    ```
    
      
    
    - **ViewController**
    
    ```Swift
    import UIKit
    
    class ViewController: UIViewController {
        
        var data: CountUpDownModel = CountUpDownModel(count: 1)
        
        override func viewDidLoad() {
            super.viewDidLoad()
            self.view = counterView
        }
        
        private lazy var counterView: CountUpDownView = {
            let view = CountUpDownView()
            view.countLabel.text = String(data.count)
            view.countDownButton.addTarget(self, action: \#selector(decreaaseCount), for: .touchUpInside)
            view.countUpButton.addTarget(self, action: \#selector(increaseCount), for: .touchUpInside)
            return view
        }()
        
        @objc func increaseCount() {
            self.data.increaseCount()
            self.updateCount()
        }
        
        @objc func decreaaseCount() {
            self.data.decreaseCount()
            self.updateCount()
        }
        
        private func updateCount() {
            self.counterView.countLabel.text = String(data.count)
        }
    }
    ```
    

## 💻 1주차 과제

---

> [!important] **화면 구현에 필요한 레이아웃과 리소스는 아래 피그마를 참고해주세요!**
> 
>   
>   
> 앞으로 1주차부터 10주차까지의 과제를 통해 여러분은 KREAM 앱을 완성하게 될 것입니다. 물론 실제 KREAM 앱과 똑같이 만들지는 않지만, 각 주차에 배운 개념들을 활용할 수 있도록 난이도에 맞춰 뷰를 직접 수정해보았습니다. 또한 피그마를 통해 제공된 디자인을 기반으로 작업할 예정이며, 1주차부터 10주차까지의 모든 과제가 연결되어 진행됩니다. 그렇기 때문에 10주차가 끝나면 여러분만의 KREAM 앱이 완성될 것입니다.  
>   
> 
> [https://www.figma.com/embed?embed_host=notion&url=https%3A%2F%2Fwww.figma.com%2Fdesign%2F47IuhJxc7LFTwOYWtDgTdi%2FiOS-%EC%9B%8C%ED%81%AC%EB%B6%81-KREAM-%ED%81%B4%EB%A1%A0%EC%BD%94%EB%94%A9%3Fnode-id%3D0-1%26t%3DewlSGg1sYHxXPfor-1](https://www.figma.com/embed?embed_host=notion&url=https%3A%2F%2Fwww.figma.com%2Fdesign%2F47IuhJxc7LFTwOYWtDgTdi%2FiOS-%EC%9B%8C%ED%81%AC%EB%B6%81-KREAM-%ED%81%B4%EB%A1%A0%EC%BD%94%EB%94%A9%3Fnode-id%3D0-1%26t%3DewlSGg1sYHxXPfor-1)

> [!important] 실습 단계와 마찬가지로 피그마의 1주차 페이지에 있는 과제 섹션의 디자인을 보시면서,
> 
> 아래 체크 사항에 맞춰 KREAM의 로그인 뷰를 완성해주시기 바랍니다.

### 1. 프로젝트 파일 생성

> [!important] **실습 체크리스트**
> 
> - [x] 10주차까지 KREAM 앱을 만들기 위한 ==**프로젝트 파일**==을 생성합니다.
> - [x] 프로젝트 파일 생성 시, Interface 부분을 StoryBoard로 지정해주세요

### 2. 스토리보드 파일 삭제 및 SceneDelegate 설정

> [!important] **실습 체크리스트**
> 
> - [x] 위 개념 혹은 실습에서 진행했듯이 ==**스토리보드 파일을 삭제**==해주세요
> - [x] 위 개념 혹은 실습에서 진행했듯이 프로젝트 파일의 ==**Info에서 StoryBoard 관련 내용을 삭제해주세요**==
> - [x] 위 개념 혹은 실습에서 진행했듯이 ==**SceneDelegate 내부에서 빌드가 되도록 코드를 넣어주세요**==

### 3. 폴더 및 파일 생성

> [!important] **실습 체크 리스트**
> 
> - [x] Models 폴더를 생성해주세요.
>     - [x] Models 폴더 내부에 LoginModel.swift 파일을 생성해주세요.
> - [x] Views 폴더를 생성해주세요.
>     - [x] LoginView.swift 파일을 생성해주세요.
>     - [x] Cocoa Touch Class로 생성해주세요.
> - [x] ViewControllers 폴더를 생성해주세요.
>     - [x] 기존 ViewController.swift 파일의 이름을 LoginViewController.swift로 수정해주세요
>     - [x] Class 이름도 마찬가지로 LoginViewController라고 수정해주세요
> - [x] SceneDelegate에서 rootViewController의 값을 LoginViewcontroller로 변경해주세요

### 4. 로그인 레이아웃 구현

> [!important] **실습 체크리스트**
> 
> - [x] Model 구현
>     - [x] ==**id, pwd 를 담당하는 변수를 관리하는 데이터 구조**==를 LoginModel.swift에 구현해주세요
> - [x] View 구현
>     - [x] ==**UIImageView**====(==상단 로고), ==**UILabel**==, ==**UITextField**==(아이디, 비밀번호 입력), ==**UIButton**==(로그인 버튼)을 사용하여 피그마의 로그인 화면을 구현해주세요.
>     - [x] 구현은 **LoginView**에 해주시기 바랍니다.
>     - [x] 모든 UI 요소에 ==**오토레이아웃을 적용**==해주시기 바랍니다.
> - [x] ViewController 구현
>     - [x] ==**LoginViewController에**== ==**LoginView를 연결**==해주세요.

### 5. 과제가 완성 되었다면 깃허브 링크와 시연 영상을 첨부해주세요!

> [!important] **시연 영상 체크리스트**
> 
> - [x] `AutoLayout`이 잘 적용되어 있음을 확인할 수 있나요?
>     - [x] `iPhone 15 Pro`, `iPhone 13 mini` 시뮬레이터에서 테스트한 내용이 모두 들어가게 영상을 업로드해주세요.
> 
>   
> ==**체크리스트 항목을 모두 만족하는 영상만 업로드**==해주시길 바랍니다.

> **깃허브 링크 임베드**

> [!info] 7th_UMC_iOS/쿠트_김의택 at main · TUK-UMC/7th_UMC_iOS  
> 7th UMC iOS.  
> [https://github.com/TUK-UMC/7th_UMC_iOS/tree/main/%EC%BF%A0%ED%8A%B8_%EA%B9%80%EC%9D%98%ED%83%9D](https://github.com/TUK-UMC/7th_UMC_iOS/tree/main/%EC%BF%A0%ED%8A%B8_%EA%B9%80%EC%9D%98%ED%83%9D)  

> **시연 영상 업로드** ==(영상 개수 제한 X)==

![[iphone15pro.mp4]]

![[iphone13mini.mp4]]

## 🤔 1주차 트러블 슈팅

---

## 📌 추가적으로 더 공부해 봤어요!

---

==추가적으로 과제를 하면서 스스로 공부해본 내용이 있다면 이곳에 자유 양식으로 정리해 보세요!==

## ❓ 이런 질문이 있어요!

---

1. 간편로그인 버튼 정렬 방법
    - 버튼을 위젯으로 만들고 touchevent 집어넣기

  

---

Copyright © 2024 Lee Youjin All rights reserved.

Copyright © 2024 Jeong Euichan All rights reserved.