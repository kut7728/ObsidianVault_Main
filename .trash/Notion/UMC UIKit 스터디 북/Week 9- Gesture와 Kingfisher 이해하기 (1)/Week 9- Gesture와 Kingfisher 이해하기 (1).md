- [[#📋 학습 목표]]
- [[#✋ 잠깐! 스터디 인증샷 찍으셨나요?]]
- [[#🔥 9주차 개념 설명]]
    - [[#1️⃣ Gesture Recognizers]]
    - [[#2️⃣ Kingfisher]]
- [[#🔥 9주차 개념 점검]]
- [[#📚 9주차 실습]]
    - [[#1. SceneDelegate 설정]]
    - [[#2. 분석]]
    - [[#3. View 작성]]
    - [[#4. ViewController 작성]]
    - [[#5. 실행 결과화면]]
- [[#💻 9주차 과제]]
    - [[#1. 이미지 컬렉션 뷰 수정]]
    - [[#2. 과제가 완성되었다면 깃허브 링크와 시연 영상을 첨부해주세요!]]
- [[#🤔 9주차 트러블 슈팅]]
- [[#📌 이번 주차에는 이런 내용을 학습했어요!]]
- [[#❓ 이런 질문이 있어요!]]

  

## 📋 학습 목표

---

> **Gesture Recognizers**  
>   
> **Kingfisher**  

## ✋ 잠깐! 스터디 인증샷 찍으셨나요?

---

> [!important] 스터디 시작 전 ==**스터디 인증샷을 촬영**==해주세요!
> 
> 스터디는 대면이 원칙이며, 비대면 스터디의 경우에도 최대한 카메라를 킨 후 진행해주세요.
> 
> 아래 임베드 블록에 인증샷을 임베드해 주시면 됩니다 🫶

[](https://www.notion.soundefined)

## 🔥 9주차 개념 설명

---

### 1️⃣ Gesture Recognizers

> Gesture Recognizer는 UIkit에서 제공하는 객체로, 사용자가 화면에서 수행하는 다양한 터치 동작을 감지하고 처리할 수 있도록 해줍니다. 즉, **사용자의 제스처를 인식하여 적절한 동작을 수행할 수 있게 도와주는 도구입니다.** 이 기능은 화면에서 터치, 스와이프, 핀치 등의 동작을 직접 처리하는 데 필요한 복잡한 작업을 단순화합니다.

> Gesture Recognizer를 사용하면 뷰에 특정 제스처를 감지하는 기능을 추가할 수 있고, 각 제스처에 맞는 콜백을 정의하여 특정 동작을 실행할 수 있습니다.  
> UIKit에서는 다양한 제스처를 쉽게 사용할 수 있도록 기본 제공하는 여러 종류의 Gesture Recognizer를 제공합니다.  

> [!info] Gestures | Apple Developer Documentation  
> Define interactions from taps, clicks, and swipes to fine-grained gestures.  
> [https://developer.apple.com/documentation/swiftui/gestures](https://developer.apple.com/documentation/swiftui/gestures)  

  

### UIkit에서는 Gesture Recognizer 종류

- **TapGesture Recognizer**
- **Swipe Gesture Recognizer**
- **Pich Gesture Recognizer**
- **Rotation Gesture Recognizer**
- **Pan Gesture Recognizer**
- **Long Pres Gesture Recognizer**

  

## 😃 TapGesture Recognizer

> Tap Gesture Recognizer는 사용자가 화면을 한 번 또는 여러 번 빠르게 터치할 때 이를 감지합니다. 주로 `버튼 클릭` 이나 `간단한 선택 동작` 을 처리하는 데 사용합니다.

> [!important]
> 
> ### 사용 예시
> 
> 사용자가 이미지를 클릭하면 이미지가 확대되거나 특정 아이템을 선택하는 경우
> 
> ### 설정
> 
> 터치 횟수(단일 탭, 더블 탭)를 설정할 수 있습니다.

```Swift
let tapGesture = UITapGestureRecognizer(target: self, action: \#selector(handleTap))
tapGesture.numberOfTapsRequired = 1 // 단일 탭, 횟수 설정
view.addGestureRecognizer(tapGesture)

@objc func handleTap() {
    print("탭탭")
}
```

![[implement-gesture-in-ios-swift-3.webp]]

## 😃 **Swipe Gesture Recognizer**

> Swipe Gesture Recognizer는 사용자가 화면에서 손가락을 특정 방향으로 스와이프할 때 이를 감지합니다. `좌우 또는 상항 방향 스크롤` , `페이지 전환` 같은 동작에 주로 사용합니다.

> [!important]
> 
> ## 사용 예시
> 
> 화면을 왼쪽으로 스와이프하면 다음 페이지로 이동하는 경우
> 
> ### 설정
> 
> 스와이프할 방향(상, 하, 좌, 우)를 설정할 수 있습니다.

```Swift
let swipeGesture = UISwipeGestureRecognizer(target: self, action: \#selector(handleSwipe))
swipeGesture.direction = .left // 왼쪽으로 스와이프
view.addGestureRecognizer(swipeGesture)

@objc func handleSwipe() {
    print("스와이프")
}
```

![[implement-gesture-in-ios-swift-8.webp]]

## 😃 **Pich Gesture Recognizer**

> Pinch Gesture Recognizer는 사용자가 두 손가락으로 화면을 `확대 또는 축소` 하는 동작을 감지합니다. 주로 이미지나 지도와 같은 객체를 확대 또는 축소할 때 사용됩니다.

> [!important]
> 
> ## 사용 예시
> 
> 사용자가 이미지를 확대하거나 축소하는 경우
> 
> ### 설정
> 
> 손가락 사이의 거리 변화에 따라 확대 또는 축소 비율을 처리합니다.

```Swift
let pinchGesture = UIPinchGestureRecognizer(target: self, action: \#selector(handlePinch))
view.addGestureRecognizer(pinchGesture)

@objc func handlePinch(sender: UIPinchGestureRecognizer) {
    sender.view?.transform = (sender.view?.transform.scaledBy(x: sender.scale, y: sender.scale))!
    sender.scale = 1.0
}
```

![[implement-gesture-in-ios-swift-6.webp]]

## 😃 **Rotation Gesture Recognizer**

> Rotation Gesture Recognizer는 사용자가 두 손가락을 회전하여 `회전 동작`을 감지합니다. 이미지나 도형 등의 객체를 회전하는 UI에서 주로 사용됩니다.

> [!important]
> 
> ## 사용 예시
> 
> 사용자가 이미지를 두 손가락으로 회전하는 경우
> 
> ### 설정
> 
> 손가락 사이의 각도 변화에 따라 회전 각도를 처리합니다.

```Swift
let rotationGesture = UIRotationGestureRecognizer(target: self, action: \#selector(handleRotation))
view.addGestureRecognizer(rotationGesture)

@objc func handleRotation(sender: UIRotationGestureRecognizer) {
    sender.view?.transform = sender.view!.transform.rotated(by: sender.rotation)
    sender.rotation = 0
}
```

![[implement-gesture-in-ios-swift-5.webp]]

## 😃 **Pan Gesture Recognizer**

> Pan Gesture Recognizer는 사용자가 손가락으로 화면에서 객체를 `드래그(이동)`할 때 이를 감지합니다. 객체를 드래그하여 다른 위치로 이동하는 동작을 구현할 때 사용됩니다.

> [!important]
> 
> ## 사용 예시
> 
> 사용자가 화면 상의 이미지를 손가락으로 드래그하여 위치를 이동하는 경우
> 
> ### 설정
> 
> 제스처의 translation 값을 통해 이동한 거리를 계산할 수 있습니다.

```Swift
let panGesture = UIPanGestureRecognizer(target: self, action: \#selector(handlePan))
view.addGestureRecognizer(panGesture)

@objc func handlePan(sender: UIPanGestureRecognizer) {
    let translation = sender.translation(in: view)
    if let gestureView = sender.view {
        gestureView.center = CGPoint(x: gestureView.center.x + translation.x, y: gestureView.center.y + translation.y)
    }
    sender.setTranslation(.zero, in: view)
}
```

![[implement-gesture-in-ios-swift-7.webp]]

## 😃 **Long Pres Gesture Recognizer**

> Long Press Gesture Recognizer는 사용자가 화면을 **길게 누르고 있을 때** 이를 감지합니다. `메뉴 활성화`나 `추가 옵션 제공`과 같은 상호작용을 만들 때 주로 사용됩니다.

> [!important]
> 
> ## 사용 예시
> 
> 사용자가 이미지를 길게 눌러 옵션 메뉴를 띄우는 경우
> 
> ### 설정
> 
> 길게 누를 최소 시간과 터치 강도를 설정할 수 있습니다.

```Swift
let longPressGesture = UILongPressGestureRecognizer(target: self, action: \#selector(handleLongPress))
longPressGesture.minimumPressDuration = 1.0 // 1초 이상 길게 눌러야 작동
view.addGestureRecognizer(longPressGesture)

@objc func handleLongPress(sender: UILongPressGestureRecognizer) {
    if sender.state == .began {
        print("롱프레스")
    }
}
```

![[implement-gesture-in-ios-swift-4.webp]]

  

### 2️⃣ Kingfisher

> 이미지 캐싱은 네트워크를 통해 다운로드한 이미지를 로컬 디바이스에 `임시 저장` 하여, 동일한 이미지에 대한 반복적인 요청을 방지하고 `성능을 최적화` 하는 중요한 기법입니다. 이미지 캐싱을 통해 네트워크 트래픽을 줄이고, 사용자에게 더 빠른 이미지 로딩 경험을 제공할 수 있습니다.

> iOS 애플리케이션에서 이미지를 캐싱하는 다양한 방법이 있습니다. 이 중에서 주로 사용하는 라이브러리 중 하나가 `Kingfisher` 입니다. `Kingfisher` 는 ==**간략하게 이미지 다운로드와 캐싱을 관리할 수 있는 강력한 라이브러리**==로, 네트워크 성능을 최적화하는 데 유용합니다.

> [!info] GitHub - onevcat/Kingfisher: A lightweight, pure-Swift library for downloading and caching images from the web.  
> A lightweight, pure-Swift library for downloading and caching images from the web.  
> [https://github.com/onevcat/Kingfisher](https://github.com/onevcat/Kingfisher)  

> [!important]
> 
> ### 이미지 캐싱의 필요성
> 
> 1. **네트워크 트래픽 감소**
>     1. 동일한 이미지를 여러 번 요청하는 것을 방지하고, 캐시에 저장된 이미지를 불러와 서버 요청을 줄입니다.
> 2. **빠른 로딩 시간**
>     1. 이미지를 로컬 캐시에서 불러오기 때문에 네트워크 대기 시간을 줄이고, 사용자에게 더 빠른 응답을 제공합니다.
> 3. **데이터 사용량 절약**
>     1. 모바일 환경에서 데이터 사용량을 줄여 사용자 경험을 향상시키는 데 도움을 줍니다.
> 4. **성능 최적화**
>     1. 이미지 캐싱은 불필요한 네트워크 호출을 방지하고, 앱의 전반적인 성능을 개선합니다.

## 😃 Kingfisher 주요 기능

### 1. 비동기 이미지 다운로드

Kingfisher는 `setImage` 메서드를 사용하여 이미지 다운로드를 비동기적으로 수행합니다. 즉, 이미지가 다운로드되는 동안 UI가 블록되지 않으며, 사용자는 애플리케이션의 다른 부분을 계속 사용할 수 있습니다.

다운로드가 완료되면 자동으로 `UIImageView`, `UIButton`, `NSImageView` 등 다양한 뷰에 이미지를 설정할 수 있습니다.

### 2. 자동 이미지 캐싱

다운로드가 완료되면 자동으로 `UIImageView`, `UIButton`, `NSImageView` 등 다양한 뷰에 이미지를 설정할 수 있습니다.

메모리 캐시는 앱이 실행되는 동안 이미지를 RAM에 저장하고, 디스크 캐시는 앱을 종료한 후에도 이미지를 디스크에 저장하여 다시 실행할 때 캐시된 이미지를 사용할 수 있도록 합니다.

### 3. 이미지 다운로드 및 캐싱 옵션

Kingfisher는 이미지 다운로드와 캐싱을 제어할 수 있는 다양한 옵션을 제공합니다. 다운로드 시 애니메이션 효과를 줄 수 있으며, 이미지를 원본 크기로 캐싱할지, 크기를 조정해서 캐싱할지 선택할 수 있습니다.

`options` 매개변수를 통해 다양한 옵션을 설정하여 사용자 정의 동작을 구현할 수 있습니다.

### 4. 플러그인 시스템

Kingfisher는 플러그인 시스템을 지원하여 기본적인 기능 외에도 확장 가능한 구조를 제공합니다. 이미지 처리 과정에서 ==**사용자 정의 필터**==나 **다운로드 동작**을 추가할 수 있습니다.

  

##  😙 Kingfisher 주요 사용법

### 1. 이미지 다운로드 및 캐싱

`**imageView.kf.setImage(with:)**`

지정된 URL에서 이미지를 다운로드하고, `UIImageView`에 설정합니다. 이미지가 한 번 다운로드되면, Kingfisher는 이를 캐시에 저장하고, 다음에 같은 URL을 사용할 때는 캐시된 이미지를 사용합니다.

```Swift
import Kingfisher

let imageView = UIImageView()
let url = URL(string: "https://example.com/image.jpg")

imageView.kf.setImage(with: url)
```

### 2. Placeholder 이미지 설정

이미지 다운로드가 완료되기 전까지 보여줄 placeholder 이미지를 설정할 수 있습니다. 이미지 로딩 중 사용자에게 비어 있는 뷰를 보여주는 대신, 임시 이미지를 표시할 수 있어 사용자 경험을 개선합니다.

```Swift
imageView.kf.setImage(
    with: url,
    placeholder: UIImage(named: "placeholderImage")
)
```

### 3. 다운로드 옵션 설정

Kingfisher는 이미지 다운로드 및 캐싱 시 다양한 옵션을 설정할 수 있습니다. 페이드 애니메이션을 적용하거나, 이미지를 특정 크기로 리사이즈할 수 있습니다.

```Swift
imageView.kf.setImage(
    with: url,
    options: [
        .transition(.fade(0.3)),  // 이미지가 로드될 때 0.3초 동안 페이드 애니메이션
        .cacheOriginalImage       // 원본 이미지를 캐시에 저장
    ]
)
```

##  😙 Kingfisher의 캐시 관리

> Kingfisher는 메모리와 디스크 캐시를 자동으로 관리하지만, 사용자가 직접 캐시를 조정하거나 삭제할 수 있는 기능도 제공합니다.

### 1. 캐시 사이즈 제한 설정

Kingfisher는 기본적으로 메모리와 디스크 캐시에 이미지를 저장하지만, 우리가 직접 스스로 캐시 크기를 조정할 수 있습니다. 특정 용량 이상으로 캐시가 커지는 것을 방지할 수 있습니다.

  

```Swift
let cache = ImageCache.default
cache.memoryStorage.config.totalCostLimit = 50 * 1024 * 1024  // 메모리 캐시 50MB 제한
cache.diskStorage.config.sizeLimit = 100 * 1024 * 1024  // 디스크 캐시 100MB 제한
```

  

### 2.캐시 삭제

캐시를 직접 삭제하고 싶을 때 사용합니다.

```Swift
// 메모리 캐시를 비웁니다.
ImageCache.default.clearMemoryCache()

// 디스크 캐시를 비웁니다.
ImageCache.default.clearDiskCache()

// 특정 URL의 이미지를 캐시에서 삭제합니다.
let url = URL(string: "https://example.com/image.jpg")
ImageCache.default.removeImage(forKey: url!.absoluteString)
```

## 🔥 9주차 개념 점검

---

> [!important] Tap Gesture Recognizer와 Swipe Gesture Reconizer의 차이점은 무엇인가요? 각각 어떤 상황에서 사용되면 좋을까요?

- **여기에 답을 적어주세요!**
    
    Tap Gesture는 버튼클릭이나 간단한 선택작용에 Swipe Gesture은 스크롤이나 화면 스와이프등의 동작에 사용
    

> [!important] Pinch Gesture Recognizer와 Rotation Gesture Recognizer를 함께 사용할 때, 두 제스처를 동시에 인식하도록 하려면 어떤 프로토콜을 사용해야 하나요? 이 프로토콜의 역할은 무엇인가요?

- **여기에 답을 적어주세요!**

> [!important] Kingfisher를 사용해 이미지를 다운로드할 때, placeholder 옵션의 역할은 무엇인가요? 이 옵션을 사용하는 이유는 무엇인가요?

- **여기에 답을 적어주세요!**
    
    이미지 로딩이 진행중일때 대신 표시하여 사용자의 사용 경험을 올려주는 역할
    

## 📚 9주차 실습

---

> 실습 내용은 짱구 이미지를 Kingfisher로 불러온 후 로테이션 제스쳐, 핀치 제스쳐, 팬 제스처를 써서 조작할 수 있도록 할 것입니다.

> 아래 피그마 링크에 들어 오셔서 디자인을 확인해주시기 바랍니다.  
> ==**Option 키를 누르고, 프레임 위에 마우스를 올려 확인 하시면서 오토레이아웃 수치를 꼭!! 확인해주시기 바랍니다.**  
>   
> ====또한== ==`SnapKit`====을 적용하여 진행하도록 하겠습니다.==

[https://embed.figma.com/design/47IuhJxc7LFTwOYWtDgTdi/iOS-%EC%9B%8C%ED%81%AC%EB%B6%81?node-id=322-1594&t=TNYnLYCxfoZYM0Nn-1&embed-host=notion&footer=false&theme=system](https://embed.figma.com/design/47IuhJxc7LFTwOYWtDgTdi/iOS-%EC%9B%8C%ED%81%AC%EB%B6%81?node-id=322-1594&t=TNYnLYCxfoZYM0Nn-1&embed-host=notion&footer=false&theme=system)

### 1. SceneDelegate 설정

==**이 부분은 생략하도록 하겠습니다. 설정 방법을 모르시면 1주차 워크북을 다시 참고해주시기 바랍니다!**==

### 2. 분석

가운데에 짱구 사진이 올 수 있도록 합니다.

로테이션 제스처, 핀치 제스처, 팬 제스처를 사용할 것이기 때문에 구현해야 합닏

### 3. View 작성

View 파일에 이미지 뷰 하나를 넣고, 화면의 가운데 오도록 스냅킷을 적용합니다.

==**그 후, 로테이션 제스처, 핀치 제스처, 팬 제스처를 구현합니다.**==

### 4. ViewController 작성

```Swift
//
//  TestView.swift
//  9st
//
//  Created by 정의찬 on 10/14/24.
//

import UIKit
import Kingfisher
import SnapKit

class GestureImageView: UIView {
    
   
    
    override init(frame: CGRect) {
        super.init(frame: frame)
        self.backgroundColor = .white
        setupView()
        constraints()
    }
    
    required init?(coder: NSCoder) {
        super.init(coder: coder)
        setupView()
    }
    
    private lazy var imageView: UIImageView = {
        let imageView = UIImageView()
        imageView.contentMode = .scaleAspectFit
        imageView.isUserInteractionEnabled = true
        return imageView
    }()
    
    // 뷰 설정 및 제스처 인식기 추가
    private func setupView() {
        addSubview(imageView)
        addGestureRecognizers()
    }

    
    private func addGestureRecognizers() {
        // 팬 제스처
        let panGesture = UIPanGestureRecognizer(target: self, action: \#selector(handlePanGesture(_:)))
        imageView.addGestureRecognizer(panGesture)

        // 회전 제스처
        let rotationGesture = UIRotationGestureRecognizer(target: self, action: \#selector(handleRotationGesture(_:)))
        imageView.addGestureRecognizer(rotationGesture)

        // 핀치 제스처
        let pinchGesture = UIPinchGestureRecognizer(target: self, action: \#selector(handlePinchGesture(_:)))
        imageView.addGestureRecognizer(pinchGesture)
    }
    
    public func loadImage(from url: String) {
        if let imageURL = URL(string: url) {
            imageView.kf.setImage(with: imageURL)
        }
    }

    // 팬 제스처 핸들러
    @objc private func handlePanGesture(_ sender: UIPanGestureRecognizer) {
        let translation = sender.translation(in: self)
        if let gestureView = sender.view {
            gestureView.center = CGPoint(x: gestureView.center.x + translation.x, y: gestureView.center.y + translation.y)
        }
        sender.setTranslation(.zero, in: self)
    }

    // 회전 제스처 핸들러
    @objc private func handleRotationGesture(_ sender: UIRotationGestureRecognizer) {
        if let gestureView = sender.view {
            gestureView.transform = gestureView.transform.rotated(by: sender.rotation)
            sender.rotation = 10
        }
    }

    // 핀치 제스처 핸들러
    @objc private func handlePinchGesture(_ sender: UIPinchGestureRecognizer) {
        if let gestureView = sender.view {
            gestureView.transform = gestureView.transform.scaledBy(x: sender.scale, y: sender.scale)
            sender.scale = 1.0
        }
    }
    
    private func constraints() {
        imageView.snp.makeConstraints {
            $0.centerX.centerY.equalToSuperview()
            $0.height.width.equalTo(300)
        }
    }
}
```

뷰 프로퍼티를 생성 후, 짱구 사진의 URL을 구글에서 복사하여 넣도록합니다.

==**시뮬레이터에서 로테이션 혹은 핀치 제스처 단축키는 옵션키를 누른상태에서 하시면 됩니다!!**==

```Swift
//
//  ViewController.swift
//  9st
//
//  Created by 정의찬 on 10/14/24.
//

import UIKit

class ViewController: UIViewController {

    override func viewDidLoad() {
        super.viewDidLoad()
        self.view = gestureView
    }
    
    private lazy var gestureView: GestureImageView = {
        let view = GestureImageView()
        view.loadImage(from: "https://i.namu.wiki/i/gBooaihLmxRO31p6RZ6NMYBBhZpi8AVdf1UZw8QXV2v0yGOdDW5Wxn4RbZKZ05tLD3FPKPzrSVQWtd1tsg2lfufar3zA507i0KHDOAtlp6i12ZGG0wO3q_DyJQIPGMQ41wlRFEG9vrUelOvtdJ2n6g.webp")
        return view
    }()


}
```

### 5. 실행 결과화면

### ==처음 화면==

![[스크린샷_2024-10-14_오후_7.21.19.png]]

### ==로테이션 제스처==

  

![[Simulator_Screen_Recording_-_iPhone_16_Pro_-_2024-10-14_at_19.24.50.mp4]]

### ==핀치 제스처==

![[Simulator_Screen_Recording_-_iPhone_16_Pro_-_2024-10-14_at_19.26.37.mp4]]

  

### ==팬 제스처==

![[Simulator_Screen_Recording_-_iPhone_16_Pro_-_2024-10-14_at_19.27.34.mp4]]

## 💻 9주차 과제

---

> [!important] **화면 구현에 필요한 레이아웃과 리소스는 아래 피그마를 참고해주세요!**
> 
>   
>   
> 
> **메인 화면 상품 물품 이미지 Kingfisher로 사용하기**
> 
> [https://embed.figma.com/design/47IuhJxc7LFTwOYWtDgTdi/iOS-%EC%9B%8C%ED%81%AC%EB%B6%81?node-id=13949-448&t=TNYnLYCxfoZYM0Nn-1&embed-host=notion&footer=false&theme=system](https://embed.figma.com/design/47IuhJxc7LFTwOYWtDgTdi/iOS-%EC%9B%8C%ED%81%AC%EB%B6%81?node-id=13949-448&t=TNYnLYCxfoZYM0Nn-1&embed-host=notion&footer=false&theme=system)

### 1. 이미지 컬렉션 뷰 수정

> [!important] **실습 체크리스트**
> 
> - [ ] Just Dropped, 본격 한파대비! 연말 필수템 모음 컬렉션 뷰의 아이템 개수 각각 10개까지 늘려주세요!
>     - [ ] 구글에서 원하는 사진 찾은 후, 이미지 url을 복사하여 Kingfisher를 통해 컬렉션뷰의 사진이 나올 수 있도록 해주세요
> - [ ] 더미 데이터 모델 수정
>     - [ ] 더미 데이터 클래스의 데이터에서 사진을 처리하는 변수를 url을 담도록 변경 후, 컬렉션에서 이 url값을 Kingfisher를 통해 불러올 수 있도록합니다.

### 2. 과제가 완성되었다면 깃허브 링크와 시연 영상을 첨부해주세요!

> [!important] **시연 영상 체크리스트**
> 
> - [ ] `AutoLayout`이 잘 적용되어 있음을 확인할 수 있나요?
>     - [ ] `iPhone 15 Pro`, `iPhone 13 mini` 시뮬레이터에서 테스트한 내용이 모두 들어가게 영상을 업로드해주세요.
> 
>   
> ==**체크리스트 항목을 모두 만족하는 영상만 업로드**==해주시길 바랍니다.

> **깃허브 링크 임베드**

[](https://www.notion.soundefined)

> **시연 영상 업로드** ==(영상 개수 제한 X)==

[](https://www.notion.soundefined)

## 🤔 9주차 트러블 슈팅

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