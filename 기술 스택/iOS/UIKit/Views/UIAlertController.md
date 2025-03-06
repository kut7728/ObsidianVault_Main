#UIKit #UIKit-View #UIKit-Alert

# 개요
사용자의 인터랙션에 띄우는 알림창 혹은 목록창

# 구현 방법
- UIAlertController 객체 선언
- UIAlertAction 객체로 버튼과 액션 설정
- 컨트롤러 객체에 액션 객체 `.addAction` 으로 장착
- 뷰 컨트롤러의 `.present` 메서드로 UIAlertController 객체 present

## 예시 코드
```swift
@IBAction func tapAddButton(_ sender: UIBarButtonItem) {
        // .alert는 팝업창, .actionSheet는 모달창같이 뜨는 목록
        let alert = UIAlertController(title: "할 일 등록", message: nil, preferredStyle: .alert)
        
        // 현재 클로저가 들어가있는 handler 파라미터는 알림창의 버튼을 눌렀을때 실행될 동작을 정의해줌
        // weak self : 두 객체가 서로를 참조하는 경우 해제되지 않는 강한 순환 참조가 일어나서 메모리 누수가 일어남
        let registerButton = UIAlertAction(title: "등록", style: .default) { [weak self] _ in
            guard let title = alert.textFields?[0].text else { return }
            let task = Task(title: title, done: false)
            self?.tasks.append(task)
            self?.tableView.reloadData()  //할일이 늘어날때마다 테이블 뷰를 갱신시키는 메서드
            
        }
        let cancelButton = UIAlertAction(title: "취소", style: .cancel, handler: nil)
        
        // 둘의 추가 순서는 뷰의 순서와는 무관, 무조건 취소가 왼쪽
        alert.addAction(registerButton)
        alert.addAction(cancelButton)
        
        // configurationHandler는 alert에 들어갈 textField 컴포넌트를 표현하는 클로저
        alert.addTextField { textField in
            textField.placeholder = "할 일을 입력해주세요."
        }
        self.present(alert, animated: true, completion: nil)
    }
```