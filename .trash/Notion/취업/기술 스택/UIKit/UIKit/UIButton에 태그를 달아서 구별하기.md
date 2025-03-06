---
내용: UMC week2 Mission
---
## 문제상황

- 두개의 버튼(`UIButton`)이 각기다른 대상을 향해 같은 동작을 할때 하나의 액션(`@objc`)을 사용하고 싶었음
- 처음에는 액션의 함수에 파라미터를 집어 넣어서 하려고 했음
    
    - 파라미터로 받은 함수를 이용해서 메소드 호출하는 방법 모름
    - `UIButton`에 `.addTarget` 할때 `action:` 파라미터에는 `#selector` 를 이용해서만 액션을 선택할 수 있었음
    
      
    

---

## 해결방법

- 각각의 버튼에 태그를 붙여서 구분할 수 있다고 함
- 액션에서는 파라미터로 `UIButton` 클래스를 받고, 클래스의 태그에 따라 `switch-case문`를 통해 나눠서 실행

  

---

## 코드

```Swift
psView.idButton.tag = 1
psView.pwButton.tag = 2
psView.idButton.addTarget(self, action: \#selector(didTapChange), for: .touchUpInside)
psView.pwButton.addTarget(self, action: \#selector (didTapChange), for: .touchUpInside)

@objc func didTapChange(_ sender: UIButton) {
    switch sender.tag {
    case 1 :
        psView.idField.text = ""
        psView.idButton.setTitle("저장", for: .normal)
    case 2 :
        psView.pwField.text = ""
        psView.pwButton.setTitle("저장", for: .normal)
    default :
        print("error")
    }
    
}
```