---
URL: https://github.com/ESTSOFT-iOS-01/PomoTodo
기술 스택:
  - CleanArchitecture
  - DependecyInjection
  - MVVM
  - SwiftData
  - SwiftUI
---
![[PomoTodo_최종_발표.pdf]]

[https://eunjin3786.tistory.com/31](https://eunjin3786.tistory.com/31)

# ETC or Tip (이 프로젝트에 대한)

- 스토리보드로 런치스크린을 만들고 Info.plist에 다음과 같이 사용하면 바로 연결 됌
    
    ![[스크린샷_2025-02-24_23.01.49.png]]
    
- AppConfig 모델은 프리셋 데이터를 의미하는것임
    
    ![[스크린샷_2025-02-24_22.15.24.png]]
    

# GitHub

Github Project

Github Action을 통한 브랜치 자동생성

(디코에다가 깃헙 알림 연동했음…)

커밋, 풀리 컨벤션 및 코드 리뷰도 진행함

![[스크린샷_2025-02-24_19.51.43.png]]

# CleanArchitecture

### Flow

- ViewModel ↔ Usecase ↔ Repository
- Entity - 앱에서 사용할 (화면에 보여주는용도?) 모델
- DTO - API 또는 DB에서 받아온 원시데이터? 모델
- 프로토콜을 타입으로 변수를 선언해서 (Usecase, Repository) 구현체에 대한 정보는 모르게 관리?

## 프로젝트 코드 예시

## ViewModel

```Swift
final class ToDoViewModel: ObservableObject {
  
  // MARK: - UI State
  @Published var todos: [Todo] = []
  @Published var tags: [Tag] = []
  
  enum Action {
    case onAppear
    case addEmptyTodo(tagId: String)
    case deleteTodo(id: String)
    case toggleTodo(id: String, status: Bool)
    case nameChanged(id: String, name: String)
  }
  
  private var pomoTodoUseCase: PomoTodoUseCase
  
  init (pomoTodoUseCase: PomoTodoUseCase) {
    self.pomoTodoUseCase = pomoTodoUseCase
    loadData()
  }
  
  func send(_ action: Action) {
    switch action {
    case .onAppear:
      loadData()
    case .addEmptyTodo(let tagId):
      let emptyTodo = Todo(tagId: tagId, name: "")
      todos.append(emptyTodo)
      pomoTodoUseCase.setTodayTodos(todos)
			...
    }
  }
}
extension ToDoViewModel {
  // MARK: - Private function
  private func loadData() {
    self.tags = pomoTodoUseCase.getAppConfig().tags
    self.todos = pomoTodoUseCase.getTodayTodos()
    if todos.isEmpty {
      tags.forEach {
        todos.append(Todo(tagId: $0.id, name: ""))
      }
    }
  }
}
```

## Usecase Protocol

```Swift
protocol PomoTodoUseCase {
  
  // MARK: - TimerUseCase
  
  /// 오늘의 `PomoDay`를 가져오는 메서드
  /// - 만약 기존에 데이터가 없으면 새로운 `PomoDay`를 생성하여 반환
  /// - Returns: 오늘 날짜의 `PomoDay`
  func getTodayPomoDay() -> PomoDay
  
  /// `tagTimeRecord`를 추가하는 메서드
  /// - Parameters:
  ///   - todayPomoDay: 업데이트할 오늘의 `PomoDay`
  ///   - tagTimeRecord: 추가할 `TagTimeRecord`
  func addTagTimeRecords(
    todayPomoDay: PomoDay,
    tagTimeRecord: TagTimeRecord
  )
  
  /// `PomoDay`의 `tomatoCnt`와 `cycleCnt` 값을 설정하는 메서드
  /// - Parameters:
  ///   - todayPomoDay: 업데이트할 오늘의 `PomoDay`
  ///   - tomatoCnt: 설정할 토마토 개수
  ///   - cycleCnt: 설정할 사이클 비율
  func updateTomatoAndCycle(
    todayPomoDay: PomoDay,
    tomatoCnt: Int,
    cycleCnt: Double
  )
  
  // MARK: - StatsUseCase
  
  /// 저장된 모든 `PomoDay` 데이터를 가져오는 메서드
  /// - Returns: 저장된 모든 `PomoDay` 리스트
  func getAllPomoDays() -> [PomoDay]
  
  // MARK: - TodoUseCase
  
  /// 오늘의 `Todo` 목록을 가져오는 메서드
  /// - Returns: 오늘 생성된 `Todo` 리스트
  func getTodayTodos() -> [Todo]
  
  /// 오늘의 `Todo` 목록을 설정하는 메서드
  /// - Parameter todos: 저장할 `Todo` 리스트
  func setTodayTodos(_ todos: [Todo])
  
  // MARK: - AppConfigUseCase
  
  /// 앱의 기본 설정(`AppConfig`)을 가져오는 메서드
  /// - Returns: 현재 앱의 설정 데이터(`AppConfig`)
  func getAppConfig() -> AppConfig
  
  /// 앱의 기본 설정(`AppConfig`)을 업데이트하는 메서드
  /// - Parameter appConfig: 변경할 앱 설정 데이터(`AppConfig`)
  func setAppConfig(_ appConfig: AppConfig)
  
}
```

## Usecase Implement

```Swift
final class PomoTodoUseCaseImpl: PomoTodoUseCase {
  
  private let pomoDayRepository: PomoDayRepository
  private let appConfigRepository: AppConfigRepository
  
  init(
    pomoDayRepository: PomoDayRepository,
    appConfigRepository: AppConfigRepository
  ) {
    self.pomoDayRepository = pomoDayRepository
    self.appConfigRepository = appConfigRepository
  }
  
  ...
  
  func getTodayTodos() -> [Todo] {
    print("Impl:", \#function)
    
    let today = Date().formattedDate
    
    let result = pomoDayRepository.fetchPomoDay(date: today)
    switch result {
    case .success(let pomoDay):
      guard let pomoDay else {
        print("오늘의 PomoDay가 존재하지 않음")
        return []
      }
      return pomoDay.todos
    case .failure(let error):
      print(error)
      return []
    }
  }
  
  func setTodayTodos(_ todos: [Todo]) {
    print("Impl:", \#function)
    
    let today = Date().formattedDate
    
    let result = pomoDayRepository.fetchPomoDay(date: today)
    switch result {
    case .success(let pomoDay):
      guard let pomoDay else {
        print("오늘의 PomoDay가 존재하지 않음")
        return
      }
      pomoDayRepository.setTodos(pomoDay: pomoDay, todos: todos)
    case .failure(let error):
      print(error)
    }
  }
  ...
}
```

## Repository Protocol

```Swift
protocol PomoDayRepository {
  func createPomoDay(_ pomoDay: PomoDay)
  func fetchPomoDay(date: Date) -> Result<PomoDay?, Error>
  func fetchAllPomoDays() -> Result<[PomoDay], Error>
  func updatePomoDay(_ pomoDay: PomoDay)
  func setTodos(pomoDay: PomoDay, todos: [Todo])
}
```

## Repository Implement

```Swift
final class PomoDayRepositoryImpl: PomoDayRepository {
  
  private let modelContext: ModelContext
  
  init(modelContext: ModelContext) {
    self.modelContext = modelContext
  }
  
  ...
  
  func fetchPomoDay(date: Date) -> Result<PomoDay?, any Error> {
    print("Impl:", \#function)
    
    let targetDate = date
    let predicate = \#Predicate<PomoDayDTO> { $0.date == targetDate }
    let descriptor = FetchDescriptor<PomoDayDTO>(predicate: predicate)
    
    do {
      guard let data = try modelContext.fetch(descriptor).first else {
        print(SwiftDataError.modelNotFound)
        return .success(nil)
      }
      return .success(data.toEntity())
    } catch {
      return .failure(SwiftDataError.fetchError)
    }
  }
  
  func fetchAllPomoDays() -> Result<[PomoDay], any Error> {
    print("Impl:", \#function)
    
    let now = Date().formattedDate
    let predicate = \#Predicate<PomoDayDTO> { $0.date <= now }
    let sort = SortDescriptor(\PomoDayDTO.date, order: .forward)
    let descriptor = FetchDescriptor(predicate: predicate, sortBy: [sort])
    
    do {
      let datas = try modelContext.fetch(descriptor)
      return .success(datas.map { $0.toEntity() })
    } catch {
      return .failure(SwiftDataError.fetchError)
    }
  }
  
  func setTodos(pomoDay: PomoDay, todos: [Todo]) {
    print("Impl:", \#function)
    
    let result = findPomoDayByDate(pomoDay.date)
    switch result {
    case .success(let model):
      model.todos.forEach { modelContext.delete($0) }
      model.todos = todos.map { TodoDTO($0) }
    case .failure(let error):
      print(error)
    }
  }
  ...
}


extension PomoDayRepositoryImpl {
  private func findPomoDayByDate(
    _ date: Date
  ) -> Result<PomoDayDTO, SwiftDataError> {
    print("Impl:", \#function)
    
    let targetDate = date
    let predicate = \#Predicate<PomoDayDTO> { $0.date == targetDate }
    let descriptor = FetchDescriptor<PomoDayDTO>(predicate: predicate)
    
    do {
      guard let data = try modelContext.fetch(descriptor).first else {
        return .failure(.modelNotFound)
      }
      return .success(data)
    } catch {
      return .failure(.fetchError)
    }
  }
}
```

  

### Clean Architectrue, Clean Swfit

정말 뜬금없지만 알아보다보니 Clean Swift라는것도 있었다… 이것도 알아두면 좋을거 같아서

- Clean Architecture
    - 계층화된 구조
    - 의존성 역전 원칙 (DIP) - 내부 계층은 외부 계층에 의존하지 않으며, 상위 계층에서 하위 계층으로 의존한다.
    - 독립성 - 비즈니스 로직(Entities)이랑 UI/프레임워크는 분리되어 있다.
- Clean Swift
    - VIP 로 구성되어있음
        - V - View (화면을 구성하는 VC)
        - I - Interactor (비즈니스 로직 처리, 데이터 연산 및 네트워크 요청 등 담당)
        - P - Presenter (UI와 상호작용하며 Interactor의 데이터를 View에 전달)
    - VIP의 특징
        - 명확한 역할 분담 - 각 계층 역할을 엄격하게 구분
        - 의존성 역전 - View는 Presenter에 의존, Presenter는 Interactor에 의존

**Clean Architecture**는 일반적인 아키텍처 개념이고, 그 자체가 플랫폼에 구애받지 않아 다양한 플랫폼에 적용이 가능

[https://eunjin3786.tistory.com/207?category=837198](https://eunjin3786.tistory.com/207?category=837198)

[https://eunjin3786.tistory.com/198](https://eunjin3786.tistory.com/198) (이건 뭔가 관련된것 같아서..)

  

**Clean Swift**는 VIP 패턴을 사용해 iOS에 특화된 아키텍처임.

[https://eunjin3786.tistory.com/165](https://eunjin3786.tistory.com/165)

[https://eunjin3786.tistory.com/383](https://eunjin3786.tistory.com/383)

[https://clean-swift.com/](https://clean-swift.com/)

[https://velog.io/@ssionii/Clean-Swift-a.k.a-VIP-%EC%97%90-%EB%8C%80%ED%95%B4-%EC%95%84%EB%9D%BC%EB%B3%B4%EC%9E%90](https://velog.io/@ssionii/Clean-Swift-a.k.a-VIP-%EC%97%90-%EB%8C%80%ED%95%B4-%EC%95%84%EB%9D%BC%EB%B3%B4%EC%9E%90)

GPT 요약

![[스크린샷_2025-02-24_22.42.28.png]]

  

# Dependency Injection (DI)

[https://eunjin3786.tistory.com/115](https://eunjin3786.tistory.com/115)

[https://eunjin3786.tistory.com/233](https://eunjin3786.tistory.com/233)

[https://eunjin3786.tistory.com/116](https://eunjin3786.tistory.com/116)

- DI 라이브러리도 존재함

## DIContainer

```Swift
@Observable
final class DIContainer {
  static let shared = DIContainer()
  
  private let repositoryProvider: RepositoryProvider
  let pomoTodoUseCase: PomoTodoUseCase
  
  init() {
    self.repositoryProvider = RepositoryProvider()
    pomoTodoUseCase = PomoTodoUseCaseImpl(
      pomoDayRepository: repositoryProvider.pomoDayRepository,
      appConfigRepository: repositoryProvider.appConfigRepository
    )
    _ = pomoTodoUseCase.getTodayPomoDay()
  }
  
  func makeToDoViewModel() -> ToDoViewModel {
    ToDoViewModel(
      pomoTodoUseCase: pomoTodoUseCase
    )
  }
  
  func makePomoViewModel() -> PomoViewModel {
    PomoViewModel(
      pomoTodoUseCase: pomoTodoUseCase
    )
  }
  
  func makeSettingViewModel() -> SettingViewModel {
    SettingViewModel(
      pomoTodoUseCase: pomoTodoUseCase
    )
  }
  
  func makeStatisticsViewModel() -> StatisticsViewModel {
    StatisticsViewModel(
      pomoTodoUseCase: pomoTodoUseCase
    )
  }
}
```

Repository와 Usecase 역시 DIContainer에서 주입해준다.

RepositoryProvider 클래스를 만들어놓고 DIContainer에서 주입할 때 사용한다.

### RepositoryProvider

```Swift
final class RepositoryProvider {
  
  private let storage: SwiftDataStorage
  
  init() {
    storage = SwiftDataStorage()
  }
  
  lazy var pomoDayRepository: PomoDayRepository = {
    PomoDayRepositoryImpl(modelContext: storage.modelContext)
  }()
  
  lazy var appConfigRepository: AppConfigRepository = {
    AppConfigRepositoryImpl(modelContext: storage.modelContext)
  }()
}
```

## MainTabBarView (여기서 DIContainer 사용) (또는 프리뷰에 뷰모델 넣어주는 용으로 사용)

```Swift
struct MainTabBarView: View {
  @State private var selectedTab: Tab = .Pomo
  @Environment(DIContainer.self) private var container: DIContainer
  
  var body: some View {
    TabView(selection: $selectedTab) {
      PomoView()
        .environmentObject(container.makePomoViewModel())
        .tabItem {
          tabItemView(for: .Pomo, isSelected: selectedTab == .Pomo)
        }
        .tag(Tab.Pomo)
      
      StatisticsView(
        viewModel: container.makeStatisticsViewModel()
      )
      .tabItem {
        tabItemView(for: .Chart, isSelected: selectedTab == .Chart)
      }
      .tag(Tab.Chart)
      
      ToDoView(viewModel: container.makeToDoViewModel())
        .tabItem {
          tabItemView(for: .Todo, isSelected: selectedTab == .Todo)
        }
        .tag(Tab.Todo)
      
      SettingView()
      .environmentObject(
        container.makeSettingViewModel()
      )
      .tabItem {
        tabItemView(for: .Setting, isSelected: selectedTab == .Setting)
      }
      .tag(Tab.Setting)
    }
    .tint(.indigoNormal)
    .onAppear {
      setupTabBarAppearance()
    }
//    .onChange(of: selectedTab) { oldTab, newTab in
//      if newTab != .Pomo {
//        // pomoVM.saveTomatoProgress()
//      }
//    }
  }
  
  //MARK: - Funcs
  
  /// 탭바 아이템 세팅
  private func tabItemView(for currentTab: Tab, isSelected: Bool) -> some View {
    VStack {
      Image(systemName: isSelected ? currentTab.selectedIcon : currentTab.unselectedIcon)
        .environment(\.symbolVariants, .none)
        .symbolRenderingMode(.hierarchical)
        .foregroundStyle(isSelected ? .primary : .secondary)
        .scaleEffect(isSelected ? 1.1 : 1.0)
        .animation(.easeInOut(duration: 0.2), value: isSelected)
      
      Text(currentTab.labelName)
        .font(.caption)
        .foregroundStyle(isSelected ? .primary : .secondary)
    }
  }
  
  /// 탭바 스타일 세팅
  private func setupTabBarAppearance() {
    let appearance = UITabBarAppearance()
    appearance.configureWithOpaqueBackground()
    UITabBar.appearance().standardAppearance = appearance
    UITabBar.appearance().scrollEdgeAppearance = appearance
  }
  
}

\#Preview {
  MainTabBarView()
    .environment(DIContainer())
}
```

# Extension

UIApplication+Extension

```Swift
import Foundation
import SwiftUI

// 한번에 하나의 제스처만 인식되게 하는 코드 (여러 제스처 동시에 인식 안되게)
// @retroactive는 Swift6에 도입, 
// 기존 정의된 클래스나 구조체에 나중에 프로토콜을 추가하는 방식으로, 이미 존재하는 타입들에 새로운 프로토콜 추가 가능
extension UIApplication: @retroactive UIGestureRecognizerDelegate {
  public func gestureRecognizer(_ gestureRecognizer: UIGestureRecognizer, shouldRecognizeSimultaneouslyWith otherGestureRecognizer: UIGestureRecognizer) -> Bool {
    return false
  }
}

extension UIApplication {
  func hideKeyboard() { //화면 아무대나 선택했을때 키보드 내려가게 하는거
    let scenes = UIApplication.shared.connectedScenes
    let windowScene = scenes.first as? UIWindowScene
    guard let window = windowScene?.windows.first else { return }
    let tapRecognizer = UITapGestureRecognizer(target: window, action: \#selector(UIView.endEditing))
    tapRecognizer.cancelsTouchesInView = false
    tapRecognizer.delegate = self
    window.addGestureRecognizer(tapRecognizer)
  }
}
```

> 해당 부분을 심도있게까지 파지는 않아서 상세한 내부사항까지는 확인을 안한상태입니다만  
> 제가 쓴 부분을 말씀드려보면 처음 쓴 이유는 화면을 터치했을때 텍스트 필드를 내리기 위해 검색을 하다가 찾아서 가져왔습니다  
> 
>   
> 추가로 해당 소스같은경우에 제가 소스를 이해하기로 gestureRecognizerdelegate 가 false를 리턴하면 제스처를 동시에 못받는다가 맞습니다. 그러면 텍스트 필드가 여러개인 저희 앱의 경우 맞지 않다고 볼수도있는데 텍스트 필드로 저부분을 false와 true로 작동해보면  
> 
>   
> false의 경우 A 텍스트 필드를 선택하고 B텍스트 필드를 선택하면 자연스럽게 이동 되지만 true로 할 경우 텍스트 필드를 터치했다는 제스처가 동시 입력이 가능해 지면서 키보드가 내려갔다가 다시 올라오게됩니다.  
> 
>   
> 아마 동시입력이 불가능해지면 텍스트 필드가 입력되고 있는 상황이 지속되는 것이고 동시입력이 가능해지면 텍스트 필드가 입력되는 상황에 새로운 텍스트 필드 터치라는 제스처가 새로 입력되면서 키보드가 내려갔다 올라오는 것 같습니다  

[https://longlivedrgn-miro.tistory.com/82](https://longlivedrgn-miro.tistory.com/82)

조금 다른 내용이지만, 제스처를 여러개 받기위해 gestureRecognizer를 사용하는 블로그글

  

UIScreen+Extension

```Swift
import SwiftUI

extension UIScreen {
  static var screenWidth: CGFloat { //기기 화면 너비
    UIScreen.main.bounds.width
  }
  
  static var screenHeight: CGFloat { //기기 화면 높이
    UIScreen.main.bounds.height
  }
}

struct DynamicPadding {
//상수로 파라미터값을 넣으면 기기크기에 비례한 비율로 계산 후 반환
  static func getHeight(_ size: CGFloat) -> CGFloat { 
    return size * UIScreen.screenHeight / 874
  }
  
  static func getWidth(_ size: CGFloat) -> CGFloat {
    return size * UIScreen.screenWidth / 402
  }
}
```

TimeInterval+Extension

```Swift
import Foundation
// typealias로 Double의 별명을 지어준것 뿐 Time rorcpdhk rkxdmsrjs dkslek.
extension TimeInterval {
  /// TimeInterval의 1분 (60초)
  static var minute: TimeInterval { return 60 }
  
  var asInt: Int {
    return Int(self)
  }
 
  func formattedTime() -> String { //시간 포맷에 맞춰서 String으로 반환
    let hours = Int(self) / 3600
    let minutes = (Int(self) % 3600) / 60
    return hours > 0 ? "\(hours)h \(minutes)m" : "\(minutes)m"
  }

  var intMin: Int {
    get { return Int(self / .minute) }
  }
}
```

Constant

```Swift
public struct Constants {
    public struct Timer { // 타이머 생성시 태그에 따른 디자인 색 정의
        public static let colorSets: [TimerColorSet] = [indigoSet, blueSet, cyanSet, tealSet]
        public static let indigoSet = TimerColorSet(id: 0, normalColor: .indigoNormal, darkColor: .indigoDark, darkerColor: .indigoDarker)
        public static let blueSet = TimerColorSet(id: 1, normalColor: .blueNormal, darkColor: .blueDark, darkerColor: .blueDarker)
        public static let cyanSet = TimerColorSet(id: 2, normalColor: .cyanNormal, darkColor: .cyanDark, darkerColor: .cyanDarker)
        public static let tealSet = TimerColorSet(id: 3, normalColor: .tealNormal, darkColor: .tealDark, darkerColor: .tealDarker)
    }
}
```

Date+Extensions

```Swift
extension Date {
// 첫 초기화로 설정이 유지 되므로 성능 최적화
  static private let configuredCalendar: Calendar = {
    var calendar = Calendar.current  //현재 시스템의 캘린더 반환
    calendar.locale = .current  // 시스템의 로케일을 사용
    calendar.timeZone = .current  // 시스템의 시간대 사용
    return calendar
  }()
  
  /// 년, 월, 일 값만 사용하기 위해 형식화한 Date - [Ex. 2024-10-31 15:00:00 +0000]
  var formattedDate: Date {
    Self.configuredCalendar.startOfDay(for: self)
  }
  
  var formattedDateToString: String {
    let formatter = DateFormatter()
    formatter.dateFormat = "M월 dd일 (E)"
    formatter.locale = Locale(identifier: "ko_KR")
    return formatter.string(from: self)
  }
}
```

  

Font+Extensions

```Swift
/// Pretendard 폰트 가중치 Enum
enum PretendardWeight: String {
    case thin = "Pretendard-Thin"
    case regular = "Pretendard-Regular"
    case medium = "Pretendard-Medium"
    case light = "Pretendard-Light"
    case extraLight = "Pretendard-ExtraLight"
    case extraBold = "Pretendard-ExtraBold"
    case bold = "Pretendard-Bold"
    case semiBold = "Pretendard-SemiBold"
    case black = "Pretendard-Black"
}

extension Font {
    static func pretendard(_ weight: PretendardWeight, size: CGFloat) -> Font {
        Font.custom(weight.rawValue, size: size)
    }
}
```

  

Int+Extensions

```Swift
extension Int {
  var asTimeInterval: TimeInterval {
    return TimeInterval(self)
  }
  
  var asDouble: Double {
    return Double(self)
  }
}
```

# Test Code

테스트 코드도 작성되어 있음 (Usecase 테스트)

```Swift
import XCTest
@testable import PomoTodo

final class PomoTodoTests: XCTestCase {
  
  var pomoTodoUseCase: PomoTodoUseCase?
  
  override func setUpWithError() throws { // 여기서 테스트에 사용할 UseCase를 정의해줌
    try super.setUpWithError()
    let testSwiftDataStorage = SwiftDataStorage()
    let appConfigRepository = AppConfigRepositoryImpl(
      modelContext: testSwiftDataStorage.modelContext
    )
    let pomoDayRepository = PomoDayRepositoryImpl(
      modelContext: testSwiftDataStorage.modelContext
    )
    pomoTodoUseCase = PomoTodoUseCaseImpl(
      pomoDayRepository: pomoDayRepository,
      appConfigRepository: appConfigRepository
    )
  }
  
  override func tearDownWithError() throws { // 이거 뭐더라 테스트 실패나 오류나면 여기 들어와서 메모리 해제하는걸로 앎
    pomoTodoUseCase = nil
    try super.tearDownWithError() 
  }
  
  // MARK: - PomoTodoUseCase 테스트
  func testPomoTodoUseCase() throws {
    guard let pomoTodoUseCase = pomoTodoUseCase else {
      XCTFail("pomoTodoUseCase should not be nil")
      return
    }
    
    // appConfig create test
    let appConfig = pomoTodoUseCase.getAppConfig()
    print(appConfig)
    
    // appConfig fetch test
    let fetchAppConfig = pomoTodoUseCase.getAppConfig()
    XCTAssertEqual(appConfig, fetchAppConfig, "appConfig가 일치하지 않습니다.")
    
    // pomoDay create test
    let pomoDay = pomoTodoUseCase.getTodayPomoDay()
    print(pomoDay)
    
    // pomoDay fetch test
    let fetchTodayPomoDay = pomoTodoUseCase.getTodayPomoDay()
    XCTAssertEqual(pomoDay, fetchTodayPomoDay, "오늘의 Pomodoro Day가 일치하지 않습니다.")
    
    
  }
}
```