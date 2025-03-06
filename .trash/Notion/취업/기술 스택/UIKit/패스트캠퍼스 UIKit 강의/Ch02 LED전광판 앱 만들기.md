## UINavigationController

`메서드` `스토리보드에서 세그를 쓰던가 이놈을 쓰던가`

`stack에 View Controller들을 추가하거나 삭제할 수 있다!`

### → <Content> View Controller

화면을 구성하는 뷰를 직접 구현하고 관련된 이벤트를 처리하는 뷰 컨트롤러

씬?

### → Container View Controller

- 하나 이상의 Child View Controller를 가지며 관리, 레이아웃과 화면전환을 담당
- 대표적으로 Navigation View Controller, Tabbar Controller 있음

### → Navigation Stack

- Last In First Out 구조의 스택 구조
- back버튼이나 엣지 스와이프를 통해 Navigation Stack을 pop

### → Navigation Bar

- Navigation Controller로 구현하면 화면상단에 항상 보여짐
- root 뷰 컨트롤러를 제외한 모든 뷰 컨트롤러에 존재

  

## UIKit에서의 화면전환 개념

  

> **소스코드를 통한 전환**

### → 뷰 컨트롤러 위에 다른 뷰 가져오기

- 좋지 않은 방법 → 메모리 누수의 위험 있음

### → 기존 뷰 컨트롤러에서 다른 뷰 컨트롤러로 전환하기 `Presentation`

- 뷰 컨트롤러를 불러와 직접 표시한다는 의미에서 presentation 방식이라고도 부름
- 대상 뷰 컨트롤러를 present() 메서드를 사용하여 호출
    
    ```Swift
    func present(_ viewControllerToPresent: UIViewController,
    		animated flag: Bool,
    		completion: (() -> Void)? = nil)
    ```
    
    1. 가고자 하는 뷰의 뷰 컨트롤러 객체를 입력
    2. 화면 전환 애니메이션 여부
    3. 화면 전환 완료시에 실행할 클로저 제공
- dismiss() 메서드를 사용하여 최상위 뷰 제거
    
    ```Swift
    func dismiss(animated flag: Bool,
    		completion: (() -> Void)? = nil)
    ```
    
    1. 화면 전환 애니메이션 여부
    2. 화면 전환 완료시에 실행할 클로저 제공

> [!important]
> 
> ### 실습 코드
> 
> ```Swift
> // presentation 활용해서 뷰 present하기
> @IBAction func tapCodePresentButton(_ sender: UIButton) {
>     guard let viewController = self.storyboard?.instantiateViewController(withIdentifier: "CodePresentViewController") else { return }
>     viewController.modalPresentationStyle = .fullScreen
>     self.present(viewController, animated: true, completion: nil)
> }
> 
> // presentation 활용해서 이전 뷰 복귀하기
> @IBAction func tapBackButton(_ sender: UIButton) {
>     self.presentingViewController?.dismiss(animated: true)
> }
> ```

### → Navigation Controller를 사용하여 화면 전환하기

- 계층적인 성격을 가지는 컨텐츠 구조를 관리하기 위한 컨트롤러
- 뷰 컨트롤러의 전환을 직접 컨트롤
- 앱의 네비게이션 정보 표현
- 네비게이션 스택으로 자식 뷰 컨트롤러 관리
- pushViewController 메서드로 화면을 호출
    
    ```Swift
    func pushViewController(_ viewController: UIViewController,
    		animated: Bool)
    ```
    
- popViewController 메서드로 화면을 제거
    
    ```Swift
    func popViewController(animated: Bool) -> UIViewController?
    ```
    
- popToRootViewController 메서드로 루트 뷰로 복귀
    
    ```Swift
    func popToRootViewController(animated: Bool)
    ```
    
      
    

> [!important]
> 
> ### 실습 코드
> 
> ```Swift
> // Navigation View Controller 사용해서 뷰 푸쉬하기
> @IBAction func tapCodePushButton(_ sender: UIButton) {
>     // 스토리보드에 있는 뷰 컨트롤러 인스턴트화 하기
>     guard let viewController = self.storyboard?.instantiateViewController(withIdentifier: "CodePushViewController") else { return }
>     self.navigationController?.pushViewController(viewController, animated: true)
> }
>     
> // Navigation View Controller 이전 뷰로 복귀하기
> @IBAction func tapBackButton(_ sender: UIButton) {
>     self.navigationController?.popViewController(animated: true)
> }
> ```

  

  

> **스토리보드를 통한 전환**

### → 화면 전환용 객체(Segueway)를 사용하여 화면 전환하기

> [!important]
> 
> ### Action Segueway
> 
> `출발지점이 버튼이나 셀인 경우, 별도의 코드 없이도 가능`
> 
> 1. show(push) - stack으로 쌓이는 방식
>     - 돌아가려면
>         
>         ```Swift
>         @IBAction func tapBackButton(_ sender: UIButton) {
>                 self.navigationController?.popViewController(animated: true)
>             }
>         ```
>         
> 2. showDetail - 아이폰에서는 show와 동일, 아이패드에서는 양쪽으로 보여줌
> 3. present Modally - 모달 창
>     - 설정 → presentation 에서 FullScreen으로 선택하면 전체화면 가능
>     - 이전창으로 돌아가려면 
>         
>         ```Swift
>         @IBAction func tapBackButton(_ sender: UIButton) {
>                 self.presentingViewController?.dismiss(animated: true)
>             }
>         ```
>         
> 4. present As Popover - 아이패드에서 사용되는 팝업 뷰 방식
> 5. custom

> [!important]
> 
> ### Manual Segueway
> 
> `출발지점이 뷰 자체일 경우, performSegue라는 메서드를 통해서 전환`