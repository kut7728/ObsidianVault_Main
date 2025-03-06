- [[#📋 학습 목표]]
- [[#✋ 잠깐! 스터디 인증샷 찍으셨나요?]]
- [[#🔥 5주차 개념 설명]]
    - [[#1. UIScrollView 이해하기]]
    - [[#2. UIScrollView의 기본 설정]]
    - [[#3. 스크롤뷰의 상하좌우 스크롤 구현]]
    - [[#4. StackView와 스크롤의 결합 사용]]
    - [[#5. 고급 UIScrollView 활용]]
- [[#🔥 5주차 개념 점검]]
- [[#📚 5주차 실습]]
    - [[#1. SceneDelegate 설정]]
    - [[#2. 분석]]
    - [[#3. 파일 및 폴더 생성]]
    - [[#4. Model 작성하기]]
    - [[#5. View 작성하기]]
    - [[#6. ViewController 작성하기]]
    - [[#7. 전체 코드 및 실행 결과 화면]]
- [[#💻 5주차 과제]]
    - [[#1. 기존의 홈탭 ScrollView 구현]]
    - [[#2. ScrollView 내부에 컴포넌트 추가]]
    - [[#3. 과제가 완성되었다면 깃허브 링크와 시연 영상을 첨부해주세요!]]
- [[#🤔 5주차 트러블 슈팅]]
    - [[#@2024년 11월 9일 오후 6:12 본격 한파대비 사진 안나옴]]
- [[#📌 이번 주차에는 이런 내용을 학습했어요!]]
- [[#❓ 이런 질문이 있어요!]]

  

## 📋 학습 목표

---

> **UIScrollView 이해하기**  
>   
> **UIScrollView의 기본 설정**  
>   
> **스크롤뷰의 상하좌우 스크롤 구현**  
>   
> **StackView와 스크롤 결합 사용**  
>   
> **고급 UIScrollView 활용**  

  

## ✋ 잠깐! 스터디 인증샷 찍으셨나요?

---

> [!important] 스터디 시작 전 ==**스터디 인증샷을 촬영**==해주세요!
> 
> 스터디는 대면이 원칙이며, 비대면 스터디의 경우에도 최대한 카메라를 킨 후 진행해주세요.
> 
> 아래 임베드 블록에 인증샷을 임베드해 주시면 됩니다 🫶

- 사진
    
    ![[KakaoTalk_Photo_2024-11-02-23-27-55.png]]
    

  

## 🔥 5주차 개념 설명

---

### 1. UIScrollView 이해하기

## 🧐 UIScrollView란?

> `UIScrollView` 는 iOS 애플리케이션에서 화면의 제한된 영역에 큰 콘텐츠를 표시하고, 사용자가 손가락으로 스크롤하여 더 많은 정보를 탐색할 수 있도록 도와주는 기본적인 뷰 컴포넌트입니다.

> [!important] `UIScrollView`는 콘텐츠를 담을 수 있는 ==**컨테이너 역할**==을 하며, 이 ==**컨테이너 안의 콘텐츠 크기가 화면을 초과할 때 사용자가 해당 콘텐츠의 나머지 부분을 탐색할 수 있도록 스크롤**==할 수 있는 기능을 지원합니다. 추가적으로, `UIScrollView`는 줌(zoom) 기능도 제공하여 이미지를 확대/축소하거나 특정 영역을 확대하는 사용자 인터랙션을 가능하게 합니다.

![[Assets/image 11.png|image 11.png]]

### 스크롤 뷰가 필요한 이유!!!

> 모바일 기기 화면은 물리적으로 크기가 제한되어 있습니다. 그 결과, 긴 텍스트, 대형 이미지, 리스트 항목 등 많은 양의 콘텐츠를 한 화면에 모두 표시하기 어려운 상황이 발생합니다. `UIScrollView`는 이 문제를 해결하기 위한 가장 대표적인 컴포넌트로, 한 번에 표시할 수 없는 콘텐츠를 스크롤을 통해 자연스럽게 탐색할 수 있도록 도와줍니다.

  

## 🤨 스크롤뷰 언제 사용해??!!

> [!important]
> 
> - **컨텐츠 크기가 화면보다 큰 경우**
>     - 화면에 표시할 수 있는 영역이 제한적일 때!! 가령, 길이가 긴 텍스트 문서나 여러 이미지가 나열된 경우, 스크롤뷰를 사용하여 사용자가 화면을 넘겨가며 내용을 탐색할 수 있도록 합니다
> - **화면에 제한된 공간에서 여러 항목을 표시해야 할 때**
>     - ==**수평 스크롤**== 또는 ==**수직 스크롤**==을 사용하여 제한된 공간에서 다수의 항목(컴포넌트들)을 표시할 수 있습니다.
> - **동적 컨텐츠**
>     - 사용자의 인터랙션이나 네트워크 호출로 인해 컨텐츠가 동적으로 추가되거나 삭제될 때 스크롤뷰는 컨텐츠의 증가/감소에 맞게 스크롤 영역을 동적으로 조정할 수 있습니다.

  

`UIScrollView` 가 무엇인지 이해했으니, 스크롤뷰를 제대로 활용하려면 몇 가지 중요한 설정을 다루는 것이 중요합니다!

`UIScrollView`의 기본 속성과 함께 콘텐츠 크기(Content Size)를 설정하는 방법, 그리고 스크롤뷰를 Auto Layout과 함께 사용할 때 알아두어야 할 중요한 개념, 스크롤뷰를 활용하여 고급 기능 구현하는 개념들을 이번 워크북을 통해 알아보도록 하겠습니다.!!

### 2. UIScrollView의 기본 설정

> `UIScrollView`는 강력한 스크롤 및 줌 기능을 제공하는 중요한 UI 구성 요소입니다. 기본적인 속성들을 설정하고, 스크롤 가능한 콘텐츠 크기를 관리하는 방법 Auto Layout을 통해 적절히 배치하는 방법을 이해해야 합니다.!!

> [!info] UIScrollView | Apple Developer Documentation  
> A view that allows the scrolling and zooming of its contained views.  
> [https://developer.apple.com/documentation/uikit/uiscrollview](https://developer.apple.com/documentation/uikit/uiscrollview)  

> [!important] 위 링크의 Apple Developer 문서에 자세한 설명들이 있습니다. 워크북에 설명한 것은 위 사이트에 있는 전부가 아닌, 스크롤뷰를 사용하시면서 유용하게 쓰일 것들 위주로 설명하도록 했습니다.<br>==**추가적인 내용이 필요하시면 위 사이트를 참고하시기 바랍니다.!! ^^**==

## 🤨 UIScrollView 기본 속성

> `UIScrollView` 에 컨텐츠를 스크롤할 수 있게 해주는 여러 속성이 있습니다. 이들 속성은 스크롤뷰의 동작과 사용자 경험을 결정하는 핵심 요소입니다.

- **contentSize**
    
    - 스크롤할 수 있는 전체 컨텐츠의 크기를 설정합니다. `contentSize` 는 스크롤할 수 있는 범위를 정의하며, ==**이 값이 설정되지 않으면 스크롤뷰는 스크롤하지 않습니다.**== `contentSize`는 보통 `CGSize(width:height:)`를 사용하여 설정하며, 이 크기는 스크롤뷰 내부에 배치된 콘텐츠의 전체 크기입니다.
    
    ```Swift
    let scrollView = UIScrollView(frame: view.bounds)
    scrollView.backgroundColor = .lightGray
    view.addSubview(scrollView)
    
    // 스크롤뷰 안에 들어갈 큰 이미지 추가
    let imageView = UIImageView(image: UIImage(named: "largeImage"))
    scrollView.addSubview(imageView)
    
    // 이미지 크기에 맞게 contentSize 설정
    scrollView.contentSize = imageView.bounds.size
    ```
    
      
    
- **contentOffSet**
    
    - 스크롤뷰의 좌표계에서 콘텐츠의 현재 위치를 나타냅니다. 즉, 스크롤된 현재 위치를 의미하며, `CGPoint(x:y:)`형태로 설정됩니다. 사용자가 스크롤할 때 `contentOffset`이 변하며, 이를 프로그래밍적으로 설정해 특정 위치로 스크롤을 이동시킬 수 있습니다.
    - ==**무한 스크롤 구현, 스크롤 위치에 따라 UI 변경하기에 주로 쓰입니다.**==
    
    ```Swift
    /* 무한 스크롤 */
    func scrollViewDidScroll(_ scrollView: UIScrollView) {
        let contentHeight = scrollView.contentSize.height
        let offsetY = scrollView.contentOffset.y
        let frameHeight = scrollView.frame.size.height
        
        if offsetY > contentHeight - frameHeight {
            // 페이징을 통해 무한 스크롤 구현 시 스크롤 끝 부분 도달 시 데이터를 로드 합니다.
            // 아래 함수는 예시로 작성한 것이며, 프로젝트 진행 시 상황에 맞춰 진행하시면 됩니다.
            loadMoreData()
        }
    }
    ```
    
    ```Swift
    /* 스크롤 위치에 따라 UI 변경 */
    /* 직관적으로 이해가 필요하시면, 당근 마켓을 설치해서 스크롤 해보시기 바라겠습니다. */
    /* 당근 마켓의 경우 스크롤해서 내리거나 올리면 오른쪽 하단의 플로팅 버튼이 바뀌는 것을 확인 할 수 있습니다. */
    /* 아래코드는 5. 고급 UIScrollView 활용 부분의 Apple Developer 사이트에서 확인할 수 있습니다. */
    func scrollViewDidScroll(_ scrollView: UIScrollView) {
        let offset = scrollView.contentOffset.y
        // offset 값에 따라 네비게이션 바의 투명도 조정
        // 아래 또한 예시 코드로 상황에 맞춰 진행하시면 됩니다.
        navigationController?.navigationBar.alpha = max(0, min(1, 1 - offset / 100))
    }
    ```
    
      
    
- **contentInset**
    
    - 스크롤 가능한 콘텐츠와 스크롤뷰 경계 사이의 여백을 지정합니다.
    - 상단, 하단, 왼쪽, 오른쪽에 각각 여백을 설정해 콘텐츠를 스크롤뷰 내부에서 적절히 여백을 두고 배치할 수 있습니다.
    - 아래 코드는 컨텐츠 크기에 맞춰 자동 여백 지정이 되면서, 자연스럽게 스크롤이 가능하도록 설정된 코드입니다.
    
    ```Swift
    /* 이미지 크기에 맞춰 스크롤을 할 때, 여백이 반영되어 스크롤 가능 */
    let scrollView = UIScrollView(frame: view.bounds)
    scrollView.backgroundColor = .lightGray
    view.addSubview(scrollView)
    
    let imageView = UIImageView(image: UIImage(named: "largeImage"))
    scrollView.addSubview(imageView)
    
    scrollView.contentSize = imageView.frame.size
    
    // 스크롤뷰의 내부 여백 설정 (상단: 50, 좌측: 20, 하단: 50, 우측: 20)
    // 상황에 맞춰 작성하시면 되는 부분입니다.
    scrollView.contentInset = UIEdgeInsets(top: 50, left: 20, bottom: 50, right: 20)
    ```
    
      
    
- **isScrollEnabled**
    
    - 스크롤 기능을 활성화하거나 비활성화할 수 있는 플래그입니다. 이 속성을 `false` 로 설정하면 스크롤이 비활성화되어 사용자가 컨텐츠를 스크롤 할 수 없게 됩니다.
    - 스크롤 기능을 비활성화 하는 경우는, ==**스크롤 뷰 내부에 사용자의 입력을 작성해야 하는 텍스트 필드가 존재할 시!!**== 텍스트 입력 시 텍스트 입력이 끝날 때까지 스크롤 뷰가 작동하지 않도록 막을 때 사용하곤 합니다.
    
    ```Swift
    /* 기본적인 설정 방법입니다. */
    
    let scrollView = UIScrollView(frame: view.bounds)
    scrollView.backgroundColor = .lightGray
    view.addSubview(scrollView)
    
    let contentView = UIView(frame: CGRect(x: 0, y: 0, width: view.bounds.width, height: 1000))
    contentView.backgroundColor = .white
    scrollView.addSubview(contentView)
    
    scrollView.contentSize = contentView.frame.size
    
    // 스크롤을 비활성화
    scrollView.isScrollEnabled = false
    ```
    
    ```Swift
    /* 텍스트 입력 시, 스크롤 설정 */
    /* 아래코드는 5. 고급 UIScrollView 활용 부분의 Apple Developer 사이트에서 확인할 수 있습니다. */
    
    func textFieldDidBeginEditing(_ textField: UITextField) {
        // 사용자가 텍스트 필드를 편집할 때 스크롤 비활성화
        scrollView.isScrollEnabled = false
    }
    
    func textFieldDidEndEditing(_ textField: UITextField) {
        // 사용자가 편집을 완료했을 때 스크롤 다시 활성화
        scrollView.isScrollEnabled = true
    }
    ```
    
      
    
- **showsVerticalScrollIndicator 및 showHorizontalScrollIndicator**
    
    - 세로 스크롤 및 가로 스크롤바를 표시할지 여부를 결정합니다. 기본값은 `true` 이며, 필요에 따라 스크롤바를 숨기거나 표시할 수 있습니다.
    
    ```Swift
    let scrollView = UIScrollView(frame: view.bounds)
    scrollView.backgroundColor = .lightGray
    view.addSubview(scrollView)
    
    let contentView = UIView(frame: CGRect(x: 0, y: 0, width: 800, height: 1200))
    contentView.backgroundColor = .white
    scrollView.addSubview(contentView)
    
    scrollView.contentSize = contentView.frame.size
    
    // 세로 스크롤바 숨기기
    scrollView.showsVerticalScrollIndicator = false
    
    // 가로 스크롤바 숨기기
    scrollView.showsHorizontalScrollIndicator = false
    ```
    
      
    
- **bounces**
    
    - 스크롤뷰의 끝에 도달했을 때 약간의 바운스 효과를 줄지 여부를 결정합니다. 기본적으로 `true` 이며, 사용자는 끝에 도달했을 때 경계를 넘어서는 스크롤을 시도할 수 있습니다. 효과는 스크롤 경험을 좀 더 부드럽게 만듭니다.
    
    ```Swift
    let scrollView = UIScrollView(frame: view.bounds)
    scrollView.backgroundColor = .lightGray
    view.addSubview(scrollView)
    
    let contentView = UIView(frame: CGRect(x: 0, y: 0, width: view.bounds.width, height: 1200))
    contentView.backgroundColor = .white
    scrollView.addSubview(contentView)
    
    scrollView.contentSize = contentView.frame.size
    
    // 기본적으로 bounces는 true (탄력 효과가 있음)
    scrollView.bounces = true
    ```
    

  

- **isPagingEnabled**
    
    - 이 속성을 `true` 로 설정하면 페이지 단위로 스크롤이 가능해집니다. 이미지 갤러리처럼 한 페이지씩 넘기는 인터페이스를 만들 때 유용합니다.
    
    ```Swift
    let scrollView = UIScrollView(frame: view.bounds)
    scrollView.backgroundColor = .lightGray
    view.addSubview(scrollView)
    
    // 각 페이지의 크기를 화면 크기와 동일하게 설정
    let pageWidth = view.bounds.width
    let pageHeight = view.bounds.height
    
    // 세 개의 페이지를 위한 contentSize 설정
    scrollView.contentSize = CGSize(width: pageWidth * 3, height: pageHeight)
    
    // 페이지 단위 스크롤을 가능하게 설정
    scrollView.isPagingEnabled = true
    
    // 페이지마다 다른 색상을 가진 뷰를 추가
    for i in 0..<3 {
        let page = UIView(frame: CGRect(x: CGFloat(i) * pageWidth, y: 0, width: pageWidth, height: pageHeight))
        page.backgroundColor = i % 2 == 0 ? .red : .blue
        scrollView.addSubview(page)
    }
    ```
    

## 😄 ContentSize 설정

> `UIScrollView`가 제대로 동작하려면 `contentSize`를 올바르게 설정해야 합니다. 이 속성은 스크롤 가능한 전체 콘텐츠 영역을 정의합니다. `contentSize`는 스크롤 가능한 콘텐츠의 너비와 높이를 설정하는 `CGSize` 구조체로 구성됩니다.

> [!important] 위 속성 설명에서는 자동으로 설정되는 예시를 보여드렸습니다.<br>여기서는 가로, 세로를 직접 설정하는 예시를 보이며 설명하도록 하겠습니다.<br>

스크롤뷰에 크기가 큰 이미지를 넣고 이를 스크롤하고 싶다면, 이미지의 크기에 맞춰 `contentSize` 를 설정해야 합니다.

```Swift
let scrollView = UIScrollView(frame: view.bounds)
let contentWidth: CGFloat = 1000
let contentHeight: CGFloat = 2000
scrollView.contentSize = CGSize(width: contentWidth, height: contentHeight)
```

**❗️❗️만약** `**contentSize**` **가 스크롤뷰의 크기보다 작다면, 스크롤이 발생하지 않으며 콘텐츠가 고정된 상태로 보이게 됩니다.❗️❗️**

![[scrollviewStructure.png]]

  

## 😉 Auto Layout과 스크롤뷰

> `UIScrollView`는 Auto Layout과 함께 사용할 때 ==**특별한 주의가 필요합니다**==. Auto Layout은 뷰의 위치와 크기를 동적으로 결정하기 위한 강력한 도구지만, ==**스크롤뷰와 결합할 때는 염두에 두어야 할 사항이 있습니다.**==

> [!important] ==**SnapKit 사용하여 예시 코드를 작성했습니다.**==

> [!important] ==**실제로 코드를 실행시켜 확인 하기 싶으시면, viewDidLoad()에 추가하여 빌드 해보시면 됩니다.**==

  

![[1sVOaMOvubvCkl9aaKGS6FA.webp]]

> [!important]
> 
> - **스크롤뷰의 자체 크기 설정**
>     
>     - 먼저, 스크롤뷰 자체에 대한 제약 조건을 설정해야 합니다. 스크롤뷰는 화면의 특정 영역을 차지하며, 이 크기는 다른 뷰들과 마찬가지로 고정되거나 부모 뷰와 상대적인 크기로 설정할 수 있습니다.
>     
>     ```Swift
>     view.addSubview(scrollView)
>     scrollView.snp.makeConstraints { make in
>         make.edges.equalToSuperview() // 부모 뷰의 모든 가장자리에 고정
>     }
>     ```
>     
>       
>     
> - **스크롤뷰 안의 컨텐츠에 대한 제약 설정**
>     
>     - 스크롤뷰 안에 배치된 컨텐츠에 대한 제약 조건을 설정할 때는 반드시 스크롤뷰의 `contentSize` 와 관련된 제약을 설정해야 합니다. 컨텐츠의 크기를 고정하지 않고 스크롤뷰의 내부에 배치된 요소들이 스크롤 가능하도록 구성해야 합니다.
>     
>     ```Swift
>     scrollView.addSubview(contentView)
>     contentView.snp.makeConstraints { make in
>         make.edges.equalTo(scrollView) // 스크롤뷰의 모든 가장자리에 맞춰 배치
>         make.width.equalTo(scrollView.snp.width) // 가로 스크롤을 방지하고 스크롤뷰와 같은 너비로 설정
>         make.height.equalTo(2000) // 콘텐츠의 세로 크기를 설정하여 세로 스크롤 가능하게 함
>     }
>     ```
>     
>       
>     
> - **동적 컨텐츠 크기 설정**
>     
>     - 만약!!, 스크롤 뷰 내부의 컨텐츠가 동적으로 변경되는 경우, 높이를 고정하지 않고 동적 제약 조건을 설정할 수 있습니다. 컨텐츠 뷰 안에 여러 개의 컴포넌트들을 배치할 수 있습니다.
>     - 아래는 Label과 Button을 스크롤 뷰안에 배치한다는 가정하에 코드를 작성했습니다.
>     
>     ```Swift
>     let label = UILabel()
>     contentView.addSubview(label)
>     label.snp.makeConstraints { make in
>         make.top.equalTo(contentView).offset(20)
>         make.left.equalTo(contentView).offset(20)
>         make.right.equalTo(contentView).offset(-20)
>     }
>     
>     let button = UIButton()
>     contentView.addSubview(button)
>     button.snp.makeConstraints { make in
>         make.top.equalTo(label.snp.bottom).offset(20)
>         make.left.equalTo(contentView).offset(20)
>         make.right.equalTo(contentView).offset(-20)
>         make.bottom.equalTo(contentView).offset(-20) // 콘텐츠의 마지막 요소가 contentView의 bottom에 닿도록 설정
>     }
>     ```
>     

### 3. 스크롤뷰의 상하좌우 스크롤 구현

> 스크롤뷰에는 **수직 스크롤, 상하 스크롤, 상하좌우 동시 스크롤**을 구현할 수 있습니다.  
> 2. UIScrollView의 기본설정에서 이미 예시 코드를 보였지만, 더 자세히 어떻게 작동하는지 원리와 코드를 보여드리도록 하겠습니다.  

  

## 🤨 수직 스크롤 구현

> ==**수직 스크롤은 화면보다 컨텐츠가 길 경우에 사용됩니다.**== ==길이가 긴 텍스트나 이미지 같은 컨텐츠가 화면을 벗어날 때 수직 스크롤이 필요합니다. 제일 중요한 점!!== ==`contentSize`== ==의== ==**높이가 스크롤 뷰의 높이보다 커야 하며, 컨텐츠의 너비는 스크롤뷰와 동일 하게 설정해야 가로 스크롤이 발생하지 않습니다.**==

  

```Swift
let scrollView = UIScrollView()
let contentView = UIView()

view.addSubview(scrollView)
scrollView.snp.makeConstraints { make in
    make.edges.equalToSuperview() // 스크롤뷰가 화면 전체에 걸치도록 설정
}

scrollView.addSubview(contentView)
contentView.snp.makeConstraints { make in
    make.edges.equalTo(scrollView) // 콘텐츠 뷰의 모든 가장자리를 스크롤뷰에 맞춰 배치
    make.width.equalTo(scrollView.snp.width) // 가로 스크롤 방지
    make.height.equalTo(2000) // 세로로 스크롤할 수 있도록 콘텐츠 높이 설정
}
```

  

## 🤨 수평 스크롤 구현

> ==**수평 스크롤은 콘텐츠의 너비가 화면보다 넓을 때 사용됩니다.**== 여러장의 이미지가 가로로 배치된 이미지 갤러리를 구현할 때 수평 스크롤이 필요합니다. 콘텐츠의 높이는 스크롤뷰와 동일하게 설정해 세로 스크롤이 발생하지 않도록 하고, 너비는 스크롤뷰보다 크게 설정해 가로 스크롤이 가능하도록 만듭니다.

```Swift
let scrollView = UIScrollView()
let contentView = UIView()

view.addSubview(scrollView)
scrollView.snp.makeConstraints { make in
    make.edges.equalToSuperview() // 스크롤뷰가 화면 전체에 걸치도록 설정
}

scrollView.addSubview(contentView)
contentView.snp.makeConstraints { make in
    make.edges.equalTo(scrollView) // 콘텐츠 뷰의 모든 가장자리를 스크롤뷰에 맞춰 배치
    make.height.equalTo(scrollView.snp.height) // 세로 스크롤 방지
    make.width.equalTo(2000) // 가로로 스크롤할 수 있도록 콘텐츠 너비 설정
}
```

  

## 🤨 상하좌우 동시 스크롤 구현

> ==**상하좌우 동시 스크롤은 컨텐츠가 화면을 가로와 세로 모두 초과하는 경우 사용됩니다.**== 커다란 이미지나 지도를 표시할 때 사용자에게 상하좌우로 자유롭게 스크롤할 수 있도록 해야합니다. 컨텐츠의 `contentSize` 너비와 높이를 모두 스크롤뷰보다 크게 설정해야 하며, 스크롤뷰가 두 방향 모두에서 스크롤할 수 있도록 허용해야 합니다.

```Swift
let scrollView = UIScrollView()
let contentView = UIView()

view.addSubview(scrollView)
scrollView.snp.makeConstraints { make in
    make.edges.equalToSuperview() // 스크롤뷰가 화면 전체에 걸치도록 설정
}

scrollView.addSubview(contentView)
contentView.snp.makeConstraints { make in
    make.edges.equalTo(scrollView) // 콘텐츠 뷰의 모든 가장자리를 스크롤뷰에 맞춰 배치
    make.width.equalTo(2000) // 가로로 스크롤할 수 있도록 너비 설정
    make.height.equalTo(2000) // 세로로 스크롤할 수 있도록 높이 설정
}
```

### 4. StackView와 스크롤의 결합 사용

> `UIStackView` 는 여러 뷰를 쉽게 수직 또는 수평으로 배치하고, 일관된 간격을 유지하면서 관리할 수 있는 강력한 도구입니다. 또한, AutoLayout 제약을 일일이 설정하지 않고도, ==**여러 뷰를 일관되게 배치하는 데 유용하며, 동적 컨텐츠를 다룰 때 매우 강력한 기능을 제공**==합니다.  
> 스크롤뷰 내부에서  
> `UIStackView` 를 사용하면 레이아웃 관리를 간소화할 수 있습니다. 특히, 여러 개의 뷰를 추가하고 정렬해야 할 때 매우 유용합니다.

> [!important] `**StackView**` **에 대한 자세한 설명은 생략하도록 하겠습니다. 아래 사이트를 통해 쉽게 이해할 수 있으며 실제 사용에 대한 연습은 실습 또는 과제를 하시면서 스스로 학습하시기 바라겠습니다**.

> [!info] UIStackView | Apple Developer Documentation  
> A streamlined interface for laying out a collection of views in either a column or a row.  
> [https://developer.apple.com/documentation/uikit/uistackview](https://developer.apple.com/documentation/uikit/uistackview)  

  

## 😙 스택뷰를 사용해야 하는 이유!!

- **Auto Layout 제약 설정 간소화**
    - `UIStackView`는 내부에 있는 뷰들의 크기와 위치를 자동으로 관리해 줍니다. 개별 뷰마다 Auto Layout 제약을 일일이 설정할 필요 없이, 간단한 설정만으로 여러 개의 뷰를 효율적으로 배치할 수 있습니다.
- **일관된 뷰 배치**
    - 수직(.vertical) 또는 수평(.horizontal)으로 뷰를 일관성 있게 배치할 수 있습니다. 각 뷰 간의 간격(spacing)을 쉽게 설정할 수 있어 레이아웃의 일관성을 유지하는 데 유리합니다.
- **동적 콘텐츠 관리 용이**
    - 스택뷰는 `addArrangedSubview()` 및 `removeArrangedSubview()` 메서드를 통해 뷰를 동적으로 추가하거나 제거할 수 있습니다.
- **가독성 높은 코드**
    - 스택뷰는 제약 조건을 코드로 직접 설정하는 것보다 간결하고 가독성이 높은 코드를 작성할 수 있도록 도와줍니다. 복잡한 Auto Layout 제약을 간단한 속성 설정으로 대체할 수 있습니다.

  

## 😝 스택뷰에 사용되는 주요 속성(중요!!!!!)

아래는 스택뷰의 주요 속성을 정리했습니다. 뷰를 배치하는 데 있어서 자주, 유용하게 사용하시길 바라겠습니다.

> [!important]
> 
> - **axis**: `UIStackView`가 뷰를 수직으로 정렬할지, 수평으로 정렬할지 결정합니다.
>     - `.vertical`: 수직으로 뷰들을 쌓습니다.
>     - `.horizontal`: 수평으로 뷰들을 나란히 배치합니다.
> - **alignment**: 스택뷰 안의 뷰들이 어떻게 정렬될지 결정합니다. 기본값은 `.fill`로, 모든 뷰의 크기를 동일하게 맞춥니다.
>     - `.fill`: 모든 뷰를 동일한 크기로 확장하여 맞춥니다.
>     - `.leading`, `.trailing`: 뷰를 앞이나 뒤에 맞춰 정렬합니다.
>     - `.center`: 뷰를 가운데 정렬합니다.
> - **distribution**: 스택뷰 안의 뷰들 사이에 공간을 어떻게 분배할지 설정합니다.
>     - `.fill`: 모든 뷰가 가능한 최대 크기로 확장됩니다.
>     - `.fillEqually`: 모든 뷰가 동일한 크기로 배치됩니다.
>     - `.fillProportionally`: 각 뷰의 고유 크기 비율을 유지한 상태로 공간이 분배됩니다.
>     - `.equalSpacing`: 뷰들 사이의 간격을 동일하게 설정합니다.
>     - `.equalCentering`: 뷰의 중심 간의 간격을 동일하게 설정합니다.
> - **spacing**: 스택뷰 안에 배치된 뷰들 사이의 간격을 설정합니다.

  

```Swift
let scrollView = UIScrollView()
let contentView = UIView()
let stackView = UIStackView()

view.addSubview(scrollView)
scrollView.snp.makeConstraints { make in
    make.edges.equalToSuperview() // 스크롤뷰를 화면 전체에 걸치도록 설정
}

scrollView.addSubview(contentView)
contentView.snp.makeConstraints { make in
    make.edges.equalTo(scrollView) // 콘텐츠 뷰의 모든 가장자리를 스크롤뷰에 맞춤
    make.width.equalTo(scrollView.snp.width) // 가로 스크롤 방지
}

contentView.addSubview(stackView)
stackView.axis = .vertical // 스택 뷰를 수직으로 설정
stackView.spacing = 20 // 각 뷰 간의 간격 설정
stackView.distribution = .fillProportionally // 뷰의 크기를 비율에 맞게 조정

stackView.snp.makeConstraints { make in
    make.edges.equalTo(contentView).inset(20) // 스택뷰를 콘텐츠에 맞춤
    make.width.equalTo(contentView.snp.width) // 가로 스크롤 방지
}

let label1 = UILabel()
label1.text = "Label 1"
stackView.addArrangedSubview(label1)

let button1 = UIButton(type: .system)
button1.setTitle("Button 1", for: .normal)
stackView.addArrangedSubview(button1)

let label2 = UILabel()
label2.text = "Label 2"
stackView.addArrangedSubview(label2)
```

### 5. 고급 UIScrollView 활용

> `UISscrollView` 는 단순히 컨텐츠를 스크롤하는 기능을 넘어서 다양한 고급 기능을 제공합니다. 이 기능들은 `UIScrollViewDelegate` 프로토콜을 활용하여 더욱 세밀하게 제어하고 커스터마이징 할 수 있습니다. `UIScrollViewDelegate` 를 사용하면 스크롤 이벤트에 대한 응답. 줌 동작의 제어, 페이징 처리, 제스처 인식 등 여러 가지 작업을 수행할 수 있습니다.

  

> [!important] 워크북에서는 ==**페이징, 줌, 제스처 처리 및 인식 이 세가지 고급 기능**====에 대해 어떻게 구현하고 활용할 수 있는지 설명하도록 하겠습니다.==

> [!info] UIScrollViewDelegate | Apple Developer Documentation  
> The interface for the delegate of a scroll view.  
> [https://developer.apple.com/documentation/uikit/uiscrollviewdelegate](https://developer.apple.com/documentation/uikit/uiscrollviewdelegate)  

  

## 😙 Paging 기능 구현

==**페이징은 스크롤뷰가 한 페이지씩 정확하게 스크롤되도록 하는 기능입니다.**== 이미지 슬라이더, 튜토리얼 화면 등에서 자주 사용합니다. `UIScrollViewDelegate`를 활용하면 페이지 전환 시점에 추가적인 작업을 수행할 수 있습니다.

  

### 페이징 설정 및 `UIScrollViewDelegate` 활용

1. `isPagingEnabled`를 `true`로 설정하여 기본적인 페이징 기능을 활성화합니다.
2. `UIScrollViewDelegate`의 `scrollViewDidEndDecelerating(_:)` 또는 `scrollViewDidScroll(_:)` 메서드를 구현하여 페이지 전환 시 추가 동작을 수행할 수 있습니다. 예를 들어, 현재 페이지 인덱스를 추적하여 페이지 컨트롤을 업데이트할 수 있습니다.

```Swift
class PagingViewController: UIViewController, UIScrollViewDelegate {
    let scrollView = UIScrollView()
    let pageControl = UIPageControl()
    let numberOfPages = 3

    override func viewDidLoad() {
        super.viewDidLoad()
        
        scrollView.isPagingEnabled = true
        scrollView.delegate = self
        scrollView.showsHorizontalScrollIndicator = false

        view.addSubview(scrollView)
        scrollView.snp.makeConstraints { make in
            make.edges.equalToSuperview()
        }

        let contentView = UIView()
        scrollView.addSubview(contentView)
        contentView.snp.makeConstraints { make in
            make.edges.equalTo(scrollView)
            make.height.equalTo(scrollView.snp.height)
            make.width.equalTo(scrollView.snp.width).multipliedBy(numberOfPages)
        }

        for i in 0..<numberOfPages {
            let page = UIView()
            page.backgroundColor = [UIColor.red, UIColor.green, UIColor.blue][i]
            contentView.addSubview(page)
            page.snp.makeConstraints { make in
                make.top.bottom.equalToSuperview()
                make.width.equalTo(scrollView.snp.width)
                make.left.equalTo(scrollView.snp.width).multipliedBy(i)
            }
        }

        // 페이지 컨트롤 설정
        pageControl.numberOfPages = numberOfPages
        pageControl.currentPage = 0
        view.addSubview(pageControl)
        pageControl.snp.makeConstraints { make in
            make.centerX.equalToSuperview()
            make.bottom.equalTo(view.safeAreaLayoutGuide.snp.bottom).offset(-20)
        }
    }

		/* extension을 통해 확장 가능 */
    // 현재 페이지를 추적하여 페이지 컨트롤 업데이트
    func scrollViewDidScroll(_ scrollView: UIScrollView) {
        let pageIndex = round(scrollView.contentOffset.x / scrollView.frame.width)
        pageControl.currentPage = Int(pageIndex)
    }
}
```

  

## 😙 Zoom 기능 설정 및 활용

줌 기능은 컨텐츠를 확대하거나 축소할 수 있도록 하는 기능입니다. 사진 갤러리나 지도 앱에서 자주 사용됩니다. `UIScrollViewDelegate`의 `viewForZooming(in:)` 메서드를 통해 어떤 뷰를 확대/축소할지 지정할 수 있습니다. 또한, 줌 이벤트에 반응하여 추가 동작을 수행할 수도 있습니다.

  

### 줌 기능 구현 방법

1. `minimumZoomScale`과 `maximumZoomScale`을 설정하여 줌 범위를 지정합니다.
2. `UIScrollViewDelegate`의 `viewForZooming(in:)` 메서드를 구현하여 줌 대상 뷰를 반환합니다.
3. `scrollViewDidZoom(_:)` 메서드를 구현하여 줌 상태 변화에 따른 추가 작업을 수행합니다.

```Swift
class ZoomViewController: UIViewController, UIScrollViewDelegate {
    let scrollView = UIScrollView()
    let imageView = UIImageView(image: UIImage(named: "sampleImage"))

    override func viewDidLoad() {
        super.viewDidLoad()
        
        scrollView.delegate = self
        scrollView.minimumZoomScale = 1.0
        scrollView.maximumZoomScale = 5.0

        view.addSubview(scrollView)
        scrollView.snp.makeConstraints { make in
            make.edges.equalToSuperview()
        }

        scrollView.addSubview(imageView)
        imageView.snp.makeConstraints { make in
            make.edges.equalTo(scrollView)
            make.width.equalTo(scrollView.snp.width)
            make.height.equalTo(scrollView.snp.height)
        }
    }

    // 줌 가능한 뷰 설정
    func viewForZooming(in scrollView: UIScrollView) -> UIView? {
        return imageView
    }

    // 줌 상태 변화에 따른 추가 작업
    func scrollViewDidZoom(_ scrollView: UIScrollView) {
				// 이미지를 가운데로 정렬
        let offsetX = max((scrollView.bounds.width - scrollView.contentSize.width) * 0.5, 0)
        let offsetY = max((scrollView.bounds.height - scrollView.contentSize.height) * 0.5, 0)
        imageView.center = CGPoint(x: scrollView.contentSize.width * 0.5 + offsetX,
                                   y: scrollView.contentSize.height * 0.5 + offsetY)
    }
}
```

  

## 😙 스크롤뷰의 제스처 처리 및 인터랙션 제어

`UIScrollView` 는 기본적으로 스크롤 및 줌과 관련된 제스처를 처리합니다. 그러나 앱에서 사용자 정의 제스처를 추가하거나, 스크롤뷰의 제스처 인식과 다른 제스처 인식기 간의 우선순위를 조정해야 하는 경우가 있습니다. `UIScrollViewDelegate`를 활용하면 이러한 제스처 처리 및 인터랙션을 세밀하게 제어할 수 있습니다.

  

### 제스처 처리와 `UISCrollViewDelegate` 활용

1. **제스처 우선순위 조정**
    1. `gestureRecognizer(_:shouldRecognizeSimultaneouslyWith:)` 메서드를 구현하여 여러 제스처 인식기가 동시에 인식될 수 있도록 제어합니다.
2. **스크롤 이벤트 감지**
    1. `scrollViewWillBeginDragging(_:)`, `scrollViewDidEndDragging(_:willDecelerate:)` 등을 구현하여 스크롤 시작 및 종료 시점에 대한 처리를 할 수 있습니다.

```Swift
class GestureViewController: UIViewController, UIScrollViewDelegate, UIGestureRecognizerDelegate {
    let scrollView = UIScrollView()

    override func viewDidLoad() {
        super.viewDidLoad()
        
        scrollView.delegate = self
        view.addSubview(scrollView)
        scrollView.snp.makeConstraints { make in
            make.edges.equalToSuperview()
        }

        // 스크롤뷰에 탭 제스처 추가
        let tapGesture = UITapGestureRecognizer(target: self, action: \#selector(handleTap(_:)))
        tapGesture.delegate = self
        scrollView.addGestureRecognizer(tapGesture)
    }

    @objc func handleTap(_ gesture: UITapGestureRecognizer) {
        // 탭 제스처 처리 로직
        print("스크롤뷰가 탭되었습니다.")
    }

    // 제스처 인식기 델리게이트 메서드 구현
    func gestureRecognizer(_ gestureRecognizer: UIGestureRecognizer, shouldRecognizeSimultaneouslyWith otherGestureRecognizer: UIGestureRecognizer) -> Bool {
        // 스크롤뷰의 제스처와 커스텀 제스처를 동시에 인식하도록 허용
        return true
    }

    // 스크롤뷰 델리게이트 메서드 구현
    func scrollViewWillBeginDragging(_ scrollView: UIScrollView) {
        print("스크롤이 시작됩니다.")
    }

    func scrollViewDidEndDragging(_ scrollView: UIScrollView, willDecelerate decelerate: Bool) {
        print("스크롤이 종료되었습니다.")
    }
}
```

  

## 끝으로!!

> [!important] `UIScrollView` 는 iOS 앱 개발에서 다양한 상황에서 유용하게 활용될 수 있습니다. 특히 ==**사용자 친화적인 컨텐츠 탐색**==과 ==**반응형 레이아웃을 구현**==할 때 중요한 역할을 합니다. 이번 워크북을 통헤 여러분은 ==**스크롤뷰를 효과적으로 활용하여 사용자에게 직관적이고 매끄러운 경험을 제공**==할 수 있을 거라 믿습니다!

## 🔥 5주차 개념 점검

---

> [!important] `UIScrollView` 에서 스크롤이 정상적으로 동작하기 위해 반드시 설정해야 하는 속성은 무엇인가요? 또한 이 속성의 역할을 설명하세요

- **여기에 답을 적어주세요!**
    
    contentsize 스크롤뷰에서 확인할 수 있는 컨텐츠의 전체 크기를 정의
    

> [!important] 상하좌우 스크롤이 모두 가능한 `UIScrollView` 를 구현하려면 어떤 설정이 필요하며, 이를 어떻게 설정할 수 있는지 설명하세요

- **여기에 답을 적어주세요!**
    
    스크롤뷰 내부에 들어가는 컨텐트뷰의 가장자리는 스크롤뷰의 크기에 맞추고 컨텐트뷰의 너비와 높이 설정
    

> [!important] `UIStackView` 를 `UIScrollView` 와 결합하여 사용할 때의 장점은 무엇인가요? 또한, 이 결합을 사용할 때 반드시 고려해야 할 점은 무엇인지 설명하세요

- **여기에 답을 적어주세요!**
    
    - **Auto Layout 제약 설정 간소화**
        - `UIStackView`는 내부에 있는 뷰들의 크기와 위치를 자동으로 관리해 줍니다. 개별 뷰마다 Auto Layout 제약을 일일이 설정할 필요 없이, 간단한 설정만으로 여러 개의 뷰를 효율적으로 배치할 수 있습니다.
    - **일관된 뷰 배치**
        - 수직(.vertical) 또는 수평(.horizontal)으로 뷰를 일관성 있게 배치할 수 있습니다. 각 뷰 간의 간격(spacing)을 쉽게 설정할 수 있어 레이아웃의 일관성을 유지하는 데 유리합니다.
    - **동적 콘텐츠 관리 용이**
        - 스택뷰는 `addArrangedSubview()` 및 `removeArrangedSubview()` 메서드를 통해 뷰를 동적으로 추가하거나 제거할 수 있습니다.
    - **가독성 높은 코드**
        - 스택뷰는 제약 조건을 코드로 직접 설정하는 것보다 간결하고 가독성이 높은 코드를 작성할 수 있도록 도와줍니다. 복잡한 Auto Layout 제약을 간단한 속성 설정으로 대체할 수 있습니다.
    
      
    

> [!important] `UIScrollView` 에서 줌 기능을 구현할 때 필요한 메서드는 무엇이며, 해당 메서드가 어떤 역할을 하는지 설명하세요

- **여기에 답을 적어주세요!**
    1. `minimumZoomScale`과 `maximumZoomScale`을 설정하여 줌 범위를 지정합니다.
    2. `UIScrollViewDelegate`의 `viewForZooming(in:)` 메서드를 구현하여 줌 대상 뷰를 반환합니다.
    3. `scrollViewDidZoom(_:)` 메서드를 구현하여 줌 상태 변화에 따른 추가 작업을 수행합니다.

## 📚 5주차 실습

---

> 실습 내용은 위에 배운 내용을 사용하여 ==**스크롤뷰를 사용하여 무지개 색 띄위기**==를 진행해보도록 하겠습니다.! 순서를 지키면서 따라와 주시기 바랍니다.

> 아래 피그마 링크에 들어 오셔서 디자인을 확인해주시기 바랍니다.  
> ==**Option 키를 누르고, 프레임 위에 마우스를 올려 확인 하시면서 오토레이아웃 수치를 꼭!! 확인해주시기 바랍니다.**  
>   
> ====또한== ==`SnapKit`====을 적용하여 진행하도록 하겠습니다.==

[https://embed.figma.com/design/47IuhJxc7LFTwOYWtDgTdi/iOS-%EC%9B%8C%ED%81%AC%EB%B6%81?node-id=2063-505&t=GIEnA3aBSrNojaHb-1&embed-host=notion](https://embed.figma.com/design/47IuhJxc7LFTwOYWtDgTdi/iOS-%EC%9B%8C%ED%81%AC%EB%B6%81?node-id=2063-505&t=GIEnA3aBSrNojaHb-1&embed-host=notion)

### 1. SceneDelegate 설정

==**이 부분은 생략하도록 하겠습니다. 설정 방법을 모르시면 1주차 워크북을 다시 참고해주시기 바랍니다!**==

### 2. 분석

위 피그마 링크에 들어가서 디자인 된 것을 보면, 단순히 무지개색 일곱가지를 스크롤뷰를 사용해 띄우고 있습니다.

  

- 화면에 보이듯이 색을 띄우는 UIView가 무지개색 갯수에 맞춰 7번 사용되고 있습니다.
- 스크롤 뷰 내부 컨텐츠로 넣어 스크롤이 되도록 합니다.
- 스크롤은 세로 스크롤이 되도록 피그마 속 프레임이 세로가 깁니다.

### 3. 파일 및 폴더 생성

`ViewControllers` 폴더 내부에 ViewController.swift 파일을 생성해주세요

`Models` 폴더 내부에 RainbowColors.swift 파일을 생성합니다.

`Views` 폴더 내부에 RainbowView.swift 파일을 생성합니다.

![[스크린샷_2024-09-30_오후_3.57.39.png]]

### 4. Model 작성하기

무지개 색은 7개입니다. 즉, 모델에는 7개의 색을 표현할 수 있도록 구현합니다.

```Swift
import Foundation
import UIKit

struct RainbowColors {
    static let colors: [UIColor] = [
        UIColor.red,
        UIColor.orange,
        UIColor.yellow,
        UIColor.green,
        UIColor.blue,
        UIColor(red: 0.294, green: 0, blue: 0.51, alpha: 1), // 남색을 표현한 코드입니다.
        UIColor.purple
    ]
}
```

### 5. View 작성하기

피그마를 보시면서 오토레이아웃에 수치에 맞춰 구현하시면 되겠습니다.

> [!important] **최대한(?) 주석을 달아서 이해할 수 있도록 했습니다.**

  

- **스크롤뷰 생성 및 오토레이아웃 지정(안전영역 맞추기)**
    
    - 피그마에 보시면 스크롤뷰가 안전영역에 맞춰 디자인 되어 있습니다.
    
    ```Swift
     private lazy var scrollView: UIScrollView = {
            let scrollView = UIScrollView()
            scrollView.showsVerticalScrollIndicator = true
            scrollView.showsHorizontalScrollIndicator = false
            return scrollView
        }()
        
        // 스크롤뷰 및 기본 레이아웃 설정
        private func setupView() {
            self.addSubview(scrollView)
            scrollView.snp.makeConstraints {
                $0.edges.equalTo(self.safeAreaLayoutGuide) // 스크롤 뷰 안전영역 지키기
            }
        }
    ```
    
      
    
- **스크롤뷰에 7개의 색상 컨텐츠 뷰 넣기**
    
    - 하나의 색상당 높이는 176으로 지정되어 있습니다.(피그마 확인)
    - 7개를 추가하는 데 모델에 정의한 색상의 갯수에 맞춰 자동으로 추가되도록 합니다.
    - 첫 번째 추가 색(빨간색) 추가 시, 스크롤 뷰의 상단에 맞춰 오토레이아웃 지정되도록 합니다.
    - 마지막 색(보라색) 추가 가시, 스크롤 뷰의 하단에 맞춰 오토레이아웃 지정되도록 합니다.
    - 그 외 색상들은 이전에 추가된 색상의 bottom에 맞춰 오토레이아웃 지정되도록 합니다.
    
    ```Swift
    // 모델의 색상 배열을 사용하여 색상 뷰 설정
        private func setupColorViews() {
            var previousView: UIView? = nil
            
            for color in RainbowColors.colors {
                let colorView = UIView()
                colorView.backgroundColor = color
                scrollView.addSubview(colorView)
                
                colorView.snp.makeConstraints {
                    $0.left.right.equalToSuperview() // 좌우로 스크롤 없이 화면 크기에 맞춤
                    $0.width.equalTo(self.snp.width) // 피그마 디자인
                    $0.height.equalTo(176) // 피그마 디자인 높이
                    
                    
                    if let previousView = previousView {
                        $0.top.equalTo(previousView.snp.bottom) // 이전 뷰의 하단에 배치
                    } else {
                        $0.top.equalToSuperview() // 첫 번째 뷰는 스크롤뷰 상단에 맞춤
                    }
                }
                
                previousView = colorView
            }
            
            // 마지막 뷰의 하단을 스크롤뷰의 하단에 맞춤으로써 스크롤 가능하게 설정
            if let lastView = previousView {
                lastView.snp.makeConstraints {
                    $0.bottom.equalToSuperview()
                }
            }
        }
    ```
    
      
    
- **뷰 전체 코드**
    
    ```Swift
    import UIKit
    import SnapKit
    
    class RainbowView: UIView {
        
        override init(frame: CGRect) {
            super.init(frame: frame)
            setupView()
            setupColorViews()
        }
        
        required init?(coder: NSCoder) {
            fatalError("init(coder:) has not been implemented")
        }
        
        private lazy var scrollView: UIScrollView = {
            let scrollView = UIScrollView()
            scrollView.showsVerticalScrollIndicator = true
            scrollView.showsHorizontalScrollIndicator = false
            return scrollView
        }()
        
        // 스크롤뷰 및 기본 레이아웃 설정
        private func setupView() {
            self.addSubview(scrollView)
            scrollView.snp.makeConstraints {
                $0.edges.equalTo(self.safeAreaLayoutGuide) // 스크롤 뷰 안전영역 지키기
            }
        }
        
        // 모델의 색상 배열을 사용하여 색상 뷰 설정
        private func setupColorViews() {
            var previousView: UIView? = nil
            
            for color in RainbowColors.colors {
                let colorView = UIView()
                colorView.backgroundColor = color
                scrollView.addSubview(colorView)
                
                colorView.snp.makeConstraints {
                    $0.left.right.equalToSuperview() // 좌우로 스크롤 없이 화면 크기에 맞춤
                    $0.width.equalTo(self.snp.width) // 피그마 디자인
                    $0.height.equalTo(176) // 피그마 디자인 높이
                    
                    
                    if let previousView = previousView {
                        $0.top.equalTo(previousView.snp.bottom) // 이전 뷰의 하단에 배치
                    } else {
                        $0.top.equalToSuperview() // 첫 번째 뷰는 스크롤뷰 상단에 맞춤
                    }
                }
                
                previousView = colorView
            }
            
            // 마지막 뷰의 하단을 스크롤뷰의 하단에 맞춤으로써 스크롤 가능하게 설정
            if let lastView = previousView {
                lastView.snp.makeConstraints {
                    $0.bottom.equalToSuperview()
                }
            }
        }
    }
    ```
    

![[스크린샷_2024-09-30_오후_4.47.43.png]]

### 6. ViewController 작성하기

뷰가 완성되었으니, 뷰를 연결만 하면 됩니다. 아주 간단합니다!!

```Swift
import UIKit
import SnapKit

class ViewController: UIViewController {
    
    override func viewDidLoad() {
        super.viewDidLoad()
        self.view = RainbowView(frame: self.view.bounds)
    }
}
```

### 7. 전체 코드 및 실행 결과 화면

모델 코드, 뷰 코드, 뷰 컨트롤러 코드를 순서대로 보이도록 하겠습니다.

코드의 아래에 최종 결과 사진이랑 영상도 같이 첨부했습니다.

  

- **Model 코드**
    
    ```Swift
    import Foundation
    import UIKit
    
    struct RainbowColors {
        static let colors: [UIColor] = [
            UIColor.red,
            UIColor.orange,
            UIColor.yellow,
            UIColor.green,
            UIColor.blue,
            UIColor(red: 0.294, green: 0, blue: 0.51, alpha: 1), // 남색을 표현한 코드입니다.
            UIColor.purple
        ]
    }
    ```
    
      
    
- **View 코드**
    
    ```Swift
    import UIKit
    import SnapKit
    
    class RainbowView: UIView {
        
        override init(frame: CGRect) {
            super.init(frame: frame)
            setupView()
            setupColorViews()
        }
        
        required init?(coder: NSCoder) {
            fatalError("init(coder:) has not been implemented")
        }
        
        private lazy var scrollView: UIScrollView = {
            let scrollView = UIScrollView()
            scrollView.showsVerticalScrollIndicator = true
            scrollView.showsHorizontalScrollIndicator = false
            return scrollView
        }()
        
        // 스크롤뷰 및 기본 레이아웃 설정
        private func setupView() {
            self.addSubview(scrollView)
            scrollView.snp.makeConstraints {
                $0.edges.equalTo(self.safeAreaLayoutGuide) // 스크롤 뷰 안전영역 지키기
            }
        }
        
        // 모델의 색상 배열을 사용하여 색상 뷰 설정
        private func setupColorViews() {
            var previousView: UIView? = nil
            
            for color in RainbowColors.colors {
                let colorView = UIView()
                colorView.backgroundColor = color
                scrollView.addSubview(colorView)
                
                colorView.snp.makeConstraints {
                    $0.left.right.equalToSuperview() // 좌우로 스크롤 없이 화면 크기에 맞춤
                    $0.width.equalTo(self.snp.width) // 피그마 디자인
                    $0.height.equalTo(176) // 피그마 디자인 높이
                    
                    
                    if let previousView = previousView {
                        $0.top.equalTo(previousView.snp.bottom) // 이전 뷰의 하단에 배치
                    } else {
                        $0.top.equalToSuperview() // 첫 번째 뷰는 스크롤뷰 상단에 맞춤
                    }
                }
                
                previousView = colorView
            }
            
            // 마지막 뷰의 하단을 스크롤뷰의 하단에 맞춤으로써 스크롤 가능하게 설정
            if let lastView = previousView {
                lastView.snp.makeConstraints {
                    $0.bottom.equalToSuperview()
                }
            }
        }
    }
    ```
    
      
    
- **ViewController 코드**
    
    ```Swift
    import UIKit
    import SnapKit
    
    class ViewController: UIViewController {
        
        override func viewDidLoad() {
            super.viewDidLoad()
            self.view = RainbowView(frame: self.view.bounds)
            self.view.backgroundColor = .white
        }
    }
    ```
    
      
    
- **결과 사진 및 영상**

무지개 색 사진입니당!!

![[스크린샷_2024-09-30_오후_4.47.43 1.png]]

스크롤이 진행되는 영상입니당!!

![[Simulator_Screen_Recording_-_iPhone_15_Pro_-_2024-09-30_at_16.51.54.mp4]]

## 💻 5주차 과제

---

> [!important] **화면 구현에 필요한 레이아웃과 리소스는 아래 피그마를 참고해주세요!**
> 
>   
>   
>   
> ==**스크롤 뷰를 이용하여**== 기존에 구현한 홈 탭을 바꿔보도록 하겠습니다.  
> ==**기존의 홈탭 코드에서 새롭게 더 추가하면 됩니다.**==  
> 새로운 홈탭 컨트롤러 만들지 않기!!  
>   
> 
> [https://embed.figma.com/design/47IuhJxc7LFTwOYWtDgTdi/iOS-%EC%9B%8C%ED%81%AC%EB%B6%81?node-id=2063-505&t=GIEnA3aBSrNojaHb-1&embed-host=notion](https://embed.figma.com/design/47IuhJxc7LFTwOYWtDgTdi/iOS-%EC%9B%8C%ED%81%AC%EB%B6%81?node-id=2063-505&t=GIEnA3aBSrNojaHb-1&embed-host=notion)

### 1. 기존의 홈탭 ScrollView 구현

> [!important] **실습 체크리스트**
> 
> - [x] 기존의 홈탭의 컨텐츠들을 UIScrollView 컨테이너에 담을 수 있도록 해주세요!
>     - [x] UIScrollView를 구현합니다.
>     - [x] 기존 홈탭의 컨텐츠들을 UIScrollView 내부로 넣어주세요!

### 2. ScrollView 내부에 컴포넌트 추가

> [!important] **실습 체크리스트**
> 
> - [x] 피그마에 보시면 스크롤로 변경 된 후 하단에 새롭게 구현해야 하는 항목들이 추가됐습니다. 구현해주도록 합니다
>     - [x] 발매 상품 컬렉션 뷰를 사용하여 구현 하도록 합니다
>     - [x] 본격 한파대비! 연말 필수템 모음 뷰를 컬렉션 뷰를 사용하여 구현 하도록 합니다.

### 3. 과제가 완성되었다면 깃허브 링크와 시연 영상을 첨부해주세요!

> [!important] **시연 영상 체크리스트**
> 
> - [x] `AutoLayout`이 잘 적용되어 있음을 확인할 수 있나요?
>     - [x] `iPhone 15 Pro`, `iPhone 13 mini` 시뮬레이터에서 테스트한 내용이 모두 들어가게 영상을 업로드해주세요.
> 
>   
> ==**체크리스트 항목을 모두 만족하는 영상만 업로드**==해주시길 바랍니다.

> **깃허브 링크 임베드**

> [!info] 7th_UMC_iOS/쿠트_김의택 at 쿠트_김의택 · TUK-UMC/7th_UMC_iOS  
> 7th UMC iOS.  
> [https://github.com/TUK-UMC/7th_UMC_iOS/tree/%EC%BF%A0%ED%8A%B8_%EA%B9%80%EC%9D%98%ED%83%9D/%EC%BF%A0%ED%8A%B8_%EA%B9%80%EC%9D%98%ED%83%9D](https://github.com/TUK-UMC/7th_UMC_iOS/tree/%EC%BF%A0%ED%8A%B8_%EA%B9%80%EC%9D%98%ED%83%9D/%EC%BF%A0%ED%8A%B8_%EA%B9%80%EC%9D%98%ED%83%9D)  

> **시연 영상 업로드** ==(영상 개수 제한 X)==

![[Assets/13mini 2.mp4|13mini 2.mp4]]

![[Assets/16pro 2.mp4|16pro 2.mp4]]

## 🤔 5주차 트러블 슈팅

---

### 2024년 11월 9일 오후 6:12 본격 한파대비 사진 안나옴

### 문제 상황

---

- 5주차 과제 - 본격 한파대비 부분 컬렉션 뷰가 뜨지 않는 문제 발생

### 해결 과정

---

- homeView에서 오토레이아웃 문제라고 추측 → scrollView 에서 자리를 차지하는걸로 보아 아닌듯 함
- winterCollectionCellView 의 오토레이아웃 문제라고 추측 → 해결

### 참고 자료

---

## 📌 이번 주차에는 이런 내용을 학습했어요!

---

==워크북을 진행하며 스스로 공부해본 내용을 이곳에 자유 양식으로 정리해 보세요!  
주차마다 하나씩은 작성해주셔야 합니다.  
==

## ❓ 이런 질문이 있어요!

---

워크북을 진행하면서 궁금했던 점 또는 해결하지 못한 부분을 미리 작성하고 스터디에서 함께 논의해 보세요!  
해결하지 못한 질문이나 궁금한 점이 있다면 언제든지 편하게 DM 주세요 🙋‍♀️  

  

---

Copyright © 2024 Lee Youjin All rights reserved.

Copyright © 2024 Jeong Euichan All rights reserved.