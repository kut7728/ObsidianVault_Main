- [[#📋 학습 목표]]
- [[#🔥 2주차 개념 설명]]
    - [[#1️⃣ iOS의 화면 전환에 대해 알아볼까요?]]
    - [[#2️⃣ AutoLayout은 무엇이고 어떻게 구현할까요?]]
    - [[#3️⃣ SnapKit은 무엇이고 어떻게 사용할까요?]]
    - [[#4️⃣ TabBarController는 무엇이고 어떻게 사용할까요?]]
- [[#🔥 2주차 개념 점검]]
- [[#📚 2주차 실습]]
    - [[#1️⃣ TabBarController 구현하기]]
    - [[#2️⃣ SnapKit으로 AutoLayout 구현하기]]
    - [[#3️⃣ Modal 방식으로 화면 전환 구현하기]]
    - [[#4️⃣ Navigation 방식으로 화면 전환 구현하기]]
- [[#💻 2주차 과제]]
    - [[# 1️⃣ 로그인 화면에서 로그인 버튼을 눌렀을 때 메인 화면으로 전환되도록 연결해주세요!]]
    - [[#2️⃣ 마이페이지의 레이아웃을 구현해주세요!]]
    - [[#3️⃣ 프로필 수정 페이지의 레이아웃을 구현하고 화면을 연결해주세요!]]
    - [[#4️⃣ 과제가 완성되었다면 깃허브 링크와 시연 영상을 첨부해주세요!]]
- [[#🤔 2주차 트러블 슈팅]]
    - [[#@2024년 10월 3일 오후 11:03 실습 중 모달 구현]]
    - [[#@2024년 10월 4일 오전 9:28 과제 중 프로필 설정, 공유 버튼 오토레이아웃]]
- [[#📌 이번 주차에는 이런 내용을 학습했어요! ]]
- [[#❓ 이런 질문이 있어요!]]

- 스터디 사진
    
    ![[KakaoTalk_Photo_2024-10-23-10-57-25-2.png]]
    

## 📋 학습 목표

---

- iOS의 `화면 전환`에 대해 이해하고 `화면 전환`의 두 가지 방식을 구현할 수 있다.
- `AutoLayout`의 개념에 대해 이해하고, SnapKit을 이용해 구현할 수 있다.
- `TabBarController`에 대해 이해하고, 직접 구현해볼 수 있다.

## 🔥 2주차 개념 설명

---

### 1️⃣ iOS의 화면 전환에 대해 알아볼까요?

- **✋ 들어가기 전에 잠깐! 우리는 왜 화면 전환을 구현해야 할까요?**
    
    ![[/image 2.png|image 2.png]]
    
    왼쪽의 사진 속 내용을 한 번 읽어볼까요?
    
    **한정된 페이지 속 양이 너무 많고 방대해서** 읽기가 힘들죠? 약간은 답답한 느낌도 경험하실 수 있으실 겁니다.
    
    ![[/image 1 2.png|image 1 2.png]]
    
    이런 느낌!
    
    사진 속 내용은 우리가 ==**애플리케이션을 통해 제공하고 싶은 기능과 정보**==에 해당합니다.
    
    한정된 페이지는 우리가 ==**애플리케이션을 볼 수 있는 매개체인 아이폰**==을 생각해보면 되겠죠?
    
    iOS로 돌아가는 ==**아이폰의 스크린 크기는 제한**==되어 있기 때문에, ==**각 화면에 맞는 정보를 알맞게 제공**==해주기 위해서 화면을 분할하고 전환시켜 주는 것입니다.
    

> Apple에서 공식적으로 제공하는 디자인 가이드라인인 HIG(Human Interface Guidelines)에서는 ==**화면 전환은**== ==`**모달(Modal)**`====**과**== ==`**네비게이션(Navigation)**`== ==**방식으로 나뉜다**==고 설명하고 있어요.
> 
> 화면 전환에 대해 공부하기 위해서는 두 개념에 대해 먼저 공부해보는 과정이 필요하겠죠? 함께 알아봅시다.

![[/image 2 2.png|image 2 2.png]]

  

왼쪽 화면은 모달과 네비게이션 중 어떤 화면 전환 방식을 사용한 화면일까요?

정답은 `모달`입니다.

용어가 생소해서 간단하게 설명을 드리자면 ==**다른 뷰를 보여주지 않고 화면 위를 덮는 형태의 화면 전환**====을 모달==이라고 하는데요!

모**달 방식으로 화면 전환을 할 때는 보통 어떤 상황일까요? 공식 HIG 문서를 함께 살펴보겠습니다.**

> [!important] **모달 형식은 콘텐츠를 분리된 전용 모드로 표시하는 디자인 기술로서, 상위 보기와의 상호작용을 방지하고, 닫으려면 명시적인 동작이 필요합니다.**<br><br>**콘텐츠를 모달 형식으로 표시하면 다음과 같은 이점이 있습니다.**<br>
> 
> - **사람들이 중요한 정보를 받고, 필요하면 조치를 취할 수 있음**
> - **사람들이 최근 동작을 확인하고 수정할 수 있는 옵션을 제공함**
> - **사람들이 이전 진행 상태를 놓치지 않으면서 개별적이고 초점이 맞춰진 작업을 수행할 수 있도록 함**
> - **사람들에게 깊이 있는 경험을 선사하거나 복잡한 작업에 집중할 수 있도록 도움**
> 
> [🍎 Human Interface Guideline 공식 문서 (한국어)](https://developer.apple.com/kr/design/human-interface-guidelines/modality)

공식 문서를 읽어보았을 때 주로 ==**일시적으로 사용자가 집중해야 하는 상황에서 컨텐츠를 띄워줄 때 사용**==하는 것 같네요!

모달로 띄운 화면에는 ==**중요한 정보들이 표시되어야 하고**==, ==**특정 액션을 요구할 수도 있으며**==, ==**닫으려면 특정 행동들이 요구**==되어야 합니다.

==**모달을 새롭게 띄울 때는**== ==`**Present**`====**, 띄워진 모달을 화면에서 제거할 때는**== ==`**Dismiss**`==라는 표현을 사용합니다.

그렇다면 오른쪽 화면은 어떤 화면 전환 방식을 사용한 화면일까요?

아무래도 위에서 모달을 설명했으니 이번에는 `네비게이션` 방식을 사용한 화면이겠죠?

네비게이션은 ==**계층적 구조로 뷰를 쌓아올려 가장 위의 뷰만 보여주는 형태의 화면 전환**==입니다.

주로 정보의 연속성이 있는 화면(설정, 메시지 등)에서 많이 사용됩니다.

==**네비게이션 방식의 화면 전환은**== ==`**UINavigationController**`====**를 이용해 구현**==됩니다.

`UINavigationController` 는 1주차에서 한번 배우신 적이 있으실텐데요! 개념을 다시 한번 깊고 넘어가겠습니다.

> [!important] **A navigation controller is a container view controller that manages one or more child view controllers in a navigation interface. In this type of interface, only one child view controller is visible at a time. Selecting an item in the view controller pushes a new view controller onscreen using an animation, hiding the previous view controller. Tapping the back button in the navigation bar at the top of the interface removes the top view controller, thereby revealing the view controller underneath.**
> 
> navigation controller는 탐색 인터페이스에서 하나 이상의 자식 view controller를 관리하는 컨테이너 보기 컨트롤러입니다. 이 유형의 인터페이스에서는 한 번에 하나의 자식 view controller만 표시됩니다. view controller에서 항목을 선택하면 애니메이션을 사용하여 새 view controller가 화면에 표시되고 이전 view controller는 숨겨집니다. 인터페이스 상단의 navigation bar에서 뒤로 버튼을 탭하면 상단 navigation controller가 제거되고 하단 navigation controller가 표시됩니다.

![[image 3.png]]

![[image 4.png]]

`UINavigationController` 는 ==**여러 개의**== ==`**ViewController**`====**를 관리하는**== ==`**Container View Controller**`====**의 성격**==을 가지고 있습니다.

이러한 ==`**ViewController**`== ==**들은**== ==`**Navigation Stack**`====**에 배열 형태로 저장**==됩니다. 왼쪽 그림을 보면 조금 더 이해가 쉽죠!

==`**Navigation Stack**`== ==**내에 있는**== ==`**ViewController**`== ==**들은 push, pop 형태로 관리**==됩니다. ==**뷰를 보여줄 때는**== ==`**Push**`====**, 뷰를 스크린에서 내릴 때는**== ==`**Pop**`==이라는 표현을 사용하는 것이죠!

또한 앱을 사용하다 보면 ==**상단에 타이틀, 뒤로가기, 설정등 특정 영역에 UI 요소들이 배치된 경우**==를 볼 수 있는데 해당 영역을 우리는 `navigationBar` 라고 부릅니다.

==**뒤로 가기 버튼이나 타이틀, 이외에도 여러 버튼들을 추가**==해 `navigationBar` 를 커스텀할 수 있습니다!

`toolbar`는 화면 상단에 표시되는 `navigationBar` 와 반대로 ==**화면 하단에 바 형태로 표시**==됩니다.

`Safari` 앱을 생각해보시면 이해가 쉬울 것 같아요. 공유하기나 페이지 같은 여러 기능들을 모아볼 수 있습니다.

`delegate` 와 관련한 개념은 난이도가 있어 이후 다른 주차에서 자세히 설명할 예정이니 여기에서는 생략하도록 할게요!

> **✋ 제가 본 화면 전환은 분명 여러 종류가 있었는데, 화면 전환이 모달과 네비게이션 방식만 있다는 게 이해가 안가요!**
> 
> 라는 의문이 충분히 들 수 있어요! 화면 전환이 여러 종류로 보이는 이유는 모달이 화면에서 표시되는 방식이 정말 다양하기 때문입니다.
> 
> 모달을 `present`하는 방식인 `UIModalPresentationStyle`은 총 [11개로 구성](https://developer.apple.com/documentation/uikit/uimodalpresentationstyle)되어 있는데요! 잘 쓰이지 않는 것들도 있고 iOS 버전에 따라 똑같이 표시되는 경우도 있어 대표적인 예시만 같이 보도록 합시다.

- **🔥 화면 전환 시 표시되는 방식(**`**UIModalPresentationStyle**`**) 예시 보기**
    
    - `.fullScreen`
    
    > 전체 화면으로 화면을 표시하고 싶은 경우 `.fullScreen`을 사용합니다.
    
    ![[Simulator_Screen_Recording_-_iPhone_15_Pro_-_2024-09-13_at_04.31.57.mp4]]
    
      
    
    - `.automatic`
    
    > 시스템에 의해 선택되는 방식입니다.
    > 
    > 대부분 아래 설명할 `.pageSheet` 방식과 동일하게 표시됩니다.
    
    ![[Simulator_Screen_Recording_-_iPhone_15_Pro_-_2024-09-13_at_04.32.17.mp4]]
    
    - `.overFullScreen`
    
    > 전체 화면으로 화면을 표시하고 싶지만 이전 화면도 함께 표시하고 싶은 경우 사용합니다. 표시되는 뷰의 alpha 값을 조절하면 이전 화면을 보이게 처리할 수 있습니다.
    
    ![[Simulator_Screen_Recording_-_iPhone_15_Pro_-_2024-09-13_at_05.04.07.mp4]]
    
    - `.pageSheet`
    
    > 원래 `ViewController`를 사라지게 하지 않고 일부분만 덮습니다.
    > 
    > 따로 `UIModalPresentationStyle` 을 설정하지 않을 경우 이 방식으로 표시됩니다.
    > 
    > 밑으로 드래그하면 `ViewController` 를 닫을 수 있습니다.
    
    ![[Simulator_Screen_Recording_-_iPhone_15_Pro_-_2024-09-13_at_04.32.17.mp4]]
    

> 기본적인 예시들을 모두 확인하셨나요? 이제 조금 화면 전환에 대한 궁금증이 풀리셨다면 좋을 것 같습니다.

### 2️⃣ AutoLayout은 무엇이고 어떻게 구현할까요?

> [!important] **Auto Layout dynamically calculates the size and position of all the views in your view hierarchy, based on constraints placed on those views.**
> 
>   
>   
> ==Auto Layout은 뷰에 설정된 제약 조건에 따라 뷰 계층에 있는 모든 뷰의 크기와 위치를 동적으로 계산합니다.  
>   
>   
> ====[🍎](https://developer.apple.com/library/archive/documentation/UserExperience/Conceptual/AutolayoutPG/index.html)== [Understanding Auto Layout](https://developer.apple.com/library/archive/documentation/UserExperience/Conceptual/AutolayoutPG/index.html)

1주차에 가볍게 `AutoLayout` 과 제약 조건 설정 방법을 배우고 실습해보았는데요! 간단하게 복습하고 넘어가도록 하겠습니다.

제약 조건을 한마디로 설명하면 뷰와 컴포넌트 간의 관계를 설정하는 것이라고 할 수 있겠죠!

제약 조건은 크게 두 가지 속성으로 나누어 분류할 수 있습니다.

> **위치 속성**

- X좌표를 결정짓는 요소
    - `CenterX`, `Leading`, `Trailing`
- Y좌표를 결정짓는 요소
    - `CenterY`, `Top`, `Bottom`

> **크기 속성**

- 너비를 결정짓는 요소
    - `Width`
- 높이를 결정짓는 요소
    - `Height`

![[Untitled.png]]

![[Frame_1920.png]]

아까 화면 전환 예시 설명에서 봤던 화면을 다시 들고 왔어요! 예시를 통해 `AutoLayout` 을 이해해봅시다.

해당 버튼을 표시하기 위해 어떻게 제약 조건을 설정해야 할까요?

첫번째 방법은 ==`**크기 속성**`====**과**== ==`**위치 속성**`====**을 모두 이용**==하는 방법입니다.

버튼은 화면의 정중앙에 위치하고 있고, 세로 길이 55와 가로 길이 255라는 정보도 주어져 있어요.

그렇다면 우리는

1. `Width`를 255, `Height`를 55로 설정해 크기 속성을 설정해주고
2. `CenterX`와 `CenterY`를 화면과 동일하게 설정하면 되겠죠?

코드로 보면 다음과 같습니다.

```Swift
private lazy var button = UIButton()
button.setTitle("NextViewController 표시하기", for: .normal)
button.translatesAutoresizingMaskIntoConstraints = false
view.addSubview(button)

NSLayoutConstraint.activate([
    button.centerXAnchor.constraint(equalTo: view.centerXAnchor),
    button.centerYAnchor.constraint(equalTo: view.centerYAnchor),
    button.heightAnchor.constraint(equalToConstant: 55),
    button.widthAnchor.constraint(equalToConstant: 255)
])
```

두번째 방법은 크기 속성을 설정하지 않고 위치 속성만 이용해 버튼을 표시하는 방법입니다.

버튼은 `Top`에서 400만큼, `Bottom`에서 400만큼 떨어져 있어요. `Leading`, `Trailing`에서는 각각 60만큼 떨어져있다는 것을 확인할 수 있습니다.

그렇다면 우리는

1. 화면 기준 `Top`과 `Bottom`에서 400만큼 떨어지게 설정한 후
2. `Leading`과 `Trailing`은 60만큼 떨어지게 설정해주면 되겠네요!

코드로 보면 다음과 같습니다.

```Swift
private lazy var button = UIButton()
button.setTitle("NextViewController 표시하기", for: .normal)
button.translatesAutoresizingMaskIntoConstraints = false
view.addSubview(button)

NSLayoutConstraint.activate([
    button.topAnchor.constraint(equalTo: view.topAnchor, constant: 400),
    button.bottomAnchor.constraint(equalTo: view.bottomAnchor, constant: -400),
    button.leadingAnchor.constraint(equalTo: view.leadingAnchor, constant: 60),
    button.trailingAnchor.constraint(equalTo: view.trailingAnchor, constant: -60)
])
```

  

![[Frame_1920 1.png]]

### 3️⃣ SnapKit은 무엇이고 어떻게 사용할까요?

![[image 5.png]]

지금은 실습 개념으로 버튼 하나의 제약 조건만 설정하면 되지만 나중에 뷰가 훨씬 복잡해진다면 어떨까요?

`AutoLayout` 말만 들어도 머리가 아프고 코드도 너무 길고 … 개념까지 복잡한데 이걸 코드로 구현하려니 더 복잡해지는 안타까운 사태가 발생합니다.

그래서 이러한 문제를 해결하고 코드를 조금이라도 더 간결하게 만들기 위한 라이브러리가 등장했어요!

바로 편리한 `AutoLayout` 코드 구현을 위한 `SnapKit`입니다.

- **✋ 들어가기 전에 잠깐!** `**Swift Package Manager**`**에 대해서 아시나요?**
    
    `Swift Package Manager`(줄여서 `SPM`)는 종속성 관리를 위한 공식 도구입니다.
    
    종속성 관리라고 하니 어려워 보이지만 그냥 ==**라이브러리나 프레임워크들의 버전을 관리해주는 공식 패키지 관리 도구**==입니다.
    
    관리라는 말이 여러 번 등장했죠? ==**Swift 빌드 시스템과 통합되어 다운로드와 컴파일, 연결 등의 각종 프로세스를 자동화**== 시켜준다고 생각하시면 이해가 쉬울 것 같습니다.
    
    공식에서 제공하는 도구, 즉 퍼스트 파티(First Party) 툴이기 때문에 안정적이라는 장점이 있어요.
    
    대부분의 라이브러리를 지원하지만 아직 지원하지 않는 라이브러리도 있어 그런 부분은 공식 도구가 아닌 서드 파티(Third Party) 툴을 이용해야 합니다. (e.g. `CocoaPods`)
    
    저희는 `SnapKit` 을 사용하기 위해 이 SPM을 이용해 `SnapKit` 을 먼저 프로젝트에 추가하는 과정을 거쳐야 합니다. 이 부분은 실습에서 같이 진행해 볼게요!
    
    ![[image 6.png]]
    

> [!info] GitHub - SnapKit/SnapKit: A Swift Autolayout DSL for iOS & OS X  
> SnapKit is a DSL to make Auto Layout easy on both iOS and OS X.  
> [https://github.com/SnapKit/SnapKit](https://github.com/SnapKit/SnapKit)  

> 위 링크가 `SnapKit` 을 사용하기 위한 깃허브 링크입니다! 실습에서는 이 링크를 이용해 `SnapKit` 을 설치하고 사용하는 과정을 거치게 될거예요.
> 
> 원래 코드를 `SnapKit` 을 이용해 표기해보는 간단한 과정을 거쳐보고 실습으로 넘어가 직접 구현해보는 시간을 가지도록 하겠습니다.

```Swift
import UIKit

import SnapKit
```

`SnapKit` 을 사용하기 위해서는 프로젝트에 추가한 후 꼭 프로젝트 내에서 최소 한 번 이상 `SnapKit` 을 import해주는 과정을 거쳐야 합니다.

모든 파일에 `import SnapKit` 을 작성하실 필요는 없어요! 한 번만 작성하시면 됩니다.

```Swift
private lazy var button = UIButton()
button.setTitle("NextViewController 표시하기", for: .normal)
button.backgroundColor = .systemIndigo
button.translatesAutoresizingMaskIntoConstraints = false
view.addSubview(button)

NSLayoutConstraint.activate([
    button.topAnchor.constraint(equalTo: view.topAnchor, constant: 400),
    button.bottomAnchor.constraint(equalTo: view.bottomAnchor, constant: -400),
    button.leadingAnchor.constraint(equalTo: view.leadingAnchor, constant: 60),
    button.trailingAnchor.constraint(equalTo: view.trailingAnchor, constant: -60)
])
```

아까 사용했던 코드를 다시 한번 끌어와보겠습니다. 이 코드를 어떻게 `SnapKit` 을 이용한 코드로 바꿀 수 있을까요? 🤔

일단 결론부터 한번 보겠습니다.

```Swift
private lazy var button = UIButton()
button.setTitle("NextViewController 표시하기", for: .normal)
button.backgroundColor = .systemIndigo
view.addSubview(button)

button.snp.makeConstraints {
    $0.top.equalToSuperview().offset(400) // SuperView의 top을 기준으로 button의 top을 400만큼 아래로 이동한다
    $0.bottom.equalToSuperview().inset(400) // SuperView의 bottom을 기준으로 button의 bottom을 400만큼 위로 이동한다
    $0.leading.equalToSuperview().offset(60) // SuperView의 leading을 기준으로 button의 leading을 60만큼 오른쪽으로 이동한다
    $0.trailing.equalToSuperview().inset(60) // SuperView의 trailing를 기준으로 button의 trailing을 60만큼 왼쪽으로 이동한다
}
```

한눈에 봐도 코드가 훨씬 간결해진 게 보이시나요? 한줄씩 뜯어보며 바뀐 부분을 자세히 들여다보도록 하겠습니다.

- `**button.snp.makeConstraints { }**`
    
    > `snp`는 `SnapKit`의 약자로, `SnapKit` 라이브러리 내의 메소드들을 사용하기 위해 `snp` 를 먼저 쓰고 시작합니다.
    > 
    > `makeConstraints` 는 그대로 해석해보면 ==**제약조건을 만들다**== 라는 뜻이죠? 그대로 이해하시면 됩니다.
    > 
    > 보통 `(컴포넌트).snp.makeConstraints { }` 와 같이 컴포넌트와 뷰 사이의 제약 조건을 만들어준다! 라는 의미로 사용하는 코드입니다.
    > 
    > 저희는 `makeConstraints` 뒤 코드 블럭({}) 내에서 해당 컴포넌트의 제약조건을 정의해주게 될 것입니다.
    

- **✋ 잠깐! 코드 블럭 내의** `**$0**`**은 뭔가요?**
    
    클로저 내의 인자 값입니다. 클로저 관련 개념은 이후 문법 워크북에서 자세히 배우게 될 거예요!
    
    ```Swift
    button.snp.makeConstraints { make in
        make.top.equalToSuperview().offset(400)
        make.bottom.equalToSuperview().inset(400)
        make.leading.equalToSuperview().offset(60)
        make.trailing.equalToSuperview().inset(60)
    }
    ```
    
    이렇게 인자 값을 미리 명시한 후 사용도 가능합니다. 생략하는 경우에는 `$0`으로 쓴다는 것만 기억해주세요!
    

- `equalToSuperView()`
    
    > `equalToSuperView()` 에 대해 이해하기 위해서는 `SuperView` 에 대한 이해가 선행되어야 합니다.
    > 
    > `SuperView` 는 ==**현재 뷰의 상위 뷰를 의미**==하는 용어입니다.
    
    > 예시로 저희가 `button` 을 View에 추가하는 과정에서 `view.addSubview(button)` 이라는 코드를 사용했는데요.
    > 
    > 해당 코드에서는 ==`**button**`====**의**== ==`**SuperView**`====**가**== ==`**view**`====**,**== ==`**view**`====**의**== ==`**SubView**`====**는**== ==`**button**`==이 되는 것입니다.
    
    > `equalToSuperView()` 는 결국 말 그대로 상위 뷰(`SuperView`)와 동일하게 한다는 의미입니다. 예시를 들어볼까요?
    > 
    > `make.top.equalToSuperview().offset(400)`의 경우 `SuperView` 인 `view` 의 top, 즉 스크린 최상단을 기준으로 400만큼 떨어트린다는 뜻이겠죠!
    > 
    > 상위 뷰를 기준으로 제약 조건이 정해진다는 점을 기억하시면 좋을 것 같습니다.
    
- `equalTo()`
    
    > 그런데 제약조건을 설정하다 보면 **꼭 상위 뷰에만 제약 조건을 맞춘다는 보장은 없을 것**입니다.
    > 
    > `buttonA`와 `buttonB`가 있을 때 `buttonB`가 `buttonA`의 `trailing`을 기준으로 20만큼 오른쪽으로 떨어져있어야 한다면 어떨까요?
    > 
    > `equalToSuperView()` 만 고려하게 된다면 A가 `SuperView` 를 기준으로 떨어져 있는 거리와 A의 너비를 모두 고려해 제약 조건을 설정해야겠죠. 생각만 해도 벌써 머리가 아픕니다.
    > 
    > 그래서 ==**우리는 기준을 자유롭게 설정할 수 있는**== ==`**equalTo()**`== ==**를 이용**==합니다. 아래와 같이 사용해볼 수 있어요!
    > 
    > ```Swift
    > buttonB.snp.makeConstraints { 
    >     $0.top.equalToSuperview().offset(400)
    >     $0.bottom.equalToSuperview().inset(400)
    >     $0.leading.equalTo(ButtonA.snp.trailing).offset(20)
    >     $0.trailing.equalToSuperview().inset(60)
    > }
    > ```
    > 
    > 다른 부분은 모두 비슷하지만 `leading` 부분을 주목해볼까요? `ButtonA.snp.trailing` , 즉 `buttonA`의 `trailing`을 기준으로 20만큼 떨어져 있는 것으로 확인할 수 있습니다.
    > 
    > 기준이 되는 뷰(또는 컴포넌트)를 자유롭게 설정할 수 있다는 점을 기억해주세요!
    
- `offset()`, `inset()`
    
    > 결론부터 말씀드리면!
    > 
    > `**inset**`**은** `**SuperView**`**와의 간격을,** `**offset**`**은** `**element**`**와의 간격**을 맞출 때 사용하는 개념입니다.
    
    `offset`의 경우 좌표평면을 생각하시면 쉽습니다.
    
    - 좌측 상단을 (0, 0)으로 두었다고 가정할 때
        - 오른쪽으로 가면 +, 왼쪽으로 가면 -입니다.
        - 위로 가면 +, 아래로 가면 -입니다.
    
    `inset`의 경우가 기준이 달라지기에 복잡해보이지만 설명 자체는 더 간결합니다.
    
    - `SuperView` 를 기준으로 안쪽 방향은 +, 바깥쪽 방향은 -입니다.
    - 다만 기준 자체가 달라지기 때문에 처음에는 조금 헷갈릴 수 있습니다! 시간을 충분히 가지시고 많은 시도로 연습해보시면서 감을 익히시면 좋을 것 같습니다.
    
    ![[image 7.png]]
    
    ![[image 8.png]]
    
- `centerX`, `centerY`, `center`
    
    > `SnapKit`을 사용하기 전 코드 예시를 하나 보겠습니다.
    > 
    > ```Swift
    > NSLayoutConstraint.activate([button.centerXAnchor.constraint(equalTo: view.centerXAnchor),
    >                              button.centerYAnchor.constraint(equalTo: view.centerYAnchor)])
    > ```
    > 
    > `button`의 `centerXAnchor`, `centerYAnchor`를 각각 `view`의 `centerXAnchor`, `centerYAnchor`에 맞춘다는 뜻이네요!
    > 
    > 이제 이 코드를 `SnapKit` 을 이용해 바꾸어 보겠습니다.
    > 
    > ```Swift
    > button.snp.makeConstarints { 
    > 	$0.centerX.centerY.equalToSuperView()
    > 	/// 또는 
    > 	$0.center.equalToSuperView()
    > }
    > ```
    > 
    > 두가지 방식으로 나타낼 수 있습니다.
    > 
    > 하나는 `centerY`, `centerX`를 각각 `SuperView` 의 `centerY`, `centerX`에 맞추는 방법, 다른 하나는 `centerY`, `centerX`를 모두 포함하는 개념인 `center`를 `SuperView` 에 맞추는 방법입니다. 편하신 대로 사용하시면 됩니다!
    
- `width`, `height`
    
    > 위에서는 계속 위치와 관련된 속성들에 대해 설명드렸는데요! 크기와 관련된 속성도 설명드리려고 합니다.
    > 
    > ```Swift
    > NSLayoutConstraint.activate([button.topAnchor.constraint(equalTo: view.bottomAnchor, constant: 40),
    >                              button.leadingAnchor.constraint(equalTo: view.leadingAnchor, constant: 40),
    >                              button.widthAnchor.constraint(equalToConstant: 255),
    >                              button.heightAnchor.constraint(equalToConstant: 55)])
    > ```
    > 
    > 위 예시 코드가 이제 좀 익숙하시죠? `view`를 기준으로 `top`과 `leading`은 40씩, `width`는 255, `height`는 55로 설정된 제약 조건이네요!
    > 
    > 이 코드를 `SnapKit` 을 이용해 바꾸어 보면 다음과 같습니다.
    > 
    > ```Swift
    > button.snp.makeConstarints { 
    > 	$0.top.leading.equalToSuperView().offset(40)
    > 	$0.width.equalTo(255)
    > 	$0.height.equalTo(55)
    > }
    > ```
    > 
    > 여기에서는 `equalToSuperView()`가 아닌 `equalTo()`를 사용했네요!
    > 
    > 특정한 값에 맞춰야 할 때는 `equalTo()` 를 사용합니다.
    
    `SnapKit` 을 사용한 코드가 사용하지 않은 코드보다 훨씬 간결하게 느껴지죠?
    
    실습 때는 `SnapKit` 를 이용해 레이아웃을 구성해보도록 하겠습니다.
    

### 4️⃣ TabBarController는 무엇이고 어떻게 사용할까요?

> [!important] **A container view controller that manages a multiselection interface, where the selection determines which child view controller to display.**<br><br>==Multiselection 인터페이스를 관리하는 Container View Controller로, 선택에 따라 표시할 자식 View Controller가 결정됩니다.<br><br>==<br>**The tab bar interface displays tabs at the bottom of the window for selecting between the different modes and for displaying the views for that mode.**
> 
> ==탭바 인터페이스는 창 하단의 다양한 모드 중에서 선택하고 해당 모드의 보기를 표시하기 위한 탭을 표시합니다.  
>   
>   
> ====[🍎 UITabBarController](https://developer.apple.com/documentation/uikit/uitabbarcontroller)==

`TabBarController` 도 1주차에서 잠깐 접하셨을 겁니다. 이해를 위해 공식 문서를 발췌했으니 읽어보시면 좋을 것 같아요.

`ContainerViewController`라는 용어가 네비게이션 때도 나왔는데 `TabBarController` 에서도 나오네요!

`ContainerViewController` 를 쉽게 설명하자면 ==**ViewController를 감싸고 있는 틀**==이라고 이해하시면 쉽습니다.

오른쪽 사진에서 검정색 배경의 뷰는 `ViewController`, 화면 전체는 `ContainerViewController` 인 `TabBarController` 가 되는 것입니다.

탭바는 여러 개의 ViewController를 자유롭게 왔다갔다 할 수 있게 하는 버튼의 집합이라고 보면 되겠죠?

오른쪽의 탭바를 구성하기 위해서는 아래와 같이 코드를 작성하면 됩니다. 한 줄씩 같이 볼까요?

```Swift
let clockVC = ClockViewController()
clockVC.tabBarItem = UITabBarItem(title: "World Clock", image: UIImage(named: "globe"), tag: 0)

let alarmVC = AlarmViewController()
alarmVC.tabBarItem = UITabBarItem(title: "Alarm", image: UIImage(named: "clock"), tag: 1)
        
let stopwatchVC = StopwatchViewController()
stopwatchVC.tabBarItem = UITabBarItem(title: "Stopwatch", image: UIImage(named: "stopwatch"), tag: 2)
        
let timerVC = TimerViewController()
timerVC.tabBarItem = UITabBarItem(title: "Timer", image: UIImage(named: "timer"), tag: 3)

let tabBarController = UITabBarController()
tabBarController.viewControllers = [clockVC, alarmVC, stopwatchVC, timerVC]
```

- `let clockVC = ClockViewController()`
    
    > 탭바의 각 아이템이 눌릴 때마다 그에 맞게 표시될 `ViewController`를 정의하는 코드입니다.
    
- `clockVC.tabBarItem = UITabBarItem(title: "World Clock", image: UIImage(named: "globe"), tag: 0)`
    
    > 정의된 `ViewController` 를 탭바에 들어갈 아이템으로 만드는 부분입니다.
    > 
    > `UITabBarItem` 을 통해 할당하며, `title`에는 아이콘 밑에 표시될 이름, `image`에는 아이콘으로 들어갈 이미지, `tag` 는 임의로 작성하시면 됩니다. 보통 보여지는 순서에 따라 `tag` 를 부여합니다.
    
- `let tabBarController = UITabBarController()`
    
    > 아이템을 넣을 `tabBarController`를 정의하는 부분입니다.
    
- `tabBarController.viewControllers = [clockVC, alarmVC, stopwatchVC, timerVC]`
    
    > `ContainerViewController` 는 관리되는 `viewController`를 배열 형태로 관리합니다. (`NavigationController`도 그랬었죠!)
    > 
    > 따라서 `tabBarController.viewControllers`에는 관리하게 될 ViewController들을 순서대로 넣어주시면 됩니다.
    > 
    > 탭바에서 보여지는 순서가 배열의 순서와 같습니다.
    

어려워 보였지만 굉장히 간단했죠? 실습에서 `tabBarController` 를 한 번 더 구현해보도록 하겠습니다.

![[image 9.png]]

## 🔥 2주차 개념 점검

---

> [!important] **iOS에서 화면 전환을 하는 방법에는 무엇이 있을까요? 각각 뷰를 띄우는 방법과 사라지게 하는 방법을 뭐라고 부르는지도 적어주세요!**

- **여기에 답을 적어주세요!**
    
    > 모달
    
    - present - 뷰 띄우기
    - dismiss - 뷰 사라지게하기
    
    > 네비게이션
    
    - push - 뷰 띄우기
    - pop - 뷰 사라지게하기

> [!important] `**UIModalPresentationStyle**` **는 정확히 무엇이고, 어떤 요소가 있으며 각각 어떻게 표시되는지 자세히 설명해주세요!**

- **여기에 답을 적어주세요!**
    - 모달을 띄우는 방식을 의미하며 총 11가지의 방식이 존재함
        - .fullScreen : 전체화면으로 모달 띄우기
        - .automatic : 시스템에 의해 선택됨
        - .pageSheet : 원래 뷰컨트롤러를 유지하면서 위에 모달을 띄움
        - .overFullScreen : 기존 뷰컨트롤러를 유지하고 위에 모달을 띄우면서 투명도를 조절해서 띄움

> [!important] `**inset**`**과** `**offset**`**의 차이는 무엇일까요?**

- **여기에 답을 적어주세요!**
    
    > inset
    
    - 뷰와의 간격으로 위치를 나타내는 방법, 모든 값이 양수로 표현됨
    
    > offset
    
    - 좌상단을 기준으로 요소의 위치를 나타내는 방법
    - 오른쪽과 아래로 가는것은 양수, 왼쪽과 위로 가는것은 음수로 나타냄

> [!important] `**TabBarController**`**를 구현하기 위한 과정을 자세히 설명해주세요!**

- **여기에 답을 적어주세요!**
    1. 탭바의 각 아이템에 표시될 뷰 컨트롤러 정의
    2. 정의된 뷰 컨트롤러를 탭바에 들어갈 아이템으로 만들기
    3. 탭바 컨트롤러 정의
    4. 뷰 컨트롤러를 배열형태로 순서대로 넣어준다

## 📚 2주차 실습

---

> [!important] 2주차 실습은 토글을 나누어 두긴 했지만 ==**모든 실습이 한 프로젝트에서 이루어집니다.**==
> 
> **2주차 실습 전에 프로젝트 파일을 생성**해주시고, ==**1주차에서 배웠던 것을 참고해서 코드를 통한 UI 생성을 위한 프로젝트 세팅을 사전에 진행**==해주세요!
> 
> 이후 과정은 사진을 보시면서 천천히 따라와주시면 됩니다.

### 1️⃣ TabBarController 구현하기

### **1️⃣** `**rootViewController**`**가 될** `**BaseViewController**` **생성하기**

![[스크린샷_2024-09-13_오전_7.57.59.png]]

  

코드 베이스 UI 구현을 위한 프로젝트 세팅을 완료하셨다면 새로운 파일을 추가해주세요!

왼쪽 프로젝트 파일 인디케이터에서 `프로젝트 최상단 폴더`에 커서를 놓으신 후 오른쪽 마우스를 클릭해주세요.

`New File…` 이라는 선택지를 찾아 눌러주시면 됩니다.

선택하신 후 뜨는 창에서 `Cocoa Touch Class`를 선택해주세요.

이후 왼쪽 사진과 같이 설정하신 후 `Next`를 눌러 파일을 생성해주세요!

  

![[스크린샷_2024-09-13_오전_7.58.20.png]]

  

다음과 같이 파일이 보인다면 성공입니다!

  

![[스크린샷_2024-09-13_오전_8.06.02.png]]

  

이후 `SceneDelegate` 파일에서 `rootViewController`가 `BaseViewController`가 되도록 설정해주세요.

실행했을 때 빈 화면이 오류 없이 잘 뜬다면 성공입니다!

### **2️⃣** `**tabBarItem**` **생성하기**

> 이번 실습에서 생성할 `tabBarItem` 은 총 2개입니다.
> 
> 이후 화면 전환 실습을 위한 `ModalViewController`와 `NavigationViewController`를 각각 `tabBarItem` 으로 사용할 예정이예요!
> 
> `ModalViewController` 와 `NavigationViewController` 를 각각 생성해주세요.

![[스크린샷_2024-09-13_오전_8.13.35.png]]

  

  

`Subclass of`는 `UIViewController`로 설정하시면 됩니다!

꼭 `ModalViewController` 와 `NavigationViewController` 를 둘 다 만들어주세요.

  

![[스크린샷_2024-09-13_오전_8.15.26.png]]

  

  

이후 `BaseViewController` 파일에서 `viewDidLoad` 윗 부분에 두 `ViewController`를 정의할 객체를 선언해주세요.

객체를 모두 선언하셨다면 `viewDidLoad` 내에서 각 `ViewController` 의 `tabBarItem` 프로퍼티에 `UITabBarItem` 객체를 할당해주세요.

`UITabBarItem` 객체를 생성하실 때는 꼭 `title`, `image`, `tag`가 있는 자동 완성 선택지를 택하셔야 하는 건 아닙니다.

이미지의 경우 `UIImage` 객체를 이용해 선언하시면 됩니다. `systemName:` 을 이용하시면 애플이 제공하는 [SF Symbol](https://developer.apple.com/sf-symbols/) 내에 있는 아이콘의 이름만 복사+붙여넣기 하시면 자유롭게 적용하실 수 있습니다!

![[스크린샷_2024-09-13_오전_8.25.01.png]]

다양한 선택지를 시도해보시고 적용해보셔도 좋을 것 같습니다.

![[스크린샷_2024-09-13_오전_8.23.29.png]]

  

왼쪽 사진과 같이 두 `ViewContoller`의 `tabBarItem`을 모두 할당하셨다면 성공적으로 `tabBarItem` 을 생성하신겁니다!

  

### **3️⃣** `**BaseViewController**` **세팅 및 완성하기**

![[스크린샷_2024-09-13_오전_8.32.21.png]]

  

`BaseViewController`가 `UIViewController`를 상속받지 않고 `UITabBarController`를 상속받도록 세팅했었죠!

개념 설명 시에는 `tabBarItem`을 추가하기 위한 `UITabBarController` 를 새로 정의해야 했지만 `BaseViewController` 가 `UITabBarController` 를 상속받고 있기 때문에 새로 정의할 필요가 없습니다.

다시 말해 tabBarItem을 추가하기 위한 `UITabBarController` 가 바로 `BaseViewController` 자신인 셈입니다!

따라서 원래는 `baseViewController.viewControllers = [modalVC, navigationVC]`로 작성해야 하겠지만…

`BaseViewController` 내에 있으니 `self.viewControllers = [modalVC, navigationVC]`로 작성해주는 게 맞겠죠?

> [!important] `BaseViewController`: 내 `viewControllers` 를 `[modalVC, navigationVC]` 로 설정할게!

정도로 이해해주시면 되겠습니다.

추가적으로 `self` 키워드는 생략하셔도 코드는 잘 돌아갑니다.

  

![[simulator_screenshot_21910E81-542A-41F0-9DDF-033013FA1B51.png]]

이후 화면을 실행해보시면 다음과 같이 코드가 잘 작동되는 것을 확인할 수 있습니다.

첫번째 실습이 마무리되었습니다!

  

### 2️⃣ SnapKit으로 AutoLayout 구현하기

### 1️⃣ `Swift Package Manager` 이용해 `SnapKit` 라이브러리 추가하기

![[스크린샷_2024-09-13_오전_9.21.48.png]]

  

`SPM`을 이용해 라이브러리를 추가하는 방법은 간단합니다.

먼저 Xcode 왼쪽 인디케이터에서 파일 구조 최상단에 있는 프로젝트 제목을 클릭해주세요.

이후 `PROJECT` > `Package Dependencies`를 순서대로 클릭하면 왼쪽과 같은 화면이 나타납니다.

`Packages (0 items)` 아래에 있는 `+` 버튼을 클릭해주세요.

  

![[스크린샷_2024-09-13_오전_9.25.26.png]]

  

이후 나타나는 팝업 창에서 SnapKit 설치를 위해 검색창에 다음 주소를 복사하신 후 입력해주세요.

```Markdown
https://github.com/SnapKit/SnapKit
```

`snapkit` 이라는 라이브러리가 정상적으로 뜰 경우 오른쪽 하단의 `Add Package` 를 클릭해주세요.

  

![[스크린샷_2024-09-13_오전_9.25.32.png]]

  

두 패키지를 설치한다고 화면이 뜨게 됩니다.

`SnapKit`은 그대로 추가해주시면 됩니다.

`SnapKit-Dynamic`은 다른 라이브러리와 충돌하는 경우가 있어 대체로 `Add to Target` 상태를 `None`으로 바꾸는 것을 권장드립니다.

단, 이번 실습에서는 `SnapKit` 이외에 새로 추가되는 라이브러리가 없으니 그냥 추가하셔도 됩니다.

==다른 라이브러리가 추가될 경우 꼭== ==`SnapKit-Dynamic`== ==은 빼고 추가해주세요!==

  

![[스크린샷_2024-09-13_오전_9.31.50.png]]

  

다음과 같이 `Packages (1 item)` 밑에 SnapKit이 정상적으로 표시된다면 성공입니다!

이제 SnapKit으로 AutoLayout 코드를 작성하기 위한 모든 준비가 완료되었습니다.

  

### 2️⃣ `ModalVC`와 `NavigationVC` 의 `AutoLayout` 구현하기

![[스크린샷_2024-09-13_오전_9.34.20.png]]

  

`ModalVC`와 `NavigationVC`에서 화면 전환을 위해 라벨과 버튼을 각각 구현해보고, `SnapKit`을 이용한 `AutoLayout`을 구현해보겠습니다.

먼저 `ModalViewController` 파일을 열어주세요! 간단한 viewDidLoad() 함수와 주석들이 있을텐데, 주석은 모두 지우셔도 됩니다.

  

![[스크린샷_2024-09-13_오전_9.39.56.png]]

  

먼저 `UILabel`과 `UIButton` 변수를 하나씩 선언해주세요.

저는 실습이기도 해서 `label`, `button`으로 변수명을 부여했으나 원하시는 대로 변수명을 바꾸셔도 됩니다.

이후 viewDidLoad 내에서 `label`과 `button`의 속성을 설정합니다.

`label`의 경우 `text`에 들어갈 내용과 표시될 `textColor` 정도만 설정해주셔도 충분합니다! 내용과 색은 원하시는 대로 설정해주세요.

`UIButton`의 경우 제목을 부여할 때 `setTitle()` 이라는 함수를 사용해야 합니다.

프로퍼티에 직접 접근해 문자열을 할당하는 `UILabel`과 다르다는 점 기억해주세요.

`button`의 `backgroundColor`도 원하시는 색깔로 설정해주시면 됩니다.

`button.backgroundColor = .` 까지 작성하면 시스템 내에서 사용 가능한 색들이 나옵니다. 내려보시고 원하시는 색으로 설정해주세요!

  

![[스크린샷_2024-09-13_오전_9.45.51.png]]

  

이후 `view.addSubview()`를 통해 `label`과 `button`을 `view`에 추가해주세요.

`AutoLayout` 설정을 위해 `SnapKit` 라이브러리도 `import UIKit` 코드 아래에 `import SnapKit` 코드 입력하셔서 같이 추가해주세요!

  

![[스크린샷_2024-09-13_오전_9.48.55.png]]

  

아까 전에 배운 내용을 활용해 자유롭게 `label`과 `button`의 제약 조건을 설정해주시면 됩니다. `NavigationViewController`도 동일하게 진행해주세요!

왼쪽 사진을 보시면 제가 `label`과 `button`의 제약조건을 `top`과 `centerX`에만 설정해둔 걸 보실 수 있는데요. 이 코드의 실행 결과는 어떻게 될까요?

  

![[simulator_screenshot_741794EE-9555-4125-853D-CEAD55D2C9AC.png]]

놀랍게도 크기 조건을 설정해주지 않았음에도 불구하고 화면에 정상적으로 출력되는 모습을 보실 수 있습니다.

뭔가 이상하지 않으신가요? 분명 제약 조건을 모두 충족해야 한다고 했는데 …

조건을 모두 입력하지 않았음에도 정상적인 출력이 가능한 이유는 ==**두 컴포넌트가**== ==`**Intrinsic Content Size**`====**를 가지는 컴포넌트**==이기 때문입니다.

`Intrinsic Content Size` 는 본래 갖추어진 사이즈를 의미하는 말로, 각 `Text`의 길이, `numberOfLines`, `font`의 크기 등에 따라 이미 `width`나 `height`가 결정되어 있다는 뜻입니다. 크기 조건을 미리 설정해두었으니 화면에 정상적으로 출력되는 거죠!

그렇다고 `width`, `height` 를 수정할 수 없다는 말은 아닙니다. 원하시는 대로 지정도 가능합니다!

  

  

  

> 지금까지 배운 내용을 바탕으로 `ModalViewController`, `NavigationViewController`에 `UILabel`, `UIButton`을 하나씩 추가해보시고 `SnapKit`을 이용해 제약 조건을 설정하셨나요?
> 
> 화면에 정상적으로 출력되는지 여부를 확인하신 이후에 화면 전환 구현 미션으로 넘어가주세요!

### 3️⃣ Modal 방식으로 화면 전환 구현하기

![[스크린샷_2024-09-13_오전_10.04.03.png]]

  

`ModalViewController`의 버튼을 누르면 `Modal` 방식을 이용해 새로운 `ViewController`로 화면이 전환되도록 구현할 예정입니다.

버튼이 눌렸을 때 실행될 메서드를 먼저 작성해볼까요?

버튼이 눌렸을 때 실행되는 액션 메서드는 다른 메서드와 다르게 꼭 함수 앞에 `@objc` 라는 키워드를 붙여야 합니다.

```Swift
@objc
private func buttonDidTap() {
    
}
```

위와 같이 작성하면 되겠죠? 메서드명은 자유롭게 설정해주셔도 됩니다.

![[스크린샷_2024-09-13_오전_10.05.18.png]]

  

이제 액션 메서드 내의 코드를 작성해볼까요?

원래는 `ModalViewController`처럼 파일을 만들어 직접 커스텀해도 되지만, 저희는 실습 단계이기 때문에 그냥 빈 `UIViewContoller` 를 선언하는 형식으로 진행합니다.

```Swift
let viewController = UIViewController()
```

위와 같이 빈 `viewController`를 선언해주시고 `UIViewController` 객체를 할당해주세요.

이후 화면 전환 확인을 위해 `viewController` 의 view `backgorundColor`를 바꿔줍니다. 저는 brown으로 진행했지만 원하시는 색으로 하셔도 상관없습니다!

`modalPresentationStyle` 또한 원하시는 방법으로 진행하시면 됩니다.

모달을 이용해서 뷰를 띄우기 위해서는 `present()` 라는 메서드를 이용합니다. 파라미터로 띄울 `ViewController`의 이름과 애니메이션(전환 효과)를 적용할지 여부를 넣어주시면 됩니다.

이제 앱을 실행해볼까요?

![[Simulator_Screen_Recording_-_iPhone_15_Pro_-_2024-09-13_at_10.16.33.mp4]]

  

아래에서 위로 올라오는 모달 방식의 화면 전환 구현에 성공했습니다!

고생하셨습니다. 만약 실행이 올바르게 되지 않는다면 꼭 문제를 직접 찾아보시고 해결해보세요!

해결되지 않는 문제가 있다면 스터디 팀원이나 파트장에게 질문하시고, 해결되었다면 트러블 슈팅도 작성해주세요!

  

### 4️⃣ Navigation 방식으로 화면 전환 구현하기

> `Navigation` 방식도 `Modal` 방식과 같이 `NavigationViewController`에 `addTarget` 함수와 액션 메서드를 작성해주시면 됩니다.
> 
> 이후 수정될 부분이 있지만 일단 같은 방식으로 구현한 후 수정하는 방식으로 실습이 진행되니 참고해주세요!

![[스크린샷_2024-09-13_오전_10.27.01.png]]

`BaseViewController` 파일을 열어주세요!

현재 `NavigationViewController`의 경우 `ViewController`를 상속받고 있는데, 이 경우 `Navigation`를 직접적으로 사용할 수 없어 `Navigation` 방식을 이용한 화면 전환이 불가능합니다.

탭바 내에서 `Navigation` 방식을 이용해 화면을 전환하기 위해서는 `NavigationViewController` 가 `UIViewController` 가 아닌`UINavigationController` 객체여야 합니다.

따라서 `BaseViewController` 에서 `navigationVC` 를 선언한 부분에서 다음과 같이 코드를 변경해주시면 됩니다!

```Swift
private let navigationVC = UINavigationController(rootViewController: NavigationViewController())
```

`NavigationViewController`를 `rootView`로 하는 `navigationVC` 객체를 생성하면 `Navigation` 방식을 사용할 수 있습니다.

  

![[스크린샷_2024-09-13_오전_10.27.50.png]]

이후 `NavigationViewController`의 액션 메서드 부분에서 `modalPresentationStyle` 코드를 삭제해주세요.

모달 방식이 아니기 때문에 굳이 넣을 필요가 없는 코드입니다!

`Navigation` 방식은 `pushViewController()` 메서드를 이용해 화면을 전환합니다.

이 경우 `ViewController` 내에 있는 `navigationContoller`에 접근해야 하는데, 만약 `UINavigationController`에 속해있지 않을 경우 코드가 아예 동작하지 않으니 주의해주세요!

그러면 이제 앱이 잘 동작하는지 확인해볼까요?

![[Simulator_Screen_Recording_-_iPhone_15_Pro_-_2024-09-13_at_10.28.36.mp4]]

화면 전환이 잘 되고 네비게이션 바가 잘 뜨는 것까지 확인했습니다.

고생하셨습니다. 만약 실행이 올바르게 되지 않는다면 꼭 문제를 직접 찾아보시고 해결해보세요!

해결되지 않는 문제가 있다면 스터디 팀원이나 파트장에게 질문하시고, 해결되었다면 트러블 슈팅도 작성해주세요.

> 2주차 실습은 이것으로 모두 마무리되었습니다.
> 
> 과제도 성실히 수행해주시길 바랍니다. 다음 주에 만나요!

## 💻 2주차 과제

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
> [https://www.figma.com/embed?embed_host=notion&url=https%3A%2F%2Fwww.figma.com%2Fdesign%2F47IuhJxc7LFTwOYWtDgTdi%2FiOS-%EC%9B%8C%ED%81%AC%EB%B6%81-KREAM-%ED%81%B4%EB%A1%A0%EC%BD%94%EB%94%A9%3Fnode-id%3D0-1%26t%3DewlSGg1sYHxXPfor-1](https://www.figma.com/embed?embed_host=notion&url=https%3A%2F%2Fwww.figma.com%2Fdesign%2F47IuhJxc7LFTwOYWtDgTdi%2FiOS-%EC%9B%8C%ED%81%AC%EB%B6%81-KREAM-%ED%81%B4%EB%A1%A0%EC%BD%94%EB%94%A9%3Fnode-id%3D0-1%26t%3DewlSGg1sYHxXPfor-1)

### 1️⃣ 로그인 화면에서 로그인 버튼을 눌렀을 때 메인 화면으로 전환되도록 연결해주세요!

> [!important] **실습 체크리스트**
> 
> - [x] 제공된 피그마 링크로 접속해 제공된 메인 화면을 `**TabBarController**`**를 이용해 구성합니다.**
>     - [x] **전환할** ==**메인 화면의**== ==`**ViewController**`==**들을 각각 생성합니다. (따로 구현은 X)**
>     - [x] `TabBarController` 를 이용해 각각의 화면을 연결합니다.
>     - [x] 단, 레이아웃은 반드시 `SnapKit`을 이용해 구현합니다.
> - [x] **1주차 과제로 제작했던 로그인 화면에서** ==**로그인 버튼을 눌렀을 때 메인 화면으로 전환**==**되도록 화면을 연결합니다.**
>     - [x] 단, 화면 전환 방식은 반드시 ==**Modal 방식을 이용**==해 구현합니다.

### 2️⃣ 마이페이지의 레이아웃을 구현해주세요!

> [!important] **실습 체크리스트**
> 
> - [x] **제공된 피그마 링크로 접속해** ==**제공된 마이페이지의 레이아웃을 구현**==**합니다.**
>     - [x] 단, 레이아웃은 ==**반드시**== ==`**SnapKit**`====**을 이용**==해 구현합니다.
>     - [x] 피그마에 명시된 레이아웃에 맞게 ==**크기와 간격을 정확히 반영**==합니다.

### 3️⃣ 프로필 수정 페이지의 레이아웃을 구현하고 화면을 연결해주세요!

> [!important] **실습 체크리스트**
> 
> - [x] **제공된 피그마 링크로 접속해 제공된** ==**프로필 수정 페이지의 레이아웃을 구현**==**합니다.**
>     - [x] 단, 레이아웃은 ==**반드시**== ==`**SnapKit**`====**을 이용**==해 구현합니다.
>     - [x] 피그마에 명시된 레이아웃에 맞게 ==**크기와 간격을 정확히 반영**==합니다.
>     - [x] 프로필 이름 부분은 `UITextField`를 이용해 구현하고, 입력이 가능하도록 처리되어야 합니다.
> - [x] **마이페이지에서** ==**프로필 관리 버튼을 눌렀을 때 프로필 수정 화면으로 전환**==**되도록 화면을 연결합니다.**
>     - [x] 단, 화면 전환 방식은 반드시 ==**Navigation 방식을 이용**==해 구현합니다.
> - [x] 프로필 수정 화면에서 ==**뒤로가기 버튼을 눌렀을 때 마이페이지 화면으로 전환**==되도록 화면을 연결합니다.
>     - [x] 단, 화면 전환 방식은 반드시 ==**Navigation 방식을 이용**==해 구현합니다.

### 4️⃣ 과제가 완성되었다면 깃허브 링크와 시연 영상을 첨부해주세요!

> [!important] **시연 영상 체크리스트**
> 
> - [x] `AutoLayout`이 잘 적용되어 있음을 확인할 수 있나요?
>     - [x] `iPhone 15 Pro`, `iPhone 13 mini` 시뮬레이터에서 테스트한 내용이 모두 들어가게 영상을 업로드해주세요.
> - [x] 로그인 화면에서 메인 화면으로 전환되는 과정을 확인할 수 있나요?
> - [x] TabBarContoller를 이용해 메인 화면을 구성했는지, 컴포넌트를 눌렀을 때 컨트롤러가 바뀌는지 확인할 수 있나요?
> - [x] 마이페이지에서 프로필 수정 화면으로 전환되는 과정을 확인할 수 있나요?
> - [x] 프로필 수정 화면에서 마이페이지로 전환되는 과정을 확인할 수 있나요?
> 
>   
> 
> ==**체크리스트 항목을 모두 만족하는 영상만 업로드**==해주시길 바랍니다.

> **깃허브 링크 임베드**

> [!info] GitHub - TUK-UMC/7th_UMC_iOS at 쿠트_김의택  
> 7th UMC iOS.  
> [https://github.com/TUK-UMC/7th_UMC_iOS/tree/%EC%BF%A0%ED%8A%B8_%EA%B9%80%EC%9D%98%ED%83%9D](https://github.com/TUK-UMC/7th_UMC_iOS/tree/%EC%BF%A0%ED%8A%B8_%EA%B9%80%EC%9D%98%ED%83%9D)  

  

> **시연 영상 업로드** ==(영상 개수 제한 X)==

![[Simulator_Screen_Recording_-_iPhone_16_Pro_-_2024-10-05_at_17.04.59.mp4]]

![[Simulator_Screen_Recording_-_iPhone_13_mini_-_2024-10-05_at_17.06.05.mp4]]

## 🤔 2주차 트러블 슈팅

---

### 2024년 10월 3일 오후 11:03 실습 중 모달 구현

### 문제 상황

---

- 실습중에 버튼을 눌러도 모달 뷰가 뜨지 않는 문제

### 해결 과정

---

- 액션 함수는 만들었지만 버튼에 연결이 안되었을거라는 생각으로 이전 실습 내용을 찾아서 버튼과 액션을 연결시켜줌
- `button.addTarget(``**self**``, action:` `**#selector**``(buttonDidTap), for: .touchUpInside)`

### 참고 자료

---

### 2024년 10월 4일 오전 9:28 과제 중 프로필 설정, 공유 버튼 오토레이아웃

### 문제 상황

---

- 과제 중 My 화면에서 프로필 설정 버튼과 프로필 공유 버튼이 아이폰13 mini 환경에서 겹치는 문제

### 해결 과정

---

- 스냅킷이 아닌 UIButton 의 속성으로 크기를 정의한 탓이라고 생각
    - 스냅킷으로 버튼의 크기를 지정해 봤으나 똑같이 겹침
- 버튼의 크기를 지정해놓은게 문제라고 생각
    
    - 버튼의 크기를 절대적이 아닌 상대적으로 설정
    - 높이는 절대적으로 설정하고 너비는 각 버튼의 안쪽을 SuperView의 중앙 x에 맞춤
    - 피그마 상에서 나온대로 버튼 사이거리 14픽셀을 지키기 위해서 offset 7씩 줌
    
    ```Swift
    profileSettingBtn.snp.makeConstraints { make in
        make.top.equalToSuperview().offset(197)
        make.left.equalToSuperview().offset(32.5)
        make.right.equalTo(super.snp.centerX).offset(-7)
        make.height.equalTo(26)
        
    }
    
    profileShareBtn.snp.makeConstraints { make in
        make.top.equalToSuperview().offset(197)
        make.right.equalToSuperview().offset(-32.5)
        make.left.equalTo(super.snp.centerX).offset(7)
        make.height.equalTo(26)
    ```
    

### 참고 자료

---

## 📌 이번 주차에는 이런 내용을 학습했어요!

---

[[UIButton에 태그를 달아서 구별하기]]

## ❓ 이런 질문이 있어요!

---

워크북을 진행하면서 궁금했던 점 또는 해결하지 못한 부분을 미리 작성하고 스터디에서 함께 논의해 보세요!  
해결하지 못한 질문이나 궁금한 점이 있다면 언제든지 편하게 DM 주세요 🙋‍♀️  

  

---

Copyright © 2024 Lee Youjin All rights reserved.

Copyright © 2024 Jeong Euichan All rights reserved.