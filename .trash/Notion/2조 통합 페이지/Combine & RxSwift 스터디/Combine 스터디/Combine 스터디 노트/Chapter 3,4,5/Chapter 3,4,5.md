---
생성일자: Invalid date
작성자: 안세훈
주차: 2주차
---
- ==**25.02.18 마무리**==
    
    - `**KeyPath**`
        
        1. `KeyPath`는 객체의 특정 프로퍼티에 접근하거나 관찰할 때 사용하는 **경로**를 의미.
        2. 특정 루트 유형(class 타입, struct 타입)에서 value type으로의 참조를 의미.
        3. Property의 reference값을 의미. (c에서의 ==포인트 개념과 유사==)
        4. ==포인터 개념==이라는걸 보니 주소값 비슷한게 나오나?
        5. PTSD오네
        
          
        
        - 그래서 ==어캐쓰는데요?==
            
            # KeyPath 사용 방법
            
            [https://ios-development.tistory.com/798](https://ios-development.tistory.com/798)
            
            Ref)킹종권
            
              
            
            - KeyPath 참조 얻어내는 방법
            
            ```Swift
            let userNameKeyPath = \\User.name
            print(userNameKeyPath)
            // Swift.KeyPath<ExSyntax.ViewController.User, Swift.String>
            
            //userNameKeyPath을 통해? 접근하기 쉽게 설정이 되었다?
            ```
            
            - KeyPath 참조를 통해 값에 접근하는 방법
            
            ```Swift
            let userNameKeyPath = \\User.name
            print(userNameKeyPath)
            // Swift.KeyPath<ExSyntax.ViewController.User, Swift.String>
            
            //세훈 : User.name을 접근하기위해 userNameKeyPath라는 메소드를 만들었다는 느낌인가?
            
            let user1 = User(name: "jake", email: "a@a.com", phoneNumber: "010-1111-5678") 
            let user = user1[keyPath: userNameKeyPath]
            //세훈 : user1의 데이터 중 name에 접근하기 위해 User.name을 사용할 수도 있지만?
            //세훈 : user1[keyPath: userNameKeyPath]로도 접근이 가능한 것이다?
            
            print(user)
            //jake
            ```
            
            - 객체 정의 자체 내에서 KeyPath를 사용할 때는 자기 자신의 클래스 이름 생략이 가능
            
            ```Swift
            class User {
            	func getName() -> String {
            		return self[keyPath: \\.name]
            	}
            }
            //오 그럼 Extension으로 따로 파서 굴려먹음 되겠노 ㅋㅋ
            ```
            
            # Swift 5.2+, KeyPath를 통한 편리한 property 접근
            
            - KeyPath를 통해 Higher Order Function (대충 고차함수라는 말인듯) 을 더욱 편리하게 사용 가능
                
                - map
                
                ```Swift
                // sample data
                let user1 = User(name: "jake", email: "a@a.com", phoneNumber: "010-1111-5678")
                let user2 = User(name: "kim", email: "b@b.com", phoneNumber: "010-2222-5678")
                let user3 = User(name: "jane", email: "c@c.com", phoneNumber: "010-3333-5678")
                let users = [user1, user2, user3]
                
                // KeyPath를 사용하지 않은 경우
                let names = users.map { $0.name }
                
                // KeyPath를 사용한 경우
                let namesUsingKeyPath = users.map(\.name)
                // users.map { $0[keyPath: \\User.email] } 와 동일
                ```
                
                - filter
                
                ```Swift
                // filter에서 KeyPath를 통한 equal 연산자 정의
                func ==<T, V: Equatable>(lhs: KeyPath<T, V>, rhs: V) -> (T) -> Bool {
                    return { $0[keyPath: lhs] == rhs }
                }
                
                // KeyPath를 사용하지 않은 경우
                let engineers = users.filter { $0.job == .engineer }
                
                // KeyPath를 사용한 경우
                let namesIncludeJUsingKeyPath = users.filter(\\.job == .engineer)
                ```
                
        
        ---
        
    - ==**Subscription**==
        
        Ref) [https://icksw.tistory.com/276](https://icksw.tistory.com/276)
        
          
        
        요약해서 적어둘까 했는데 블로그에 너무 잘 되어있어서… 차라리 같이 보는게 더 나을듯 싶습니다.
        
    - `**NotificationCenter**` 왜 삭제해도 **completion**이 되지 않는가
        
        Ref) ChatGPT
        
        → 의문이였던게 이게 맞나? 정흠님이 설명하셨던것도 이거랑 같은거같은데;;
        
          
        
        `NotificationCenter`를 사용하여 Combine에서 `Publisher`를 구독할 때, 해당 `Publisher`를 취소(`.cancel()`)하더라도 **completion이 호출되지 않는 이유**는 `NotificationCenter`의 동작 방식 때문이에요.
        
        ### 🔍 이유
        
        1. `NotificationCenter`의 `Publisher`는 일반적인 **완료(completion)** 개념이 없어요.
        2. `NotificationCenter`는 특정 조건에서 종료되지 않으며, 기본적으로 **계속 알림을 보낼 준비가 되어 있음**.
        3. 즉, **외부에서 명시적으로 complete 이벤트를 발생시키지 않기 때문에** `**.sink**`**의 completion 클로저가 실행되지 않음**.
        
        ### ✅ 예제 코드
        
        ```Swift
        import Combine
        import Foundation
        
        let publisher = NotificationCenter.default
            .publisher(for: UIApplication.didEnterBackgroundNotification)
            //백그라운드에 진입했을때 노티로 알려줌
            
        let cancellable = publisher.sink(
            receiveCompletion: { _ in print("Completed") },
            receiveValue: { notification in print("Received Notification:", notification) }
        )
        
        // NotificationCenter에서 구독 취소
        cancellable.cancel()
        
        // ❌ "Completed"가 출력되지 않음
        
        ```
        
        👉 `cancellable.cancel()`을 호출해도 **receiveCompletion 클로저가 실행되지 않음**!
        
        ---
        
        ### 💡 해결 방법: `.handleEvents()` 사용
        
        `handleEvents(receiveCancel:)`을 활용하면 **취소될 때 직접 클로저를 실행**할 수 있어요.
        
        ```Swift
        
        import Combine
        
        let publisher = NotificationCenter.default
            .publisher(for: UIApplication.didEnterBackgroundNotification)
            .handleEvents(receiveCancel: { print("Subscription Cancelled") })
        
        let cancellable = publisher.sink(
            receiveCompletion: { _ in print("Completed") },
            receiveValue: { notification in print("Received Notification:", notification) }
        )
        
        // 구독 취소
        cancellable.cancel()
        
        // ✅ "Subscription Cancelled" 출력됨
        
        ```
        
        이렇게 하면 **구독이 취소되었을 때(**`**.cancel()**`**) 실행할 코드**를 직접 정의할 수 있어요.
        
        ---
        
        ### 🎯 정리
        
        - `NotificationCenter.Publisher`는 기본적으로 **completion 이벤트를 발생시키지 않음**.
        - `.cancel()`을 호출해도 **completion이 호출되지 않음**.
        - **구독이 취소되었을 때 특정 동작을 수행하려면** `**handleEvents(receiveCancel:)**`**을 사용하면 됨**.
    
      
    

---

- ==**25.02.25**==
    
    # **Chapter 3. Transforming Operators**
    
    ---
    
    **Operators and publishers**
    
    - operator method는 ==사실 publisher를 return 함==
        - publisher → operator → publisher(연산을 한 값?) → subscriber 라는겨?
    - upstream data → operator에서 가공 → downstream으로 전달
    - error handling을 위한 operator가 아니면, error를 downstream으로 흘려보내줌
    
      
    
    ---
    
      
    
    ## **Collecting Value**
    
    - ==**Collect()**==
        
        - 개별 value -> array로 변경
        - value를 버퍼에 쌓고, completion 때 array로 만들어줌
        
        ```Swift
        example(of: "collect") {
          ["A", "B", "C", "D", "E"].publisher  // (1) Publisher 생성 배열을 publisher로 변환
          .collect(2)                           // (2) operator 사용
          .sink(receiveCompletion: { print($0) }, // (3) Subscriber 생성
                receiveValue: { print($0) })
          .store(in: &subscriptions)            // (4) Subscription 저장
        }
        
         
        //——— Example of: collect ———
        //["A", "B"]
        //["C", "D"]
        //["E"]  collect(2)가 채워지기 전에 stream이 끝나서 ["E"]로 출력됨
        //finished
        ```
        
    
    ## **Mapping Value**
    
    - ==**map(_:)**==
        
        ```Swift
        let formatter = NumberFormatter()
        formatter.numberStyle = .spellOut
         
        //sepllOut은 숫자를 문자로 변환시켜줌.
        //.percent → 30%
        //.currency → $10,000,000
        //.spellOut → ten thousand
        
        [123, 4, 56].publisher
        .map { formatter.string(for: NSNumber(integerLiteral: $0)) ?? "" }
        .sink(receiveValue: { print($0) })
        .store(in: &subscriptions)
        
        //——— Example of: map ———
        //one hundred twenty-three
        //four
        //fifty-six
        ```
        
    - ==**Map key paths**==
        - keyPath를 통해 바로 매핑해주는 방법
        - 3개까지 프로퍼티 매핑이 가능함
        - .map { ($0.x, $0.y) } 보다 조금 더 간결하다는 점은 장점
            
            ```Swift
            let publisher = PassthroughSubject<Coordinate, Never>() //에러따위 없음
            //PassthroughSubject는 직접 값을 발행가능한 publisher
            
            publisher
              .map(\.x, \.y)
              .sink(receiveValue: { x, y in
                  print("The coordinate at (\(x), \(y)) is in quadrant", quadrantOf(x: x, y: y))
              })
              .store(in: &subscriptions)
            
            //외부에서 .send(_:)를 호출해서 데이터를 직접 보낼 수 있음
            publisher.send(Coordinate(x: 10, y: -8)) 
            publisher.send(Coordinate(x: 0, y: 5))
            
            //The coordinate at (10, -8) is in quadrant 4
            //The coordinate at (0, 5) is in quadrant boundary
            ```
            
    - ==**tryMap(_:)**==
        
        - tryMap을 쓰면 클로저 안에서 error를 throw할 수 있음
        - 세훈 : 이해모담…
        
        ```Swift
        Just("Directory name that does not exist")
          .tryMap { try FileManager.default.contentsOfDirectory(atPath: $0) }
          .sink(receiveCompletion: { print($0) },
                receiveValue: { print($0) })
          .store(in: &subscriptions)
          
        //failure(Error Domain=NSCocoaErrorDomain Code=260 "The folder “Directory name that does not exist” doesn’t exist." UserInfo={NSUserStringVariant=(
        //    Folder
        //), NSFilePath=Directory name that does not exist, NSUnderlyingError=0x6000023e1ad0 {Error Domain=NSPOSIXErrorDomain Code=2 "No such file or directory"}})
        ```
        
    
    ## **Flattening publisherss**
    
    - ==**flatMap(maxPublishers:**==_==**:**==_==**)**==
        
        여러개의 publisher upstream -> single downstream으로 변환
        
        ```Swift
        func decode(_ codes: [Int]) -> AnyPublisher<String, Never> {
            Just(
                codes.compactMap { code in
                    guard (32...255).contains(code) else { return nil } // 유효한 문자 코드만 필터링
                    return String(UnicodeScalar(code) ?? " ") // 코드 → 문자 변환
                }
                .joined() // 문자들을 하나의 문자열로 합침
            )
            .eraseToAnyPublisher() // AnyPublisher<String, Never>로 변환
        }
        
        [72, 101, 108, 108, 111, 44, 32, 87, 111, 114, 108, 100, 33]
            .publisher
            .collect() //1차원 배열로 모아서
            .flatMap(decode)
            .sink(receiveValue: { print($0) })
            .store(in: &subscriptions)
            
        //Hello, World!
        ```
        
    
    ## **Replacing upstream output**
    
    - ==**replaceNil(with:)**==
        
        optional을 특정 값으로 바꿔줌
        
        ```Swift
        ["A", nil, "C"].publisher
            .eraseToAnyPublisher() // Combine Bug 방어 위해 사용
            .replaceNil(with: "-") // nil -> "-"
            .sink(receiveValue: { print($0) })
            .store(in: &subscriptions)
        // A
        // -
        // C
        ```
        
    - ==**replaceEmpty(with:)**==
        
        upstream에서 value가 emit되지 않고 completion 되면, value를 하나 넣어주는 것
        
        ```Swift
        let empty = Empty<Int, Never>()
        
        empty
          .replaceEmpty(with: 1)
          .sink(receiveCompletion: { print($0) },
                receiveValue: { print($0) })
          .store(in: &subscriptions)
        
        //1
        //finished
        ```
        
    
    ## **Incrementally transforming output**
    
    - ==**scan(**==_==**:**==_==**:)**==
        
        value 를 누적해서 계산할 수 있음
        
        ```Swift
        var dailyGainLoss: Int { .random(in: -10...10) }
        
        let august2019 = (0..<22)
          .map { _ in dailyGainLoss }
          .publisher
        
        august2019
          .scan(50) { latest, current in
              max(0, latest + current)
          }
          .sink(receiveValue: { _ in })
          .store(in: &subscriptions)
        ```
        
    
    # **Chapter 4. Filtering Operators**
    
    - ==**Filtering basics**==
        
        ```Swift
        example(of: "filter") {
        let numbers = (1...10).publisher
        
        numbers
          .filter { $0.isMultiple(of: 3) } // collection에 filter 쓰는거랑 똑같음
          .sink(receiveValue: { n in
              print("\(n) is a multiple of 3")
          })
          .store(in: &subscriptions)
        }
        //——— Example of: filter ———
        //3 is a multiple of 3
        //6 is a multiple of 3
        //9 is a multiple of 3
        ```
        
        ```Swift
        example(of: "removeDuplicates") {
        let words = "hey hey hey there! want to listen to mister mister ?"
          .components(separatedBy: " ")
          .publisher
        
        words
          .removeDuplicates() // 연속해서 같은 value가 오면 나중에 오는 value는 무시해줌
          .sink(receiveValue: { print($0) })
          .store(in: &subscriptions)
        }
        //——— Example of: removeDuplicates ———
        //hey
        //there!
        //want
        //to
        //listen
        //to
        //mister
        //?
        ```
        
        ```Swift
        example(of: "removeDuplicates2") {
        struct CustomValue {
          let value: String
        }
        
        let words = "hey hey hey there! want to listen to mister mister ?"
          .components(separatedBy: " ")
          .map { CustomValue(value: $0) }
          .publisher
        
        words
          .removeDuplicates(by: { $0.value == $1.value }) 
          // Equatable을 준수하지 않는 객체인 경우에는 비교문으로 구현 가능
          .sink(receiveValue: { print($0) })
          .store(in: &subscriptions)
        }
        //——— Example of: removeDuplicates2 ———
        //CustomValue(value: "hey")
        //CustomValue(value: "there!")
        //CustomValue(value: "want")
        //CustomValue(value: "to")
        //CustomValue(value: "listen")
        //CustomValue(value: "to")
        //CustomValue(value: "mister")
        //CustomValue(value: "?")
        ```
        
    - ==**Compacting and ignoring**==
        
        ```Swift
        example(of: "compactMap") {
        let strings = ["a", "1.24", "3", "def", "45", "0.23"].publisher
        
        strings
          .compactMap { Float($0) } // nil이면 무시해줌
          .sink(receiveValue: {
              print($0)
          })
          .store(in: &subscriptions)
        }
        //——— Example of: compactMap ———
        //1.24
        //3.0
        //45.0
        //0.23
        ```
        
        ```Swift
        example(of: "ignoreOutput") {
        let numbers = (1...10_000).publisher
        
        numbers
          .ignoreOutput()
          .sink(receiveCompletion: { print("Completed with: \($0)") },
                receiveValue: { print($0) })
          .store(in: &subscriptions)
        }
        //——— Example of: ignoreOutput ———
        //Completed with: finished
        ```
        
    - ==**Finding values**==
        - ==**first(where:)**==
            
            lazy한 특성. 만족하는 조건이 나오면, 더 이상 검사를 실행하지 않음
            
            ```Swift
            example(of: "first(where:)") {
            let numbers = (1...9).publisher
            
            numbers
              .print("numbers")
              .first(where: { $0 % 2 == 0 }) // lazy 효과를 내는데, 유효한 value 하나를 충족하면 emit 후 complete됨
              .sink(receiveCompletion: { print("Completed with: \($0)") },
                    receiveValue: { print($0) })
              .store(in: &subscriptions)
            }
            
            //——— Example of: first(where:) ———
            //numbers: receive subscription: (1...9)
            //numbers: request unlimited
            //numbers: receive value: (1)
            //numbers: receive value: (2)
            //numbers: receive cancel
            //2
            //Completed with: finished
            ```
            
        - ==**last(where:)**==
            
            ```Swift
            example(of: "last(where:)") {
            let numbers = (1...9).publisher
            
            numbers
              .last(where: { $0 % 2 == 0 }) // greedy. 모든 value를 검사함
              .sink(receiveCompletion: { print("Completed with: \($0)") },
                    receiveValue: { print($0) })
              .store(in: &subscriptions)
            }
            
            //——— Example of: last(where:) ———
            //8
            //Completed with: finished
            ```
            
    - ==**Dropping values**==
        
        ```Swift
        example(of: "dropFirst") {
        let numbers = (1...10).publisher
        
        numbers
          .dropFirst(8)
          .sink(receiveValue: { print($0) })
          .store(in: &subscriptions)
        }
        
        //——— Example of: dropFirst ———
        //9
        //10
        ```
        
        - ==**drop(while:)**==
            
            **drop(while:) 도 lazy한 특성을 띄는데, print(“x”)가 다섯번만 실행되는걸 알 수 있다.**
            
            ```Swift
            example(of: "drop(while:)") {
            let numbers = (1...10).publisher
            
            numbers
              .drop(while: { // * 조건 만족하는게 나올때까지 drop
                  print("x") // * 한번 조건 만족하면 실행되지 않음
                  return $0 % 5 != 0 
                  // 조건 : 5로 나누었을때 나머지가 0이 나오지 않을때까지
              })
              .sink(receiveValue: { print($0) })
              .store(in: &subscriptions)
            }
            //——— Example of: drop(while:) ———
            //x
            //x
            //x
            //x
            //x
            //5
            //6
            //7
            //8
            //9
            //10
            ```
            
        - ==**drop(untilOutputFrom:)**==
            
            viewController에서 화면이 나타나고 나서 어떤 작업을 하고 싶을 때 사용 가능
            
            viewWillappear에 적용?
            
            ```Swift
            example(of: "drop(untilOutputFrom:)") {
            let isReady = PassthroughSubject<Void, Never>()
            let taps = PassthroughSubject<Int, Never>()
            
            taps
                .drop(untilOutputFrom: isReady)
                .sink(receiveValue: { print($0) })
                .store(in: &subscriptions)
            
            (1...5).forEach { n in
                taps.send(n)
            
                if n == 3 {
                    isReady.send()
                }
            }
            }
            //——— Example of: drop(untilOutputFrom:) ———
            //4
            //5
            ```
            
    - ==**Limiting values**==
        
        ```Swift
        example(of: "prefix") {
        let numbers = (1...10).publisher
        
        numbers
          .prefix(2) // 2개만 value를 받고 이후로는 무시. lazy
          .sink(receiveCompletion: { print("Completed with: \($0)") },
                receiveValue: { print($0) })
          .store(in: &subscriptions)
        }
        ——— Example of: prefix ———
        1
        2
        Completed with: finished
        ```
        
        - `**prefix(while:)**`
            
            ```Swift
            example(of: "prefix(while:)") {
            let numbers = (1...10).publisher
            
            numbers
              .prefix(while: { $0 < 3 }) // 한번 조건을 만족하면, complete
              .sink(receiveCompletion: { print("Completed with: \($0)") },
                    receiveValue: { print($0) })
              .store(in: &subscriptions)
            }
            ——— Example of: prefix(while:) ———
            1
            2
            Completed with: finished
            ```
            
        - `prefix(untilOutputFrom:)`
            
            ```Swift
            example(of: "prefix(untilOutputFrom:)") {
            let isReady = PassthroughSubject<Void, Never>()
            let taps = PassthroughSubject<Int, Never>()
            
            taps
              .prefix(untilOutputFrom: isReady)
              .sink(receiveCompletion: { print("Completed with: \($0)") },
                    receiveValue: { print($0) })
              .store(in: &subscriptions)
            
            (1...5).forEach { n in
              taps.send(n)
            
              if n == 2 {
                  isReady.send()
              }
            }
            }
            //——— Example of: prefix(untilOutputFrom:) ———
            //1
            //2
            //Completed with: finished
            ```
            
    
      
    
    ---
    
    # **Chapter 5. Combining Operators**
    
    ### ==**prepend**==
    
    - Prepend가 앞에 추가한다는 뜻
    - value / collection / publisher를 앞에 추가할 수 있음
    - Publisher를 prepend 할때는 앞에 붙인 publisher가 complete 되고나서야 그 다음 publisher가 값을 전달함
    
    ### ==**append**==
    
    - Append 는 sequence 맨뒤에 붙는것
    
    ### ==**switchLatest**==
    
    - publisher들을 보내는 publisher를 만들었을 떄, 가장 최근에 전달된 publisher로 전환해줌
    
    세훈 : 네?
    
    - 버튼을 터치하면 API 호출하는 상황에서, 터치를 여러번 할 수 있는데 switchToLatest를 쓰면 마지막 publisher만 사용하게 된다.
    
    세훈 : 아아아아아 이해함ㅇㅇ
    
    ```Swift
    let publishers = PassthroughSubject<PassthroughSubject<Int, Never>, Never>()
    
    publishers
        .switchToLatest()
    ```
    
    ### ==**merge**==
    
    여러 publisher를 하나로 합쳐줌 merge된 publisher가 전부 complete 되어야, merge된 publisher도 complete 됨
    
    ### ==**combineLatest**==
    
    모든 publisher들의 value가 하나라도 방출되었을 때 부터, 튜플로 묶어서 전달함 Publisher A에서 1, 2를 방출하고 Publisher B에서 “a”를 방출헀다면 (2, “a”)가 튜플로 묶여서 보내진다. 그리고 다시 Publisher B에서 “b”를 방출하면 (2, “b”)가 튜플로 묶여서 보내진다. 모든 publisher 들이 complete되어야 combineLatest로 묶인 publisher도 complete 된다
    
    ### ==**zip**==
    
    publisher들의 value를 튜플로 묶어서 전달함 각 publisher들의 value가 짝이 맞는대로 튜플로 만듦 여러번 튜플로 묶이지는 않음
    
    ---
    
      
    
- ==**스톱워치 만들기 !**==
    
    > [!info] ESTsoft/ESTSoft/SwiftUI/Combine/250225 Combine at main · HISEHOONAN/ESTsoft  
    > 이스트소프트 프론티어 과정.  
    > [https://github.com/HISEHOONAN/ESTsoft/tree/main/ESTSoft/SwiftUI/Combine/250225%20Combine](https://github.com/HISEHOONAN/ESTsoft/tree/main/ESTSoft/SwiftUI/Combine/250225%20Combine)  
    
    이번에도 Chat gpt 70% + 본인 30%…
    
    아직 combine을 자유롭게 사용하기엔 시간이 꽤걸릴듯ㅠ
    
    ```Swift
    //주요 코드
    
    //publisher
    @Published var timeString: String = "00:00.00"
    @Published var isRunning = false
    @Published var laps: [String] = []
    
    private var startTime: Date?
    private var elapsedTime: TimeInterval = 0
    private var timer: AnyCancellable? // "timer"로 구독관리ㅇㅇ
    
    private func start() {
          startTime = Date() - elapsedTime //기본 0
          isRunning = true
          
          //Timer.publish라는 publisher
          timer = Timer.publish(every: 0.01, on: .main, in: .common)
              .autoconnect() //이새끼뭐노
              
              //  .sink라는 subscriber가 구독해서 Timer.publish가 원하는 
              //  0.01초마다 updateTime()을 호출함
              .sink { [weak self] _ in //closure 메모리 새는거 방지 [weak self] 약한참조ㅇㅇ
                  self?.updateTime()
           }
    }
        
    private func updateTime() {
        guard let startTime = startTime else { return }
        
        //  timeIntervalSince는 Date() - startTime을 계산
        elapsedTime = Date().timeIntervalSince(startTime)
        
        //  저장된 elapsedTime을 timeString으로 저장하는데 formatTime으로 시간으로 포멧
        timeString = formatTime(elapsedTime)
    }
    
    private func stop() {
          isRunning = false
          timer?.cancel() //타이머를 멈춤 == 구독해제
    }
    ```
    
      
    
    ---
    
    **timer publisher는 아래와 같이 만들 수 있습니다.**
    
    Ref) [https://peppo.tistory.com/183](https://peppo.tistory.com/183)
    
    ```Swift
    let main = Timer.publish(every: 1.0, on: .main, in: .common)
    ```
    
      
    
    두 가지 매개변수의 (on, in) 역할
    
      
    
    **On:** 어떤 RunLoop에서 타이머를 사용할지, (위 예제에선 main thread)
    
    **In:** 어떤 방식으로 타이머 Runloop를 실행할 건지, (여기선 기본값 common)
    
      
    
    타이머가 반환하는 Publisher는 ConnectablePublisher 인데,  
    이 Publisher를 구독하여 실행하려면 ==connect()== 메서드를 호출해야합니다.  
    첫 subscriber가 구독할때, ==자동으로 연결==시켜주는 자매품 ==autoconnect()== 메서드도 있어요!
    

  

---

여담으로 개인적으로 나누고 싶은 부분

- ==**UIkit 주의**==
    
    - 나도 오늘알게됨.
    
      
    
    네이버페이 결제, 웬만한 공지사항, 여러가지 정책등등을 웹에서 사용하기 위해 WebView를 사용.
    
    ==import WebKit== 프레임워크를 사용하고
    
    ==WKUIDelegate== 프로토콜을 채택한 ViewController가 있다.
    
      
    
    ```Swift
    var url: WebUrl = https://www.naver.com
    
    func openWebPage() {
        guard let url = URL(string: self.url.rawValue) else { return }
        let request = URLRequest(url: url)
            
        webView.load(request)
    }
    ```
    
    이렇게 선언해주면 url창을 열 수 있는 함수가 생김.
    
    ```Swift
    override func viewDidLoad() {
         super.viewDidLoad()
         view.backgroundColor = .white
         openWebPage()
     }
    ```
    
    이걸 viewDidLoad에 넣어주면 댐.
    
      
    
    ---
    
      
    
    ==WKWebView== 프로퍼티를 선언하고
    
    loadView라는 함수를 override시켜서 사용.
    
    ~~(그냥 구글링해서 사용했는데, 공식문서에 loadView라고 만들어서 모두 그렇게 쓰는듯.)~~
    
      
    
    - [https://developer.apple.com/documentation/webkit/wkwebview](https://developer.apple.com/documentation/webkit/wkwebview)
    - [https://developer.apple.com/documentation/webkit/wkuidelegate](https://developer.apple.com/documentation/webkit/wkuidelegate)
    
    ```Swift
    var webView: WKWebView!
    
    override func loadView() {
       let webConfiguration = WKWebViewConfiguration() 
       //WKWebViewConfiguration 웹뷰의 기본 config설정
       webView = WKWebView(frame: .zero, configuration: webConfiguration)
       webView.uiDelegate = self //델리게이트는 self
            
       view = UIView() //보여질 뷰를 만들고
       view.addSubview(webView) // 그 뷰에 웹뷰를 담음
           
    }
    ```
    
      
    
    ---
    
    근데
    
      
    
    ![[KakaoTalk_Photo_2025-02-25-14-51-51.png]]
    
      
    
    밑에 하단바 짤리는게 너무 ~~꼴보기~~ 불편하다는 cs가 들어옴.
    
    ```Swift
    override func viewWillAppear(_ animated: Bool) {
         super.viewWillAppear(animated)
         let navBarAppearance = UINavigationBarAppearance()
         navBarAppearance.configureWithOpaqueBackground()
         navBarAppearance.backgroundColor = UIColor.white
         self.navigationController?.navigationBar.standardAppearance = navBarAppearance
         self.navigationController?.navigationBar.scrollEdgeAppearance = navBarAppearance
         self.navigationController?.navigationBar.isHidden = true
     }
     
     //아 네비게이션바를 hidden해서 그렇구나 라고 생각했는데 그게아님.
     //여기서 네비게이션바 hidden false시키면 최상단 모든 부모뷰까지 다 네비바가 먹힘..;
     //여기서 네비바 hidden을 처리해도 이미 navigationStack으로 감싸져있음ㅇㅇ
     //즉 pop이 가능함ㅇㅇ
    ```
    
    ```Swift
    override func loadView() {
         let webConfiguration = WKWebViewConfiguration()
         webView = WKWebView(frame: .zero, configuration: webConfiguration)
         webView.uiDelegate = self
       
         view = UIView()
         view.addSubview(webView)
           
         webView.snp.makeConstraints { ///요기
           $0.top.bottom.equalTo(view.safeAreaLayoutGuide) //위, 아래는 안전구역ㅇㅇ
           $0.leading.trailing.equalToSuperview()//양옆은 슈퍼뷰와 동일시
       }
       
    }
    ```
    
    **웹뷰 객체의** ==**AutoLayout설정**==**을 안해줘서 그런거였음;;**
    
    ![[KakaoTalk_Photo_2025-02-25-15-02-31.png]]
    
    편안………………………………..
    
    결론 : webView도 따로 UIView로서 AutoLayout을 정해주지않으면 저절로 상위뷰로 지정됨.
    
    - ==전체코드==
        
        ```Swift
        //
        //  MyPageWebViewController.swift
        //  WithMorning_iOS
        //
        //  Created by 안세훈 on 8/21/24.
        //
        
        import UIKit
        import Foundation
        import WebKit
        import SnapKit
        import Then
        
        class MypageWebViewController: UIViewController, WKUIDelegate {
            
            var webView: WKWebView!
            var url: WebUrl = .perm
            
            override func loadView() {
                let webConfiguration = WKWebViewConfiguration()
                webView = WKWebView(frame: .zero, configuration: webConfiguration)
                webView.uiDelegate = self
                
                view = UIView()
                view.addSubview(webView)
                
                webView.snp.makeConstraints{
                    $0.top.bottom.equalTo(view.safeAreaLayoutGuide)
                    $0.leading.trailing.equalToSuperview()
                }
            }
            
            override func viewWillAppear(_ animated: Bool) {
                super.viewWillAppear(animated)
                let navBarAppearance = UINavigationBarAppearance()
                navBarAppearance.configureWithOpaqueBackground()
                navBarAppearance.backgroundColor = UIColor.white
                self.navigationController?.navigationBar.standardAppearance = navBarAppearance
                self.navigationController?.navigationBar.scrollEdgeAppearance = navBarAppearance
                self.navigationController?.navigationBar.isHidden = true
            }
            
            override func viewDidLoad() {
                super.viewDidLoad()
                view.backgroundColor = .white
                openWebPage()
            }
            
            func openWebPage() {
                guard let url = URL(string: self.url.rawValue) else { return }
                let request = URLRequest(url: url)
                
                webView.load(request)
            }
            
            
        }
        ```
        

---

  

  

  

- AccessToken - 만료시간 상대적으로 짧음 (보통 2시간)
    - 저 키 있어요
- RefreshToken - 만료시간이 상대적으로 김 (보통 7~14일)
    - 저 키를 위한 보조키가 있어욧.
    - AccessToken이 만료가 된다면, RefreshToken을 이용해 AccessToken을 재발급받음
    - 만약 AcessToken, RefreshToken이 모두 만료가 된다면, 재로그인을 진행함.