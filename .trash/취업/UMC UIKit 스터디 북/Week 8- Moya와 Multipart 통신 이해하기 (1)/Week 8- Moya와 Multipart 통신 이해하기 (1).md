- [[#📋 학습 목표]]
- [[#✋ 잠깐! 스터디 인증샷 찍으셨나요?]]
- [[#🔥 8주차 개념 설명]]
    - [[#1️⃣ Moya란 무엇일까요?]]
    - [[#2️⃣ Multipart는 무엇일까요?]]
    - [[#3️⃣ Multipart를 사용해 어떻게 통신할까요?]]
- [[#🔥 8주차 개념 점검]]
- [[#📚 8주차 실습]]
    - [[# 1️⃣ Moya를 이용해서 유저 정보 받아오기]]
    - [[# 2️⃣ 서버에 이미지 업로드하기]]
- [[#💻 8주차 과제]]
    - [[#1. 검색 화면 및 검색 세부 화면 레이아웃을 구현해주세요!]]
    - [[#2. 메인 화면과 검색 화면 간 화면 전환을 구현해주세요!]]
    - [[#3. 주어진 API 명세서를 활용해 검색 세부 화면에서 통신 및 데이터 바인딩을 진행해주세요!]]
    - [[#4. 과제가 완성 되었다면 깃허브 링크와 시연 영상을 첨부해주세요!]]
- [[#🤔 8주차 트러블 슈팅]]
- [[#📌 이번 주차에는 이런 내용을 학습했어요!]]
- [[#❓ 이런 질문이 있어요!]]

  

## 📋 학습 목표

---

- `Moya` 라이브러리에 대해 이해하고 해당 라이브러리를 사용해 API 통신을 구현할 수 있다.
- `Multipart` 통신에 대해 이해하고 이미지 통신을 구현할 수 있다.

## ✋ 잠깐! 스터디 인증샷 찍으셨나요?

---

> [!important] 스터디 시작 전 ==**스터디 인증샷을 촬영**==해주세요!
> 
> 스터디는 대면이 원칙이며, 비대면 스터디의 경우에도 최대한 카메라를 킨 후 진행해주세요.
> 
> 아래 임베드 블록에 인증샷을 임베드해 주시면 됩니다 🫶

- 사진
    
    ![[KakaoTalk_Photo_2024-11-24-00-22-10.png]]
    
      
    

## 🔥 8주차 개념 설명

---

### 1️⃣ Moya란 무엇일까요?

> [!important] 저번 주차에서 `URLSession`과 `Alamofire`에 대해 다뤘는데 기억하시나요?
> 
> 오늘 배울 `Moya` 라이브러리는 `URLSession`과 `Alamofire` 에 기반하기 때문에 저번 주에 배운 개념을 짚고 넘어가보도록 하겠습니다.

`URLSession`은 iOS 앱 내에서 서버와 통신하기 위해 Apple이 제공하는 네트워킹 API입니다.

`Swift`에서 제공하는 가장 기본적인 서버 통신 API이기 때문에 **로우 레벨의 코드를 작성**할 수 있고, **가장 기본적인 방법으로 서버 통신을 구현**할 수 있어요!

**다른 서드파티 라이브러리를 사용하지 않는다는 장점**이 있지만 **사용이 복잡하고 코드의 가독성이 떨어진다는 단점** 또한 존재합니다.

`Alamofire` 는 이러한 `URLSession`의 단점을 보완하기 위해 `URLSession` 를 `**추상화**`해 만들어진 오픈소스 라이브러리입니다.

**✋ 여기서 잠깐! 추상화라는 개념이 이해가 안가요**

> `**추상화**`는 6주차에서 배웠던 개념인데요! 객체지향 프로그래밍의 4가지 특징 중 하나로 등장했던 것을 기억하시나요?
> 
> 객체의 공통적인 부분들만 추출해 구현했기 때문에 구체적인 부분을 구현하지 않고, 추상적인 부분만 구현되어 있어요.
> 
> 객체들의 공통적인 부분만을 따로 추출해 구현해 놓은 것이라고 보시면 좋을 것 같습니다.

이렇게 `URLSession` 을 한번 추상화한 라이브러리인 `Alamofire` 는 코드가 간소화되고 가독성 측면에서 보다 성능이 개선되었다는 특징이 있죠!

그럼에도 불구하고 유지보수가 힘들다는 단점 또한 존재합니다. 이 부분에 대해 조금 더 자세히 알아볼까요?

우리가 곧 배우게 될 `Moya`의 깃허브 리드미 중 일부분을 미리 인용해서 한 번 읽어볼게요!

> [!important] You're a smart developer. You probably use [Alamofire](https://github.com/Alamofire/Alamofire) to abstract away access to `URLSession` and all those nasty details you don't really care about. But then, like lots of smart developers, you write ad hoc network abstraction layers. They are probably called `APIManager` or `NetworkModel`, and they always end in tears.<br><br>==당신은 똑똑한 개발자입니다. 아마== ==`URLSession`====에 대한 액세스와 그다지 신경 쓰지 않는 모든 지저분한 세부 사항을 추상화하기 위해== ==[Alamofire](https://github.com/Alamofire/Alamofire)====를 사용했을 지도 몰라요. 그러나 많은 똑똑한 개발자처럼 네트워크 추상화 레이어를 작성할 겁니다. 그건 아마도== ==`APIManager`== ==또는== ==`NetworkModel`====이라고 불리겠죠, 그리고 이 작업은 항상 눈물로 끝이 납니다.==
> 
>   
>   
> [✏️ Moya Github 리드미](https://github.com/Moya/Moya)

위 리드미에서는 `Alamofire`가 네트워크 레이어를 작성해야 한다는 문제를 지적하고 있어요.

바로 이 부분이 `Alamofire` 의 유지보수가 힘들어지는 원인이며 큰 단점이 되는 부분입니다.

모든 API 통신 시 `AF.request` 를 하나하나 작성하기 굉장히 번거롭기 때문에 보통 `Alamofire` 를 사용할 때는 `APIManager` 또는 `NetworkModel` 이라고 부르는 추상화 레이어를 하나 더 작성합니다.

뭔가 어려워 보이지만 그냥 `**Alamofire**` **를 조금 더 간편한 형태로 사용하기 위해 감싸놓은 것!** 정도로 이해하시면 되겠습니다.

이렇게 사용자가 직접 `Alamofire` 를 사용하기 위해 네트워크 레이어라는 것을 정의해야 하는데, 이 부분이 나중에 유지보수하기에도 번거롭다는 단점이 있습니다. 공식 문서에서는 눈물까지 난다고 하네요.

이런 부분을 보완하기 위해 `Alamofire` 를 한 번 더 추상화해서 나온 라이브러리가 바로 `Moya` 라이브러리입니다!

![[7a3a01bf-8b66-409d-97de-f35ae0be878b.png]]

  

> [!info] GitHub - Moya/Moya: Network abstraction layer written in Swift.  
> Network abstraction layer written in Swift.  
> [https://github.com/Moya/Moya](https://github.com/Moya/Moya)  

![[c5b5a24e-3421-4f6f-b90c-c71cf9e7e317.png]]

한눈에 봐도 위 표보다는 훨씬 간결해보이죠?

`Moya`는 `Alamofire` 의 네트워크 레이어를 열거형 `enum` 을 사용해 안전하고 정돈된 방식으로 캡슐화해 사용해요. 네트워크 레이어를 템플릿화했다고 생각하시면 이해가 편하실 것 같습니다.

사용자가 네트워크 레이어를 정의할 필요가 없으니 유지보수에도 용이하고, `enum`을 사용하기 때문에 `type-safe`한 방식으로 통신할 수 있다는 장점이 있습니다.

또한 재사용성과 가독성 또한 높아지기 때문에 개발자가 네트워크 통신에 있어 `Request`, `Response`에만 집중할 수 있게 해준다는 장점 또한 존재합니다!

그래서 모야가 모야? 라고 물으신다면 … 이제부터 함께 알아가보도록 하겠습니다.

### 📡 `Moya` 를 사용한 네트워크 통신은 어떻게 이루어질까요?

`Moya`를 사용한 네트워크 통신은 크게 5단계로 이루어지는데요! 개괄적으로 나타내면 다음과 같습니다.

> **1️⃣ 사용할 API 목록들을 작성한** `**enum**` **객체 선언**
> 
> **2️⃣ 1번에서 선언한 객체의** `**extension**`**을 작성하고** `**TargetType**` **프로토콜 채택 및 내용 지정**
> 
> **3️⃣ 요청 및 응답 내용을 저장할 모델 생성**
> 
> **4️⃣ 네트워크 요청을 수행할** `**Provider**` **인스턴스 생성**
> 
> **5️⃣ 실제 네트워크 요청 및 응답 처리**

무슨 말인지 하나도 모르겠다고 하신다면 정상입니다! 특히 `TargetType` , `Provider` 와 같은 개념은 `Moya` 라이브러리 내에 존재하기 때문에 현재는 모르실 수밖에 없어요.

이제 단계별로 하나하나 살펴보도록 하겠습니다.

> **1️⃣ 사용할 API 목록들을 작성한** `**enum**` **객체 선언**

예를 들어 유저와 관련된 `API`들이 있다면 이 `API`를 모두 모아 `enum` 객체를 선언할 수 있습니다.

이 객체는 이후 `extension`에서 `TargetType` 프로토콜을 채택하게 되기 때문에 `(용도)TargetType` 형식으로 변수명을 지어주는 것을 권장드립니다.

저는 유저와 관련된 `API`를 `enum` 안에 `case` 형식으로 선언했기 때문에 `UserTargetType`이라는 변수명을 지어주었어요.

`enum` 내 케이스는 각각 `API` 하나씩을 뜻한다고 생각하시면 됩니다.

괄호로 둘러쌓여 요구되는 변수들은 `API`에서 요청 시 요구하는 파라미터들입니다.

```Swift
enum UserTargetType {
    case appleLogin(identityToken: String)
    case kakaoLogin(accessToken: String)
    case refreshToken(refreshToken: String)
    case getUserInfo
}
```

> **2️⃣ 1번에서 선언한 객체의** `**extension**`**을 작성하고** `**TargetType**` **프로토콜 채택 및 내용 지정**

Moya에서 제공해주는 `TargetType`을 통해서 각 도메인에서 생기는 다양한 서버 통신 내용들을 `enum`을 통해 분기 처리해 손쉽게 제작할 수 있어요!

1번에서 `enum`으로 작성한 객체에 대해 `extension`을 생성하고 `TargetType` 이라는 프로토콜을 채택하는 형식으로 진행하는데요.

이후 `comfirm`을 진행하게 되면 API 통신에 필요한 요소들이 자동으로 추가되고 내용을 작성할 수 있게 됩니다.

하나씩 알아보도록 할게요!

```Swift
var baseURL: URL {
        return "https://api.base.url"
    }
```

`baseURL` 부분에는 서버에서 제공하는 `BaseURL`을 작성합니다.

`BaseURL` 뒤에 `/기능` 형식으로 주소가 길어지는 것이 일반적이기 때문에 만약 `BaseURL` 을 모르신다면 모든 API의 공통적인 부분까지 작성하신다고 생각하시면 됩니다!

```Swift
var path: String {
        switch self {
        case .appleLogin, .kakaoLogin:
            return "/api/v1/auth/signin"
        case .refreshToken:
            return "/api/v1/auth/reissue"
        case .getUserInfo:
            return "/api/v1/users/me"
        }
    }
```

`baseURL` 부분에서 요청 URL의 공통적인 부분을 작성하셨다면 `path` 부분에는 이후 API마다 달라지는 선택적인 부분들을 작성해주시면 됩니다.

```Swift
var method: Moya.Method {
        switch self {
        case .appleLogin, .kakaoLogin, .refreshToken:
            return .post
        case .getUserInfo:
            return .get
        }
    }
```

`method` 부분에는 HTTP method를 적어주시면 됩니다.

`.get`, `.post`, `.patch` 처럼 입력하시면 되고 `.`을 누르면 자동완성을 사용할 수 있으니 참고하시면 좋을 것 같습니다!

```Swift
var task: Task {
        switch self {
        case let .appleLogin:
            return .requestJSONEncodable(SocialLoginRequestModel(provider: "APPLE"))
        case let .kakaoLogin:
            return .requestJSONEncodable(SocialLoginRequestModel(provider: "KAKAO"))
        case .refreshToken:
            return .requestPlain
        case .getUserInfo:
            return .requestPlain
        }
    }
```

`task` 에서는 API마다 어떤 방식으로 통신할 것인지를 정의합니다.

`JSON` 데이터의 경우 `.requestJSONEncodable` 을 사용하며, 요청에 필요한 파라미터가 있다면 괄호를 열어 API 형식과 동일한 모델을 작성해주시면 됩니다!

```Swift
var headers: [String : String]? {
        switch self {
        case .appleLogin(let identityToken):
            return ["Authorization": identityToken, "Content-Type": "application/json"]
        case .kakaoLogin(let accessToken):
            return ["Authorization": accessToken, "Content-Type": "application/json"]
        case .getUserInfo:
            guard let token = DefaultKeychainService.shared.accessToken else {
                fatalError("No access token available")
            }
            return [
                "Content-Type": "application/json",
                "Authorization": "Bearer \(token)"
            ]
        }
    }
```

`headers` 에는 요청 시 `header`에 들어갈 내용을 작성합니다.

위 코드에서는 대부분이 토큰 관련이기 때문에 `Authorization`에 토큰을 넣어주고 `JSON` 기반 통신이기 때문에 `Content-Type`을 `application/json` 으로 설정해주고 있네요!

```Swift
extension UserTargetType: TargetType {
    var baseURL: URL {
         guard let baseURL = URL(string: "https://api.base.url") else {
            fatalError("Error: Invalid URL")
        }
        
        return baseURL
    }
    
    var path: String {
        switch self {
        case .appleLogin, .kakaoLogin:
            return "/api/v1/auth/signin"
        case .refreshToken:
            return "/api/v1/auth/reissue"
        case .getUserInfo:
            return "/api/v1/users/me"
        }
    }
    
    var method: Moya.Method {
        switch self {
        case .appleLogin, .kakaoLogin, .refreshToken:
            return .post
        case .getUserInfo:
            return .get
        }
    }
    
    var task: Task {
        switch self {
        case let .appleLogin:
            return .requestJSONEncodable(SocialLoginRequestModel(provider: "APPLE"))
        case let .kakaoLogin:
            return .requestJSONEncodable(SocialLoginRequestModel(provider: "KAKAO"))
        case .refreshToken:
            return .requestPlain
        case .getUserInfo:
            return .requestPlain
        }
    }
    
    var headers: [String : String]? {
        switch self {
        case .appleLogin(let identityToken):
            return ["Authorization": identityToken, "Content-Type": "application/json"]
        case .kakaoLogin(let accessToken):
            return ["Authorization": accessToken, "Content-Type": "application/json"]
        case .getUserInfo:
            guard let token = DefaultKeychainService.shared.accessToken else {
                fatalError("No access token available")
            }
            return [
                "Content-Type": "application/json",
                "Authorization": "Bearer \(token)"
            ]
        }
    }
}
```

> **3️⃣ 요청 및 응답 내용을 저장할 모델 생성**

서버에서 제공하는 요청 및 응답 `JSON` 데이터에 맞게 요청 및 응답 내용을 저장할 구조체를 생성합니다.

이 부분은 8주차에서 `Alamofire` 실습을 진행했던 것과 동일하게 진행해주시면 됩니다.

`Codable` 프로토콜을 준수해야 한다는 점도 잊지 마세요!

```Swift
struct SocialLoginRequestModel: Codable {
    let provider: String
}
```

> **4️⃣ 네트워크 요청을 수행할** `**Provider**` **인스턴스 생성**

`Provider`는 네트워크 요청이 수행될 때 사용되는 제네릭 타입의 객체입니다.

`TargetType`의 프로토콜을 준수하는 `enum`을 받는다는 점이 특징인데요! 1, 2번에서 세팅해준 `TargetType`을 넣어주면 됩니다.

오른쪽과 같이 객체를 정의하고 선언해서 사용할 수 있습니다.

```Swift
let provider = MoyaProvider<UserTargetType>()
```

> **5️⃣ 실제 네트워크 요청 및 응답 처리**

4번에서 생성한 `Provider`를 가지고 실제 `request`를 진행합니다.

`Provider`의 `request`의 파라미터로 `TargetType`을 전달하면 된다.

이때 반환되는 `response`는 `Result<Response, MoyaError>`형태를 띄고 있어요!

이제 반환된 `response`의 `data`를 원하는 곳에 바인딩해 사용하면 됩니다.

  

```Swift
provider.request(.appleLogin()) { response in
    switch response {
        case .success(let result):
            do {
                let userResponse = try result.map(SocialLoginResponseModel.self)
                print("Successfully mapped response: \(loginResponse)")
            } catch {
                print("Mapping error: \(error.localizedDescription)")
            }
        case .failure(let error):
            print(error.localizedDescription)
    }
}
```

> [!important] `Moya`를 이용한 네트워크 통신은 위와 같이 수행됩니다. 너무 어렵지는 않으셨을까요?
> 
> 처음 듣는 개념들이 많아 충분히 어려우실 수 있으실 것 같습니다. 최대한 많이 읽어보시면서 이해하신 후 실습에서 실제 통신을 진행해보신다면 원활하게 이해가 가능하실 거예요!

### 2️⃣ Multipart는 무엇일까요?

`Multipart`에 대해 알아보기 전에 `Content-Type` 이라는 개념에 대해 잠깐 짚고 넘어가보도록 할까요?

> `Content-Type` 은 HTTP 통신에서 전송되는 데이터의 타입을 명시하기 위해 Header에 실어 보내는 정보인데요!
> 
> 우리가 API를 요청할 때 `Request`에 실어 보내는 데이터(즉, Body)의 타입을 명시해준다고 생각하시면 됩니다.

우리가 자주 사용하는 JSON 타입으로 서버 통신을 진행할 때는 다음과 같이 Header에 `Content-Type`을 명시합니다.

```JSON
Content-Type: application/json
```

우리가 자주 사용하게 될 `JSON`은 사실 `String`, `Number`, `Object`, `Array`, `Boolean`, `Null` 의 여섯 가지 타입만 처리할 수 있습니다.

그러나 우리가 취급하는 대부분의 데이터가 이 6가지에 모두 포함되기 때문에 `JSON`을 중요하게 다루었던 것입니다!

> 그렇다면 … 만약 이 6가지가 아닌 다른 타입을 다룬다면 어떻게 될까요?
> 
> 만약 `이미지`나 `비디오`를 서버에 보내고 싶다면 어떻게 하면 좋을까요? `JSON` 타입으로는 `PNG`, `JPG`, `MP4` 등의 타입을 표현할 수 없을텐데 말이죠!

맞습니다. 이미지나 비디오를 다룰 경우 `JSON` 타입으로는 통신이 불가능해요!

그렇다면 우리는 이제 JSON이 아닌 다른 `Content-Type`을 찾아 떠나야 합니다.

그리고 예상하셨겠지만 이 `Content-Type`이 바로 우리가 배우게 될 `Multipart` , 정확하게는 `multipart/form-data`입니다.

헤더에는 다음과 같이 작성한답니다!

```JSON
Content-Type: multipart/form-data
```

`Content-Type`의 종류가 `JSON` 뿐만이 아니라는 것을 알 수 있는데요. 실제로도

> `Multipart Related MIME`
> 
> `XML Media`
> 
> `Application`
> 
> `Audio`
> 
> `Multipart`
> 
> `Text`

등등 … 여기에 나온 것들을 제외하고도 여러 종류들이 존재합니다.

위에서 나온 종류들 중 `MIME Type`에 대해 조금 더 알아보도록 할게요.

> `MIME Type`은 인터넷에서 전송되는 다양한 타입의 자료들을 판별하기 위한 형식 정도로 간단히 이해해볼 수 있어요.

이 `MIME` 타입 중 `HTML` 폼에서 파일을 업로드할 때 사용되는 타입이 바로 `multipart/form-data`입니다.

이 `multipart/form-data` 를 이용해 파일을 업로드하는 방식은 다음의 로직을 따릅니다. 함께 볼까요?

> 1️⃣ 클라이언트에서 `HTTP` 요청 본문을 `**multipart/form-data**` 형식으로 인코딩해 서버에 전송
> 
> 2️⃣ 서버에서는 이 요청을 처리해 **각 부분(part)에서 파일 정보를 추출**

이와 같은 과정을 통해 `multipart/form-data` 는 클라이언트가 여러 개의 파일과 데이터를 하나의 `HTTP` 요청에 포함할 수 있도록 처리해주는 것입니다!

그렇다면 `multipart/form-data` 를 이용해 네트워크 통신을 진행하는 방법 또한 알아봐야겠죠?

### 3️⃣ Multipart를 사용해 어떻게 통신할까요?

### 1️⃣ `Content-Type` 을 설정해주세요!

이미지나 비디오, 또는 오디오 통신을 위해 가장 중요한 부분은 `Request Header`의 `Content-Type`을 `multipart/form-data`로 설정해주는 것입니다.

```JSON
Content-Type: multipart/form-data
```

만약 `Moya`로 네트워크 통신을 진행하게 된다면 `TargetType` 프로토콜을 추가해주는 과정에서 `header`를 설정해주시게 될텐데요! 다음과 같이 코드를 작성해볼 수 있겠네요.

```Swift
var headers: [String : String]? {
		return ["Content-Type": "multipart/form"]
}
```

### 2️⃣ `MultipartFormData` 에 데이터를 할당해주세요!

`multipart/form-data`로 통신하기 위해서는 데이터를 `**MultipartFormData**` 타입의 리스트에 담아서 통신해야 하는데요!

`MultipartFormData` 의 4가지 속성은 다음과 같습니다.

> ==`**provider**`==: 데이터 제공 방식을 나타내는 `FormDataProvider` 열거형 값
> 
> - `.data(Foundation.Data)`: 데이터 자체를 제공합니다. 보통 이 형식으로 진행하시게 될거예요!
> - `.file(URL)`: 파일의 URL을 제공합니다.
> - `.stream(InputStream, UInt64)`: 입력 스트림과 데이터 크기를 제공합니다.
> 
> ==`**name**`==**:** `key` 값을 의미합니다. `String` 형식으로 작성합니다.
> 
> ==`**fileName**`==: 서버에 업로드 될 이름을 의미합니다. `String` 형식으로 작성합니다.
> 
> ==`**mimeType**`==: 파일 형식을 의미해요. `String` 형식으로 작성합니다.

조금 헷갈리실 수 있어 실제 `TargetType` 의 `Task` 부분에 이미지 데이터를 할당하는 코드 예시를 함께 보도록 할게요.

```Swift
extension UserTargetType: TargetType {
//...
    public var task: Task {
        switch self {
        case let .updateUserInfo(data):
            let multipartData = MultipartFormData(provider: .data(data), name: "image", fileName: "image.jpeg", mimeType: "image/jpeg")

            return .uploadMultipart([multipartData])
        }
    }
//...
```

위 코드에서는 `UserTargetType`이라는 `enum` 형식의 변수를 `TargetType` 프로토콜을 채택해 확장하고 있네요!

이후 `Task` 연산 프로퍼티 부분에서 요청에 대한 구체적인 작업 내용을 명시해주고 있습니다.

`MultipartFormData` 타입의 변수를 선언하고 `provider`에 우리가 전달하고자 하는 `data`를 전달하고 있네요!

이후 return 시 `.uploadMultipart()` 를 이용해 전달하고 있어요.

🚨 이 때 주의해야 할 점은 `.uploadMultipart()` 이 파라미터로 `MultipartFormData` 의 배열을 요구하기 때문에 꼭 데이터를 배열 형태로 전달해야 한다는 점입니다. 배열 형태로 전달하지 않을 경우 오류가 발생하니 참고해주세요!

나머지는 기존 `Moya`를 이용한 서버 통신 방식과 같습니다. 그대로 해주시면 됩니다!

## 🔥 8주차 개념 점검

---

> [!important] `**Moya**`**는** `**Alamofire**`**의 어떤 단점을 개선한 라이브러리일까요?**

- **여기에 답을 적어주세요!**
    
    유지보수하기 어려운 점
    

> [!important] `**Moya**`**를 사용한 네트워크 통신 방법을 단계별로 작성해주세요!**

- **여기에 답을 적어주세요!**
    
    사용할 API 목록들을 작성한 enum 객체 선언
    
    선언한 객체의 extension을 작성하고 TargetType 프로토콜 채택 및 내용 지정
    
    요청 및 응답 내용을 저장할 모델 생성
    
    네트워크 요청을 수행할 Provider 인스턴스 생성
    
    실제 네트워크 요청 및 응답 처리
    

> [!important] **이미지를 서버에 보내고 싶을 때** `**header**`**에 담아 보낼** `**Content-Type**`**은 무엇으로 명시되어야 할까요?**

- **여기에 답을 적어주세요!**
    
    `multipart/form-data`
    

> [!important] `**MultipartFormData**` **에 데이터를 할당하고** `**return**`**할 때 주의해야 할 점은 무엇일까요?**

- **여기에 답을 적어주세요!**
    
    데이터를 배열 형태로 전달
    

## 📚 8주차 실습

---

> [!important] 8주차의 ==**모든 실습은 한 프로젝트에서 이루어집니다.**==
> 
> **실습 전에 프로젝트 파일을 생성**해주시고, ==**코드를 통한 UI 생성을 위한 프로젝트 세팅을 사전에 진행**==해주세요!
> 
> 이후 과정은 사진을 보시면서 천천히 따라와주시면 됩니다.

### 1️⃣ Moya를 이용해서 유저 정보 받아오기

> [!important] 이번 실습에서는 아래 페이지에 접속하신 후 가장 상단에 보이는 `**Get all users**` 부분을 참고해 모든 유저의 정보를 불러오는 네트워크 통신을 진행해보도록 하겠습니다!
> 
> 약간 복잡할 수 있으니 천천히 따라와주시면 좋을 것 같습니다 🫶
> 
> > [!info] Users  
> > Endpoints for Users  
> > [https://fakeapi.platzi.com/en/rest/users/](https://fakeapi.platzi.com/en/rest/users/)  

### 1️⃣ `Moya` 라이브러리 추가하기

`Package Dependencies`에서 `+` 버튼을 클릭해 라이브러리를 추가해봅시다!

```Plain
https://github.com/Moya/Moya
```

검색창에 위의 링크를 입력하신 후 나타나는 `Moya`를 클릭해주신 후 `Add Package`를 클릭해주세요.

  

![[스크린샷_2024-10-14_오후_1.27.51.png]]

이후 나타나는 모든 `Package Product`를 추가해주시면 됩니다.

`Add Package` 버튼을 한 번 더 눌러주세요!

![[스크린샷_2024-10-14_오후_1.28.13.png]]

다음과 같이 `Moya`가 정상적으로 추가되었다면 성공입니다.

다른 라이브러리들은 이번 실습에서는 사용하지 않으니 없어도 무방합니다!

  

![[스크린샷_2024-10-14_오후_1.28.20.png]]

### 2️⃣ 실습을 진행할 `UserViewController`를 생성해주세요!

`Cocoa Touch Class` 파일을 하나 생성해보겠습니다.

  

![[스크린샷_2024-10-14_오후_1.28.34.png]]

이름은 `UserViewController`로 설정해주신 뒤 파일을 생성해주세요!

  

![[스크린샷_2024-10-14_오후_1.28.57.png]]

이후 생성되는 주석들은 모두 삭제해주시면 됩니다.

이번 실습에서는 UI 관련 요소를 다루지 않기 때문에 `view.backgroundColor` 또한 설정해주지 않으셔도 무방합니다!

  

![[스크린샷_2024-10-14_오후_1.29.15.png]]

이후 `SceneDelegate`에서 `rootViewController`를 `UserViewController`로 변경해주세요.

  

![[스크린샷_2024-10-14_오후_1.29.31.png]]

이후 `UserViewController` 상단에 `import Moya`를 추가해주세요!

나머지 라이브러리들은 추가하지 않으셔도 됩니다.

![[스크린샷_2024-10-14_오후_1.30.20.png]]

### 3️⃣ `UserTargetType`을 작성해주세요!

서버 통신과 관련한 내용들을 `enum` 을 이용해서 작성해보도록 하겠습니다.

`UserTargetType` 에서 작성하게 될텐데요!

클래스 파일을 생성해주시고 이름은 `UserTargetType` 으로 설정해주세요.

파일 폴더링도 해주시면 좋습니다. 저는 `Network` 폴더 내에 `UserTargetType` 파일을 위치시켰어요.

  

![[스크린샷_2024-10-14_오후_1.35.29.png]]

통신할 API가 하나이므로 다음과 같이 코드를 작성합니다.

```Swift
enum UserTargetType {
    case getAllUsers
}
```

각 `case`에는 API의 내용이 담기도록 네이밍하면 좋아요! 보통 `method+내용` 형식으로 작성합니다.

  

![[스크린샷_2024-10-14_오후_1.36.23.png]]

이후 `extension`을 선언해 `TargetType` 프로토콜을 추가해줍니다.

`TargetType` 프로토콜만 추가하게 되면 오류가 발생하게 되는데요.

필수 요소들을 추가하지 않아 그런 것이니 침착하게 `fix` 버튼을 클릭해줍시다!

  

![[스크린샷_2024-10-14_오후_1.36.52.png]]

아래와 같이 필수 연산 프로퍼티들이 추가된 것을 볼 수 있습니다.

이제 내용을 모두 채워보겠습니다.

![[스크린샷_2024-10-14_오후_1.36.55.png]]

```Swift
var baseURL: URL {
        guard let baseURL = URL(string: "https://api.escuelajs.co") else {
            fatalError("Error: Invalid URL")
        }
        
        return baseURL
    }
```

모든 API의 공통 URL을 작성하는 부분이었죠!

`https://api.escuelajs.co` 까지를 공통 URL로 봐주시면 됩니다.

이후 `URL` 객체에 담아 `guard let` 구문으로 선언하고, 만약 URL 주소가 올바르지 않을 경우 `fatalError` 구문이 실행되도록 작성합니다.

URL 주소가 올바를 경우에는 URL 객체를 리턴합니다!

```Swift
var path: String {
        switch self {
        case .getAllUsers:
            return "/api/v1/users"
        }
    }
```

`BaseURL`을 제외한 나머지 `URL` 부분을 작성합니다.

```Swift
var method: Moya.Method {
        switch self {
        case .getAllUsers:
            return .get
        }
    }
```

우리가 이용하는 `API`의 `method`는 `GET`입니다.

`.get` 을 리턴해주시면 됩니다!

```Swift
var task: Moya.Task {
        switch self {
        case .getAllUsers:
            return .requestPlain
        }
    }
```

`.requestPlain` 은 처음 보실텐데요!

요청 시 아무것도 필요하지 않은 경우가 있습니다.

파라미터를 쿼리에 담아 날려 보내거나 정말 요청 시 아무것도 요구하지 않는 경우인데요.

이런 경우에는 `.requestPlain` 을 사용해주시면 됩니다.

이번에도 요청 시 서버에서 요구하는 부분이 없기 때문에 `.requestPlain` 을 사용하도록 할게요.

```Swift
var headers: [String : String]? {
        return ["Content-Type" : "application/json"]
    }
```

`JSON`으로 응답을 받아올 것이기 때문에 `Content-Type` 을 `application/json`으로 설정해주었습니다.

이제 모든 `TargetType` 설정이 완료되었습니다!

![[스크린샷_2024-10-14_오후_1.44.36.png]]

  

### 4️⃣ 응답 데이터 구조체를 생성해주세요!

`Model` 폴더를 만든 후 폴더 내에서 `UserResponseModel` 이라는 이름으로 파일 하나를 생성해주세요.

파일 내에는 명세서를 참고해 응답 `JSON`과 같은 형식으로 구조체를 생성해주시면 됩니다!

이 때 `Codable` 프로토콜을 채택하는 것도 잊지 마세요!

![[스크린샷_2024-10-14_오후_2.00.42.png]]

### 5️⃣ `Provider` 객체를 선언하고 네트워크 요청/응답을 처리해주세요!

`UserViewController`에서 네트워크 요청을 수행할 `Provider` 객체를 선언해보겠습니다.

```Swift
private let provider = MoyaProvider<UserTargetType>()
```

이후 요청을 수행할 `getUserInfo()` 함수를 선언해주세요!

  

![[스크린샷_2024-10-14_오후_1.52.08.png]]

```Swift
provider.request(.getAllUsers) { result in
}
```

위 코드를 `getUserInfo()` 함수 내에 작성합니다.

요청 이후 결과를 처리할 `result` 도 작성해주세요!

  

![[스크린샷_2024-10-14_오후_1.52.28.png]]

이후 `result`의 값에 따라 분기 처리를 진행합니다.

네트워크 요청이 성공할 경우와 실패할 경우로 나누어 작성하시면 됩니다.

![[스크린샷_2024-10-14_오후_1.52.54.png]]

```Swift
case .success(let response):
    do {
	    let userResponse = try response.map([UserResponseModel].self)
      print("Successfully mapped response: \(userResponse)")
    } catch {
      print("Mapping error: \(error.localizedDescription)")
    }
```

통신에 성공했을 경우 `Response` 타입의 객체를 반환받습니다.

이 객체를 위에서는 `response` 로 선언했는데요!

이 객체를 우리가 미리 만들어둔 `UserResponseModel` 의 형식에 맞게 매핑해주는 과정을 거칩니다.

이 때 주의할 점은 응답이 배열 형태로 오기 때문에 `UserResponseModel.self`가 아닌 `[UserResponseModel].self` 형식으로 작성해야 한다는 점입니다.

주의해서 작성해주세요!

```Swift
case .failure(let error):
	print("Network request error: \(error.localizedDescription)")
```

실패 시에는 어떤 에러인지 출력할 구문을 작성합니다.

이후 `getUserInfo()` 를 `viewDidLoad()`에 추가해 테스트 가능한 상태로 만들어주세요!

![[스크린샷_2024-10-14_오후_2.00.36.png]]

이후 앱을 실행해보면 다음과 같이 응답 데이터를 잘 받아오는 것을 확인하실 수 있습니다!

![[스크린샷_2024-10-14_오후_2.01.04.png]]

### 2️⃣ 서버에 이미지 업로드하기

> [!important] 이번 실습에서는 아래 페이지에 접속하신 후 가장 상단에 보이는 `**Upload File**` 부분을 참고해서 `multipart/form-data` 타입의 데이터를 서버로 전송하는 실습을 진행해보도록 할게요.
> 
> 약간 복잡할 수 있으니 천천히 따라와주시면 좋을 것 같습니다 🫶
> 
> > [!info] Files  
> > Endpoints for Categories  
> > [https://fakeapi.platzi.com/en/rest/files/](https://fakeapi.platzi.com/en/rest/files/)  

### 1️⃣ `UserTargetType`에 `case`를 추가해주세요!

1번에서 실습할 때 제작한 `UserTargetType` 을 이용할건데요!

```Swift
enum UserTargetType {
    case getAllUsers
    case postFile(image: Data)
}
```

UserTargetType에 새로운 API인 postFile을 추가해주겠습니다.

오른쪽 사진에는 `image: Data`가 없지만 위 코드처럼 파라미터를 추가해주셔야 합니다!

  

![[스크린샷_2024-10-14_오후_3.02.51.png]]

`case`를 추가하게 되면 오른쪽처럼 `switch` 문마다 오류 문구가 생기게 됩니다.

모두 눌러서 `case`를 추가해주세요!

  

![[스크린샷_2024-10-14_오후_3.03.01.png]]

오른쪽과 같이 추가된 `case`를 모두 작성해보도록 하겠습니다.

`baseURL`의 경우 API가 모두 같은 `baseURL`을 공유하니 따로 수정하지 않으셔도 됩니다!

```Swift
var path: String {
        switch self {
        case .getAllUsers:
            return "/api/v1/users"
        case .postFile:
            return "/api/v1/files/upload"
        }
    }
```

`path`의 경우 추가된 `postFile`의 경로를 작성해주시면 됩니다.

```Swift
var method: Moya.Method {
        switch self {
        case .getAllUsers:
            return .get
        case .postFile:
            return .post
        }
    }
```

`method` 또한 추가된 `API`의 `method` 인 `POST`를 작성해주시면 됩니다.

```Swift
var task: Moya.Task {
        switch self {
        case .getAllUsers:
            return .requestPlain
        case let .postFile(imageData):
            let formData = MultipartFormData(
                provider: .data(imageData),
                name: "file",
                fileName: "jokeBear",
                mimeType: "image/png"
            )
            
            return .uploadMultipart([formData])
        }
    }
```

`task` 부분에서 기존 `JSON` 형식과 약간 차이가 있는데요!

이 경우 파라미터로 데이터를 받아오기 때문에 파라미터가 없던 `getAllUsers` 가 `case .getAllUsers` 처럼 작성한 것과 대비되게 `case let .postFile(imageData)` 처럼 작성합니다.

`let` 키워드 넣는 것 까먹으시면 안됩니다!

이후 `MultipartFormData` 형식으로 전송하기 위해 `MultipartFormData` 객체를 선언해주겠습니다.

API 문서 내에서 이름은 `file` 로 설정해달라고 했기 때문에 `name`은 `file`로 설정해줄게요.

파일 이름은 원하시는 대로 설정해주시면 됩니다.

`mimeType`은 `png` 형식으로 전송할 것이기 때문에 `image/png` 로 설정해주세요.

provider 같은 경우 `imageData` 라는 데이터 형식으로 제공할 것이기 때문에 `.data(imageData)` 처럼 작성해주시면 됩니다.

```Swift
var headers: [String : String]? {
        switch self {
        case .getAllUsers:
            return ["Content-Type" : "application/json"]
        case .postFile:
            return ["Content-Type" : "multipart/form-data"]
        }
    }
```

`headers` 의 경우 아까 배웠던 것처럼 `"Content-Type" : "multipart/form-data"` 로 작성해주세요!

![[스크린샷_2024-10-14_오후_3.26.25.png]]

  

### 3️⃣ 응답 데이터 구조체를 생성해주세요!

API 문서를 참고하셔서 응답 구조체를 생성해주시면 됩니다.

이 부분은 1번 실습과 동일한 부분이므로 따로 설명 없이 넘어갈게요!

  

![[스크린샷_2024-10-14_오후_3.06.14.png]]

### 4️⃣ 이미지를 추가하고 네트워크 통신을 진행해주세요!

`Asset`에서 원하시는 이미지를 하나 추가해주세요!

이미지 이름은 원하시는 대로 설정하셔도 좋지만 이후 통신 시 이용되기 때문에 기억하고 계셔야 합니다.

![[스크린샷_2024-10-14_오후_3.07.35.png]]

이후 `UserViewController`에서 `postFile()`이라는 함수를 생성해주겠습니다.

이미지 데이터를 `PNG` 형식 `Data`로 변환하기 위해 guard let 구문을 사용할게요!

```Swift
guard let image = Image(named: "tempImage")?.pngData() else {
    fatalError("Error: Invalid image!")
}
```

이 때 위에서 설정하신 이미지를 `named:` 옆에 넣어주시면 됩니다.

이후 기존 `provider` 객체를 이용해서 `request`를 진행해볼게요.

```Swift
provider.request(.postFile(image: image)) { result in
    switch result {
        case .success(let response):
            do {
                let fileResponse = try response.map(FileResponseModel.self)
                print("Successfully mapped response: \(fileResponse)")
            } catch {
                print("Mapping error: \(error.localizedDescription)")
            }
        case .failure(let error):
            print("Network request error: \(error.localizedDescription)")
        }
    }
```

기존 `request`와 거의 비슷하지만 `.postFile(image: image)` 처럼 파라미터에 Data를 담아 보내고 있다는 점이 약간 다르죠?

이 부분에 주의하셔서 코드를 작성해주시면 되겠습니다.

이제 `viewDidLoad()`에 `getUserInfo()`를 추가한 후 코드를 실행해볼까요?

![[스크린샷_2024-10-14_오후_3.55.52.png]]

콘솔 창에 응답 결과가 성공적으로 잘 나타나고 있음을 확인할 수 있네요!

이상으로 모든 실습이 마무리되었습니다.

8주차 과제도 화이팅입니다 🫶

![[스크린샷_2024-10-14_오후_4.03.57.png]]

  

## 💻 8주차 과제

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
> [https://embed.figma.com/design/47IuhJxc7LFTwOYWtDgTdi/iOS-%EC%9B%8C%ED%81%AC%EB%B6%81?node-id=13858-565&t=rPrbqvmVgNGoeJmP-1&embed-host=notion&footer=false&theme=system](https://embed.figma.com/design/47IuhJxc7LFTwOYWtDgTdi/iOS-%EC%9B%8C%ED%81%AC%EB%B6%81?node-id=13858-565&t=rPrbqvmVgNGoeJmP-1&embed-host=notion&footer=false&theme=system)

### 1. 검색 화면 및 검색 세부 화면 레이아웃을 구현해주세요!

> [!important] **실습 체크리스트**
> 
> - [ ] **제공된 피그마 링크로 접속해** ==**제공된 검색 화면과 검색 세부 화면의 레이아웃을 구현**==**합니다.**
>     - [ ] 단, 레이아웃은 ==**반드시**== ==`**SnapKit**`====**을 이용**==해 구현합니다.
>     - [ ] 피그마에 명시된 레이아웃에 맞게 ==**크기와 간격을 정확히 반영**==합니다.
>     - [ ] 검색 창은 자유롭게 구현하셔도 괜찮으나 ==**눌렀을 때 세부 화면으로 넘어갈 수 있도록 구현**==해야 합니다!
>     - [ ] 검색 화면의 추천 검색어 부분은 `CollectionView`를 이용해 구현해주세요!
>         - [ ] `UICollectionViewFlowLayout`을 이용해 구현해주세요!

### 2. 메인 화면과 검색 화면 간 화면 전환을 구현해주세요!

> [!important] **실습 체크리스트**
> 
> - [ ] ==**메인 화면의 검색 바를 눌렀을 때 검색 화면으로**== 넘어가도록, ==**검색 화면의 검색 바를 눌렀을 때 검색 세부 화면으로 넘어가도록**== 화면 전환을 구현합니다.
>     - [ ] ==**화면 전환은**== ==`**Modal**`== ==**형식을 사용해 구현**==합니다.
>     - [ ] ==**검색 화면과 검색 세부 화면의**== ==`**취소**`== ==**버튼**==을 눌렀을 때는 ==**메인 화면**==이 나타나야 합니다.
>         - [ ] `Present`가 아닌 다른 방식으로 구현해주세요!
>     - [ ] ==**검색 세부 화면의 화살표 버튼**==을 눌렀을 때는 ==**검색 화면**==이 나타나야 합니다.
>         - [ ] `Present`가 아닌 다른 방식으로 구현해주세요!

### 3. 주어진 API 명세서를 활용해 검색 세부 화면에서 통신 및 데이터 바인딩을 진행해주세요!

> [!important]

> [!important] **실습 체크리스트**
> 
> - [ ] 주어진 API 명세서를 활용해 세부 화면에서 검색어를 입력했을 때 통신이 이루어지도록 합니다.
>     - [ ] `Moya`를 사용해 API 통신을 구현합니다.
>     - [ ] 키보드에서 ==**완료 또는**== ==`**Return**`== ==**버튼을 클릭했을 때 통신**==이 이루어지도록 구현합니다.
>         - [ ] 클릭했을 때 ==**아무것도 입력되지 않은 경우 서버 통신이 이루어지지 않도록**== 구현합니다.
> - [ ] 검색 결과로 받아온 데이터 중 `title`이 검색창 밑에 차례대로 표시되도록 구현합니다.
>     - [ ] 이 때 ==**검색 결과는 모두**== ==`**UITableView**`====**를 이용해 표시**==되도록 구현합니다.

### 4. 과제가 완성 되었다면 깃허브 링크와 시연 영상을 첨부해주세요!

> [!important] **시연 영상 체크리스트**
> 
> - [ ] `AutoLayout`이 잘 적용되어 있음을 확인할 수 있나요?
>     - [ ] `iPhone 15 Pro`, `iPhone 13 mini` 시뮬레이터에서 테스트한 내용이 모두 들어가게 영상을 업로드해주세요.
> 
>   
> ==**체크리스트 항목을 모두 만족하는 영상만 업로드**==해주시길 바랍니다.

> **깃허브 링크 임베드**

[](https://www.notion.soundefined)

> **시연 영상 업로드** ==(영상 개수 제한 X)==

[](https://www.notion.soundefined)

## 🤔 8주차 트러블 슈팅

---

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