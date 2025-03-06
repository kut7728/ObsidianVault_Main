### 1. 프로젝트에 `SwiftUI View.swift` 파일 만들고 코드 복사

```Swift
\#if DEBUG
import SwiftUI

extension UIViewController {
    private struct Preview: UIViewControllerRepresentable {
            let viewController: UIViewController

            func makeUIViewController(context: Context) -> UIViewController {
                return viewController
            }

            func updateUIViewController(_ uiViewController: UIViewController, context: Context) {
            }
        }

        func toPreview() -> some View {
            Preview(viewController: self)
        }
}
\#endif
```

  

### 2. ViewController 파일에 다음 코드 복사

```Swift
\#if DEBUG
import SwiftUI

struct VCPreView: PreviewProvider {
    static var previews: some View {
        파일이름().toPreview()
    }
}
\#endif
```

- 파일이름은 해당 ViewController의 파일 이름 기재

  

### 3. 다음 단축어로 사용

- 새로고침 : `Command + Option + P`
- Canvas 창 열기 / 닫기 : `Command + Option + Enter`