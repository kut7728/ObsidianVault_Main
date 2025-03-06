- [[#📋 학습 목표]]
- [[#✋ 잠깐! 스터디 인증샷 찍으셨나요?]]
- [[#🔥 3주차 개념 설명]]
    - [[#1️⃣ UITableView 알기]]
    - [[#2️⃣ Data 전달하기]]
    - [[#3️⃣ UserDefaults 알기]]
- [[#🔥 3주차 개념 점검]]
- [[#📚 3주차 실습]]
    - [[#1️⃣ UserDefaults에 데이터 저장 및 출력]]
    - [[#2️⃣ TableView로 주사위 1~6까지 나타내기]]
- [[#💻 3주차 과제]]
    - [[#1. SAVED 탭 Cell, Model 구]]
    - [[#2. SAVED 탭 TableView 구현]]
    - [[#3. LoginView Model 수정]]
    - [[#4. 마이페이지 뷰 구현]]
    - [[#5. 프로필 관리 뷰 구현]]
    - [[#6. 과제가 완성 되었다면 깃허브 링크와 시연 영상을 첨부해주세요!]]
- [[#🤔 3주차 트러블 슈팅]]
    - [[#@2025년 1월 2일 오후 6:15 문제 이름]]
- [[#📌 이번 주차에는 이런 내용을 학습했어요! ]]
- [[#❓ 이런 질문이 있어요!]]

## 📋 학습 목표

---

> **UITableView 알기**  
>   
> **Data 전달하기**  
>   
> **UserDefaults 알기**  

## ✋ 잠깐! 스터디 인증샷 찍으셨나요?

---

> [!important] 스터디 시작 전 ==**스터디 인증샷을 촬영**==해주세요!
> 
> 스터디는 대면이 원칙이며, 비대면 스터디의 경우에도 최대한 카메라를 킨 후 진행해주세요.
> 
> 아래 임베드 블록에 인증샷을 임베드해 주시면 됩니다 🫶

- 사진
    
    ![[KakaoTalk_Photo_2024-10-23-10-57-25-5.png]]
    

## 🔥 3주차 개념 설명

---

### 1️⃣ UITableView 알기

> **UITableView**는 iOS 앱에서 데이터를 리스트 형태로 보여주기 위한 핵심적인 UI 컴포넌트입니다. iOS 사용자라면 뉴스 앱에서 기사 목록을 스크롤하거나, 연락처 목록을 확인하는 등의 경험을 해본 적이 있을 것입니다. 이 모든 UI는 **UITableView를** 기반으로 동작합니다.

![[스크린샷_2024-09-08_오후_2.56.37.png]]

  

## 🔴 언제 UITableView를 사용하는가?

### ==리스트형 데이터 작성==

많은 데이터를 한 번에 표시하는 대신 스크롤 가능한 리스트로 사용자에게 보여주고 싶을 때 사용합니다.

### ==반복적인 데이터 구조==

동일한 형태의 UI 컴포넌트에 다양한 데이터를 반복적으로 표시할 때 사용합니다.

### ==동적 데이터==

데이터가 동적으로 추가, 삭제, 수정될 수 있고 이러한 변경 사항을 UI에 반영해야 할 때 사용합니다.

  

## 🔴 UITableView의 기본 구조

> UITableView는 여러 개의 섹션과 각 섹션마다 여러 행(셀)을 가질 수 있습니다. 사용자는 이 테이블 뷰를 통해 정보를 보고, 선택하며, 조작할 수 있습니다. UITableView의 구성 요소를 살펴보도록 하겠습니다.

  

### ==셀(Cell)==

가장 기본적인 단위로, ==**각 행에 해당**==합니다. 셀은 텍스트, 이미지, 스위치 등 다양한 형태의 데이터를 포함할 수 있습니다.

![[스크린샷_2024-09-08_오후_3.12.24.png]]

위 사진은 셀의 기본 형태입니다. 실제 앱에서 어떻게 사용되는지 아래 사진과 비교해서 참고하시기 바랍니다.

![[IMG_1D3D57569248-1.jpeg]]

  

### ==섹션(Section)==

관련된 셀들을 그룹화할 수 있는 방법을 제공합니다. 아이폰의 연락처 앱을 들어가면 성의 알파벳 순으로 섹션을 나누어 정렬되어 있습니다. 이렇듯 그룹화하여 나누는 것을 말합니다.

![[스크린샷_2024-09-08_오후_3.33.46.png]]

  

### ==헤더(Header) 및 푸터(Footer)==

각 섹션의 시작과 끝에 추가적인 정보를 표시할 수 있습니다. 예를 들어 섹션 헤더에는 제목을, 섹션 푸터에는 추가 정보나 요약을 넣을 수 있습니다.

![[스크린샷_2024-09-08_오후_3.29.20.png]]

  

UITableView는 정보를 목록 형태로 정리하여 표시할 필요가 있을 때 사용됩니다. 설정 메뉴, 연락처 목록, 이메일의 인박스 등 일상적인 많은 앱에서 **UITableView**를 찾아볼 수 있습니다. 사용자는 스와이프, 탭 등의 직관적인 제스처를 사용하여 UITableView와 상호 작용할 수 있습니다. 또한 사용자가 데이터를 쉽게 탐색하고 필요한 정보를 빠르게 찾을 수 있도록 돕습니다.

  

## 🔴 UITableView 설정 및 구성

> **UITableView**를 설정하고 구성하는 과정은 앱의 요구사항과 개발 환경에 따라 다양하게 진행될 수 있습니다. 코드를 사용하여 기본 **UITableView**를 설정하는 방법 그리고 필수 프로토콜인 `UITableViewDataSource`와 `UITableViewDelegate` 의 기본 구현에 대해 설명하고자 합니다.

> [!important] 실제 테이블 뷰를 작성하는 방법은 개념 설명이 끝나고 실습 단계를 통해 익히게 될 것입니다. 가볍게 아래 코드와 개념을 보면서 코드로 테이블 뷰를 작성하는 방법을 확인하시기 바랍니다.

  

`UITableView` 를 설정 및 구성하는 방법에는 두가지 방법이 있습니다.

  

- ==**기본 Cell을 사용할 때**==

1. **UITableView 인스턴스 생성 및 추가**
2. **DataSource 및 Delegate 설정**
3. **Layout Constraints 설정**
4. **UITableViewDataSource 및 UITableViewDelegate 프로토콜 구현**

  

- ==**커스텀 Cell 구현하여 사용할 때**==

1. **UITableViewCell 서브클래스 생성**
2. **UITableView 인스턴스 생성 및 추가, 커스텀 셀 등록**
3. **DataSource 및 Delegate 설정**
4. **Layout Constraints 설정**
5. **UITableViewDataSource 및 UITableViewDelegate 프로토콜 구현**

  

이렇게 상황에 맞게 순서대로 구현을 하시면 됩니다.

==**커스텀 Cell 구현하여 사용할 때**== 어떻게 코드를 순차적으로 작성하며 완성하는지 배워보도록 합시다.

  

### ==1. UITableViewCell 서브클래스 생성==

새로운 커스텀 Cell 클래스를 `UITableViewCell` 을 상속받아 생성합니다.

```Swift
class CustomTableViewCell: UITableViewCell {

    let customLabel = UILabel()
    
    override init(style: UITableViewCell.CellStyle, reuseIdentifier: String?) {
        super.init(style: style, reuseIdentifier: reuseIdentifier)
        setupViews()
    }
    
    required init?(coder: NSCoder) {
        super.init(coder: coder)
        setupViews()
    }

    func setupViews() {
        // UI 요소를 셀에 추가하고 레이아웃 설정
        contentView.addSubview(customLabel)
        // Auto Layout 또는 frame을 이용한 레이아웃 설정
        
        /*
        상세 코드는 생략하도록 하겠습니다. 
        추후 실습을 통해 배울 수 있도록 아래 실습 단계에서 확인해주세요!
        */
    }
}
```

### ==2.== ==**UITableView 인스턴스 생성 및 추가, 커스텀 셀 등록**==

`UITableView` 인스턴스를 생성하고 뷰 계층에 추가합니다.

- 아래 코드는 `UITableView` 의 인스턴스를 생성하고, 현재 뷰의 서브뷰로 추가합니다.
- `translatesAutoresizingMaskIntoConstraints` 속성을 `false` 로 설정하여 `Auto Layout` 을 사용하겠다는 것을 명시합니다.

```Swift
import UIKit

class ViewController: UIViewController {

  override func viewDidLoad() {
        super.viewDidLoad()
        // 테이블 뷰를 뷰에 추가
        view.addSubview(tableView)
    }

    // UITableView를 lazy로 생성
    private lazy var tableView: UITableView = {
        let tableView = UITableView()
        // 커스텀 셀 등록
        tableView.register(CustomTableViewCell.self, forCellReuseIdentifier: "customCell")
        return tableView
    }()
}
```

  

### ==3. DataSource 및 Delegate 설정==

`UITableView` 의 `dataSource` 와 `delegate` 를 설정하여 뷰 컨트롤러가 이를 처리하도록 합니다.

```Swift
import UIKit

class ViewController: UIViewController {

 override func viewDidLoad() {
        super.viewDidLoad()
        // 테이블 뷰를 뷰에 추가
        view.addSubview(tableView)
    }

    // UITableView를 lazy로 생성
    private lazy var tableView: UITableView = {
        let tableView = UITableView()
        // 커스텀 셀 등록
        tableView.register(CustomTableViewCell.self, forCellReuseIdentifier: "customCell")
        return tableView
        
        // DataSource 및 Delegate 설정
        tableView.dataSource = self
        tableView.delegate = self
    }()
}
```

  

### ==4. Layout Constraints 설정==

> [!important] **SnapKit을 사용하지 않았습니다. SnapKit으로 변경하여 코드를 작성해도 무관합니다.**

코드를 사용하여 `UITableView` 의 위치와 크기를 정의합니다.

- 아래 코드는 `UITableView` 가 부모 뷰의 상단, 하단, 왼쪽, 오른쪽에 꽉 차도록 설정합니다.

```Swift
import UIKit

class ViewController: UIViewController {

  override func viewDidLoad() {
        super.viewDidLoad()
        
        // 테이블 뷰를 뷰에 추가하고 레이아웃 설정
        view.addSubview(tableView)
        setupConstraints()
    }

    // UITableView를 lazy로 생성
    private lazy var tableView: UITableView = {
        let tableView = UITableView()
        // 커스텀 셀 등록
        tableView.register(CustomTableViewCell.self, forCellReuseIdentifier: "customCell")
        return tableView
        
        // DataSoure 및 Delegate 설정
        tableView.dataSource = self
        tableView.delegate = self
        
        // Layout Constraints 지정을 위해 false로 변경
        tableView.translatesAutoresizingMaskIntoConstraints = false
    }()
    
     // Layout Constraints 설정
    private func setupConstraints() {
        NSLayoutConstraint.activate([
            tableView.topAnchor.constraint(equalTo: view.topAnchor),
            tableView.leftAnchor.constraint(equalTo: view.leftAnchor),
            tableView.bottomAnchor.constraint(equalTo: view.bottomAnchor),
            tableView.rightAnchor.constraint(equalTo: view.rightAnchor)
        ])
    }
}
```

  

### ==5. UITableViewDataSource 및 UITableViewDelegate==

> `UITableView` 의 핵심 기능은 `UITableViewDataSource`와 `UITableviewDelegate` 프로토콜을 구현함으로써 활성화됩니다. 이 프로토콜들은 테이블 뷰의 데이터 관리 및 사용자 인터랙션을 처리하는 데 필수적입니다. `UITableViewDataSource` 는 테이블 뷰에 표시될 데이터의 양과 종류를 결정하며 데이터를 적절한 셀에 할당하는 역할을 합니다.  
> 반면,  
> `UITableViewDelegate` 는 셀의 높이, 헤더와 푸터의 렌더링, 셀의 선택과 같은 사용자 인터랙션을 관리합니다.  
> 이 두 프로토콜의 조합을 통해 개발자는 매우 동적이고 반응적인 사용자 인터페이스를 구축할 수 있으며, 이는 iOS 애플리케이션에서 풍부하고 직관적인 사용자 경험을 제공하는 데 기여합니다.  

  

==**❗️ numberOfRowsInSection**==

이 메서드는 각 섹션에 표시할 행의 수를 반환합니다. 여기서 `dataList` 는 테이블 뷰에 표시할 데이터 배열입니다.

```Swift
func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
    return dataList.count
}
```

  

==**❗️ cellForRowAt**==

==**위에 작성했던 커스텀 셀을 재사용 큐에서 가져와 데이터를 설정하는 부분입니다.**==

셀을 재사용 큐에서 가져오거나 새로 생성하여, 해당 데이터의 내용을 셀에 표시합니다.

  

이 코드는 아래 개념 에서 더 자세히 설명하도록 하겠습니다.

```Swift
func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
    let cell = tableView.dequeueReusableCell(withIdentifier: "cell", for: indexPath)
    cell.textLabel?.text = dataList[indexPath.row]
    return cell
}
```

  

==**❗️ didSelectRowAt**==

사용자가 특정 행을 선택했을 때 호출되는 메서드입니다. 선택 효과를 애니메이션과 함께 해제합니다.

```Swift
func tableView(_ tableView: UITableView, didSelectRowAt indexPath: IndexPath) {
    tableView.deselectRow(at: indexPath, animated: true)
}
```

  

여기까지 위 세가지 ==**numberOfRowsInSection, cellForRowAt, didSelectRowAt**====는 UITableViewDataSource, UITableViewDelegate 프로토콜을 상속 받았음으로== ==**꼭!!! 구현 하셔야 하는 필수적인 부분입니다!**==

  

> [!important] `UITableViewDataSource`와 `UITableViewDelegate` 프로토콜을 통해 구현할 수 있는 다양한 메서드들이 있습니다. 아래 사이트를 통해 무엇들이 있고, 언제 어떻게 사용하면 되는지 확인하시면 되겠습니다.

> [!info] UITableViewDataSource | Apple Developer Documentation  
> The methods that an object adopts to manage data and provide cells for a table view.  
> [https://developer.apple.com/documentation/uikit/uitableviewdatasource](https://developer.apple.com/documentation/uikit/uitableviewdatasource)  

> [!info] UITableViewDelegate | Apple Developer Documentation  
> Methods for managing selections, configuring section headers and footers, deleting and reordering cells, and performing other actions in a table view.  
> [https://developer.apple.com/documentation/uikit/uitableviewdelegate](https://developer.apple.com/documentation/uikit/uitableviewdelegate)  

  

`UITableView` 의 기본 설정 및 구성을 마무리하면서, 우리는 이제 테이블 뷰의 외관과 사용자 인터랙션을 개선하는 다음 단계로 넘어가서 새롭게 개념을 익히도록 하겠습니다.

## 🔴 사용자 인터페이스 커스터마이징

> `UITableView` 는 사용자에게 정보를 제공하는 핵심적인 인터페이스 요소입니다. 그러나 단순히 데이터를 표시하는 것 이상으로 `UITableView` 를 통해 강력하고 개인화된 사용자 경험을 제공할 수 있습니다.  
> 셀의 스타일과 레이아웃, 섹션 헤더와 푸터 그리고 다양한 사용자 인터랙션을 커스터마이징 하는 방법을 자세히 설명하도록 하겠습니다.  

### ==1. 셀의 스타일과 레이아웃 커스터마이징==

==**❗️기본 셀 스타일 조정**==

`UITablewVieCell` 은 몇 가지 기본 스타일을 제공합니다. 이 스타일들은 간단한 변경만으로도 다양한 표현이 가능합니다.

```Swift
func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
    let cell = tableView.dequeueReusableCell(withIdentifier: "BasicCell", for: indexPath)
    cell.textLabel?.text = "Main Title"
    cell.detailTextLabel?.text = "Subtitle"
    cell.imageView?.image = UIImage(named: "icon")
    return cell
}
```

  

==**❗️커스텀 셀 디자인**==

자체적으로 `UITableViewCell` 클래스를 생성하여, 더 복잡한 레이아웃을 구현할 수 있습니다.

> [!important] **아래 코드는 예시 코드로, 더 복잡한 레이아웃을 구성하며 커스텀 하는 과정을 실습과정을 통해 익히게 될 것입니다.**

```Swift
class CustomCell: UITableViewCell {
    var titleLabel: UILabel!
    var detailLabel: UILabel!

    override init(style: UITableViewCell.CellStyle, reuseIdentifier: String?) {
        super.init(style: style, reuseIdentifier: reuseIdentifier)
        setupCell()
    }

    required init?(coder aDecoder: NSCoder) {
        super.init(coder: aDecoder)
        setupCell()
    }

    private func setupCell() {
        titleLabel = UILabel()
        detailLabel = UILabel()
        // 뷰 설정과 레이아웃 코드
    }
}
```

  

### ==2. 섹션 헤더와 푸터 커스터마이징==

==**❗️표준 헤더와 푸터**==

표준 헤더와 푸터를 사용하는 경우, `UITableView` 는 기본적인 텍스트 기반의 헤더와 푸터를 제공합니다. 이를 사용하기 위해 `titleForHeaderInSection` 메서드와 `titleForFooterInSection` 메서드를 구현할 수 있습니다.

표준 헤더와 푸터를 작성하는 방법은 커스터마이징이 제한적이지만, 간단한 텍스트 정보를 섹션의 시작과 끝에 표시하기 위해 빠르고 쉽게 사용할 수 있습니다.

```Swift
import UIKit

class ViewController: UIViewController, UITableViewDelegate, UITableViewDataSource {
    var tableView: UITableView!
    let sectionTitles = ["Section 1", "Section 2", "Section 3"]

    override func viewDidLoad() {
        super.viewDidLoad()
        tableView = UITableView(frame: self.view.bounds, style: .grouped)
        tableView.delegate = self
        tableView.dataSource = self
        self.view.addSubview(tableView)
    }

    func numberOfSections(in tableView: UITableView) -> Int {
        return sectionTitles.count
    }

    func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
        return 5
    }

    func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
        let cell = tableView.dequeueReusableCell(withIdentifier: "cell") ?? UITableViewCell(style: .default, reuseIdentifier: "cell")
        cell.textLabel?.text = "Row \(indexPath.row)"
        return cell
    }

    // 헤더 작성
    func tableView(_ tableView: UITableView, titleForHeaderInSection section: Int) -> String? {
        return sectionTitles[section]
    }

    // 푸터 작성
    func tableView(_ tableView: UITableView, titleForFooterInSection section: Int) -> String? {
        return "푸터 \(sectionTitles[section])"
    }
}
```

  

==**❗️헤더와 푸터 뷰 커스텀 구현**==

표준 헤더/푸터 대신에 커스텀 뷰를 사용하여 섹션의 시작과 끝을 더 돋보이게 할 수 있다.

```Swift
func tableView(_ tableView: UITableView, viewForHeaderInSection section: Int) -> UIView? {
    let header = CustomHeaderView()
    header.titleLabel.text = "Section \(section)"
    return header
}
```

  

==**❗️헤더와 푸터 높이 조정**==

헤더와 푸터 높이를 동적으로 설정하여, 더 많은 정보를 표시하거나 시각적으로 눈에 띄게 할 수 있습니다.

```Swift
func tableView(_ tableView: UITableView, heightForHeaderInSection section: Int) -> CGFloat {
    return 70.0 // 적절한 높이 설정
}
```

  

위 과정을 통해 `UITableView` 의 사용자 인터페이스를 커스터마이징하는 방법을 살펴보았습니다. 성능 최적화와 인터랙티브 액션 추가는 `UITableView` 를 더욱 동적이고 사용자 친화적으로 만드는 중요한 부분입니다.

  

### ==3. 스크롤 최적화==

> 스크롤 성능의 최적화는 사용자가 매끄럽게 정보를 탐색할 수 있도록 도와줍니다. 예를 들어, 셀 안에 이미지가 포함되어 있다는 가정하에, 이미지를 로딩할 때 비동기 처리를 하거나 셀이 화면에 보이기 직전에 필요한 데이터를 로딩하는 것은 애플리케이션의 반응성을 크게 향상 시킵니다.
> 
> 이러한 최적화는 대량의 데이터를 스크롤할 때 발생할 수 있는 지연을 줄이고 전반적인 사용자 경험을 개선합니다.

  

==**❗️데이터 프리패칭**==

`UITableView` 와 `UICollectionView` 에 데이터 프리패칭 기능이 있습니다. 이를 활용하면 화면에 보이기 전에 데이터를 미리 로드할 수 있어 스크롤 시 지연을 줄일 수 있습니다.

`UITableViewDataSourcePrefetching` 프로토콜의 `prefetchRowAt` 메서드를 사용하여, 사용자가 스크롤하여 해당 셀이 보일 것으로 예상되는 시점에 미리 데이터를 로드합니다.

데이터 로딩 로직은 일반적으로 네트워크 요청, 데이터베이스 조회, 파일 시스템 접근 등을 포함할 수 있습니다. 여러분들이 작성하는 목적에 맞추어 알맞게 사용하면 됩니다.

이 방법을 통해 스크롤 성능을 최적화 함으로써 사용자 경험을 크게 개선할 수 있습니다.

  

아래 코드는 비동기적으로 네트워크에서 이미지 데이터를 미리 로드하고 캐시하는 코드입니다.

```Swift
import UIKit

class ViewController: UIViewController, UITableViewDataSource, UITableViewDelegate, UITableViewDataSourcePrefetching {
    var tableView: UITableView!
    var images: [UIImage?] = []
    
    // 아래 이미지 URL은 예시로 작성한 것입니다.
    var imageUrls: [URL] = [URL(string: "https://xxxxx/image1.jpg")!, URL(string: "https://xxxxx/image2.jpg")!, URL(string: "https://xxxxx/image3.jpg")!]
    
    override func viewDidLoad() {
        super.viewDidLoad()
        tableView = UITableView(frame: self.view.bounds)
        
        tableView.dataSource = self
        tableView.delegate = self
        tableView.prefetchDataSource = self
        
        tableView.register(UITableViewCell.self, forCellReuseIdentifier: "cell")
        view.addSubview(tableView)
        images = Array(repeating: nil, count: imageUrls.count)
    }

    func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
        return imageUrls.count
    }

    func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
        let cell = tableView.dequeueReusableCell(withIdentifier: "cell", for: indexPath)
        cell.imageView?.image = images[indexPath.row] ?? UIImage(named: "placeholder") // Use a placeholder image
        return cell
    }

    // 데이터 프리페칭 메소드
    func tableView(_ tableView: UITableView, prefetchRowsAt indexPaths: [IndexPath]) {
        for indexPath in indexPaths {
            preloadDataForItem(at: indexPath.row)
        }
    }
    
		// 이미지 데이터 로딩 로직
    func preloadDataForItem(at index: Int) {
        let url = imageUrls[index]
        let task = URLSession.shared.dataTask(with: url) { data, response, error in
            guard let data = data, error == nil, let image = UIImage(data: data) else {
                return
            }
            DispatchQueue.main.async {
                self.images[index] = image
                let indexPath = IndexPath(row: index, section: 0)
                if self.tableView.indexPathsForVisibleRows?.contains(indexPath) ?? false {
                    self.tableView.reloadRows(at: [indexPath], with: .fade)
                }
            }
        }
        task.resume()
    }
}
```

  

==**위 코드의 작동 방식을 한 번 살펴볼까요??**==

### 1. 데이터 프리패칭 메소드

`tableView(_:prefetchRowsAt:)` 메서드는 `UITableView`가 특정 셀들을 화면에 표시하기 전에 호출됩니다. 이 메서드는 테이블 뷰가 곧 표시할 셀들의 위치(`indexPaths`)를 알려줍니다. 이 위치 정보를 사용하여 필요한 데이터를 미리 로드합니다.

```Swift
func tableView(_ tableView: UITableView, prefetchRowsAt indexPaths: [IndexPath]) {
    for indexPath in indexPaths {
        preloadDataForItem(at: indexPath.row)
    }
}
```

  

### 2. 이미지 데이터 로딩 로직

`preloadDataForItem(at:)` 메서드는 주어진 인덱스에 해당하는 이미지 URL에서 이미지 데이터를 비동기적으로 로드합니다.

```Swift
func preloadDataForItem(at index: Int) {
    let url = imageUrls[index]
    let task = URLSession.shared.dataTask(with: url) { data, response, error in
        guard let data = data, error == nil, let image = UIImage(data: data) else {
            return
        }
        DispatchQueue.main.async {
            self.images[index] = image
            let indexPath = IndexPath(row: index, section: 0)
            if self.tableView.indexPathsForVisibleRows?.contains(indexPath) ?? false {
                self.tableView.reloadRows(at: [indexPath], with: .fade)
            }
        }
    }
    task.resume()
}
```

- **비동기 요청**
    - `URLSession.shared.dataTask` 를 사용하여 네트워크에서 이미지 데이터를 비동기적으로 요청합니다. 이는 네트워크 지연이 UI를 차단하지 않도록 메인 스레드가 아닌 백그라운드 스레드에서 실행됩니다.
- **이미지 로드**
    - 로드가 완료되면, 응답 데이터를 `UIImage` 로 변환합니다.
- **메인 스레드로의 동기화**
    - 이미지가 성공적으로 로드되면, `DispatchQueue.main.async` 를 통해 메인 스레드로 돌아와 `images` 배열에 이미지를 저장합니다.

  

### 3. UI 업데이트

이미지가 메인 스레드에서 배열에 저장된 후, 해당 이미지가 화면에 보이는지 확인합니다. 이미 화면에 보이는 경우, `reloadRows(at: with:)` 메서드를 사용하여 해당 셀을 업데이트하여 사용자에게 새로 로드된 이미지를 보여줍니다.

위 코드를 살피면 `tableView.indexPathsForVisibleRows?.contains(indexPath) ?? false` 이 부분은 해당 셀이 현재 보이는 상태인지 확인하고, 보이는 경우에만 해당 셀을 업데이트 합니다.

  

> 데이터의 프리패칭은 스크롤 중 발생할 수 있는 끊김 현상을 줄이고, 반응성을 유지하는 데 큰 도움이 됩니다. 이 기술을 통해 사용자가 매끄럽게 정보를 탐색할 수 있도록 도와주며, 스와이프로 삭제, 편집 모드 진입, 셀 드래그 앤 드롭과 같은 인터랙팁 액션을 추가함으로써 테이블 뷰와의 상호작용을 더 직관적이고 효율적으로 만들 수 있습니다. 이러한 ==**주제들을 깊게 다루지는 않겠지만 향후 필요한 상황이 있을 때 이 기법들을 참고하여 사용자에게 매력적이고 반응적이며 효율적인 인터페이스를 제공할 수 있도록 제공할 수 있도록 도움이 되기를 바랍니다.**==

  

이렇게 해서 스크롤 최적화의 설명은 끝이 났습니다.

  

마지막으로, 이제 재사용 가능한 ==**셀을 통한 메모리 관리**== 대해 살펴보도록 하겠습니다.

  

## 🔴 셀을 통한 메모리 관리(중요!)

> `UITableView`는 셀 재사용 메커니즘을 사용하여 메모리 사용을 최적화합니다.  
>   
> `dequeueReusableCell(withIdentifier:)` 메소드를 사용하여 화면에 보이는 셀만 메모리에 유지하고, 스크롤되어 화면 밖으로 사라진 셀은 재사용 큐에 추가해 필요할 때 다시 사용할 수 있도록 합니다.

위의 개념설명을 차근차근 보고 왔다면 아래의 코드가 계속해서 등장하고 있다는 것을 파악했을 겁니다.

```Swift
func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
    let cell = tableView.dequeueReusableCell(withIdentifier: "cellIdentifier", for: indexPath)
    cell.textLabel?.text = "Item \(indexPath.row)"
    return cell
}
```

  

간단하게 이 코드를 설명해보고자 합니다.

1. **함수 선언**
    1. `tableView(_:cellForRowAt:)`
        1. 이 메서드는 `UITableViewDataSource` 프로토콜의 일부로서, 각 테이블 뷰의 행(row)에 대한 셀을 요청할 때마다 호출됩니다. 이 메서드는 특정 위치(`indexPath`)에 대한 셀을 구성하고 반환하는 데 사용됩니다.
2. **셀 재사용**
    1. `dequeueReusableCell(withIdentifier:for:)`
        1. 이 함수는 테이블 뷰의 재사용 가능한 셀 풀에서 식별자(`identifier`)에 해당하는 셀을 찾아 재사용하거나 새로운 셀을 생성합니다. 여기서 "cellIdentifier"는 스토리보드 또는 코드에서 미리 정의된 셀의 식별자입니다. 이 메커니즘은 메모리 사용을 최적화하고 성능을 향상시키기 위해 중요합니다.
3. **셀 내용 설정**
    1. `cell.textLabel?.text = "Item \(indexPath.row)"` 
        1. `UITableViewCell`의 `textLabel` 속성에 접근하여 텍스트를 설정합니다. 여기서 `indexPath.row`는 현재 셀이 위치한 행 번호를 나타내며, 이를 사용해 각 행의 고유한 텍스트를 설정합니다. 예를 들어, 첫 번째 행의 경우 "Item 0"이라는 텍스트가 설정됩니다.
4. **셀 반환**
    1. `return cell`
        1. 설정이 완료된 셀을 테이블 뷰에 반환합니다. 이 셀은 테이블 뷰에 의해 요청된 위치에 표시됩니다.

  

  

  

`UITableView` 에 대한 기본 설정, 구성, 성능 최적화에 대한 다양한 측면을 자세히 살펴 보았습니다. 이를 통해 `UITableView` 의 기능과 사용 방법에 대한 풍부한 이해를 얻었기를 바랍니다.

  

다음 단계로, 데이터 전달 기법을 깊게 다룰 예정입니다. 사용자가 선택한 데이터를 다른 뷰 컨트롤러로 전달하는 방법과 같은, 데이터 흐름을 관리하는 기술들을 더욱 깊게 다룰 것입니다.

==**애플리케이션의 다양한 구성 요소가 서로 정보를 공유하고 반응하게 하는 데 필수적인 부분이므로, 이에 대한 이해를 높이는 것이 중요합니다.**==

### 2️⃣ Data 전달하기

iOS 앱 개발에서 데이터 전달은 매우 중요한 역할을 합니다. 앱을 사용하면서 화면 간의 전환이 이루어질 때, 한 화면에서 다른 화면으로 데이터를 넘기는 것은 필수적인 과정입니다.

만약 로그인 화면에서 입력된 사용자 정보를 다음 화면으로 전달하거나, 사용자 설정을 저장하여 이후에 그 데이터를 다른 화면에서 활용하는 등 다양한 시나리오에서 데이터 전달이 필요합니다.

  

데이터를 올바르게 전달하는 것은 **사용자 경험의 일관성**을 유지하고, 앱의 **기능성을 확장**하는 데 중요한 요소입니다. 잘못된 데이터 전달은 화면 전환 후에도 데이터가 올바르게 반영되지 않거나, 데이터 손실 또는 예기치 않은 오류를 유발할 수 있습니다. 따라서 데이터 전달은 앱의 안정성과 사용자 만족도를 높이는 데 매우 중요한 요소입니다!

  

코드로 작성된 뷰간에 데이터를 전달하는 다양한 방법을 학습해보도록 하겠습니다. 또한, 화면 전환 시 데이터를 전달할 수 있는 다양한 패턴과 방법들을 학습해보도록 하겠습니다.

  

세 가지 방법을 중심으로 살펴 보도록 하겠습니다.

1. **직접 할당을 통한 데이터 전달**
2. **델리게이트 패턴을 통한 데이터 전달**
3. **클로저를 통한 데이터 전달**

  

각각의 방법을 단계별로 알아보도록 하겠습니다.

## 🔴 직접 할당을 통한 데이터 전달

> 가장 간단한 방법으로, 뷰 컨트롤러 간에 변수를 직접 할당하여 데이터를 전달합니다.  
> ==**하나의 뷰 컨트롤러**==에서 ==**다른 뷰 컨트롤러의 변수를 직접 수정**==하는 방식입니다.  
> 화면 전환을 하면서 데이터를 전달할 때 이 방식이 유용합니다.  

이 방법은 **직접적인 참조**를 사용해 데이터를 전달합니다. 하나의 뷰 컨트롤러가 다른 뷰 컨트롤러의 인스턴스를 생성한 후, 그 인스턴스의 속성에 데이터를 할당하는 방식입니다. 화면 간의 데이터가 한 방향으로만 이동하고, 데이터 전달이 간단한 경우에 적합합니다.

### 사용 순서

1. 데이터를 전달할 ==**목적지 뷰 컨트롤러**==에서 ==**public 변수를 선언**==합니다.
2. 데이터를 전달하는 ==**출발 뷰 컨트롤러**==에서 ==목적지 뷰 컨트롤러를 생성==하고, 해당 변수에 데이터를 할당합니다.
3. 화면 전환을 통해 목적지 뷰 컨트롤러에 도착한 후, 전달된 데이터를 사용합니다.

  

그럼 위 사용 순서에 맞춰 코드를 작성해서 실제 구현을 해보도록 하겠습니다.

  

==**만약 아래 코드를 작성해서 실행해 보고 싶으시면, SceneDelegate의 코드를 아래 코드 처럼 변경하면 됩니다.**==

```Swift
func scene(_ scene: UIScene, willConnectTo session: UISceneSession, options connectionOptions: UIScene.ConnectionOptions) {
        guard let windows = (scene as? UIWindowScene) else { return }
        window = UIWindow(frame: windows.coordinateSpace.bounds)
        window?.windowScene = windows
        window?.rootViewController = UINavigationController(rootViewController: FirstViewController())
        window?.makeKeyAndVisible()
    }
```

  

아래 코드는 **첫 번째 화면 (출발 뷰 컨트롤러)입니다. 텍스트를 입력하여 두 번째 화면(목적지 뷰 컨트롤러)**로 전달하는 코드입니다.

```Swift
//
//  FIrstViewController.swift
//  MVCExample_1st
//
//  Created by 정의찬 on 9/9/24.
//

import UIKit

class FirstViewController: UIViewController {
    
    private lazy var textField: UITextField = {
        let textField = UITextField()
        textField.borderStyle = .roundedRect
        textField.placeholder = "텍스트를 입력해주세요"
        textField.translatesAutoresizingMaskIntoConstraints = false
        return textField
    }()
    
    private lazy var button: UIButton = {
        let btn = UIButton(type: .system)
        btn.setTitle("두 번째 화면으로 넘어가기", for: .normal)
        btn.translatesAutoresizingMaskIntoConstraints = false
        return btn
    }()
    
    
    override func viewDidLoad() {
        super.viewDidLoad()
        view.backgroundColor = .white
        setupView()
    }
    
    func setupView() {
        self.view.addSubview(textField)
        self.view.addSubview(button)
        
        NSLayoutConstraint.activate([
            textField.centerXAnchor.constraint(equalTo: view.centerXAnchor),
            textField.centerYAnchor.constraint(equalTo: view.centerYAnchor),
            
            button.topAnchor.constraint(equalTo: textField.bottomAnchor, constant: 20),
            button.centerXAnchor.constraint(equalTo: view.centerXAnchor)
        ])
        
        button.addTarget(self, action: \#selector(didTapButton), for: .touchUpInside)
    }
    
    @objc func didTapButton() {
            // SecondViewController 인스턴스를 생성
            let secondVC = SecondViewController()
            
            // 사용자가 입력한 텍스트를 SecondViewController의 변수에 전달
            secondVC.receivedData = textField.text
            
            // 화면 전환
            navigationController?.pushViewController(secondVC, animated: true)
        }
}
```

  

아래 코드는 두 번째 화면(목적지 뷰 컨트롤러)입니다.

```Swift
class SecondViewController: UIViewController {
    
    // 데이터를 받을 public 변수 선언
    public var receivedData: String?

    // UI 요소 생성
    private lazy var label: UILabel = {
        let label = UILabel()
        label.translatesAutoresizingMaskIntoConstraints = false
        return label
    }()
    
    override func viewDidLoad() {
        super.viewDidLoad()
        view.backgroundColor = .white
        setupLabel()
        
        // 전달받은 데이터를 레이블에 표시
        if let data = receivedData {
            label.text = data
        }
    }
    
    func setupLabel() {
        view.addSubview(label)
        NSLayoutConstraint.activate([
            label.centerXAnchor.constraint(equalTo: view.centerXAnchor),
            label.centerYAnchor.constraint(equalTo: view.centerYAnchor)
        ])
    }
}
```

  

### 코드 분석

- **FirstViewController**
    - 사용자가 텍스트 필드에 입력한 데이터를 두 번째 화면으로 전달합니다.
    - 버튼을 눌렀을 때 `SecondViewController` 의 인스턴스르 생성하고, 그 인스턴스의 `receivedData` 변수에 텍스트 필드의 값을 할당한 후 `pushViewController` 를 통해 화면을 전환합니다.
- **SecondViewController**
    - 데이터를 받을 준비를 하고 있습니다.
    - `receivedData` 라는 public 변수를 선언하여 외부에서 데이터를 전달받습니다. `viewDidLoad()` 메서드에서 이 데이터를 사용해 레이블에 표시합니다.

  

### 결과 화면

==**FirstViewController**==

![[스크린샷_2024-09-09_오후_8.13.02.png]]

  

==**SecondViewController**==

![[스크린샷_2024-09-09_오후_8.13.07.png]]

### 장점

==**코드가 매우 직관적이며, 간단한 경우에는 최소한의 코드로 데이터를 전달할 수 있습니다.**== 또한 복잡한 패턴이나 추가적인 구조가 필요 없기 때문에 데이터를 쉽게 전달할 수 있습니다.

### 단점

==**직접 할당 방식은 단방향으로 데이터를 전달하는 데 적합**==합니다. 하지만 데이터를 역방향으로 전달하거나, 데이터 전달을 다수의 화면 간에 해야 할 경우에는 복잡해집니다.

또한, ==**화면 간에 강하게 결합되어 있기 때문에, 뷰 컨트롤러 간의 의존성이 높아집니다.**== 이는 코드의 재사용성을 떨어뜨릴 수 있습니다.

  

> [!important] **직접 할당을 통한 데이터 전달은 iOS 앱에서 가장 단순하면서도 직관적인 데이터 전달 방식입니다. 이 방법은 두 개의 뷰 컨트롤러 간 데이터 이동이 간단하고 한 방향으로만 이루어질 때 매우 유용합니다. 복잡한 데이터 전달이나 양방향 데이터 전달이 필요한 경우에는 더 구조화된 방법을 선택하는 것이 좋습니다.**

## 🔴 델리게이트 패턴을 통한 데이터 전달

> 두 뷰 컨트롤러 간의 데이터를 역방향으로 전달할 때 유용한 패턴입니다. 프로토콜을 사용하여 데이터 전달 책임을 다른 객체에 위임합니다.

이 방법은 두 뷰 컨트롤러 간에 ==**역방향으로 데이터를 전달**==할 떄 자주 사용되는 디자인 패턴입니다. 이 패턴은 뷰 컨트롤러 A에서 뷰 컨트롤러 B로 이동한 후, 뷰 컨트롤러 B에서 발생한 데이터를 다시 A로 전달하고자 할 때 유용합니다. 이를 위해 ==**프로토콜**==을 사용하여 데이터 전달의 책임을 다른 객체(이전 화면에 해당하는 뷰 컨트롤러)에게 위임합니다.

  

**그럼 언제 주로 사용하는가?**

1. 사용자 인터페이스에서 발생한 이벤트를 상위 뷰 컨트롤러에 전달하고자 할 때
2. 화면을 전환한 후, 이전 화면으로 데이터를 다시 전달할 필요가 있을 때

  

### 사용 순서

1. **프로토콜 선언**
2. **델리게이트 선언**
3. **프로토콜 메서드 호출**

  

그럼 위 사용 순서에 맞춰 코드를 작성해서 실제 구현을 해보도록 하겠습니다.

  

==**만약 아래 코드를 작성해서 실행해 보고 싶으시면, SceneDelegate의 코드를 아래 코드 처럼 변경하면 됩니다.**==

```Swift
func scene(_ scene: UIScene, willConnectTo session: UISceneSession, options connectionOptions: UIScene.ConnectionOptions) {
        guard let windows = (scene as? UIWindowScene) else { return }
        window = UIWindow(frame: windows.coordinateSpace.bounds)
        window?.windowScene = windows
        window?.rootViewController = UINavigationController(rootViewController: FirstViewController())
        window?.makeKeyAndVisible()
    }
```

  

먼저, 데이터를 전달할 책임을 명시하는 **프로토콜**을 선언합니다.

아래 새롭게 정의한 프로토콜을 채택하는 객체는 반드시 `sendData` 메서드를 구현해야 합니다.

```Swift
protocol DataSendingDelegate: AnyObject {
    func sendData(_ data: String)
}
```

  

**FirstViewController에서 프로토콜을 채택하고, 델리게이트 설정합니다.**

이제 첫 번째 뷰 컨트롤러에서 이 프로토콜을 **채택**하고, 두 번째 뷰 컨트롤러가 데이터를 전달할 때 그 데이터를 받을 준비를 합니다.

```Swift
class FirstViewController: UIViewController, DataSendingDelegate {
    
    // UI 요소들 선언
    private lazy var label: UILabel = {
        let label = UILabel()
        label.translatesAutoresizingMaskIntoConstraints = false
        label.text = "전달된 데이터 없음"
        return label
    }()
    
    private lazy var button: UIButton = {
        let button = UIButton(type: .system)
        button.setTitle("두 번째 화면으로", for: .normal)
        button.translatesAutoresizingMaskIntoConstraints = false
        return button
    }()
    
    override func viewDidLoad() {
        super.viewDidLoad()
        view.backgroundColor = .white
        setupViews()
    }
    
    func setupViews() {
        view.addSubview(label)
        view.addSubview(button)
        
        NSLayoutConstraint.activate([
            label.centerXAnchor.constraint(equalTo: view.centerXAnchor),
            label.centerYAnchor.constraint(equalTo: view.centerYAnchor),
            
            button.topAnchor.constraint(equalTo: label.bottomAnchor, constant: 20),
            button.centerXAnchor.constraint(equalTo: view.centerXAnchor)
        ])
        
        // 버튼 클릭 시 두 번째 화면으로 전환
        button.addTarget(self, action: \#selector(didTapButton), for: .touchUpInside)
    }
    
    @objc func didTapButton() {
        let secondVC = SecondViewController()
        secondVC.delegate = self  // 델리게이트를 자신(FirstViewController)으로 설정
        navigationController?.pushViewController(secondVC, animated: true)
    }
    
    // 프로토콜 메서드 구현 - 데이터를 받을 준비
    func sendData(_ data: String) {
        label.text = data
    }
}
```

  

  

**SecondViewController에서 데이터 전달합니다.**

두 번째 뷰 컨트롤러에서는 사용자가 입력한 데이터를 델리게이트를 통해 첫 번째 뷰 컨트롤러로 전달합니다.

```Swift
class SecondViewController: UIViewController {
    
    // 델리게이트를 위한 weak 변수 선언 (메모리 누수 방지)
    weak var delegate: DataSendingDelegate?
    
    // UI 요소들 선언
    private lazy var textField: UITextField = {
        let textField = UITextField()
        textField.borderStyle = .roundedRect
        textField.placeholder = "데이터를 입력해주세요"
        textField.translatesAutoresizingMaskIntoConstraints = false
        return textField
    }()
    
    private lazy var button: UIButton = {
        let button = UIButton(type: .system)
        button.setTitle("데이터 보내기", for: .normal)
        button.translatesAutoresizingMaskIntoConstraints = false
        return button
    }()
    
    override func viewDidLoad() {
        super.viewDidLoad()
        view.backgroundColor = .white
        setupViews()
    }
    
    func setupViews() {
        view.addSubview(textField)
        view.addSubview(button)
        
        NSLayoutConstraint.activate([
            textField.centerXAnchor.constraint(equalTo: view.centerXAnchor),
            textField.centerYAnchor.constraint(equalTo: view.centerYAnchor),
            
            button.topAnchor.constraint(equalTo: textField.bottomAnchor, constant: 20),
            button.centerXAnchor.constraint(equalTo: view.centerXAnchor)
        ])
        
        // 버튼 클릭 시 데이터를 전달
        button.addTarget(self, action: \#selector(didTapButton), for: .touchUpInside)
    }
    
    @objc func didTapButton() {
        // 델리게이트를 통해 데이터 전달 후 이전 화면으로 돌아감
        if let data = textField.text {
            delegate?.sendData(data)
            navigationController?.popViewController(animated: true)
        }
    }
}
```

  

### 코드 분석

- **프로토콜 선언**
    - 데이터를 전달하는 역할을 명시하기 위해 `DataSendingDelegate` 라는 프로토콜을 정의합니다.
- **FirstViewController**
    - 델리게이트를 채택하고 데이터를 전달 받을 준비를 합니다. 두 번째 화면으로 이동할 때 자신을 델리게이트로 설정하여, 두 번째 화면에서 데이터를 전달받을 수 있도록 합니다.
- **SecondViewController**
    - 텍스트 필드에 입력된 데이터를 델리게이트를 통해 첫 번째 뷰 컨트롤러로 전달합니다.

  

### 결과 화면

==**전달 받기 전 첫 번째 화면**==

![[스크린샷_2024-09-09_오후_8.39.57.png]]

==**두 번째 화면**==

![[스크린샷_2024-09-09_오후_8.40.07.png]]

  

==**전달 받은 후 첫 번째 화면**==

![[스크린샷_2024-09-09_오후_8.40.09.png]]

### 장점

두 번째 화면에서 데이터를 수정한 후 첫 번째 화면으로 데이터를 전달할 수 있습니다.

또한 뷰 컨트롤러 간의 의존성을 줄이고, 델리게이트를 통해 다양한 객체에 데이터를 전달할 수 있습니다.

  

### 단점

델리게이트를 설정하고, 프로토콜을 정의하는 과정이 추가되기 때문에 코드가 약간 복잡해질 수 있습니다.

  

> [!important] ==**델리게이트 패턴**==은 뷰 컨트롤러 간의 데이터 전달에서 역방향으로 데이터를 전달하는 경우 매우 유용합니다. 특히, 두 번째 화면에서 데이터를 수정한 후 다시 첫 번째 화면에 그 데이터를 전달하고자 할 때 효과적입니다. 델리게이트 패턴은 ==**유연하고 재사용성이 높은 구조**==를 제공하며, 앱의 다양한 화면 간 데이터 전달을 효율적으로 처리할 수 있게 해줍니다.

  

## 🔴 클로저를 통한 데이터 전달

> 간결하고 직관적인 방식으로, 클로저를 사용해 데이터를 전달합니다. 특히 비동기 작업이나 단방향 데이터 흐름에서 유용합니다.

==**클로저는 코드 블록을 변수처럼 사용하여 다른 함수나 메서드의 인자로 전달할 수 있으며, 데이터를 주고받는 역할을 간단하고 효율적으로 처리할 수 있습니다.**==

클로저를 사용하면 뷰 컨트롤러 간의 데이터 전달이 매우 직관적이고 간단해집니다. 이 방식은 델리게이트 패턴보다 코드의 양이 적고, 특정 상황에서 더 명확하게 사용할 수 있습니다.

  

문법 워크북에서 클로저에 대해 배우게 될겁니다. 그래서 간단히 개념만 설명하도록 하겠습니다.

> [!important] 클로저는 익명 함수로, 데이터 전달하거나 연산을 처리한 후, 다른 함수 또는 메서드의 호출이 끝난 후에도 그 연산 결과를 사용할 수 있도록 설계된 구조입니다. Swift에서는 클로저는 **일급 시민**으로 변수에 저장하거나 함수의 매개변수로 전달될 수 있으며, 함수에서 값을 반환할 수 있습니다.

  

데이터 전달과 관련하여 클로저를 사용하면 ==**한 화면에서 다른 화면으로 데이터를 전달할 때**====,== ==**네트워크 호출**==**이나** ==**이벤트가 완료된 후 데이터를 전달할 때**== 유용합니다.

  

클로저의 기본 형태는 아래와 같은 형태를 가지고 있습니다.

```Swift
{ (매개변수 목록) -> 반환형 in
    실행할 코드
}
```

  

그럼 클로저에 대해 간단히 알아봤으니, 아래 예제를 통해 데이터 전달을 어떻게 하는지 살펴보도록 하겠습니다.

  

첫 번째 화면에서 두 번째 화면으로 전환할 때, 클로저를 사용하여 데이터를 전달하는 방법을 학습하도록 하겠습니다. 두 번째 화면에서 데이터를 입력하고, 그 데이터를 첫 번째 화면에 전달하는 방식입니다.

  

### FirstViewController에서 클로저를 설정합니다.

**FirstViewController**에서 두 번째 화면으로 이동할 때, 데이터를 전달받기 위해 **클로저를 설정**합니다.

```Swift

class FirstViewController: UIViewController {
    
    // UI 요소들 선언
    private lazy var label: UILabel = {
        let label = UILabel()
        label.translatesAutoresizingMaskIntoConstraints = false
        label.text = "전달된 데이터 없음"
        return label
    }()
    
    private lazy var button: UIButton = {
        let button = UIButton(type: .system)
        button.setTitle("두 번째 화면으로", for: .normal)
        button.translatesAutoresizingMaskIntoConstraints = false
        return button
    }()
    
    override func viewDidLoad() {
        super.viewDidLoad()
        view.backgroundColor = .white
        setupViews()
    }
    
    func setupViews() {
        view.addSubview(label)
        view.addSubview(button)
        
        NSLayoutConstraint.activate([
            label.centerXAnchor.constraint(equalTo: view.centerXAnchor),
            label.centerYAnchor.constraint(equalTo: view.centerYAnchor),
            
            button.topAnchor.constraint(equalTo: label.bottomAnchor, constant: 20),
            button.centerXAnchor.constraint(equalTo: view.centerXAnchor)
        ])
        
        // 버튼 클릭 시 두 번째 화면으로 전환
        button.addTarget(self, action: \#selector(didTapButton), for: .touchUpInside)
    }
    
    @objc func didTapButton() {
        let secondVC = SecondViewController()
        
        // 클로저를 설정하여 두 번째 화면에서 데이터를 전달받음
        secondVC.completionHandler = { [weak self] data in
            self?.label.text = data
        }
        
        // 화면 전환
        navigationController?.pushViewController(secondVC, animated: true)
    }
}
```

  

### SecondViewController에서 데이터 전달

**SecondViewController**에서 사용자가 텍스트 필드에 입력한 데이터를 completionHandler 클로저를 통해 전달합니다.

```Swift
lass SecondViewController: UIViewController {
    
    // 데이터를 전달할 클로저 타입의 변수 선언
    var completionHandler: ((String) -> Void)?
    
    // UI 요소들 선언
    private lazy var textField: UITextField = {
        let textField = UITextField()
        textField.borderStyle = .roundedRect
        textField.placeholder = "데이터를 입력해주세요"
        textField.translatesAutoresizingMaskIntoConstraints = false
        return textField
    }()
    
    private lazy var button: UIButton = {
        let button = UIButton(type: .system)
        button.setTitle("데이터 전달하기", for: .normal)
        button.translatesAutoresizingMaskIntoConstraints = false
        return button
    }()
    
    override func viewDidLoad() {
        super.viewDidLoad()
        view.backgroundColor = .white
        setupViews()
    }
    
    func setupViews() {
        view.addSubview(textField)
        view.addSubview(button)
        
        NSLayoutConstraint.activate([
            textField.centerXAnchor.constraint(equalTo: view.centerXAnchor),
            textField.centerYAnchor.constraint(equalTo: view.centerYAnchor),
            
            button.topAnchor.constraint(equalTo: textField.bottomAnchor, constant: 20),
            button.centerXAnchor.constraint(equalTo: view.centerXAnchor)
        ])
        
        // 버튼 클릭 시 클로저를 통해 데이터를 전달
        button.addTarget(self, action: \#selector(didTapButton), for: .touchUpInside)
    }
    
    @objc func didTapButton() {
        // 사용자가 입력한 텍스트를 클로저를 통해 전달하고 화면을 이전으로 전환
        if let text = textField.text {
            completionHandler?(text)
            navigationController?.popViewController(animated: true)
        }
    }
}
```

  

### 코드 분석

- **FirstViewController**
    - 첫 번째 뷰 컨트롤러는 **클로저**를 이용해 두 번째 뷰 컨트롤러에소 데이터를 전달받을 준비를 합니다. **completionHandler**라는 클로저를 설정하고, 이를 통해 데이터를 받아 UI에 반영합니다.
- **SecondViewController**
    - 두 번째 뷰컨트롤러에서는 사용자가 입력한 데이터를 `completionHandler` 클로저를 통해 전달하고, 이전 화면으로 돌아갑니다.

  

### 결과 화면

==**전달 받기 전 첫 번째 화면**==

![[스크린샷_2024-09-10_오후_1.13.40.png]]

==**두 번째 화면**==

![[스크린샷_2024-09-10_오후_1.13.59.png]]

==**전달 받은 후 첫 번째 화면**==

![[스크린샷_2024-09-10_오후_1.14.01.png]]

  

### 장점

코드의 흐름이 매우 직관적이며, 특히 단방향 데이터 흐름에서 사용하기 좋습니다.

또한, 델리게이트 패턴보다 코드가 간결하며, 데이터 전달을 간단하게 처리할 수 있습니다.

  

### 단점

클로저는 참조 순환을 유발할 수 있습니다. 클로저 내부에서 `self` 를 강하게 참조하면 메모리 누수가 발생할 수 있으므로, **weak self**를 사용해야 합니다. 이에 대한 자세한 설명은 문법 워크북에서 학습하게 될 것입니다.

  

> [!important] **클로저를 통한 데이터 전달**은 간결하고 직관적인 데이터 전달 방식으로, 단방향 데이터 흐름과 비동기 작업에서 특히 유용합니다. 델리게이트 패턴보다 코드가 짧고 이해하기 쉬운 장점이 있어 특정 상황에서 빠르고 효율적으로 데이터를 전달할 수 있습니다.

  

## ❗️❗️❗️ 정리 ❗️❗️❗️

위 내용을 다시 정리해보도록 하겠습니다

  

- **직접 할당을 통한 데이터 전달**
    - 가장 기본적인 방식으로, 뷰 컨트롤러 간에 데이터를 직접 할당하여 전달합니다. 간단한 데이터 전달 시 빠르고 쉽게 구현할 수 있지만, 단방향 데이터 흐름에 적합하며 복잡한 데이터 처리에는 적절하지 않을 수 있습니다.
- **델리게이트 패턴을 통한 데이터 전달**
    - 데이터의 역방향 전달을 필요로 할 때 매우 유용한 패턴입니다. 프로토콜을 사용하여 데이터를 전달하는 책임을 위임하고, 명확한 역할 분리를 통해 코드의 재사용성과 확장성을 높일 수 있습니다.

  

- **클로저를 통한 데이터 전달**
    - 간결하고 직관적인 방식으로, 비동기 작업이나 특정 이벤트에 대한 반응에서 데이터를 전달할 때 유용합니다.

  

이 세 가지 데이터 전달 방식은 각각의 상황에 따라 적합한 방법을 선택하여 사용할 수 있습니다. 앱 개발 과정에서 데이터 전달이 필요한 순간에 각 방식의 장단점을 고려하여 적절한 방법을 사용하는 것이 중요합니다.

  

이제 화면 간 데이터 전달을 넘어서, 앱이 종료된 후에도 데이터를 유지하고, 앱 전체에서 데이터를 쉽게 관리할 수 있는 방법에 대해 알아볼 것입니다. 이때 가장 많이 사용되는 것이 **UserDefaults**입니다.

  

**UserDefaults**는 앱 내에서 간단한 사용자 설정이나 정보를 저장하고 불러오는 데 유용한 도구로, 앱의 데이터 관리에 있어 중요한 역할을 합니다. 화면 간 데이터 전달뿐만 아니라, 사용자 기본 설정이나 로그인 정보와 같은 지속성이 요구되는 데이터를 다루기 위해 **UserDefaults**를 활용하는 방법을 배워보도록 하겠습니다.

### 3️⃣ UserDefaults 알기

앱 개발에서는 사용자가 설정한 값이나 작은 데이터를 앱이 종료되어도 기억하고 있어야 할 때가 많습니다. 예를 들어, 로그인 상태 테마 설정, 마지막으로 방문한 화면 정보 등을 저장하고 앱을 재실행할 때 이전 상태를 유지하는 것이 중요합니다.

  

만약 앱 실행 과정에서 저장해야할 데이터가 단순하다면 기본 저장에 저장하는 것이 좋습니다.

우리는 이 데이터를 편리하고 안정적으로 데이터를 저장할 수 있는 **UserDefaults 객체**에 대해 알아 볼 것입니다.

> **UserDefaults**는 iOS와 macOS에서 사용되는 간단하고 경량의 데이터 저장소로 문자열, 숫자, 날짜, 배열 등의 값을 저장할 수 있습니다. 이러한 데이터는 사용자의 디바이스에 로컬로 저장돠며 앱이 종료된 후에도 유지됩니다. 즉, 사용자가 앱을 다시 실행했을 때도 해다 데이터를 다시 불러와서 사용할 수 있도록 해줍니다.

> [!info] UserDefaults | Apple Developer Documentation  
> An interface to the user’s defaults database, where you store key-value pairs persistently across launches of your app.  
> [https://developer.apple.com/documentation/foundation/userdefaults](https://developer.apple.com/documentation/foundation/userdefaults)  

  

위 사이트에서 **UserDefaults**에 대해 읽어보면, **UserDefaults**는 싱글톤패턴을 따르는 클래스로 설계되어 있습니다.

> [!important] ==**싱글톤 패턴은**== ==**특정 클래스의 인스턴스가 오직 하나만 존재하도록 보장하는 디자인 패턴**====**입니다.**<br>**애플리케이션 전역에서 데이터를 쉽게 공유하고 관리할 수 있게 합니다.**<br>==

싱글톤 패턴으로 설계되어 있기 때문에 UserDefaults를 통해 앱의 여러곳에서 데이터를 저장하고 불러오더라도 동일한 인스턴스를 사용하기 때문에 항상 동일한 데이터에 접근할 수 있습니다.

  

즉, 로그인 정보나 앱 설정을 앱의 다양한 화면에서 접근할 때 각 화면에서 별도로 인스턴스를 생성할 필요 없이 동일한 **UserDefaults** 인스턴스를 공유하여 데이터를 쉽게 관리할 수 있습니다.

  

또한 UserDefaults는 `스레드 안전성` 을 염두에 두고 설계된 클래스입니다.

앱 내에서 여러 스레드가 동시에 UserDefaults에 접근하거나 데이터를 읽고 쓸 때 데이터 일관성을 유지하고, 방지하는 매커니즘을 갖추고 있기 때문에 동시성 문제로부터 안전하게 사용할 수 있도록 설계되어 있습니다.

  

즉, ==**우리는 UserDefaults 객체를 동시에 여러 곳에서 호출하여 데이터를 읽고 쓰더라도 순서가 꼬이거나 서로 영향을 끼칠 걱정 없이 마음 놓고 사용하면 됩니다.**==

  

그럼 이제 **UserDefaults** 실제 사용법을 익혀 보겠습니다.

  

하지만 설명하기에 앞서 꼭!!! 위에 북마크한 Apple Developer 문서 링크에 접속해서 **UserDefaults**에 관한 내용을 읽어 주시기 바랍니다.!

## 🔴  UserDefaults에 데이터 저장하기

==**UserDefaults**==를 통해 데이터를 저장하려면 `UserDefaults.standard` 객체의 `set(_:forKey:)` 메서드를 사용합니다. 이때 데이터는 키-값 쌍으로 저장되며, 데이터를 불러올 때 같은 키를 사용하여 데이터를 검색할 수 있습니다.

```Swift
let defaults = UserDefaults.standard

// 기본 자료형 데이터 저장하기
defaults.set(true, forKey: "isLoggedIn")   // Bool 값 저장
defaults.set(25, forKey: "userAge")        // Int 값 저장
defaults.set("John", forKey: "username")   // String 값 저장

// 배열과 딕셔너리 저장하기
defaults.set(["Apple", "Banana", "Orange"], forKey: "fruits")
defaults.set(["name": "John", "age": 25], forKey: "userDetails")
```

## 🔴  UserDefaults에 데이터 불러오기

`UserDefaults`에 저장된 값을 불러오려면 `UserDefaults.standard` 객체의 `bool(forKey:)`, `integer(forKey:)`, `string(forKey:)` 등 자료형에 맞는 메서드를 사용합니다. 불러올 때 사용하는 키는 데이터를 저장할 때 사용한 키와 일치해야 합니다.

```Swift
let isLoggedIn = defaults.bool(forKey: "isLoggedIn")   // Bool 값 불러오기
let userAge = defaults.integer(forKey: "userAge")      // Int 값 불러오기
let username = defaults.string(forKey: "username")     // String 값 불러오기

let fruits = defaults.array(forKey: "fruits") as? [String]   // 배열 불러오기
let userDetails = defaults.dictionary(forKey: "userDetails") as? [String: Any]  // 딕셔너리 불러오기
```

  

불러올 데이터가 없는 경우, 각 메서드는 자료형에 맞는 기본값을 반환합니다. 즉, `bool(forKey:)`는 키가 없을 경우 `false`를 반환하며, `integer(forKey:)`는 0을 반환합니다. 옵셔널 자료형은 해당 데이터가 없으면 `nil`을 반환합니다.

## 🔴  UserDefaults에 데이터 삭제하기

UserDefaults에 저장된 데이터를 삭제하려면 `removeObject(forKey:)` 메서드를 사용합니다. 특정 키에 연결된 데이터를 삭제할 수 있습니다.

```Swift
defaults.removeObject(forKey: "isLoggedIn")   // "isLoggedIn" 키에 연결된 데이터 삭제
defaults.removeObject(forKey: "fruits")       // "fruits" 배열 삭제
```

  

> [!important] UserDefaults는 암호화되지 않으므로, 중요한 정보(토큰 저정, 비밀번호 저장 등등)는 저장하지 않는 것이 좋습니다. 보안이 필요한 데이터는 iOS의 ==**키체인**==을 사용하는 것이 좋습니다.<br><br>==**키체인**==에 대한 설명은 Extra 워크북에서 내용만 다루고 있습니다. 꼭 이에 대해 읽어주시기 바랍니다.

  

**UserDefaults**는 간단한 설정이나 앱 상태를 저장하고 불러오는 데 매우 유용한 도구입니다. 다양한 데이터 타입을 저장할 수 있으며, 앱의 여러곳에서 전역적으로 접근할 수 있어 사용 편의성이 높습니다. 위의 기본 사용법을 통해 **UserDefaults**를 쉽게 사용할 수 있을 것입니다.

# 🔥 3주차 개념을 끝으로!!

> 이번 학습을 통해 iOS 앱의 데이터 관리와 사용자 인터페이스 구현에 있어 더 나은 이해와 실력을 쌓을 수 있었을 것입니다. 이를 토대로 앞으로의 워크북 진행, 프로젝트 개발에 있어서 더욱 효율적이고 견고한 앱을 제작하고 코드를 작성할 수 있을 것입니다. `UITableView` 와 `데이터 전달` 은 앱 개발의 핵심적인 요소로 워크북의 내용을 자주 복습하며 이해하고 알아가길 바라겠습니다!

## 🔥 3주차 개념 점검

---

> [!important] UITableView의 셀을 구성하기 위해 반드시 구현해야 하는 두 가지 메서드는 무엇인가요?<br>각각의 역할을 설명하세요<br>

- **여기에 답을 적어주세요!**
    
    `UITableViewDataSource` - 테이블 뷰에 표시될 데이터의 양과 종류를 결정하며 데이터를 적절한 셀에 할당하는 역할을 합니다.
    
    `UITableViewDelegate` - 셀의 높이, 헤더와 푸터의 렌더링, 셀의 선택과 같은 사용자 인터랙션을 관리합니다.
    

> [!important] UITableView에서 셀의재사용 메커니즘은 어떻게 동작하나요? <br>이 메커니즘이 중요한 이유는 무엇인가요?<br>

- **여기에 답을 적어주세요!**
    
    `dequeueReusableCell(withIdentifier:)` 메소드를 사용하여 화면에 보이는 셀만 메모리에 유지하고, 스크롤되어 화면 밖으로 사라진 셀은 재사용 큐에 추가해 필요할 때 다시 사용
    
    메모리 사용을 최적화하고 성능을 향상시키기 위해 중요
    

> [!important] iOS 애플리케이션에서 두 뷰 컨트롤러 간에 데이터를 전달하는 방법 세 가지를 설명하세요<br>각각의 장점과 단점도 비교해주세요<br>

- **여기에 답을 적어주세요!**
    
    > 직접 할당을 통한 전달
    
    - 다음 화면의 뷰 컨트롤러 클래스에 변수를 생성하고 이전 화면 클래스에서 다음 화면 인스턴스를 생성하면서 변수에 직접 데이터를 전달
        - 장점 : 코드가 간결, 직관적
        - 단점 : 코드 의존성이 높아지고, 단뱡향으로 전달 할때만 편함
    
    > 델리게이트 패턴을 통한 전달
    
    - 두 뷰 컨트롤러 간의 데이터를 역방향으로 전달할 때 유용한 패턴. 프로토콜을 사용하여 데이터 전달 책임을 다른 객체에 위임합니다.
        - 장점 : 뷰 컨트롤러간의 의존성 약화, 역방향 데이터 전달 가능
        - 단점 : 코드가 복잡해짐
    
    > 클로저를 통한 전달
    
    - 클로저를 사용해 데이터를 전달. 비동기 작업이나 단방향 데이터 흐름에서 유용
        - 장점 : 데이케이트 패턴 방식보다 코드가 간결
        - 단점 : 강한 순환 참조 발생 가능

> [!important] UserDefaults를 사용하여 데이터를 저장할 때 주의해야 할 점이나 한계는 무엇인가요?

- **여기에 답을 적어주세요!**
    - 암호화 되지 않기 때문에 보안이 중요한 정보의 경우 iOS의 키체인을 사용하는 것이 좋음

## 📚 3주차 실습

---

> 실습 내용은 위에 배운 내용을 사용하여  
> ==**1. UserDefaults에 데이터 저장 및 출력, 2. TableView로 주사위 1~6까지 나타내기**  
>   
> ====이 두가지를 실습할 것입니다. 순서를 지키면서 따라와 주시기 바랍니다.==

> 아래피그마 링크에 들어 오셔서 디자인을 확인하시기 바랍니다.  
> ==**Option 키를 누르고, 프레임 위에 마우스를 올려 확인 하시면서 오토레이아웃 수치를 꼭!! 확인해주시기 바랍니다.**  
>   
> ====또한== ==`SnapKit`====을 적용하여 진행하도록 하겠습니다.==

[https://www.figma.com/embed?embed_host=notion&url=https%3A%2F%2Fwww.figma.com%2Fdesign%2F47IuhJxc7LFTwOYWtDgTdi%2FiOS-%EC%9B%8C%ED%81%AC%EB%B6%81%3Fnode-id%3D322-1594%26t%3DBbBfsHii9RhWKbzh-1](https://www.figma.com/embed?embed_host=notion&url=https%3A%2F%2Fwww.figma.com%2Fdesign%2F47IuhJxc7LFTwOYWtDgTdi%2FiOS-%EC%9B%8C%ED%81%AC%EB%B6%81%3Fnode-id%3D322-1594%26t%3DBbBfsHii9RhWKbzh-1)

### 1️⃣ UserDefaults에 데이터 저장 및 출력

### 1. SceneDelegate 설정

==**이 부분은 생략하도록 하겠습니다. 설정 방법을 모르시면 1주차 워크북을 다시 참고해주시기 바랍니다!**==

### 2. 분석

위 피그마 링크에 가서 디자인 된 것을 보면, `UserDefaults 실습 뷰` 라는 타이틀 아래에 `텍스트필드`를 통해 값을 입력하고 `UserDefaults에 저장하기` 버튼을 통해 값을 저장합니다. 그 후, 화면 하단에 UserDefaults에 저장한 값을 출력시킵니다.

  

- 텍스트 필드의 placeholder는 “아무 텍스트나 입력해주세요”로 설정되어 있습니다.
- UserDefaults 값 출력 라벨은 **UserDefaults의 값이 없을 경우, “UserDefaults 값이 출력됩니다.”로 기본 텍스트 값이 설정**되어 있습니다.
- **만약 UserDefaults에 값이 저장된다면, 저장된 값으로 출력되도록 합니다.**

### 3. 파일 및 폴더 생성

`ViewControllers` 폴더 내부에 ViewController.swift 파일을 생성해주세요

`Models` 폴더 내부에 UserDefaultsModel.swift 파일을 생성합니다.

`Views` 폴더 내부에 UserDefaultsView.swift 파일을 생성합니다.

![[스크린샷_2024-09-19_오후_1.28.13.png]]

### 4. Model 작성하기

UserDefaults를 사용해서 텍스트 필드에 입력하는 값을 저장해야 합니다.

또한, UserDefaults에 저장한 값을 불러와서 화면에 보여야 합니다.

즉, 텍스트 필드에 값을 넣고 `UserDefaults에 저장하기 버튼`을 누르면 Model을 통해 저장이 되도록 해야 합니다.

  

- **class를 사용하여 모델 작성**
    
    > [!important]
    > 
    > - **struct**
    >     - 값 타입입니다. 즉, 구조체의 인스턴스를 복사할 때마다 별도의 복사본이 생성됩니다. 복사된 인스턴스는 원본과 독립적입니다.
    > - **class**
    >     - 참조 타입입니다. 클래스의 인스턴스를 복사해도 동일한 인스턴스를 참조하게 됩니다.
    
    > [!important] Model을 `class`로 작성하는 이유는 `**UserDefaults**` 처럼 글로벌한 상태를 유지해야 하는 데이터를 참조 타입으로 관리함으로써 데이터 일관성과 효율적인 메모리 관리를 할 수 있기 때문입니다. `struct` 로 사용할 경우 인스턴스가 복사될 때마다 별도의 복사본을 만들기 때문에 동일한 `**UserDefaults**` 객체에 접근하기 위한 일관성을 유지하는 것이 어려울 수 있습니다.
    
    ```Swift
    import Foundation
    
    class UserDefaultsModel {
        private let userDefaults = UserDefaults.standard
    }
    ```
    
      
    
- **UserDefaults에 값을 저장하고, 불러올 수 있는 함수를 구현합니다.**
    
    - 저장하고 불러오기 위한 키값을 먼저 지정한 후, 키를 사용하여 함수를 구현합니다.
    
    ```Swift
    import Foundation
    
    class UserDefaultsModel {
        private let userDefaults = UserDefaults.standard
        private let userTextKey: String = "userText"
        
        /// 유저가 입력한 텍스트 값을 UserDefaults에 저장합니다.
        /// - Parameter text: 유저가 입력한 텍스트 값
        public func saveUserText(_ text: String) {
            userDefaults.set(text, forKey: userTextKey)
        }
        
        /// UserDefaults에 저장된 값을 불러옵니다.
        /// - Returns: 저장된 값 String으로 return
        public func loadUserText() -> String? {
            return userDefaults.string(forKey: userTextKey)
        }
    }
    ```
    

### 5. View 작성하기

피그마를 보시면서 오토레이아웃에 수치에 맞춰 구현하시면 되겠습니다.

화면 상단에 있는 `실습뷰 타이틀 라벨` , `텍스트 필드`, `저장하기 버튼`을 만들도록 하겠습니다.

화면 하단에 있는 `값 출력 타이틀 라벨` , `값 출력 라벨` 을 만들도록 하겠습니다.

  

> [!important] ==**ViewController에 꼭 뷰를 넣어주시고 빌드해보세요!**<br>**뷰에 코드를 작성한것이기 때문에 뷰 컨트롤러에 넣어줘야합니다!!**<br>==
> 
> ```Swift
> class ViewController: UIViewController {
> 
>     override func viewDidLoad() {
>         super.viewDidLoad()
>         self.view = userDefaultsview
>     }
>     
>     private lazy var userDefaultsview: UserDefaultsView = {
>         let view = UserDefaultsView()
>         return view
>     }()
> }
> ```

  

- **상단 StackView 작성**
    
    - 실습뷰 라벨 타이틀, 텍스트 필드, 저장하기 버튼을 먼저 구현한 후, StackView에 넣도록 하겠습니다.
    - 아래 코드는 `UserDefaultsView` 파일을 작성한 것입니다. 코드 작성후 실행하기 위해 ViewController에서 뷰를 할당해줘야합니다.!
    
      
    
    먼저 필요한 컴포넌트들을 구현하도록 하겠습니다.
    
    ```Swift
     // MARK: - 상단 컴포넌트들 구현
        
        private lazy var titleLabel: UILabel = {
            let label = UILabel()
            label.text = "UserDefaults 실습 뷰"
            label.font = UIFont.systemFont(ofSize: 20)
            label.textColor = UIColor.black
            return label
        }()
        
        public lazy var inputTextField: UITextField = {
            let textField = UITextField()
            textField.placeholder = "아무 텍스트나 입력해주세요"
            textField.textColor = UIColor.black
            textField.font = UIFont.systemFont(ofSize: 14)
            
            /* 텍스트 필드 placeholder 왼쪽 여백*/
            /* 피그마에서 텍스트필드 테두리와 placeholder 왼쪽 여백의 수치가 15이므로 width에 15를 넣습니다. */
            textField.leftView = UIView(frame: CGRect(x: 0.0, y: 0.0, width: 15.0, height: 0.0))
            textField.leftViewMode = .always
            
            /* 텍스트 필드 테두리 지정 */
            textField.borderStyle = .none
            textField.layer.borderColor = UIColor.black.cgColor
            textField.layer.borderWidth = 2
            textField.layer.cornerRadius = 10
            
            return textField
        }()
        
        public lazy var saveButton: UIButton = {
            let btn = UIButton()
            btn.setTitle("UserDefaults에 저장하기", for: .normal)
            btn.setTitleColor(UIColor.red, for: .normal)
            btn.titleLabel?.font = UIFont.systemFont(ofSize: 14)
            btn.backgroundColor = UIColor.gray
            
            return btn
        }()
        
        private lazy var topStackView: UIStackView = {
            let stackView = UIStackView()
            stackView.axis = .vertical
            stackView.distribution = .equalSpacing
            stackView.alignment = .center
            /* 피그마를 참고해보면 그룹 내부의 여백이 26으로 동일합니다. */
            stackView.spacing = 26
            return stackView
        }()
    ```
    
      
    
    위에 구현한 컴포넌트들을 스택뷰에 넣고, 스택뷰에 오토레이아웃과 스택뷰 내부에 들어가는 컴포넌트들의 width, height 값을 주면 됩니다. 아래코드와 같이 작성하면 됩니다.
    
    ```Swift
    private func setStackView() {
            topStackView.addArrangedSubview(titleLabel)
            topStackView.addArrangedSubview(inputTextField)
            topStackView.addArrangedSubview(saveButton)
        }
        
        private func addViewConstraints() {
            self.addSubview(topStackView)
            
            topStackView.snp.makeConstraints {
                $0.top.equalToSuperview().offset(197)
                $0.left.equalToSuperview().offset(42)
                $0.right.equalToSuperview().offset(-42)
            }
            
            inputTextField.snp.makeConstraints {
                $0.height.equalTo(52)
                $0.width.equalTo(309)
            }
            
            saveButton.snp.makeConstraints {
                $0.height.equalTo(42)
                $0.width.equalTo(222)
            }
        }
    ```
    
    ```Swift
    override init(frame: CGRect) {
            super.init(frame: frame)
            self.backgroundColor = .white
            setStackView()
            addViewConstraints()
        }
    ```
    
    아래 사진은 위 코드의 결과화면입니다. 상단 컴포넌트들을 상단 스택뷰에 넣어서 구현했습니다.
    
    ![[스크린샷_2024-09-19_오후_11.54.10.png]]
    
- **하단 StackView 작성**
    
    - 값 출력 타이틀 라벨, 값 출력 라벨을 먼저 구현한 후, StackView에 넣도록 하겠습니다.
    - 위의 방식처럼 작성하면 됩니다. 위에 작성한 뷰 코드에 이어서 작성하시면 되겠습니다.
    
      
    
    먼저 필요한 컴포넌트들부터 구현하도록 하겠습니다.
    
    ```Swift
    private lazy var subTitleLabel: UILabel = {
            let label = UILabel()
            label.font = UIFont.systemFont(ofSize: 20)
            label.text = "UserDefaults 값 출력 라벨"
            label.textColor = UIColor.black
            label.textAlignment = .center
            return label
        }()
        
        public lazy var showTextValue: UILabel = {
            let label = UILabel()
    
            label.font = UIFont.systemFont(ofSize: 20)
            label.text = "UserDefaults 값이 출력됩니다."
            label.textColor = UIColor.black
            label.textAlignment = .center
            
            label.layer.borderWidth = 3
            label.layer.borderColor = UIColor.blue.cgColor
            label.layer.cornerRadius = 10
            return label
        }()
        
        private lazy var bottomStackView: UIStackView = {
            let stackView = UIStackView()
            stackView.axis = .vertical
            stackView.distribution = .equalSpacing
            stackView.alignment = .center
            stackView.spacing = 21
            return stackView
        }()
    ```
    
      
    
    위에 구현한 컴포넌트들을 스택뷰에 넣고, 스택뷰에 오토레이아웃과 스택뷰 내부에 들어가는 컴포넌트들의 width, height 값을 주면 됩니다. 아래코드와 같이 작성하면 됩니다.
    
    ```Swift
    private func setStackView() {
            topStackView.addArrangedSubview(titleLabel)
            topStackView.addArrangedSubview(inputTextField)
            topStackView.addArrangedSubview(saveButton)
            
            bottomStackView.addArrangedSubview(subTitleLabel)
            bottomStackView.addArrangedSubview(showTextValue)
        }
        
        private func addViewConstraints() {
            self.addSubview(topStackView)
            self.addSubview(bottomStackView)
            
            topStackView.snp.makeConstraints {
                $0.top.equalToSuperview().offset(197)
                $0.left.equalToSuperview().offset(42)
                $0.right.equalToSuperview().offset(-42)
            }
            
            inputTextField.snp.makeConstraints {
                $0.height.equalTo(52)
                $0.width.equalTo(309)
            }
            
            saveButton.snp.makeConstraints {
                $0.height.equalTo(42)
                $0.width.equalTo(222)
            }
            
            bottomStackView.snp.makeConstraints {
                $0.top.equalTo(topStackView.snp.bottom).offset(114)
                $0.left.equalToSuperview().offset(56.5)
                $0.right.equalToSuperview().offset(-56.5)
            }
            
            subTitleLabel.snp.makeConstraints {
                $0.width.equalTo(280)
                $0.height.equalTo(24)
            }
            
            showTextValue.snp.makeConstraints {
                $0.width.equalTo(280)
                $0.height.equalTo(172)
            }
        }
    ```
    
    ![[스크린샷_2024-09-20_오전_12.31.21.png]]
    
    `UserDefaultView.swift` 의 전체 코드는 아래와 같습니다.
    
    ```Swift
    import UIKit
    import SnapKit
    
    class UserDefaultsView: UIView {
        
        override init(frame: CGRect) {
            super.init(frame: frame)
            self.backgroundColor = .white
            setStackView()
            addViewConstraints()
        }
        
        required init?(coder: NSCoder) {
            fatalError("init(coder:) has not been implemented")
        }
        
        // MARK: - 상단 컴포넌트들 구현
        
        private lazy var titleLabel: UILabel = {
            let label = UILabel()
            label.text = "UserDefaults 실습 뷰"
            label.font = UIFont.systemFont(ofSize: 20)
            label.textColor = UIColor.black
            return label
        }()
        
        public lazy var inputTextField: UITextField = {
            let textField = UITextField()
            textField.placeholder = "아무 텍스트나 입력해주세요"
            textField.textColor = UIColor.black
            textField.font = UIFont.systemFont(ofSize: 14)
            
            /* 텍스트 필드 placeholder 왼쪽 여백*/
            /* 피그마에서 텍스트필드 테두리와 placeholder 왼쪽 여백의 수치가 15이므로 width에 15를 넣습니다. */
            textField.leftView = UIView(frame: CGRect(x: 0.0, y: 0.0, width: 15.0, height: 0.0))
            textField.leftViewMode = .always
            
            /* 텍스트 필드 테두리 지정 */
            textField.borderStyle = .none
            textField.layer.borderColor = UIColor.black.cgColor
            textField.layer.borderWidth = 2
            textField.layer.cornerRadius = 10
            
            return textField
        }()
        
        public lazy var saveButton: UIButton = {
            let btn = UIButton()
            
            btn.setTitle("UserDefaults에 저장하기", for: .normal)
            btn.setTitleColor(UIColor.red, for: .normal)
            btn.titleLabel?.font = UIFont.systemFont(ofSize: 14)
            btn.backgroundColor = UIColor.gray
            
            return btn
        }()
        
        private lazy var topStackView: UIStackView = {
            let stackView = UIStackView()
            stackView.axis = .vertical
            stackView.distribution = .equalSpacing
            stackView.alignment = .center
            /* 피그마를 참고해보면 그룹 내부의 여백이 26으로 동일합니다. */
            stackView.spacing = 26
            return stackView
        }()
        
        // MARK: - 하단 컴포넌트들 구현
        
        private lazy var subTitleLabel: UILabel = {
            let label = UILabel()
            label.font = UIFont.systemFont(ofSize: 20)
            label.text = "UserDefaults 값 출력 라벨"
            label.textColor = UIColor.black
            label.textAlignment = .center
            return label
        }()
        
        public lazy var showTextValue: UILabel = {
            let label = UILabel()
    
            label.font = UIFont.systemFont(ofSize: 20)
            label.text = "UserDefaults 값이 출력됩니다."
            label.textColor = UIColor.black
            label.textAlignment = .center
            
            label.layer.borderWidth = 3
            label.layer.borderColor = UIColor.blue.cgColor
            label.layer.cornerRadius = 10
            return label
        }()
        
        private lazy var bottomStackView: UIStackView = {
            let stackView = UIStackView()
            stackView.axis = .vertical
            stackView.distribution = .equalSpacing
            stackView.alignment = .center
            stackView.spacing = 21
            return stackView
        }()
        
        
        // MARK: - 상단, 하단 컴포넌트들 스택뷰 추가 및 스택뷰 오토레이아웃 지정
        
        private func setStackView() {
            topStackView.addArrangedSubview(titleLabel)
            topStackView.addArrangedSubview(inputTextField)
            topStackView.addArrangedSubview(saveButton)
            
            bottomStackView.addArrangedSubview(subTitleLabel)
            bottomStackView.addArrangedSubview(showTextValue)
        }
        
        private func addViewConstraints() {
            self.addSubview(topStackView)
            self.addSubview(bottomStackView)
            
            topStackView.snp.makeConstraints {
                $0.top.equalToSuperview().offset(197)
                $0.left.equalToSuperview().offset(42)
                $0.right.equalToSuperview().offset(-42)
            }
            
            inputTextField.snp.makeConstraints {
                $0.height.equalTo(52)
                $0.width.equalTo(309)
            }
            
            saveButton.snp.makeConstraints {
                $0.height.equalTo(42)
                $0.width.equalTo(222)
            }
            
            bottomStackView.snp.makeConstraints {
                $0.top.equalTo(topStackView.snp.bottom).offset(114)
                $0.left.equalToSuperview().offset(56.5)
                $0.right.equalToSuperview().offset(-56.5)
            }
            
            subTitleLabel.snp.makeConstraints {
                $0.width.equalTo(280)
                $0.height.equalTo(24)
            }
            
            showTextValue.snp.makeConstraints {
                $0.width.equalTo(280)
                $0.height.equalTo(172)
            }
        }
    }
    ```
    

### 6. ViewController 작성하기

이제 뷰가 완성되었고, 뷰를 연결했으니 텍스트필드에 넣은 값을 버튼을 눌러 저장하면,  
UserDefaults에 저장되고 즉시, 아래의 라벨에 저장된 값이 출력되도록 합니다.  

또한, ==**UserDefaults에 저장되었으니 앱을 껐다가 다시 들어왔을 때 실제로 계속 저장되어 있는지 확인**==할 수 있도록 ==**저장된 값이 있으면 값을 불러오도록 구현**==합니다.

```Swift
class ViewController: UIViewController {
    
    private let userDefaultsModel = UserDefaultsModel()

    override func viewDidLoad() {
        super.viewDidLoad()
        self.view = userDefaultsview
        loadTextValue()
    }
    
    private lazy var userDefaultsview: UserDefaultsView = {
        let view = UserDefaultsView()
        view.saveButton.addTarget(self, action: \#selector(saveButtonClicked), for: .touchUpInside)
        return view
    }()
    
    @objc func saveButtonClicked() {
        guard let text = userDefaultsview.inputTextField.text, !text.isEmpty else {
            return
        }
        
        // 모델을 통해 텍스트 저장합니다.
        userDefaultsModel.saveUserText(text)
        
        // 저장된 텍스트 라벨에 표시
        userDefaultsview.showTextValue.text = text
    }
    
    // 저장된 텍스트 값이 있을 경우 가져오기
    private func loadTextValue() {
        if let savedText = userDefaultsModel.loadUserText() {
            userDefaultsview.showTextValue.text = savedText
        }
    }
}
```

### 7. 전체 코드 및 실행 결과 화면

모델 코드, 뷰 코드, 뷰 컨트롤러 코드를 순서대로 보이도록 하겠습니다.

코드의 아래에 최종 결과 사진이랑 영상도 같이 첨부했습니다

  

- **Model 코드**

```Swift
import Foundation

class UserDefaultsModel {
    private let userDefaults = UserDefaults.standard
    private let userTextKey: String = "userText"
    
    /// 유저가 입력한 텍스트 값을 UserDefaults에 저장합니다.
    /// - Parameter text: 유저가 입력한 텍스트 값
    public func saveUserText(_ text: String) {
        userDefaults.set(text, forKey: userTextKey)
    }
    
    /// UserDefaults에 저장된 값을 불러옵니다.
    /// - Returns: 저장된 값 String으로 return
    public func loadUserText() -> String? {
        return userDefaults.string(forKey: userTextKey)
    }
}
```

  

- **View 코드**

```Swift
import UIKit
import SnapKit

class UserDefaultsView: UIView {
    
    override init(frame: CGRect) {
        super.init(frame: frame)
        self.backgroundColor = .white
        setStackView()
        addViewConstraints()
    }
    
    required init?(coder: NSCoder) {
        fatalError("init(coder:) has not been implemented")
    }
    
    // MARK: - 상단 컴포넌트들 구현
    
    private lazy var titleLabel: UILabel = {
        let label = UILabel()
        label.text = "UserDefaults 실습 뷰"
        label.font = UIFont.systemFont(ofSize: 20)
        label.textColor = UIColor.black
        return label
    }()
    
    public lazy var inputTextField: UITextField = {
        let textField = UITextField()
        textField.placeholder = "아무 텍스트나 입력해주세요"
        textField.textColor = UIColor.black
        textField.font = UIFont.systemFont(ofSize: 14)
        
        /* 텍스트 필드 placeholder 왼쪽 여백*/
        /* 피그마에서 텍스트필드 테두리와 placeholder 왼쪽 여백의 수치가 15이므로 width에 15를 넣습니다. */
        textField.leftView = UIView(frame: CGRect(x: 0.0, y: 0.0, width: 15.0, height: 0.0))
        textField.leftViewMode = .always
        
        /* 텍스트 필드 테두리 지정 */
        textField.borderStyle = .none
        textField.layer.borderColor = UIColor.black.cgColor
        textField.layer.borderWidth = 2
        textField.layer.cornerRadius = 10
        
        return textField
    }()
    
    public lazy var saveButton: UIButton = {
        let btn = UIButton()
        
        btn.setTitle("UserDefaults에 저장하기", for: .normal)
        btn.setTitleColor(UIColor.red, for: .normal)
        btn.titleLabel?.font = UIFont.systemFont(ofSize: 14)
        btn.backgroundColor = UIColor.gray
        
        return btn
    }()
    
    private lazy var topStackView: UIStackView = {
        let stackView = UIStackView()
        stackView.axis = .vertical
        stackView.distribution = .equalSpacing
        stackView.alignment = .center
        /* 피그마를 참고해보면 그룹 내부의 여백이 26으로 동일합니다. */
        stackView.spacing = 26
        return stackView
    }()
    
    // MARK: - 하단 컴포넌트들 구현
    
    private lazy var subTitleLabel: UILabel = {
        let label = UILabel()
        label.font = UIFont.systemFont(ofSize: 20)
        label.text = "UserDefaults 값 출력 라벨"
        label.textColor = UIColor.black
        label.textAlignment = .center
        return label
    }()
    
    public lazy var showTextValue: UILabel = {
        let label = UILabel()

        label.font = UIFont.systemFont(ofSize: 20)
        label.text = "UserDefaults 값이 출력됩니다."
        label.textColor = UIColor.black
        label.textAlignment = .center
        
        label.layer.borderWidth = 3
        label.layer.borderColor = UIColor.blue.cgColor
        label.layer.cornerRadius = 10
        return label
    }()
    
    private lazy var bottomStackView: UIStackView = {
        let stackView = UIStackView()
        stackView.axis = .vertical
        stackView.distribution = .equalSpacing
        stackView.alignment = .center
        stackView.spacing = 21
        return stackView
    }()
    
    
    // MARK: - 상단, 하단 컴포넌트들 스택뷰 추가 및 스택뷰 오토레이아웃 지정
    
    private func setStackView() {
        topStackView.addArrangedSubview(titleLabel)
        topStackView.addArrangedSubview(inputTextField)
        topStackView.addArrangedSubview(saveButton)
        
        bottomStackView.addArrangedSubview(subTitleLabel)
        bottomStackView.addArrangedSubview(showTextValue)
    }
    
    private func addViewConstraints() {
        self.addSubview(topStackView)
        self.addSubview(bottomStackView)
        
        topStackView.snp.makeConstraints {
            $0.top.equalToSuperview().offset(197)
            $0.left.equalToSuperview().offset(42)
            $0.right.equalToSuperview().offset(-42)
        }
        
        inputTextField.snp.makeConstraints {
            $0.height.equalTo(52)
            $0.width.equalTo(309)
        }
        
        saveButton.snp.makeConstraints {
            $0.height.equalTo(42)
            $0.width.equalTo(222)
        }
        
        bottomStackView.snp.makeConstraints {
            $0.top.equalTo(topStackView.snp.bottom).offset(114)
            $0.left.equalToSuperview().offset(56.5)
            $0.right.equalToSuperview().offset(-56.5)
        }
        
        subTitleLabel.snp.makeConstraints {
            $0.width.equalTo(280)
            $0.height.equalTo(24)
        }
        
        showTextValue.snp.makeConstraints {
            $0.width.equalTo(280)
            $0.height.equalTo(172)
        }
    }
}
```

  

- **ViewController 코드**

```Swift
import UIKit

class ViewController: UIViewController {
    
    private let userDefaultsModel = UserDefaultsModel()

    override func viewDidLoad() {
        super.viewDidLoad()
        self.view = userDefaultsview
        loadTextValue()
    }
    
    private lazy var userDefaultsview: UserDefaultsView = {
        let view = UserDefaultsView()
        view.saveButton.addTarget(self, action: \#selector(saveButtonClicked), for: .touchUpInside)
        return view
    }()
    
    @objc func saveButtonClicked() {
        guard let text = userDefaultsview.inputTextField.text, !text.isEmpty else {
            return
        }
        
        // 모델을 통해 텍스트 저장합니다.
        userDefaultsModel.saveUserText(text)
        
        // 저장된 텍스트 라벨에 표시
        userDefaultsview.showTextValue.text = text
    }
    
    // 저장된 텍스트 값이 있을 경우 가져오기
    private func loadTextValue() {
        if let savedText = userDefaultsModel.loadUserText() {
            userDefaultsview.showTextValue.text = savedText
        }
    }
}
```

  

- **결과 사진 및 영상**

값을 입력하고 버튼을 눌러 저장한 후의 화면입니다.

![[스크린샷_2024-09-20_오전_1.00.15.png]]

값이 저장되는 화면과 저장 후, 앱에 다시 들어왔을 때 값이 유지되고 있는 것을 확인할 수 있습니다.

![[Simulator_Screen_Recording_-_iPhone_15_Pro_-_2024-09-20_at_01.01.10.mp4]]

### 2️⃣ TableView로 주사위 1~6까지 나타내기

### 1. SceneDelegate 설정

==**이 부분은 생략하도록 하겠습니다. 설정 방법을 모르시면 1주차 워크북을 다시 참고해주시기 바랍니다!**==

### 2. 분석

위 피그마 링크에 가서 디자인 된 것을 보면, 상단에 `타이틀 라벨` , `주사위 1~6까지 나타내는 테이블 뷰` 로 구성되어 있습니다. 즉 테이블 뷰를 만들기 위한 `Cell` 을 먼저 만들고, 테이블 뷰에 사용할 데이터들을 생성 후 테이블 뷰에 셀들이 나타나도록 하면 됩니다.

  

- **피그마의** `**주사위 프레임**` **에 있는 주사위 6개를 다운 받아주세요!**

### 3. 파일 및 폴더 생성

`ViewControllers` 폴더 내부에 DiceViewController.swift 파일을 생성해주세요

`Models` 폴더 내부에 DiceModel.swift 파일을 생성합니다.

`Views` 폴더 내부에 DiceView.swift 파일을 생성합니다.

`Cells` 폴더 내부에 DiceCell.swift 파일을 생성합니다.

`Assets.xcassets` 폴더 내부에 다운 받은 주사위 사진 6장을 추가합니다.

아래 사진과 같이 진행되도록 하시면 됩니다.

==**DiceCell.swift 파일 생성 시 아래 사진처럼 클래스를 지정 후 생성하시면 되겠습니다.**==

![[스크린샷_2024-09-20_오전_8.39.37.png]]

  

==**Assets.xcassets 내부에 아래 사진과 같이 다운 받은 주사위 사진 6개를 넣어주세요!**==

![[스크린샷_2024-09-20_오전_8.41.24.png]]

**파일 및 폴더 구조는 아래과 같이 되도록 합니다.**

![[스크린샷_2024-09-20_오전_8.40.40.png]]

  

**ViewContoroller 파일 이름과 클래스 이름을 바꾸었으니 SceneDelegate의 rootViewController의 값을 바꾼 이름에 맞춰 수정해줍니다**

![[스크린샷_2024-09-20_오전_8.42.36.png]]

### 4. Model 작성

`Cell` 에 사용되는 Model을 만들면 됩니다. 피그마에 보시면 `Cell` 에는 ==**주사위 사진**==과 ==**주사위 이름**==을 사용하고 있습니다. 즉, Model에는 두 개를 담을 수 있도록 만들어줍니다.

> [!important] Model을 만들고 ==**Model에 더미 데이터**==를 넣어줘야 합니다! 저희가 서버에서 데이터를 가져오는 것도 아니고, 파이어베이스를 사용하고 있는 것도 아니기 때문에 ==**더미 데이터 클래스**==를 만들어서 뷰에서 테이블 뷰를 작성할 때 사용하도록 하겠습니다.

  

- **Model 작성하기**
    
    아래와 같이 상수로 모델을 작성합니다. 당연히, `DiceModel.swift` 파일에 작성하시면 됩니다.
    
    ```Swift
    struct DiceModel {
        let diceImage: String
        let diceName: String
    }
    ```
    
      
    
- **더미 데이터 작성하기**
    
    더미 데이터 클래스 수정을 하지 못하도록 `final` 키워드를 사용하고, 싱글톤으로 더미 데이터를 사용할 수 있도록 `static` 키워드를 사용해서 만들도록 하겠습니다.
    
    저희는 테이블 뷰에서 주사위 6개를 보여야 합니다. 즉, 6개의 더미데이터를 만들면 됩니다.
    
    위에 Model 작성한 코드 아래에 새로운 클래스를 만들어서 작성하도록 하겠습니다.
    
    ```Swift
    final class dummyDiceModel {
        static let diceDatas: [DiceModel] = [
            DiceModel(diceImage: "dice 1.png", diceName: "주사위 1"),
            DiceModel(diceImage: "dice 2.png", diceName: "주사위 2"),
            DiceModel(diceImage: "dice 3.png", diceName: "주사위 3"),
            DiceModel(diceImage: "dice 4.png", diceName: "주사위 4"),
            DiceModel(diceImage: "dice 5.png", diceName: "주사위 5"),
            DiceModel(diceImage: "dice 6.png", diceName: "주사위 6")
        ]
    }
    ```
    
      
    
- **Model 전체 코드**
    
    ```Swift
    import Foundation
    
    struct DiceModel {
        let diceImage: String
        let diceName: String
    }
    
    final class dummyDiceModel {
        static let diceDatas: [DiceModel] = [
            DiceModel(diceImage: "dice 1.png", diceName: "주사위 1"),
            DiceModel(diceImage: "dice 2.png", diceName: "주사위 2"),
            DiceModel(diceImage: "dice 3.png", diceName: "주사위 3"),
            DiceModel(diceImage: "dice 4.png", diceName: "주사위 4"),
            DiceModel(diceImage: "dice 5.png", diceName: "주사위 5"),
            DiceModel(diceImage: "dice 6.png", diceName: "주사위 6")
        ]
    }
    ```
    

### 5. Cell 작성

`Cell` 의 모습(컴포넌트 배치, 오토레이아웃 수치)는 모두 공통으로 같습니다.

그렇기 때문에 아래 사진의 셀을 보면서 셀을 구현합니다. 당연히, DiceCell.swift 파일에 구현하면 됩니다.

![[스크린샷_2024-09-20_오전_8.55.19.png]]

  

- **Cell 식별자 넣어주기**
    
    - 테이블 뷰에서 Cell을 연결하기 위한 식별자를 생성해줍니다.
    
    ```Swift
    static let identifier = "DiceCell"
    ```
    

  

- **TableViewCell 초기화하기**.
    
    - 3개의 초기화 코드를 작성하도록 합니다. 아래 코드와 같습니다.
    - `init(style:reuseIdentifier:)`: 코드로 셀을 초기화할 때 호출되는 메서드입니다.
    - `prepareForReuse()` 메서드를 오버라이드하여 셀이 재사용되기 전에 초기화된 상태로 만들어줍니다.
    
    ```Swift
    override init(style: UITableViewCell.CellStyle, reuseIdentifier: String?) {
            super.init(style: style, reuseIdentifier: reuseIdentifier)
        }
        
        override func prepareForReuse() {
            super.prepareForReuse()
        }
        
        required init?(coder: NSCoder) {
            fatalError("init(coder:) has not been implemented")
        }
    ```
    
      
    
    그럼 전체 코드는 아래와 같습니다. Cell 파일을 처음 생성하면 두 개의 함수가 작성되어 있을겁니다. 거기에 추가로 위 3개 초기화까지 작성된 코드입니다.
    
    ```Swift
    import UIKit
    
    class DiceCell: UITableViewCell {
    
        override func awakeFromNib() {
            super.awakeFromNib()
            // Initialization code
        }
    
        override func setSelected(_ selected: Bool, animated: Bool) {
            super.setSelected(selected, animated: animated)
    
            // Configure the view for the selected state
        }
        
        override init(style: UITableViewCell.CellStyle, reuseIdentifier: String?) {
            super.init(style: style, reuseIdentifier: reuseIdentifier)
        }
        
        override func prepareForReuse() {
            super.prepareForReuse()
        }
        
        required init?(coder: NSCoder) {
            fatalError("init(coder:) has not been implemented")
        }
    }
    ```
    
      
    
- **TableViewCell에 UI 컴포넌트들 넣기**
    
    - 실습을 하면서 View에 컴포넌트들을 작성했듯이 똑같이 진행하면 됩니다.
    - 이번 Cell에서는 StackView를 사용하지 않고 진행하도록 하겠습니다.
    - 당연히, `SnapKit` 은 사용하도록 하겠습니다.
    
    ```Swift
    private lazy var diceImageView: UIImageView = {
            let imageView = UIImageView()
            
            /* 주사위 이미지 값은 ViewController에서 작성하게 됩니다. */
            // imageView.image = UIImage(named: "여기에 더미 데이터 값이 들어갑니다.")
            
            return imageView
        }()
        
        private lazy var diceName: UILabel = {
            let name = UILabel()
            name.font = UIFont.systemFont(ofSize: 20)
            name.textColor = UIColor.black
            
            /* 주사위 이름 값은 ViewController에서 작성하게 됩니다. */
            //name.text = "여기에 더미 데이터 값이 들어갑니다."
            
            return name
        }()
        
        private func setViews() {
            self.addSubview(diceImageView)
            self.addSubview(diceName)
        }
        
        private func setConstaints() {
            diceImageView.snp.makeConstraints {
                $0.top.equalToSuperview().offset(11)
                $0.left.equalToSuperview().offset(13)
                $0.bottom.equalToSuperview().offset(-10)
                $0.width.height.equalTo(75)
            }
            
            diceName.snp.makeConstraints {
                $0.top.equalToSuperview().offset(36.5)
                $0.left.equalTo(diceImageView.snp.right).offset(87)
                $0.right.equalToSuperview().offset(-144)
            }
        }
    ```
    
      
    
- `**prepareForReuse()**` , `**init(style:reuseIdentifier:)**` 에 값 넣어주기
    
    ```Swift
     override init(style: UITableViewCell.CellStyle, reuseIdentifier: String?) {
            super.init(style: style, reuseIdentifier: reuseIdentifier)
            self.setViews()
            self.setConstaints()
        }
        
        override func prepareForReuse() {
            super.prepareForReuse()
            self.diceImageView.image = nil
            self.diceName.text = nil
        }
    ```
    
      
    
    그럼 위 코드에서 사진의 이미지 값과 이름 라벨의 텍스트 값은 ViewController에서 작성하게 된다 했습니다. 그럼 ==**ViewController가 Cell에 접근하여 Cell 내부 컴포넌트의 값을 바꿀 수 있도록**== `public` 으로 공개된 함수가 필요합니다.
    
    즉, `UITableViewCell` 클래스 내부에 값을 설정하는 메서드를 만들어서 사용할 수 있도록 해야 합니다.
    
      
    
- **값 설정 메서드 만들기**
    
    - 위에서 만든 Model인 DiceModel 타입을 인자로 받아서 값을 변경할 수 있도록 합니다.
    - 더미 데이터 타입이 DiceModel 이기 때문입니다.
    
    ```Swift
    public func configure(model: DiceModel) {
            self.diceImageView.image = UIImage(named: model.diceImage)
            self.diceName.text = model.diceName
        }
    ```
    
      
    
    위 함수를 통해 ViewController에서 셀을 생성하면서 셀의 값을 바꾸면서 불러오게 됩니다.
    
      
    
- **전체 Cell 코드**
    
    ```Swift
    import UIKit
    import SnapKit
    
    class DiceCell: UITableViewCell {
        
        static let identifier = "DiceCell"
    
        override func awakeFromNib() {
            super.awakeFromNib()
            // Initialization code
        }
    
        override func setSelected(_ selected: Bool, animated: Bool) {
            super.setSelected(selected, animated: animated)
    
            // Configure the view for the selected state
        }
        
        override init(style: UITableViewCell.CellStyle, reuseIdentifier: String?) {
            super.init(style: style, reuseIdentifier: reuseIdentifier)
            self.setViews()
            self.setConstaints()
        }
        
        override func prepareForReuse() {
            super.prepareForReuse()
            self.diceImageView.image = nil
            self.diceName.text = nil
        }
        
        required init?(coder: NSCoder) {
            fatalError("init(coder:) has not been implemented")
        }
        
        private lazy var diceImageView: UIImageView = {
            let imageView = UIImageView()
            
            /* 주사위 이미지 값은 ViewController에서 작성하게 됩니다. */
            // imageView.image = UIImage(named: "여기에 더미 데이터 값이 들어갑니다.")
            
            return imageView
        }()
        
        private lazy var diceName: UILabel = {
            let name = UILabel()
            name.font = UIFont.systemFont(ofSize: 20)
            name.textColor = UIColor.black
            
            /* 주사위 이름 값은 ViewController에서 작성하게 됩니다. */
            //name.text = "여기에 더미 데이터 값이 들어갑니다."
            
            return name
        }()
        
        private func setViews() {
            self.addSubview(diceImageView)
            self.addSubview(diceName)
        }
        
        private func setConstaints() {
            diceImageView.snp.makeConstraints {
                $0.top.equalToSuperview().offset(11)
                $0.left.equalToSuperview().offset(13)
                $0.bottom.equalToSuperview().offset(-10)
                $0.width.height.equalTo(75)
            }
            
            diceName.snp.makeConstraints {
                $0.top.equalToSuperview().offset(36.5)
                $0.left.equalTo(diceImageView.snp.right).offset(87)
                $0.right.equalToSuperview().offset(-144)
            }
        }
        
        public func configure(model: DiceModel) {
            self.diceImageView.image = UIImage(named: model.diceImage)
            self.diceName.text = model.diceName
        }
    }
    ```
    

### 6. View 작성

이제 `View`에 상단 타이틀 제목을 넣고, 테이블 뷰를 넣어주도록 하겠습니다.

  

- **컴포넌트들 작성**
    
    - 라벨로 타이틀 제목을 넣고, 그 아래 테이블 뷰를 넣어 오토레이아웃 적용하도록 합니다.
    
    ```Swift
    class DiceView: UIView {
    
        override init(frame: CGRect) {
            super.init(frame: frame)
    				self.backgroundColor = .white
            setViews()
            setConstaints()
        }
        
        required init?(coder: NSCoder) {
            fatalError("init(coder:) has not been implemented")
        }
        
        private lazy var title: UILabel = {
            let label = UILabel()
            label.text = "주사위 테이블 뷰 만들기"
            label.font = UIFont.systemFont(ofSize: 20, weight: .bold)
            label.textColor = UIColor.black
            return label
        }()
        
        public lazy var tableView: UITableView = {
            let table = UITableView()
            table.register(DiceCell.self, forCellReuseIdentifier: DiceCell.identifier)
            table.separatorStyle = .singleLine
            return table
        }()
        
        private func setViews() {
            self.addSubview(title)
            self.addSubview(tableView)
        }
        
        private func setConstaints() {
            title.snp.makeConstraints {
                $0.top.equalToSuperview().offset(50)
                $0.left.equalToSuperview().offset(12)
                $0.right.equalToSuperview().offset(-183)
            }
            
            tableView.snp.makeConstraints {
                $0.top.equalTo(title.snp.bottom).offset(14)
                $0.left.right.bottom.equalToSuperview()
            }
        }
    }
    ```
    
      
    
    이제 뷰 코드 작성은 끝났습니다. 뷰 컨트롤러로 넘어가서 `tableView`의 `delegate`와 `dataSource`를 설정하여 테이블 뷰를 구성합니다
    

### 7. ViewController 작성

이제 뷰 컨트롤러에서 DiceView를 불러와서 `tableView`의 `dataSoucre`와 `delegate`를 구현해보겠습니다.

또한 더미 데이터를 불러와서 Cell에 넣도록 하겠습니다.

  

- **더미 데이터를 받아오기**
    
    - 위에 모델을 작성할 때 싱글톤으로 하여 접근할 수 있도록 해뒀습니다.
    - 새로운 상수를 작성해서 데이터를 받아오도록 합니다.
    
    ```Swift
    let data = dummyDiceModel.diceDatas
    ```
    
      
    
- **DiceView 내부에 있는** `**tableView**` **의** `**dataSoucre**`**와** `**delegate**` **구현하기**
    
    ```Swift
    private lazy var diceView: DiceView = {
            let view = DiceView()
            view.tableView.dataSource = self
            view.tableView.delegate = self
            return view
        }()
    ```
    
      
    
    위 코드처럼 self 값을 넣어줍니다. 그럼 오류가 생길겁니다. 위 개념 설명에서 보았듯이 꼭 구현해야 하는 메서드가 구현이 되어있지 않기 때문입니다. `exension` 을 사용하여 구현해보도록 하겠습니다.
    
      
    
- **Extension을 통해** `**dataSoucre**`**와** `**delegate**` **구현**
    
    - ViewController 코드 바깥에 `extension`을 작성하여 두 메소드를 작성합니다.
    - 이제 두 메서드에 값을 넣어주면 됩니다.
    
    ```Swift
    extension DiceViewController: UITableViewDataSource, UITableViewDelegate {
        func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
            <\#code#>
        }
        
        func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
            <\#code#>
        }
    }
    ```
    
      
    
- `**numberOfRowsInSection**` **구현하기**
    
    - `numberOfRowsInSection`: `data` 배열의 요소 개수만큼 행의 개수를 반환합니다.
    - 셀의 개수는 더미 데이터의 갯수 만큼 필요하니 `count` 속성을 사용하여 채울 수 있도록 합니다.
    
    ```Swift
    func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
            data.count
        }
    ```
    
      
    
- `**cellForRowAt**` **구현하기**
    
    - `DiceCell`을 `dequeueReusableCell` 메서드를 통해 재사용하고, `data`의 해당 항목을 셀에 설정합니다.
    - 아래 코드처럼 작성하면 됩니디. 아까 셀을 작성할 때 `public func configure` 를 구현하여 내부 컴포넌트들의 값을 바꿀 수 있도록 했습니다. 이 메소드에서 사용됩니다.
    
    ```Swift
     func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
            guard let cell = tableView.dequeueReusableCell(withIdentifier: DiceCell.identifier, for: indexPath) as? DiceCell else {
                return UITableViewCell()
            }
            
            cell.configure(model: data[indexPath.row])
            
            return cell
        }
    ```
    
      
    
- **전체 코드**
    
    ```Swift
    import UIKit
    
    class DiceViewController: UIViewController {
        
        let data = dummyDiceModel.diceDatas
    
        override func viewDidLoad() {
            super.viewDidLoad()
            self.view = diceView
        }
        
        private lazy var diceView: DiceView = {
            let view = DiceView()
            view.tableView.dataSource = self
            view.tableView.dataSource = self
            return view
        }()
    }
    
    
    extension DiceViewController: UITableViewDataSource, UITableViewDelegate {
        func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
            data.count
        }
        
        func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
            guard let cell = tableView.dequeueReusableCell(withIdentifier: DiceCell.identifier, for: indexPath) as? DiceCell else {
                return UITableViewCell()
            }
            
            cell.configure(model: data[indexPath.row])
            
            return cell
        }
    }
    ```
    

### 8. 전체 코드 및 실행 결과 화면

모델 코드, 뷰 코드, 뷰 컨트롤러 코드를 순서대로 보이도록 하겠습니다.

코드의 아래에 최종 결과 사진이랑 영상도 같이 첨부했습니다

  

- **Model 코드**
    
    ```Swift
    import Foundation
    
    struct DiceModel {
        let diceImage: String
        let diceName: String
    }
    
    final class dummyDiceModel {
        static let diceDatas: [DiceModel] = [
            DiceModel(diceImage: "dice 1.png", diceName: "주사위 1"),
            DiceModel(diceImage: "dice 2.png", diceName: "주사위 2"),
            DiceModel(diceImage: "dice 3.png", diceName: "주사위 3"),
            DiceModel(diceImage: "dice 4.png", diceName: "주사위 4"),
            DiceModel(diceImage: "dice 5.png", diceName: "주사위 5"),
            DiceModel(diceImage: "dice 6.png", diceName: "주사위 6")
        ]
    }
    ```
    
      
    
- **Cell 코드**
    
    ```Swift
    import UIKit
    import SnapKit
    
    class DiceCell: UITableViewCell {
        
        static let identifier = "DiceCell"
    
        override func awakeFromNib() {
            super.awakeFromNib()
            // Initialization code
        }
    
        override func setSelected(_ selected: Bool, animated: Bool) {
            super.setSelected(selected, animated: animated)
    
            // Configure the view for the selected state
        }
        
        override init(style: UITableViewCell.CellStyle, reuseIdentifier: String?) {
            super.init(style: style, reuseIdentifier: reuseIdentifier)
            self.setViews()
            self.setConstaints()
        }
        
        override func prepareForReuse() {
            super.prepareForReuse()
            self.diceImageView.image = nil
            self.diceName.text = nil
        }
        
        required init?(coder: NSCoder) {
            fatalError("init(coder:) has not been implemented")
        }
        
        private lazy var diceImageView: UIImageView = {
            let imageView = UIImageView()
            
            /* 주사위 이미지 값은 ViewController에서 작성하게 됩니다. */
            // imageView.image = UIImage(named: "여기에 더미 데이터 값이 들어갑니다.")
            
            return imageView
        }()
        
        private lazy var diceName: UILabel = {
            let name = UILabel()
            name.font = UIFont.systemFont(ofSize: 20)
            name.textColor = UIColor.black
            
            /* 주사위 이름 값은 ViewController에서 작성하게 됩니다. */
            //name.text = "여기에 더미 데이터 값이 들어갑니다."
            
            return name
        }()
        
        private func setViews() {
            self.addSubview(diceImageView)
            self.addSubview(diceName)
        }
        
        private func setConstaints() {
            diceImageView.snp.makeConstraints {
                $0.top.equalToSuperview().offset(11)
                $0.left.equalToSuperview().offset(13)
                $0.bottom.equalToSuperview().offset(-10)
                $0.width.height.equalTo(75)
            }
            
            diceName.snp.makeConstraints {
                $0.top.equalToSuperview().offset(36.5)
                $0.left.equalTo(diceImageView.snp.right).offset(87)
                $0.right.equalToSuperview().offset(-144)
            }
        }
        
        public func configure(model: DiceModel) {
            self.diceImageView.image = UIImage(named: model.diceImage)
            self.diceName.text = model.diceName
        }
    }
    ```
    
      
    
- **View 코드**
    
    ```Swift
    import UIKit
    import SnapKit
    
    class DiceView: UIView {
    
        override init(frame: CGRect) {
            super.init(frame: frame)
            self.backgroundColor = .white
            setViews()
            setConstaints()
        }
        
        required init?(coder: NSCoder) {
            fatalError("init(coder:) has not been implemented")
        }
        
        private lazy var title: UILabel = {
            let label = UILabel()
            label.text = "주사위 테이블 뷰 만들기"
            label.font = UIFont.systemFont(ofSize: 20, weight: .bold)
            label.textColor = UIColor.black
            return label
        }()
        
        public lazy var tableView: UITableView = {
            let table = UITableView()
            table.register(DiceCell.self, forCellReuseIdentifier: DiceCell.identifier)
            table.separatorStyle = .singleLine
            return table
        }()
        
        private func setViews() {
            self.addSubview(title)
            self.addSubview(tableView)
        }
        
        private func setConstaints() {
            title.snp.makeConstraints {
                $0.top.equalToSuperview().offset(50)
                $0.left.equalToSuperview().offset(12)
                $0.right.equalToSuperview().offset(-183)
                $0.height.equalTo(24)
            }
            
            tableView.snp.makeConstraints {
                $0.top.equalTo(title.snp.bottom).offset(14)
                $0.left.right.bottom.equalToSuperview()
            }
        }
    }
    ```
    

- **ViewController 코드**
    
    ```Swift
    import UIKit
    
    class DiceViewController: UIViewController {
        
        let data = dummyDiceModel.diceDatas
        
        override func viewDidLoad() {
            super.viewDidLoad()
            self.view = diceView
            
        }
        
        private lazy var diceView: DiceView = {
            let view = DiceView()
            view.tableView.dataSource = self
            view.tableView.dataSource = self
            return view
        }()
    }
    
    
    extension DiceViewController: UITableViewDataSource, UITableViewDelegate {
        func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
            data.count
        }
        
        func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
            guard let cell = tableView.dequeueReusableCell(withIdentifier: DiceCell.identifier, for: indexPath) as? DiceCell else {
                return UITableViewCell()
            }
            
            cell.configure(model: data[indexPath.row])
            
            return cell
        }
    }
    ```
    
      
    
- **결과 화면**
    
    ![[스크린샷_2024-09-20_오전_10.15.38.png]]
    

  

## 💻 3주차 과제

---

> [!important] **화면 구현에 필요한 레이아웃과 리소스는 아래 피그마를 참고해주세요!**
> 
>   
>   
> **테이블뷰를 이용하여 SAVED 탭 화면을 구현**  
> 할 것입니다.  
> 또한, 마이페이지와 프로필 관리 페이지를 만들어 뷰를 연결하고,  
> **로그인 화면에서 입력한 이메일과 비밀번호를 UserDefaults에 저장할 수 있도록 하고 그 값을 프로필 관리 페이지에서 확인 및 변경**할 수 있도록 하려 합니다!  
>   
> 
> [https://www.figma.com/embed?embed_host=notion&url=https%3A%2F%2Fwww.figma.com%2Fdesign%2F47IuhJxc7LFTwOYWtDgTdi%2FiOS-%EC%9B%8C%ED%81%AC%EB%B6%81%3Fnode-id%3D322-1594%26t%3DfbhdHUCVzOTAX95j-1](https://www.figma.com/embed?embed_host=notion&url=https%3A%2F%2Fwww.figma.com%2Fdesign%2F47IuhJxc7LFTwOYWtDgTdi%2FiOS-%EC%9B%8C%ED%81%AC%EB%B6%81%3Fnode-id%3D322-1594%26t%3DfbhdHUCVzOTAX95j-1)

> [!important] 아래 체크 사항에 맞춰 뷰를 완성해주시기 바랍니다.

### 1. SAVED 탭 Cell, Model 구

> [!important] **실습 체크리스트**
> 
> - [x] 테이블 뷰의 셀을 관리하는 폴더 및 파일을 생성합니다.
> - [x] 테이블 뷰 셀 디자인에 맞춰 `SnapKit`을 사용하여 완성합니다.
> - [x] 3주차 실습에서 진행했듯이, ==**더미 데이터를 만들어 최소 10개 이상의 데이터**==를 채워 넣습니다.

### 2. SAVED 탭 TableView 구현

> [!important] **실습 체크리스트**
> 
> - [x] View 파일을 생성하여 테이블 뷰를 구현합니다.
> - [x] 테이블 뷰 위의 “전체 10개”는 Cell에 사용하는 더미 데이터의 개수에 맞춰 동적으로 변하도록 합니다.
> - [x] ViewController에 위에 작성한 뷰를 넣어줍니다.
> - [x] ==**Extension**==으로 ==**TableView의 Delegate와 DataSource 메서드를 구현**==합니다.

### 3. LoginView Model 수정

> [!important] **실습 체크리스트**
> 
> - [x] 지난 주차에 만들었던 로그인 뷰의 모델을 ==**UserDefaults에 저장될 수 있도록 리팩토링**==합니다.
> - [x] 로그인 화면에서 입력한 이메일과 비밀번호가 UserDefaults에 저장되도록 합니다.

### 4. 마이페이지 뷰 구현

> [!important] **실습 체크리스트**
> 
> - [x] 마이페이지를 구현합니다.
>     - [x] 프로필 사진은 아무 사진 넣어서 이미지뷰를 통해 나타나도록 합니다.
>     - [x] 닉네임과 팔로워 수, 팔로잉은 라벨을 사용하여 자유롭게 넣어주세요
> - [x] 프로필 관리와 프로필 공유는 버튼으로 구현해주세요
>     - [x] 프로필 관리 버튼을 누르면 프로필 관리 페이지로 넘어갈 수 있도록 합니다.
>     - [x] 프로필 공유 버튼을 누르면 아무런 액션이 없습니다.

### 5. 프로필 관리 뷰 구현

> [!important] **실습 체크리스트**
> 
> - [x] 마이페이지의 프로필 이미지를 프로필 관리 뷰의 프로필 이미지와 동일하게 표시합니다.
>     - [x] ==**마이페이지에서 사용한 프로필 이미지**==를 ==**프로필 관리 뷰로 전달하여 해당 이미지가 표시**==되도록 합니다.
> - [x] UserDefaults에 저장된 유저 이메일과 비밀번호가 프로필 정보 ==**텍스트 필드**==에 출력되도록 합니다.
>     - [x] 변경 버튼을 누르기 전까지 텍스트 필드의 값을 수정할 수 없도록 합니다.
>     - [x] 텍스트 필드에서 `isUserInteractionEnabled` 속성을 활용하면 수정 활성/비활성을 할 수 있습니다.
> - [x] 변경 버튼을 누르면 버튼의 텍스트가 “확인”으로 바뀌도록 합니다.
>     - [x] 변경 버튼이 눌린 후, 텍스트 필드의 값을 수정할 수 있습니다.
>     - [x] 값을 수정하고 “확인”을 누르면 수정된 값이 새롭게 UserDefaults에 저장되도록 합니다.

### 6. 과제가 완성 되었다면 깃허브 링크와 시연 영상을 첨부해주세요!

> [!important] **시연 영상 체크리스트**
> 
> - [x] `AutoLayout`이 잘 적용되어 있음을 확인할 수 있나요?
>     - [x] `iPhone 15 Pro`, `iPhone 13 mini` 시뮬레이터에서 테스트한 내용이 모두 들어가게 영상을 업로드해주세요.
> 
>   
> ==**체크리스트 항목을 모두 만족하는 영상만 업로드**==해주시길 바랍니다.

> **깃허브 링크 임베드**

> [!info] 7th_UMC_iOS/쿠트_김의택/week01_mission at 쿠트_김의택 · TUK-UMC/7th_UMC_iOS  
> 7th UMC iOS.  
> [https://github.com/TUK-UMC/7th_UMC_iOS/tree/%EC%BF%A0%ED%8A%B8_%EA%B9%80%EC%9D%98%ED%83%9D/%EC%BF%A0%ED%8A%B8_%EA%B9%80%EC%9D%98%ED%83%9D/week01_mission](https://github.com/TUK-UMC/7th_UMC_iOS/tree/%EC%BF%A0%ED%8A%B8_%EA%B9%80%EC%9D%98%ED%83%9D/%EC%BF%A0%ED%8A%B8_%EA%B9%80%EC%9D%98%ED%83%9D/week01_mission)  

> **시연 영상 업로드** ==(영상 개수 제한 X)==

![[13mini.mp4]]

![[16pro.mp4]]

## 🤔 3주차 트러블 슈팅

---

### 2025년 1월 2일 오후 6:15 문제 이름

### 문제 상황

---

### 해결 과정

---

### 참고 자료

---

## 📌 이번 주차에는 이런 내용을 학습했어요!

---

==추가적으로 과제를 하면서 스스로 공부해본 내용이 있다면 이곳에 자유 양식으로 정리해 보세요!==

## ❓ 이런 질문이 있어요!

---

워크북을 진행하면서 궁금했던 점 또는 해결하지 못한 부분을 미리 작성하고 스터디에서 함께 논의해 보세요!  
해결하지 못한 질문이나 궁금한 점이 있다면 언제든지 편하게 DM 주세요 🙋‍♀️  

  

---

Copyright © 2024 Lee Youjin All rights reserved.

Copyright © 2024 Jeong Euichan All rights reserved.