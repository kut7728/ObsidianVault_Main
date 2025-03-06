#UIKit #FastCampus

# 사용된 기술 스택
[[화면 전환하기]]
[[다른 뷰 컨트롤러에 데이터 넘겨주기]]

<br>

>[!note] LED전광판 앱 개요
>- 루트뷰에서 레이블과 뷰 배경색으로 글자를 나타내는 앱
>- 설정뷰로 넘어가면 텍스트, 텍스트색, 배경색을 설정할 수 있고
>- 루트뷰 설정뷰 간에 설정이 서로 전달됨
>	- 루트뷰 → 설정뷰 : 뷰 컨트롤러 다운캐스팅해서 프로퍼티에 주입
>	- 설정뷰 → 루트뷰 : delegate 패턴

``` swift fold title:"ViewController"
import UIKit

class ViewController: UIViewController, LEDBoardSettingDelegate {
    // 델리게이트로 설정뷰에서 데이터 받아오는
    func changedSetting(text: String, textColor: UIColor, backgroundColor: UIColor) {
        self.ContentsLabel.text = text
        self.ContentsLabel.textColor = textColor
        self.view.backgroundColor = backgroundColor
    }
    
    @IBOutlet weak var ContentsLabel: UILabel!
    
    override func viewDidLoad() {
        super.viewDidLoad()
        
        /// 왜 옵셔널 체이닝? -> IBOutlet 변수는 기본적으로 nil상태
        /// 다른 뷰로 넘어가면서 ViewController가 해제되고 ContentsLabel역시 nil이 되버림
        self.ContentsLabel?.textColor = .yellow
    }
    
    // segue를 실행하기 전에 호출되는 메서드, 루트뷰를 설정뷰의 델리게이트 객체로 설정 & 루트뷰->설정뷰 데이터 이동을 위한 메서드
    override func prepare(for segue: UIStoryboardSegue, sender: Any?) {
        
        // segue.destination은 스토리보드의 목표 뷰. 즉, 설정 뷰
        if let settingViewController = segue.destination as? SettingViewController {  // 설정뷰를 다운캐스팅 (프로퍼티를 사용하기 위해)
            settingViewController.delegate = self  // 루트뷰를 설정뷰의 델리게이트 객체로 설정
            
            // 루트뷰의 속성값들을 설정뷰로 넘겨주는 절차
            settingViewController.ledText = self.ContentsLabel?.text
            settingViewController.textColor = self.ContentsLabel?.textColor ?? .yellow
            settingViewController.backgroundColor = self.view.backgroundColor ?? .black
        }
    }
}


```

``` swift fold title:"SettingViewController"
import UIKit

// 델리게이트 패턴을 위한 프로토콜 선언
protocol LEDBoardSettingDelegate: AnyObject {
    func changedSetting(text: String, textColor: UIColor, backgroundColor: UIColor)
}

class SettingViewController: ViewController {
    @IBOutlet weak var textField: UITextField!
    
    // 왜 Outlet도 선언함? 선택된 버튼은 알파값을 바꿔야하기 때문 (속성변경)
    @IBOutlet weak var orangeButton: UIButton!
    @IBOutlet weak var blueButton: UIButton!
    @IBOutlet weak var blackButton: UIButton!
    
    @IBOutlet weak var greenButton: UIButton!
    @IBOutlet weak var purpleButton: UIButton!
    @IBOutlet weak var yellowButton: UIButton!
    
    // 델리게이트 객체 변수 선언 -> 나중에 루트뷰가 이 객체가 됨
    weak var delegate: LEDBoardSettingDelegate?
    
    // 루트뷰에서 보낸 데이터를 담는 프로퍼티
    var ledText: String?
    var textColor: UIColor = .yellow
    var backgroundColor: UIColor = .black
    
    
    override func viewDidLoad() {
        super.viewDidLoad()
        self.configureView()
    }
    
    /// 루트뷰에서 넘어온 데이터를 장착해주는 메서드
    private func configureView() {
        if let ledText = self.ledText {
            self.textField.text = ledText
        }
        self.changeTextColor(color: self.textColor)
        self.changeBackgroundColor(color: self.backgroundColor)
    }
    
    // 버튼 세개를 다 같이 연결했는데 어케 인식함? -> sender파라미터로 가능!
    @IBAction func tapTextColorButton(_ sender: UIButton) {
        if sender == self.yellowButton {
            changeTextColor(color: .yellow)
            self.textColor = .yellow
        } else if sender == self.purpleButton {
            changeTextColor(color: .purple)
            self.textColor = .purple
        } else {
            changeTextColor(color: .green)
            self.textColor = .green
        }
    }
    
    @IBAction func tapBackgroudColorButton(_ sender: UIButton) {
        if sender == self.blackButton {
            changeBackgroundColor(color: .black)
            self.backgroundColor = .black
        } else if sender == self.blueButton {
            changeBackgroundColor(color: .blue)
            self.backgroundColor = .blue
        } else {
            changeBackgroundColor(color: .orange)
            self.backgroundColor = .orange
        }
    }
     
    // delegate패턴으로 루트뷰로 데이터 보내는 메서드 & 루트뷰로 돌아가는 메서드
    @IBAction func tapSaveButton(_ sender: UIButton) {
        self.delegate?.changedSetting(text: self.textField.text ?? "",
                                      textColor: self.textColor,
                                      backgroundColor: self.backgroundColor)
        self.navigationController?.popViewController(animated: true)
    }
    
    private func changeTextColor(color: UIColor) {
        // 버튼 탭으로 넘겨받은 색 아규먼트와 같은색의 버튼은 알파값 1, 아니면 0.2로 설정
        self.yellowButton.alpha = (color == UIColor.yellow ? 1 : 0.2)
        self.purpleButton.alpha = (color == UIColor.purple ? 1 : 0.2)
        self.greenButton.alpha = (color == UIColor.green ? 1 : 0.2)
    
    }
    
    private func changeBackgroundColor(color: UIColor) {
        // 버튼 탭으로 넘겨받은 색 아규먼트와 같은색의 버튼은 알파값 1, 아니면 0.2로 설정
        self.blackButton.alpha = (color == UIColor.black ? 1 : 0.2)
        self.blueButton.alpha = (color == UIColor.blue ? 1 : 0.2)
        self.orangeButton.alpha = (color == UIColor.orange ? 1 : 0.2)
    
    }
    
}

```

