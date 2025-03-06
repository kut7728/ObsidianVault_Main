---
생성일자: Invalid date
작성자: 안세훈
주차: 1주차
---
  

# Chapter 1 **Hello, Combine!**

- ==**컴바인이**== ==뭔데?==
    - 시간의 흐름에 따라 발생하는 이벤트를 처리하기 위한 API.
        
        ![[스크린샷_2025-02-18_오전_9.02.14.png]]
        

- ==**Publisher**==
    
    - ==Publisher==는 value들을 보내는(emit) 역할.
    - Output 타입과 Failure 타입이 존재.
        - 에러가 발생했을 경우 Failure 타입 그렇지 않다면 Output 타입을 전달
            
            ```Swift
            protocol Publisher {
                associatedtype Output
                associatedtype Failure : Error
                func receive<S>(subscriber: S) where S : Subscriber, Self.Failure == S.Failure, Self.Output == S.Input
            }
            //receive 함수로 Subscriber와 연결이 되어있음.
            ```
            
    - ==Publisher====가== ==Subscriber====로 전달 가능한 이벤트 종류==
    
    1. Output
    2. Completion: successful completion
    3. Failure: completion with an error
    
    ==Publisher==는 Output을 안보내고 있거나 여러번 보낼 수 있으며, Completion 이나 Failure를 한번 보내고 나면 더 이상의 이벤트는 보낼 수 없다.
    
- ==**Operators**==
    
    ==**Operators**==는 ==**Publisher**== 프로토콜에 선언되어 있음. 같거나 새로운 ==**Publisher**==를 반환하는 메소드. ==**Operators**==들을 체이닝해서 사용할 수 있기 때문에 유용함.
    
- ==**Subscriber**==
    
    - ==**Subscriber**====는== ==**Publisher**====**의**== ==Output====**타입과 동일한 Input타입과, 그리고 동일한 Failure**====타입을 가져야함==
    - **2개의 내장된** ==Subscriber==
        - sink: output value와 completion을 받을 수 있는 클로저를 제공할 수 있음
        - assign: output을 key path를 통해 data model의 property 나 UI control에 바로 바인딩 할 수
    
    ```Swift
    public protocol Subscriber : CustomCombineIdentifierConvertible {
        associatedtype Input
        associatedtype Failure : Error
    
        func receive(subscription: Subscription)
        func receive(_ input: Self.Input) -> Subscribers.Demand
        func receive(completion: Subscribers.Completion<Self.Failure>)
    }
    ```
    
      
    
    - ==**Subscriptions**==
        
        ==**Subscriptions**==의 끝에 ==**Subscriber**==를 추가 -> 체이닝의 맨 앞에 있는 ==**Publisher**==를 활성화. output을 수신해줄 ==**Subscriber**==가 없으면 ==**Publisher**==는 어떤 value도 전달하지 않음
        
        - ~~실습을 해봐야 이해가 될 듯하다..~~
        - ==**Subscriber**==와 ==**Publisher**==의 연결을 나타내는 프로토콜
        
          
        

  

- 컴바인은 비동기 이벤트를 위한 선언적, 반응형 프레임워크
- 비동기 프로그래밍의 기존 문제를 해결하는 것이 목표
- 주요 3 타입: ==**Publisher**== (이벤트 발행) -> ==**Operators**== (이벤트 처리, 조작) -> ==**Subscriber**== (결과물 소비)

  

---

# Chapter 2 **Publishers & Subscribers**

- ==**Cancellable**==
    
    - ==**Subscriber**==가 더 이상 값을 받을 필요 없을 때 cancel() 사용
    - cancel()을 직접 호출하지 않으면, denit될 때까지 구독됨
    
      
    
- ==**Publisher**== **와** ==**Subscriber**== **의 흐름**
    
    ![[스크린샷_2025-02-18_오전_9.32.17.png]]
    
    - ==**Subscriber**====**가**== ==**Publisher**====**를 구독.**==
    - ==**Publisher**====**가**== ==**Subscriber**====**로**== ==**Subscriptions**== ==**전달.**==
    - ==**Subscriber**====**가**== ==**Publisher**====**에게**== ==**value**====**를 요청**==
    - ==**Publisher**====**가**== ==**Subscriber**====**로**== ==**value**== ==**전달.**==
        - value 여러개 전달 가능
    - ==**Publisher**====**가**== ==**Subscriber**====**로 Completion 전달.**==
- ==**Publisher Protocol**==
    
    ```Swift
    public protocol Publisher {
      // 1: emit할 수 있는 value
      associatedtype Output
    
      // 2: 예외 발생할 경우 사용되는 에러.
      // 에러가 발생하지 않는다고 보장할 수 있으면, `Never` 사용
      associatedtype Failure : Error
    
      // 4: publisher에 subscirber를 붙이기 위해서 호출 됨
      
      //세훈 : 이 붙힌다. 라는 표현이 모호해서 헷갈림..
      func receive<S>(subscriber: S)
        where S: Subscriber,
        Self.Failure == S.Failure, //타입 일치 !!!
        Self.Output == S.Input //타입 일치 !!!
    }
    
    //extension
    extension Publisher {
      // 3
      public func subscribe<S>(_ subscriber: S)
        where S : Subscriber,
        Self.Failure == S.Failure,
        Self.Output == S.Input
    }
    ```
    
    - `Output`: Publisher가 방출할 수 있는 값의 타입을 정의.
    - `Failure`: 발생할 수 있는 에러의 타입을 정의합니다. 에러가 발생하지 않는다고 확신할 수 있는 경우에는 `Never` 타입을 사용합니다.
    - `receive(subscriber:)`: Subscriber를 실제로 Publisher에 연결하는 핵심 메서드입니다. 이때 Publisher의 Output 타입은 Subscriber의 Input 타입과 일치해야 하며, Failure 타입도 서로 일치해야 합니다.
    - `subscribe()`: 메서드는 Publisher에 Subscriber를 연결하는 편의 메서드입니다.
- ==**Subscriber Protocol**==
    
    ```Swift
    public protocol Subscriber: CustomCombineIdentifierConvertible {
      // 1: receive 할 수 있는 value
      associatedtype Input
    
      // 2: receive 할 수 있는 error
      associatedtype Failure: Error
    
      // 3
      func receive(subscription: Subscription)
    
      // 4
      func receive(_ input: Self.Input) -> Subscribers.Demand
    
      // 5
      func receive(completion: Subscribers.Completion<Self.Failure>)
    }
    ```
    
    - `Input`: Subscriber가 받을 수 있는 값의 타입을 정의합니다.
    - `Failure`: Subscriber가 처리할 수 있는 에러의 타입을 정의합니다.
    - `receive(subscription:)`: Publisher와 연결이 성공했을 때 호출되는 메서드입니다. 이때 Subscription 객체를 받아서 데이터 요청을 시작할 수 있습니다.
    - `receive(_ input:)`: Publisher로부터 새로운 값을 받았을 때 호출되는 메서드입니다. 반환값으로 Demand를 통해 추가로 받고 싶은 값의 개수를 지정할 수 있습니다.
    - `receive(completion:)`: Publisher가 모든 데이터를 전송했거나 에러가 발생했을 때 호출되는 메서드입니다.

  

---

# 예제를 들어보자 !

SwiftUI + Combine을 이용한 MVVM 회원가입!

- ==Model==
    
    ```Swift
    struct User {
        var email: String
        var password: String
        var passwordConfirmation: String
    }
    ```
    
- ==View==
    
    ```Swift
    //
    //  MainView.swift
    //  250218 Combine
    //
    //  Created by 안세훈 on 2/18/25.
    //
    
    import SwiftUI
    
    struct MainView : View {
        
        @StateObject private var viewModel = ViewModel()
        
        var body: some View {
            NavigationView {
                Form {
                    Section(header: Text("계정 정보")) {
                        TextField("이메일", text: $viewModel.email)
                            .autocapitalization(.none)
                            .keyboardType(.emailAddress)
                        
                        SecureField("비밀번호", text: $viewModel.password)
                        SecureField("비밀번호 확인", text: $viewModel.passwordConfirmation)
                    }
                    
                    Section(header: Text("유효성 상태")) {
                        HStack {
                            Text("이메일 형식")
                            Spacer()
                            Image(systemName: viewModel.isEmailValid ? "checkmark.circle.fill" : "xmark.circle.fill")
                                .foregroundColor(viewModel.isEmailValid ? .green : .red)
                        } //viewModel.isEmailValid의 true/false에 따라 foregroundColor색 변환.
                        
                        HStack {
                            Text("비밀번호 길이 (최소 8자)")
                            Spacer()
                            Image(systemName: viewModel.isPasswordValid ? "checkmark.circle.fill" : "xmark.circle.fill")
                                .foregroundColor(viewModel.isPasswordValid ? .green : .red)
                        } //viewModel.isPasswordValid의 true/false에 따라 foregroundColor색 변환.
                        
                        HStack {
                            Text("비밀번호 일치")
                            Spacer()
                            Image(systemName: viewModel.isPasswordMatch ? "checkmark.circle.fill" : "xmark.circle.fill")
                                .foregroundColor(viewModel.isPasswordMatch ? .green : .red)
                        }//iewModel.isPasswordMatch의 true/false에 따라 foregroundColor색 변환.
                    }
                    
                    Button(action: {
                        viewModel.signUp()
                    }) {
                        Text("회원가입")
                            .frame(maxWidth: .infinity)
                            .padding()
                    }
                    .disabled(!viewModel.canSubmit)
                    //viewModel.canSubmit에 따라 able/ disable처리.
                    .buttonStyle(.borderedProminent)
                }
                .navigationTitle("회원가입")
            }
        }
        
    }
    
    
    \#Preview {
        MainView()
    }
    ```
    
- ==ViewModel==
    
    ```Swift
    //
    //  ViewModel.swift
    //  250218 Combine
    //
    //  Created by 안세훈 on 2/18/25.
    //
    
    import Foundation
    import Combine
    
    class ViewModel : ObservableObject { // <- ObservableObject프로토콜 채택ㅇㅇ
        
        //@Published를 통해 바로바로 변화를 감지할 수 있음.
        //앱이 종료되면 메모리에서 제거댐ㅇㅇ
        
        
        //입력필드
        @Published var email = ""
        @Published var password = ""
        @Published var passwordConfirmation = ""
        
        //유효성 검사
        @Published var isEmailValid = false
        @Published var isPasswordValid = false
        @Published var isPasswordMatch = false
        @Published var canSubmit = false
        
        
        
        //구독을 위한 set
        private var cancellables = Set<AnyCancellable>()
        
        
        init(){
            //이메일 유효성 검사
            $email // Publisher<String, Never> 타입의 스트림 시작 -> 문자열이냐? or ""이냐
                .map{ email in // 들어오는 이메일 문자열을 변환
                let emailRegex = "[A-Z0-9a-z._%+-]+@[A-Za-z0-9.-]+\\.[A-Za-z]{2,64}"
                let emailPredicate =  NSPredicate(format: "SELF MATCHES %@", emailRegex)
                return emailPredicate.evaluate(with: email) // Bool값으로 변환
            } .assign(to: \.isEmailValid, on: self) //결과를 isEmailValid에 할당.
                .store(in: &cancellables) //구독을 저장?
            
            //비밀번호 유효성 검사, 최소 8글자 이상
            $password  // Publisher<String, Never> 타입의 스트림 시작
                .map { $0.count >= 8 } // 문자열 길이가 8 이상인지 확인하여 Bool로 변환
                .assign(to: \.isPasswordValid, on: self)  // 결과를 isPasswordValid에 할당
                .store(in: &cancellables) // 구독을 저장
            
            //오 퍼블리셔가 뷰모델에서 등장하는구나!
            
            // 비밀번호 일치
            Publishers.CombineLatest($password, $passwordConfirmation)
            // 두 개의 Publisher를 결합
            // (String, String) 튜플을 받아서 비교
                .map { password, passwordConfirmation in
                    return !password.isEmpty && password == passwordConfirmation
                } //비어있지 않은 비밀번호, 비밀번호일치 string이 같을경우에만 isPasswordMatch에 true를 할당.
                .assign(to: \.isPasswordMatch, on: self) // 결과를 isPasswordMatch에 할당
                .store(in: &cancellables) // 구독을 저장
            
            // 회원가입의 가능여부 -> 모든 것들이 true가 아닐 경우 안댐ㅇㅇ
            Publishers.CombineLatest3($isEmailValid, $isPasswordValid, $isPasswordMatch)
                                    // (Bool, Bool, Bool) 튜플을 받아서 모든 조건이 true인지 확인
                .map { isEmailValid, isPasswordValid, isPasswordMatch in
                    return isEmailValid && isPasswordValid && isPasswordMatch
                }
                .assign(to: \.canSubmit, on: self) // 결과를 canSubmit에 할당
                .store(in: &cancellables) // 구독을 저장
        }
        
        func signUp() {
            // 실제 회원가입 로직 구현
            print("회원가입 처리: \(email)")
        }
        
        
    }
    
    ```
    

  

1. **이메일 검사 흐름**:
    - 이메일 입력 ==(View)== → 정규식 검사==(ViewModel)== → Bool 결과==(ViewModel)== → isEmailValid 업데이트 ==(View)==
2. **비밀번호 검사 흐름**:
    - 비밀번호 입력==(View)== → 길이 검사==(ViewModel)== → Bool 결과==(ViewModel)== → isPasswordValid 업데이트 ==(View)==
3. **비밀번호 일치 검사 흐름**:
    - (비밀번호, 확인) 입력==(View)==→ 값 비교==(ViewModel)== → Bool 결과==(ViewModel)== → isPasswordMatch 업데이트 ==(View)==
4. **전체 폼 검사 흐름**:
    
    - (이메일valid, 비밀번호valid, 비밀번호match) ==(View)==→ AND 연산==(ViewModel)== → Bool 결과==(ViewModel)==→ canSubmit 업데이트 ==(View)==
    
      
    

중요한 Combine 개념들:

- `$` 접두어: Published 프로퍼티의 Publisher를 얻음
- `map`: 값을 변환
- `CombineLatest`: 여러 Publisher의 최신 값을 결합
- `assign`: 결과를 프로퍼티에 할당
- `store(in: &cancellables)`: 메모리 누수 방지를 위한 구독 저장

### 배운 점

```Swift
//이걸 실전에 적용하라고?
//공부 ㅈ빠지게 해야겠다 ㄹㅇ
//예제를 한 10개 정도 만들면 되지 않을까?
```

  

근디 왜 뷰모델 인스턴스 쓸때 @ObservedObject 말고 @StateObject씀? 둘다 실시간객체값확인아님????ㅅㅂ

- 인스턴스내에 프로퍼티 변경에 따라서 ㅇㅇ

[https://velog.io/@jeunghun2/ObservedObject-StateObject-언제-어떻게-무엇을-사용해야-하는가](https://velog.io/@jeunghun2/ObservedObject-StateObject-%EC%96%B8%EC%A0%9C-%EC%96%B4%EB%96%BB%EA%B2%8C-%EB%AC%B4%EC%97%87%EC%9D%84-%EC%82%AC%EC%9A%A9%ED%95%B4%EC%95%BC-%ED%95%98%EB%8A%94%EA%B0%80)