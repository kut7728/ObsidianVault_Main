- [[#📋 학습 목표]]
- [[#✋ 잠깐! 스터디 인증샷 찍으셨나요?]]
- [[#🔥 4주차 개념 설명]]
    - [[#1️⃣ UICollectionView는 무엇일까요?]]
    - [[#2️⃣ UICollecitonViewFlowLayout은 무엇일까요?]]
    - [[#3️⃣ UISegmentedControl은 무엇일까요?]]
- [[#🔥 4주차 개념 점검]]
- [[#📚 4주차 실습]]
    - [[#1️⃣ UISegmentedControl 구현하기]]
    - [[#2️⃣ UICollectionView 구현하기]]
- [[#💻 4주차 과제]]
    - [[#1. 메인 화면 레이아웃을 구현해주세요!]]
    - [[#2. 과제가 완성 되었다면 깃허브 링크와 시연 영상을 첨부해주세요!]]
- [[#🤔 4주차 트러블 슈팅]]
    - [[#@2024년 11월 8일 오전 8:37 배너 크기 맞추기]]
    - [[#@2024년 11월 8일 오후 9:29 세그먼트 뷰 밑줄넣기]]
- [[#📌 이번 주차에는 이런 내용을 학습했어요!]]
- [[#❓ 이런 질문이 있어요!]]

## 📋 학습 목표

---

- `UICollectionView`의 개념에 대해 이해하고 구현할 수 있다.
- `UISegmentedControl`에 대해 이해하고, 직접 구현해볼 수 있다.

  

## ✋ 잠깐! 스터디 인증샷 찍으셨나요?

---

> [!important] 스터디 시작 전 ==**스터디 인증샷을 촬영**==해주세요!
> 
> 스터디는 대면이 원칙이며, 비대면 스터디의 경우에도 최대한 카메라를 킨 후 진행해주세요.
> 
> 아래 임베드 블록에 인증샷을 임베드해 주시면 됩니다 🫶

- 사진
    
    [](https://www.notion.soundefined)
    

  

## 🔥 4주차 개념 설명

---

### 1️⃣ UICollectionView는 무엇일까요?

> [!important] **An object that manages an ordered collection of data items and presents them using customizable layouts.**
> 
> ==정렬된 데이터 항목 컬렉션을 관리하고 사용자 지정 가능한 레이아웃을 사용하여 표시하는 개체입니다.==

![[IMG_9421.jpeg]]

> 3주차에 배웠던 `UITableView`는 가로 스크롤을 지원하지 않는다고 했던 것을 기억하시나요?
> 
> `UITableView` 와 `UICollectionView` 는 데이터 아이템 리스트를 관리하고 화면에 출력한다는 점에서는 유사한 속성을 가지고 있습니다.
> 
> 전체적인 동작 원리, `UIScrollView`의 상속을 받는 것, `Delegate` 패턴을 활용하는 것도 비슷하죠!
> 
> `UICollectionView` 는 `UITableView` 보다 조금 더 복잡하고 다양한 형태로 커스터마이징이 가능하게 반복적인 형태의 구조를 만듭니다. 더 복잡한 뷰를 구성한다고 생각하시면 이해가 쉬울 것 같아요!
> 
> 우리가 자주 사용하는 인스타그램의 게시물 그리드와 스토리 하이라이트가 바로 `CollectionView`를 이용해 만들어졌는데요!
> 
> 가로 스크롤 또는 그리드 형태의 데이터 리스트는 모두 `UICollectionView` 를 이용한다고 생각하시면 됩니다.

  

아까 공식 문서의 내용을 살펴볼 때 `사용자 지정 가능한 레이아웃을 사용하여 표시한다` 는 내용이 있었는데요!

`UICollectionView` 는 콘텐츠의 레이아웃이나 배치 관리를 위해 데이터와 컨텐츠 표시 방식에 `UICollectionViewLayout` 을 사용합니다.

따라서 `UICollectionView`를 사용하려면 `UICollectionViewLayout` 이 반드시 필요합니다!

이번 워크북에서는 `UICollectionViewLayout` 의 종류 중 하나인 `UICollecitonViewFlowLayout` 에 대해 알아볼 예정입니다.

그 전에 잠깐 `UICollectionView` 가 어떻게 화면에 데이터를 표시하는지에 대해 짚고 넘어가보도록 할게요!

`UICollectionView` 는 화면에 표시할 데이터(`Content-Related Objects`)와 그 데이터를 스크린에 표시하고 배치하는 방법(`Layout-Related Data Objects`)으로 구성됩니다.

오른쪽 그림을 보며 `UICollectionView`가 어떻게 데이터를 관리하고, 배치해 보여주는지 자세히 알아봅시다!

> `**DataSource**` **및** `**Delegate**`은 화면에 보여줄 데이터(Cell)를 관리합니다.
> 
> 단순히 데이터 뿐만 아니라 셀의 선택 또는 강조 등 셀과 관련된 기능들까지 관리해요!

> `**Collection view layout**` 은 해당 셀이 어느 위치에 속할지 결정합니다.
> 
> 이후 하나 이상의 `layout attribute` 객체를 `UICollectionView` 에 전달해요!

이후 레이아웃 정보와 실제 셀들의 정보를 취합해 `UICollectionView` 는 실제 화면에 표시되는 것입니다.

`UICollectionView` 인터페이스를 생성할 때는 오른쪽 그림처럼 컬렉션뷰 객체가 가장 중심이 됩니다.

따라서 먼저 `UICollectionView` 객체를 생성한 이후에 관련 객체(`layout`, `data source`)등을 생성해야 해요!

즉, `UICollectionView` 객체를 만들기 전에 다른 객체를 생성해서는 안된다는 이야기입니다.

![[Assets/image 10.png|image 10.png]]

`UICollectionView` 는 `UITableView`와 동일하게 재사용 큐(`reuse queue`)를 사용합니다.

아마 알고 계시겠지만 간단하게 큐(`Queue`)의 개념부터 다시 짚고 넘어가보겠습니다.

> 큐(`Queue`)는 `FIFO`(First In First Out) 형식을 띄는 대표적인 자료 구조입니다.
> 
> `Back` 쪽으로는 데이터의 삽입, `enqueue`가 일어나고 `Front` 쪽으로는 데이터의 삭제, `dequeue`가 일어납니다.
> 
> 현실에서 들 수 있는 가장 대표적인 예시로 매표소 줄서기가 있습니다! 먼저 줄을 선 사람이 먼저 표를 구매하고 먼저 매표소를 빠져나가는 구조를 생각하시면 되겠습니다.

그러면 왜 `UICollectionView` 에서 큐의 개념이 등장하는 걸까요?

![[Assets/image 1 3.png|image 1 3.png]]

![[Assets/image 2 3.png|image 2 3.png]]

`UICollectionView` 는 다양한 형태로 반복적인 형태의 구조를 만든다고 말씀드렸는데요!

그 말인 즉슨 많은 데이터를 화면에 뿌린다는 뜻이 되겠죠?

물론 10개, 20개 정도의 적은 데이터가 화면에 뿌려질 수도 있겠지만 … 만약 100개, 1000개로 데이터의 수가 늘어난다면 어떻게 될까요?

> 화면의 크기는 한정되어 있기 때문에 만약 1000개의 데이터가 있다면 우리는 스크롤을 올려 데이터를 확인하게 될겁니다.
> 
> 그런데 이 모든 데이터를 셀에 하나하나 등록시켜야 한다면 … 메모리 낭비가 너무 심하지 않을까요? 스크롤을 내리는데 앱이 터지면 어쩌죠?
> 
> 이러한 메모리 낭비를 막기 위해 셀이 스크린에서 벗어났을 때 셀을 재사용 큐에 넣고, 이후 스크린에 다시 나타날 때 셀들을 차례대로 재활용하는 것입니다.

이런 방식을 사용하면 모든 셀을 메모리에 한번에 할당하지 않아도 되니 효율적이고, 앱이 터지지도 않겠죠!

대신 이 방법을 사용했을 때의 문제는 셀을 재사용하면서 셀의 선택 상태나 데이터가 초기화되지 않고 그대로 올라오는 경우가 생긴다는 건데요!

이러한 경우를 방지하기 위해 `prepareForReuse`를 사용합니다. 함께 알아볼까요?

> [!important] **When the collection view dequeues your view for use, it calls this method before the corresponding dequeue method returns the view to your code. Override this method in your subclass to reset properties to their default values and make the view ready to use again. Don’t use this method to assign any new data to the view; that’s the responsibility of your data source object.**<br><br>
> 
> ==CollectionView가 사용자의 뷰 대기열을 해제하면 해당 대기열 해제 메서드가 뷰를 코드로 반환하기 전에 이 메서드를 호출합니다. 하위 클래스에서 이 메서드를 재정의하여 속성을 기본값으로 재설정하고 뷰를 다시 사용할 준비가 되도록 합니다. 이 메서드를 사용하여 뷰에 새 데이터를 할당하지 마세요, 그건 데이터 소스 개체의 책임입니다.==

읽어보니 셀이 스크린 밖으로 나가 재사용 큐로 다시 들어갔을 때 `prepareForReuse` 가 호출된다는 것 같네요!

`prepareForReuse` 는 셀이 재사용되기 전에 호출되어 셀을 초기화하는 역할을 수행합니다.

`UITableView`와 `UICollectionView` 모두에서 사용될 수 있어요.

`UITableViewCell`을 구현하는 클래스와 `UICollectionViewCell`을 구현하는 클래스 내부에서 구현됩니다.

```Swift
class ReuseCell: UICollectionViewCell {
		let imageView = UIImageView()
		
    override func prepareForReuse() {
        super.prepareForReuse()
        
        imageView.image = nil
    }
}
```

위와 같이 셀 이미지의 재사용을 막기 위해 `imageView`의 `image`를 초기화 할 수 있습니다.

![[Assets/image 3 2.png|image 3 2.png]]

아까 화면에 보여줄 데이터(Cell)를 관리할 때 `Delegate` 와 `DataSource` 를 사용한다고 말씀드렸는데요!

이 두 개념에 대해 조금 더 자세히 알아보겠습니다. 먼저 `UICollectionViewDelegate` 에 대해 조금 자세히 알아볼까요?

먼저 `Delegate`에 대한 개념을 약간 짚고 넘어가겠습니다. `Delegate`란 무엇일까요?

> 단어의 의미 상 `Delegate` 는 `위임하다`, `대리하다` 라는 뜻을 가지고 있죠! iOS 개발에서 `Delegate`라는 단어는 꽤 여러 번 등장하니 잘 기억해두시길 바랍니다.
> 
> iOS 개발에서도 `Delegate`는 비슷한 의미로 이해하시면 됩니다. 객체가 해야 할 일을 다른 객체에게 위임한다고 생각하시면 되는데요.
> 
> ~~이거 완전 짬때리는 거 아니야?~~ 라는 생각이 드실 수 있지만 사실 그런 건 아닙니다.
> 
> Swift는 객체지향 언어라고 0주차에서 말씀드렸는데요. `Delegate`는 Swift의 객체지향적 성격을 띄고 있는 개념입니다.
> 
> 객체지향 프로그래밍에서는 하나의 객체가 모든 일을 하지 않고 일들의 일부를 다른 객체에게 **위임**합니다.
> 
> 기능을 위임할 수 있는 객체가 있다는 건 객체 내에서 직접 구현해야 하는 부분이 적어지는 것이기 때문에 효율성 면에서 장점을 가진다고 볼 수 있는데요!
> 
> 객체지향 관련 내용은 6주차에 자세하게 배워볼 예정이니 이번 주차에서는 간단하게만 하고 넘어가도록 하겠습니다!

`UICollectionViewDelegate` 는 간단하게 이야기해서 `UICollectionView` 의 기능을 다른 객체에 위임하는 것입니다.

보통 `UICollectionViewDelegate` 는 `ViewController`에서 선언되기 때문에 `ViewController`가 `UICollectionView` 의 기능을 일부 위임받는다고 생각해볼 수 있겠네요!

아까 `Delegate` 가 화면에 보여줄 데이터(Cell)를 관리한다고 말씀드렸는데요, 그러면 `ViewController` 는 `UICollectionView` 의 데이터 관리 기능을 위임받는다고 생각해볼 수 있겠네요!

그러면 이정도로 `UICollectionViewDelegate` 를 이해한 후 공식 문서의 설명을 보도록 합시다.

> [!important] **The methods adopted by the object you use to manage user interactions with items in a collection view.**
> 
> ==CollectionView에서 아이템과 사용자 상호 작용을 관리하는 데 사용하는 객체가 채택한 메서드입니다.==

> `UICollectionViewDelegate` 는 곧 아이템과 사용자 상호 작용과 관련된 기능들을 위임하기 위한 메서드겠군요!
> 
> 어떤 메서드들이 있는지 한번 살펴보겠습니다.

![[스크린샷_2024-09-29_오후_2.35.20.png]]

> `shouldSelectItemAt`, `didSelectItemAt`, `shouldDeselectItemAt` 등 사용자가 아이템을 눌렀을 때, 선택 해제했을 때 등 상호작용에 관련된 내용들이 주를 이루고 있네요!
> 
> `UICollectionViewDelegate` 는 사용자와 Cell 사이 상호작용을 관리하는 메서드들을 `ViewController`에 위임하기 위한 프로토콜로 이해해보면 좋을 것 같습니다.

그렇다면 `UICollectionViewDataSource` 는 어떤 역할을 할까요?

  

> [!important] **The methods adopted by the object you use to manage data and provide cells for a collection view.**
> 
> ==데이터를 관리하고 CollectionView에 Cell을 제공하는 데 사용하는 객체에서 채택한 메서드입니다.==

> `UICollectionViewDelegate` 가 **셀과 사용자 간 상호작용**과 관련된 부분을 담당했다면, `UICollectionViewDataSource` 는 **데이터 관리**와 관련된 부분을 담당하는 것 같네요!
> 
> 이번에도 어떤 메서드들이 있는지 한번 살펴보겠습니다.

> 여기에서는 `**numberOfItemsInSection**`**,** `**cellForItemAt**` 에 집중할 필요가 있습니다.
> 
> `UICollectionViewDelegate` 를 채택했을 때는 필수로 구현해야 하는 메소드가 없었지만 `UICollectionViewDataSource` 를 채택했을 때는 위 두 메소드를 필수적으로 구현해야 하기 때문입니다.
> 
> `**numberOfItemsInSection**` **은** 이 `UICollectionView` 에 몇 개의 셀을 띄워주어야 하는지를 `Int` 타입 정수로 반환합니다.
> 
> `UICollectionView` 가 몇 개의 셀로 이루어져 있는지 구현하는 부분이라고 보시면 되겠습니다.
> 
> `**cellForItemAt**` **은** 해당 셀에 어떤 데이터가 들어가야 할 지 구현하는 부분입니다. 가장 중요한 부분이겠죠?
> 
> 이 부분은 실습에서 어떻게 구현하는지, 어떻게 데이터가 들어가는지 조금 더 자세히 알아보도록 하겠습니다.

![[스크린샷_2024-09-29_오후_2.42.59.png]]

### 2️⃣ UICollecitonViewFlowLayout은 무엇일까요?

> [!important] **A layout object that organizes items into a grid with optional header and footer views for each section.**
> 
> ==각 섹션에 대한 머리글 및 바닥글 보기 옵션을 사용하여 항목을 그리드로 구성하는 레이아웃 객체입니다.==

`UICollecitonViewFlowLayout` 는 애플에서 제공하는 `UICollectionViewLayout` 의 한 종류로, `UICollectionView` 의 아이템을 어떻게 배치할지 결정하는 레이아웃입니다.

`UICollecitonViewFlowLayout` 이라고 불리는 이유는 이름대로 자연스럽게 흐르듯 아이템을 순차적으로 배치하기 때문입니다.

한 행의 공간이 모두 채워지면 다음 행으로 넘어가는 선형 배치의 형식을 띄고 있어 `FlowLayout` 이라고 부르는 것이죠!

오른쪽 그림의 화살표로 이해해보시면 조금 더 쉬울 것 같습니다.

`UICollecitonViewFlowLayout` 을 이용하면 아이템의 크기나 행의 간격, 섹션의 여백, 스크롤의 방향이나 유무 등 레이아웃 속성을 지정할 수 있습니다.

그리드 형태의 레이아웃에 많이 사용되지만 유연하고 동적인 인터페이스를 만들 수 있어 다른 형태를 구현할 수도 있어요!

![[Assets/image 4 2.png|image 4 2.png]]

![[스크린샷_2024-09-29_오후_3.07.20.png]]

`UICollecitonViewFlowLayout` 에서 자주 사용하는 프로퍼티들에 대해 언급하고 넘어가도록 하겠습니다.

> `scrollDirection`은 `UICollectionView` 의 스크롤 방향을 결정합니다.
> 
> `.vertical` (세로)과 `.horizontal` (가로) 중 선택할 수 있어요!
> 
> `minimumInteritemSpacing` 은 셀 간의 최소 간격을 리턴해주는 프로퍼티입니다.
> 
> 같은 라인 내에 위치한 셀 간 간격을 설정한다고 생각해주시면 됩니다!
> 
> `minimumLineSpacing` 은 라인과 라인 사이의 최소 간격을 설정해주는 프로퍼티입니다.
> 
> `estimatedItemSize` 에 대해서는 실습에서 조금 더 알아보도록 할게요!

  

### 3️⃣ UISegmentedControl은 무엇일까요?

> [!important] **A horizontal control that consists of multiple segments, each segment functioning as a discrete button.**
> 
> ==여러 세그먼트로 구성된 가로형 컨트롤로, 각 세그먼트는 개별 버튼으로 작동합니다.==

> 애플 생태계의 일원이라면 한번 정도는 무조건 봤을 컴포넌트 중 하나인데요!
> 
> 요즘은 `UISegmentedControl` 을 대부분 커스텀해 사용하기 때문에 오른쪽 사진과 같은 기본형은 iOS 기본 내장 애플리케이션을 제외하고는 많이 보지 못하셨을 겁니다.
> 
> `UISegmentedControl` 은 각 세그먼트마다 인덱스를 부여하고, 세그먼트를 클릭할 때마다 선택된 세그먼트의 인덱스를 업데이트 해주는 원리를 가지고 있어요!
> 
> `UISegmentedControl` 의 경우 개념에서는 크게 다룰 부분이 없기 때문에 실습에서 직접 구현해보며 순차적으로 알아보도록 하겠습니다.

![[Assets/image 5 2.png|image 5 2.png]]

## 🔥 4주차 개념 점검

---

> [!important] `UITableView`와 `UICollectionView`의 공통점과 차이점은 무엇일까요?

- **여기에 답을 적어주세요!**
    
    리스트 형태의 데이터를 표시해줌, uicollectionview가 더 복잡한 뷰를 생성할 수 있음
    

> [!important] `UICollectionView` 에서 재사용 큐를 사용하는 이유는 무엇일까요?

- **여기에 답을 적어주세요!**
    
    리스트 형태의 데이터를 표시하는데 모든 데이터를 모두 불러오면 성능에 문제가 생기니 정해진 갯수만큼의 셀만 보여줌
    

> [!important] `UICollectionViewDelegate` 와 `UICollectionViewDataSource` 는 각각 어떤 역할을 할까요?

- **여기에 답을 적어주세요!**
    
    delegate 는 사용자와의 인터랙션을 담당하고
    
    datasource 는 데이터 관리부분을 담당
    

> [!important] `UICollecitonViewFlowLayout` 에서 스크롤의 방향을 결정하는 프로퍼티의 이름은 무엇일까요?

- **여기에 답을 적어주세요!**
    
    scrolldirection
    

## 📚 4주차 실습

---

> [!important] 4주차의 ==**모든 실습은 한 프로젝트에서 이루어집니다.**==
> 
> **실습 전에 프로젝트 파일을 생성**해주시고, ==**1주차에서 배웠던 것을 참고해서 코드를 통한 UI 생성을 위한 프로젝트 세팅을 사전에 진행**==해주세요!
> 
> 이후 과정은 사진을 보시면서 천천히 따라와주시면 됩니다.
> 
> 4주차 실습에서는 티니핑의 사진과 이름을 보여주는 `UICollectionView`를 구현해볼텐데요! 요즘 티니핑 이름 맞히기가 유행이라는데 실습 진행하시면서 티니핑 이름을 외울 수 있는 시간이 된다면 좋을 것 같습니다 ㅎㅎ
> 
> 화면 최상단에는 `티니핑`, `not 티니핑` 세그먼트를 가지고 있는 `UISegmentedControl`을 구현해 `티니핑` 세그먼트를 클릭했을 때는 티니핑 `UICollectionView`가 나타나도록, `not 티니핑` 세그먼트를 클릭했을 때는 휑~ 이라는 `UILabel`이 나타나도록 구현해보도록 하겠습니다.
> 
> [https://www.figma.com/embed?embed_host=notion&url=https%3A%2F%2Fwww.figma.com%2Fdesign%2F47IuhJxc7LFTwOYWtDgTdi%2FiOS-%EC%9B%8C%ED%81%AC%EB%B6%81%3Fnode-id%3D2063-1286%26t%3DHRdyrhj5o1Aojkds-1](https://www.figma.com/embed?embed_host=notion&url=https%3A%2F%2Fwww.figma.com%2Fdesign%2F47IuhJxc7LFTwOYWtDgTdi%2FiOS-%EC%9B%8C%ED%81%AC%EB%B6%81%3Fnode-id%3D2063-1286%26t%3DHRdyrhj5o1Aojkds-1)

### 1️⃣ UISegmentedControl 구현하기

### 1️⃣  실습을 위한 `ViewController` 와 `View`를 생성하고 `SceneDelegate`를 수정해주세요!

![[스크린샷_2024-09-29_오전_8.12.56.png]]

![[스크린샷_2024-09-29_오전_8.19.47.png]]

실습을 위해 `TeenipingViewController`와 `View`로 설정할 `TeenipingView`를 각각 생성해주세요!

`ViewController`와 `View`의 이름은 각각 원하시는 대로 설정해주셔도 됩니다 😀

이번 실습에서는 편의를 위해 `TeenipingViewController` 와 `TeenipingView` 로 통칭하겠습니다.

  

![[스크린샷_2024-09-29_오전_8.20.55.png]]

이후 `TeenipingViewController`에서 `TeenipingView` 를 선언해주세요.

`TeenipingView` 를 선언하셨다면 `viewDidLoad()` 에서 `view`를 `TeenipingView` 로 설정해주시면 됩니다!

  

![[스크린샷_2024-09-29_오전_8.14.10.png]]

`view`를 설정하셨다면 `SceneDelegate` 에서 `rootViewController`를 `TeenipingViewController로` 설정해주세요!

###  2️⃣ 화면에 필요한 컴포넌트와 `UISegmentedControl`을 선언해주세요!

![[스크린샷_2024-09-29_오전_8.28.32.png]]

이번 실습에 필요한 컴포넌트는 총 4가지입니다.

> `segmentedControl`: `티니핑`, `not 티니핑`을 눌렀을 때 화면에 나타나는 컴포넌트를 바꿔줄 `UISegmentedControl`
> 
> `divideLine`: `segmentedControl`과 `teenipingCollectionView`, `emptyLabel`을 구분해줄 `UIView`
> 
> `teenipingCollectionView`: 티니핑들의 정보를 표시해줄 `UICollectionView`
> 
> `emptyLabel`: `not 티니핑`을 눌렀을 때 나타날 `휑~` `UILabel`

각각의 컴포넌트를 `TeenipingView` 에 선언해보겠습니다!

`segmentedControl` 의 경우 다음과 같이 선언합니다.

```Swift
let segmentedControl = UISegmentedControl(items: ["티니핑", "not 티니핑"])
```

아이템으로 `티니핑`, `not 티니핑` 을 가지고 있는 `UISegmentedControl`을 선언한다고 이해하시면 되겠습니다.

`teenipingCollectionView` 도 다음과 같이 선언해주세요!

```Swift
let teenipingCollectionView = UICollectionView()
```

###  3️⃣ 컴포넌트들의 AutoLayout을 설정해주세요!

![[스크린샷_2024-09-29_오전_8.29.51.png]]

`Snapkit`을 이용해 피그마와 동일하도록 각 컴포넌트에 제약 조건을 추가해주겠습니다.

먼저 제약조건을 추가하기 전에 각 컴포넌트를 `View`에 `addSubview`해주는 과정을 거치도록 할게요!

`forEach` 문을 이용하면 왼쪽 코드와 같이 한번에 컴포넌트를 `addSubview` 할 수 있습니다.

![[스크린샷_2024-09-29_오전_8.33.51.png]]

피그마를 참고해 각 컴포넌트의 제약조건을 설정해주세요!

이후 앱을 실행해보도록 하겠습니다.

  

![[스크린샷_2024-09-29_오전_8.35.53.png]]

앱을 실행했더니 오류가 발생하네요!

```Swift
Thread 1: "UlCollectionView must be initialized with a non-nil layout parameter"
```

`UICollectionView` 는 nil 값이 아닌 레이아웃 파라미터와 함께 초기화되어야 한다고 합니다.

이게 어떤 의미인지는 조금 이후에 `UICollectionView` 를 구현하며 함께 알아보도록 할게요.

  

![[스크린샷_2024-09-29_오전_8.36.43.png]]

![[스크린샷_2024-09-29_오전_8.48.18.png]]

일단은 `segmentedControl` 이 구현되었는지 확인해야겠죠?

`teenipingCollectionView` 의 선언문, addSubView 부분, 제약조건 설정 부분을 전부 주석 처리해주세요!

이후 앱을 다시 실행시켜보겠습니다.

![[simulator_screenshot_6C8F85FA-68BA-42F3-933B-2D8EFFFD1D15.png]]

  

정상적으로 `segmentedControl` 이 구현되었음을 확인할 수 있습니다.

그런데 피그마와는 생긴 모양이 조금 다르네요…?

현재는 `segmentedControl` 을 따로 커스텀해주지 않았기 때문에 기본 `UISegmentedControl`로 나타나고 있습니다.

이제 피그마처럼 보이게 하기 위해 `segmentedControl` 을 커스텀해보겠습니다!

  

###  4️⃣ `UISegmentedControl`을 커스텀해주세요!

![[스크린샷_2024-09-29_오전_8.39.19.png]]

먼저 `segmentedControl` 의 제약조건을 일부 수정하겠습니다.

원래 `horizontalEdges` 에 맞춰져 있던 제약조건을 `centerX`에 맞추어줄 건데요!

커스텀하면서 `segmentedControl` 의 가로 길이가 늘어날 예정이기 때문에 길이를 제한하지 않도록 미리 설정해주는 것입니다.

  

![[스크린샷_2024-09-29_오전_8.46.38.png]]

  

이후 `segmentedControl` 의 선언부에서 `then` 을 이용해 속성을 선언해 보겠습니다.

만약 `then`의 사용법을 아직 모르신다면 2주차 Extra 워크북을 확인하시길 바랍니다!

```Swift
let segmentedControl = UISegmentedControl(items: ["티니핑", "not 티니핑"]).then {
        $0.setBackgroundImage(UIImage(), for: .normal, barMetrics: .default)
        $0.setBackgroundImage(UIImage(), for: .selected, barMetrics: .default)
        $0.setBackgroundImage(UIImage(), for: .highlighted, barMetrics: .default)
        $0.setDividerImage(UIImage(), forLeftSegmentState: .selected, rightSegmentState: .normal, barMetrics: .default)
        
        $0.setTitleTextAttributes(
            [
                NSAttributedString.Key.foregroundColor: UIColor.black,
                .font: UIFont.systemFont(ofSize: 16, weight: .light)
            ],
            for: .normal
        )
        $0.setTitleTextAttributes(
              [
                NSAttributedString.Key.foregroundColor: UIColor.black,
                .font: UIFont.systemFont(ofSize: 16, weight: .bold)
              ],
              for: .selected
            )
    }
```

코드는 다음과 같습니다.

`.normal`과 `.selected`, `.highlighted`에 따라 뒷 배경을 없애주기 위해 `setBackgroundImage()` 를 `UIImage()` 로 설정해줍니다!

세그먼트가 선택되었을 때 글자가 굵어지는 효과를 표현하기 위해 `setTitleTextAttributes()` 를 이용해 각각 선택되었을 때(`.selected`)와 선택되지 않았을 때(`.normal`)의 `TextAttributes`를 설정합니다.

이후 다시 앱을 실행해보겠습니다.

![[Simulator_Screenshot_-_iPhone_15_Pro_-_2024-09-29_at_08.54.14.png]]

분명 세그먼트를 선택했을 때 글자가 굵어지도록 했는데 막상 앱을 실행시키니 아무것도 달라진게 없습니다.

앱을 실행시켰을 때 기본적으로 선택될 세그먼트를 설정해주지 않았기 때문인데요.

기본 세그먼트 설정은 인덱스를 이용합니다. 함께 볼까요?

![[스크린샷_2024-09-29_오전_8.55.02.png]]

```Swift
$0.selectedSegmentIndex = 0
```

아까 코드에 위의 코드가 추가된 게 보이시나요?

`UISegmentedControl` 에서 선택된 세그먼트는 인덱스를 활용해 관리됩니다.

`UISegmentedControl` 을 선언할 때 `items`를 배열로 선언했었죠! 그 배열의 인덱스를 가리키는 것입니다.

선언된 순서대로 화면에 표시되고, 인덱스 순서 또한 동일하다고 생각하시면 됩니다.

이제 다시 실행해볼까요?

![[simulator_screenshot_90E308CA-E666-46BE-8BAF-BC7A0ED74E1F.png]]

  

이제 초기 화면에서도 세그먼트가 잘 선택되어 있음을 확인할 수 있습니다.

  

###  5️⃣ `UISegmentedControl`의 인덱스 값이 업데이트 되었을 때 실행될 메서드를 연결해주세요!

![[스크린샷_2024-09-29_오전_9.01.04.png]]

  

```Swift
private func setupAction() {
        rootView.segmentedControl.addTarget(
            self,
            action: \#selector(segmentedControlValueChanged(segment:)),
            for: .valueChanged
        )
    }

@objc
private func segmentedControlValueChanged(segment: UISegmentedControl) {
   // TODO: segment 인덱스에 따라 collectionview 표시 여부 결정
}
```

`UISegmentedControl` 의 인덱스 값이 업데이트 되었을 때 실행될 메서드를 선언 및 연결하는 부분은 `TeenipingViewController` 에서 이루어져야 합니다.

먼저 실행될 메서드인 `segmentedControlValueChanged()` 를 선언합니다.

`UISegmentedControl` 의 인덱스에 따라 어떤 컴포넌트가 표시될지 분기 처리를 진행해야 하기 때문에 매개변수로 해당 `segment`를 받아올겁니다!

이후 `addTarget`을 연결할 `setupAction()` 메서드를 선언하고 `segmentedControl`의 인덱스가 바뀌었을 때(`.valueChanged`) 실행될 `segmentedControlValueChanged()`를 연결해주세요.

인덱스에 따라 분기처리를 진행하는 부분은 `CollectionView`를 구현한 이후에 진행하도록 하겠습니다!

### 2️⃣ UICollectionView 구현하기

### 1️⃣ `UICollectionView` 를 선언해주세요!

![[스크린샷_2024-09-29_오전_9.02.04.png]]

아까 주석처리했던 부분을 모두 풀어주세요!

이후 선언부에서 `UICollectionView`를 다시 작성하게 되면 자동완성에서 `(frame: collectionViewLayout: )` 를 확인할 수 있습니다. 클릭해주세요!

  

![[스크린샷_2024-09-29_오전_9.02.59.png]]

이후 `frame`은 `.zero`로, `collectionViewLayout`은 `UICollectionViewFlowLayout()`으로 설정해주시길 바랍니다.

🚨 ==**왼쪽 코드에는**== ==`**UICollectionViewFlowLayout**`== ==**이 아닌**== ==`**UICollectionViewLayout**`== ==**으로 설정되어 있습니다. 잘못 나와있는 부분이니 꼭**== ==`**UICollectionViewFlowLayout**`== ==**으로 설정하셔야 합니다!**==

```Swift
Thread 1: "UlCollectionView must be initialized with a non-nil layout parameter"
```

위에서 확인했던 `UlCollectionView`가 레이아웃 파라미터를 가지고 초기화되어야 한다는 오류는 `collectionViewLayout` 을 설정해주지 않아 생기는 오류였습니다.

`UlCollectionView` 는 선언 시 `collectionViewLayout` 을 꼭 선언해야 한다는 점에 유의하세요!

  

### 2️⃣ `TeenipingCollectionViewCell` 을 생성해주세요!

![[스크린샷_2024-09-29_오전_9.03.44.png]]

`CollectionView`도 `TableView`와 동일하게 구성 요소인 `Cell`을 클래스로 구현해야 합니다.

생성 화면에서 `UICollectionViewCell` 을 선택하신 후 파일을 생성해주세요!

  

![[스크린샷_2024-09-29_오전_9.04.30.png]]

`TeenipingCollectionViewCell` 파일을 생성하면 아예 빈 파일인 경우도, 기본 코드가 적혀 있는 경우도 있을텐데 상관 없이 아래 코드만 작성해주시면 됩니다!

```Swift
override init(frame: CGRect) {
    super.init(frame: frame)
}
    
required init?(coder: NSCoder) {
    fatalError("init(coder:) has not been implemented")
}
```

### 3️⃣ `TeenipingCollectionViewCell` 을 구현해주세요!

![[스크린샷_2024-09-29_오전_10.41.54.png]]

우리는 왼쪽과 같은 셀을 구현해야 하는데요!

티니핑의 사진과 티니핑의 이름으로 구성되어 있는 것 같네요.

코드로 함께 구현해보겠습니다.

![[스크린샷_2024-09-29_오전_9.07.57.png]]

`UIImageView`를 이용해 사진을, `UILabel`을 이용해 이름 라벨을 구현해보도록 하겠습니다!

  

![[스크린샷_2024-09-29_오전_9.09.41.png]]

이후 각각 `addSubview`를 진행해주시고 제약조건도 설정해주세요.

저는 `setupView` 함수에 담아 `init` 함수와 코드를 분리했습니다!

![[스크린샷_2024-09-29_오전_9.11.31.png]]

then을 이용해 `TeenipingCollectionView` 의 속성을 구현해 보겠습니다.

```Swift
let teenipingCollectionView = UICollectionView(frame: .zero, collectionViewLayout: UICollectionViewFlowLayout()).then {
        $0.backgroundColor = .clear
        $0.isScrollEnabled = false
        $0.register(TeenipingCollectionViewCell.self, forCellWithReuseIdentifier: )
    }
```

배경색은 `clear`로 설정하고, 데이터가 8개밖에 없기 때문에 스크롤 가능 여부는 `false`로 설정했습니다.

`CollectionView`는 선언 시 어떤 셀을 등록할 것인지, 해당 셀의 식별자는 무엇인지 등록해주어야 합니다. 해당 부분이 바로 `register`인데요!

식별자는 자유롭게 등록해주셔도 좋지만 이후 셀과 데이터를 바인딩하는 부분에서도 함께 사용해야 하고 여러 `CollectionView`를 한 `ViewController`에서 사용할 수도 있기 때문에 식별자는 `Cell` 파일 안에서 선언해 사용하는 것이 좋습니다.

![[스크린샷_2024-09-29_오전_9.12.58.png]]

```Swift
static let identifier = "TeenipingCollectionViewCell"
```

저는 이런 방식으로 식별자로 사용할 `identifier` 변수를 선언했습니다!

식별자 변수 이름과 내용은 임의로 설정해주시면 됩니다.

  

![[스크린샷_2024-09-29_오전_9.13.16.png]]

```Swift
$0.register(TeenipingCollectionViewCell.self, forCellWithReuseIdentifier: TeenipingCollectionViewCell.identifier)
```

이후 `TeenipingCollectionView` 의 속성 선언부에서 다음과 같이 사용할 수 있습니다.

  

![[스크린샷_2024-09-29_오전_9.15.22.png]]

이후에는 `UICollectionViewFlowLayout`의 속성을 선언해줄텐데요!

```Swift
let teenipingCollectionView = UICollectionView(frame: .zero, collectionViewLayout: UICollectionViewFlowLayout().then {
        $0.estimatedItemSize = .init(width: 162, height: 144)
        $0.minimumInteritemSpacing = 12
    }).then {
        $0.backgroundColor = .clear
        $0.isScrollEnabled = false
        $0.register(TeenipingCollectionViewCell.self, forCellWithReuseIdentifier: TeenipingCollectionViewCell.identifier)
    }
```

각 셀의 사이즈를 `estimatedItemSize`로 미리 선언해주도록 하겠습니다.

`estimatedItemSize` 는 위 코드처럼 `.init`을 이용해 `width`와 `height`를 미리 설정해주는 방법도 있지만

```Swift
$0.estimatedItemSize = UICollectionViewFlowLayout.automaticSize
```

제약조건을 충돌 없이 잘 설정하면 위와 같은 방법도 활용해볼 수 있으니 참고하시면 좋을 것 같습니다.

### 3️⃣ `TeenipingCollectionView` 에 데이터를 바인딩 해주세요!

![[스크린샷_2024-09-29_오전_9.16.49.png]]

이제는 레이아웃을 모두 설정했으니 데이터를 바인딩해볼 차례입니다.

데이터 바인딩을 위해 `teenipingCollectionView`의 `dataSource` 속성을 `self`로 설정해주세요.

그러면 왼쪽과 같이 오류 코드를 발견하실 수 있으실텐데요.

![[스크린샷_2024-09-29_오전_9.17.24.png]]

당황하지 마시고 `extension` 을 아래 작성해주시고 `UICollectionViewDataSource` 프로토콜을 채택해주세요.

이래도 오류가 사라지지 않네요 … 침착하게 오류를 클릭해보면

```Swift
Do you want to add protocol stubs? [Fix]
```

라는 부분이 있습니다.

`UICollectionViewDataSource` 프로토콜에서 기본적으로 구현해야 하는 메서드가 두 개 있는데, 이 메서드를 구현하지 않았을 때 뜨는 오류입니다.

![[스크린샷_2024-09-29_오전_9.17.34.png]]

침착하게 `Fix` 버튼을 눌러주시면 Xcode에서 자동으로 두 메서드를 자동으로 추가해주는 것을 확인하실 수 있습니다.

오류도 사라졌네요! 다행입니다.

![[스크린샷_2024-09-29_오전_9.25.07.png]]

이제 데이터를 바인딩하기 위해 `TeenipingCollectionView` 에 들어갈 더미 데이터를 만들어보겠습니다.

먼저 피그마에서 사진을 `Export`한 후 다음과 같이 `Assets`에 드래그 앤 드랍으로 추가해보겠습니다.

사진을 모두 선택하신 후 오른쪽 인스펙터에서 `Scales`를 선택해주시고 `Single Scale`로 설정해주세요!

이미지 이름은 각 티니핑의 이름으로 설정해주시면 됩니다.

![[스크린샷_2024-09-29_오전_9.19.17.png]]

사진을 모두 세팅하셨다면 다시 돌아와서 `TeenipingModel` 이라는 구조체를 생성해주세요!

우리는 `TeenipingModel` 배열을 생성하고 그 안에 각 티니핑의 정보를 넣어 데이터 바인딩에 활용할 겁니다.

`TeenipingModel` 내에는 이미지 데이터와 이름 데이터를 받아오기 위한 변수를 선언해주세요!

  

![[스크린샷_2024-09-29_오전_9.25.44.png]]

이후에는 더미 데이터를 만들기 위해 `TeenipingModel` 의 `extension`을 선언해보겠습니다.

`extension` 에서는 직접 변수를 선언하고 저장할 수 없기 때문에 `TeenipingModel` 배열을 반환하는 `dummy`라는 메서드를 만들어주도록 할게요.

이후 `return` 될 배열에 각 티니핑의 정보를 넣어주도록 하겠습니다.

`image`를 입력하실 때는 `.`을 먼저 입력하시고 이미지 이름을 입력하시면 자동완성으로 이름이 표시됩니다.

해당되는 이름 클릭하시면 `.hachuping`과 같이 간편하게 입력할 수 있으니 참고해주세요!

![[스크린샷_2024-09-29_오전_9.27.06.png]]

다음과 같이 모든 티니핑의 정보를 작성하셨다면 이제 `CollectionView`에 바인딩해보도록 하겠습니다.

![[스크린샷_2024-09-29_오전_9.27.43.png]]

아까 `extension`을 통해 만들어 둔 두 메서드 중 `numberOfItemsInSection` 메서드를 먼저 채워보겠습니다.

`numberOfItemsInSection` 메서드는 이 `CollectionView`에 몇개의 데이터가 들어갈지를 `Int` 타입의 변수로 반환하는 메서드입니다.

```Swift
func collectionView(_ collectionView: UICollectionView, numberOfItemsInSection section: Int) -> Int {
        return TeenipingModel.dummy().count
    }
```

우리는 `TeenipingModel.dummy()` 의 갯수만큼 데이터를 바인딩하므로 `TeenipingModel.dummy().count` 를 반환해주도록 할게요!

  

![[스크린샷_2024-09-29_오전_9.29.01.png]]

  

`cellForItemAt` 메서드에는 어떤 내용이 표시될 지 구현해야 합니다.

이 메서드는 `UICollectionViewCell`을 반환하므로 셀을 선언한 후 데이터를 바인딩하고 바인딩 된 셀을 반환해주면 됩니다!

`guard let`을 이용해 옵셔널 바인딩을 함께 진행해줄 텐데요!

`cell`을 선언하고 만약 셀의 값이 nil일 경우 `UICollectionViewCell`을 반환해주도록 선언합니다.

이 때 `dequeueReusableCell`()을 이용하는데요. 재사용 큐에서 필요한 `cell`을 `dequeue` 하기 위한 함수입니다!

```Swift
guard let cell = collectionView.dequeueReusableCell(
            withReuseIdentifier: TeenipingCollectionViewCell.identifier,
            for: indexPath
        ) as? TeenipingCollectionViewCell else {
            return UICollectionViewCell()
        }
```

재사용 큐에서는 식별자를 통해 셀을 구분하는데요! 구분을 위해 `withReuseIdentifier` 를 받게 됩니다.

또한 행 식별을 위해 `indexPath` 도 함께 파라미터로 받는 것을 보실 수 있습니다.

위와 같이 `cell`을 선언하면 데이터를 바인딩 할 준비가 끝나게 됩니다!

![[스크린샷_2024-09-29_오전_9.30.11.png]]

이후 `cell`를 리턴해주는 구문도 작성해줍니다.

  

![[스크린샷_2024-09-29_오전_9.31.33.png]]

이후 각 셀의 인덱스에 맞게 `TeenipingModel.dummy()` 의 데이터를 바인딩합니다.

```Swift
let list = TeenipingModel.dummy()
        
cell.imageView.image = list[indexPath.row].image
cell.titleLabel.text = list[indexPath.row].name
```

![[스크린샷_2024-09-29_오전_9.34.24.png]]

이후 `ViewController`의 `ViewDidLoad` 부분에 `setupAction`과 `setupDelegate` 메서드를 추가해줍니다.

이제 정말 `CollectionView`에 데이터가 표시되기를 기대하며 앱을 실행해볼게요!

![[simulator_screenshot_1644782E-6C6A-4F79-A704-585ABE6E16D9.png]]

데이터가 각 셀에 알맞게 바인딩되어 `CollectionView`에 나타나는 것을 확인했습니다!

이제 `SegmentedControl`의 인덱스에 따라 각 컴포넌트를 어떻게 표시할지에 대해서만 실습해보도록 할게요.

### 4️⃣ `UISegmentedControl` 의 인덱스에 따라 분기 처리를 진행해주세요!

![[스크린샷_2024-09-29_오전_9.35.35.png]]

분기처리를 진행하기 전 `TeenipingView`에서 `emptyLabel`의 접근제어자 `private` 을 제거해주도록 하겠습니다.

`TeenipingViewController`에서 emptyLabel의 속성인 isHidden에 직접 접근해야 하기 때문인데요!

자세한 부분은 뒤에서 조금 더 알아보도록 하겠습니다.

![[스크린샷_2024-09-29_오전_9.36.23.png]]

  

```Swift
@objc
    private func segmentedControlValueChanged(segment: UISegmentedControl) {
        if segment.selectedSegmentIndex == 0 {
            rootView.teenipingCollectionView.isHidden = false
            rootView.emptyLabel.isHidden = true
        }
        else {
            rootView.teenipingCollectionView.isHidden = true
            rootView.emptyLabel.isHidden = false
        }
    }
```

작성해놨던 `segmentedControl`의 인덱스가 바뀌면 불리는 메서드 `segmentedControlValueChanged()` 를 다시 보도록 하겠습니다.

매개변수로 받아온 `segment` 의 속성에는 선택된 인덱스를 나타내는 `selectedSegmentIndex` 가 있는데요!

이 인덱스가 0일 경우 `티니핑` 세그먼트가 클릭된 때이므로 `teenipingCollectionView`의 `isHidden` 변수는 `false`로, `emptyLabel`의 `isHidden` 변수는 `true`로 설정해줍니다.

이외의 경우는 인덱스가 1일 경우밖에 없으므로 else로 처리한 뒤 각 컴포넌트의 `isHidden` 변수를 반대로 설정합니다.

![[스크린샷_2024-09-29_오전_9.36.40.png]]

이제 마지막으로 `emptyLabel` 은 초기 화면에서 숨겨져 있어야 하므로 `emptyLabel` 의 기본 속성 중 `isHidden` 값을 `true`로 처리합니다.

이제 정말 앱을 실행해볼까요?

![[Simulator_Screen_Recording_-_iPhone_15_Pro_-_2024-09-29_at_11.44.40.mp4]]

  

왼쪽 화면과 같이 실행되는 것을 확인하셨나요?

실습 고생하셨습니다. 과제도 화이팅입니다! 🔥

## 💻 4주차 과제

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
> [https://www.figma.com/embed?embed_host=notion&url=https%3A%2F%2Fwww.figma.com%2Fdesign%2F47IuhJxc7LFTwOYWtDgTdi%2FiOS-%EC%9B%8C%ED%81%AC%EB%B6%81%3Fnode-id%3D1773-294%26t%3DQaHFEpDpDv14wDKT-1](https://www.figma.com/embed?embed_host=notion&url=https%3A%2F%2Fwww.figma.com%2Fdesign%2F47IuhJxc7LFTwOYWtDgTdi%2FiOS-%EC%9B%8C%ED%81%AC%EB%B6%81%3Fnode-id%3D1773-294%26t%3DQaHFEpDpDv14wDKT-1)

### 1. 메인 화면 레이아웃을 구현해주세요!

> [!important] **실습 체크리스트**
> 
> - [x] **제공된 피그마 링크로 접속해** ==**제공된 메인 화면의 레이아웃을 구현**==**합니다.**
>     - [x] 단, 레이아웃은 ==**반드시**== ==`**SnapKit**`====**을 이용**==해 구현합니다.
>     - [x] 피그마에 명시된 레이아웃에 맞게 ==**크기와 간격을 정확히 반영**==합니다.
>     - [x] 검색 창은 자유롭게 구현하셔도 괜찮으나 ==**눌렀을 때 다른 화면으로 넘어갈 수 있도록 구현**==해야 합니다!
>     - [x] `UISegmentedControl`을 사용하셔서 SegmentedControl을 구현해주세요!
>         - [x] 이번 워크북에서는 `추천` 세그먼트의 화면만 구현할 예정이기 때문에 다른 세그먼트를 선택했을 때는 빈 화면이 표시되도록 구현해주시면 됩니다.
>     - [x] 각 세그먼트를 눌렀을 때 아래 밑줄이 움직이도록 구현해주세요!
>     - [x] 각 세그먼트를 눌렀을 때 해당 세그먼트 텍스트가 볼드 처리되도록 구현해주세요!
>     - [x] `지금도 늦지 않았다!` 광고 이미지를 Export 하셔서 화면에 배치해주세요! 이미지를 눌렀을 때 화면 이동이나 액션은 따로 없으니 구현하지 않으셔도 됩니다.
>     - [x] `크림 드로우`, `실시간 차트` 등의 메뉴는 `CollectionView`를 이용해 구현해주세요!
>         - [x] `UICollectionViewFlowLayout`을 이용해 구현해주세요!

### 2. 과제가 완성 되었다면 깃허브 링크와 시연 영상을 첨부해주세요!

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

![[iPhone_13_mini.mp4]]

![[iPhone_16_Pro.mp4]]

## 🤔 4주차 트러블 슈팅

---

### 2024년 11월 8일 오전 8:37 배너 크기 맞추기

### 문제 상황

---

- 4주차 과제 (홈화면 만들기) 중 이미지로 넣은 배너가 크기가 안맞아 왼쪽에 붙는 문제

### 해결 과정

---

- horizontalEdges를 superview에 맞추고 contentMode를 scaleAspectFill로 해서 꽉차게 하는데는 성공 → 크기가 늘어나면서 위에 segment를 침범함
- 배너의 오토레이아웃 기준점을 늘어난 top으로 맞추는 방법을 찾아봤으나 실패
- 결국 scaleAspectFill로 늘리되 늘어난 부분을 clipsToBound로 잘라내서 안겹치도록 함

### 참고 자료

---

> [!info] SnapKit 키워드 정리 - equalTo, offset, inset 등  
> equalTo, lessThanOrEqualTo, greaterThanOrEqualTo, 상수 값 부여 ① 여러 경우 - 동일한 경우 : .  
> [https://younngjun.tistory.com/38](https://younngjun.tistory.com/38)  

### 2024년 11월 8일 오후 9:29 세그먼트 뷰 밑줄넣기

### 문제 상황

---

- 세그먼트 뷰 밑에 밑줄 넣는 방법 찾기

### 해결 과정

---

### 참고 자료

---

> [!info] 220801 TIL [Custom SegmentedControl]  
> 오늘의 집 어플을 보면 위와같이 선택에 따라 좌우로 밑줄도 같이 움직이는 메뉴가 있다개인 프로젝트에서도 위와 같은 메뉴를 적용시키고 싶어서 찾아봤는데 버튼을 이용해 구현할 수도 있고 콜렉션뷰를 통해서 구현할 수도 있고 기존 세그먼트 컨트롤을 커스텀 하는 방법도 있고 여  
> [https://velog.io/@doogie97/220801-TIL-Custom-SegmentedControl](https://velog.io/@doogie97/220801-TIL-Custom-SegmentedControl)  

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