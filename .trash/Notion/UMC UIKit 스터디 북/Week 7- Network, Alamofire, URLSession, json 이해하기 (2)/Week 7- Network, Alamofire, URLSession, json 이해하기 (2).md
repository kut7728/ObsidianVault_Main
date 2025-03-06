- [[#📋 학습 목표]]
- [[#✋ 잠깐! 스터디 인증샷 찍으셨나요?]]
- [[#🔥 7주차 개념 설명]]
    - [[#1️⃣ 네트워킹 기초]]
    - [[#2️⃣ URLSession 소개]]
    - [[#3️⃣ JSON 데이터 처리]]
    - [[#4️⃣ Alamofire 기초부터 심화까지]]
    - [[#5️⃣ Alamofire 인증 관리]]
- [[# 🔥 7주차 개념 점검]]
- [[#📚 7주차 실습]]
    - [[#1. SceneDelegate 설정]]
    - [[#2. 분석]]
    - [[#3. 카카오톡 Daum 검색 API 등록하기]]
    - [[#4. 파일 및 폴더 생성]]
    - [[#5. Model 작성하기]]
    - [[#6. View 작성]]
    - [[#7. API 연결하기]]
    - [[#8. ViewController 작성]]
    - [[#9. 실행 결과화면]]
- [[#💻 7주차 과제]]
    - [[#1. 카카오톡 API 애플리케이션 등록]]
    - [[#2. 카카오톡 로그인 버튼에 카카오톡 API 연결하기]]
    - [[#3. 로그인 후, 화면 연결]]
    - [[#4. 과제가 완성되었다면 깃허브 링크와 시연 영상을 첨부해주세요!]]
- [[#🤔 7주차 트러블 슈팅]]
- [[#📌 이번 주차에는 이런 내용을 학습했어요!]]
- [[#❓ 이런 질문이 있어요!]]

  

  

## 📋 학습 목표

---

> **네트워킹 기초**  
>   
> **URLSession 소개**  
>   
> **JSON 데이터 처리**  
>   
> **Alamofire 기초부터 심화까지**  
>   
> **Alamofire 인증 관리**  

  

## ✋ 잠깐! 스터디 인증샷 찍으셨나요?

---

> [!important] 스터디 시작 전 ==**스터디 인증샷을 촬영**==해주세요!
> 
> 스터디는 대면이 원칙이며, 비대면 스터디의 경우에도 최대한 카메라를 킨 후 진행해주세요.
> 
> 아래 임베드 블록에 인증샷을 임베드해 주시면 됩니다 🫶

[](https://www.notion.soundefined)

## 🔥 7주차 개념 설명

---

### 1️⃣ 네트워킹 기초

> 네트워크는 물리적 또는 가상의 연결을 통해 데이터를 교환하는 시스템입니다. 클라이언트(모바일 앱, 웹 브라우저)와 서버 간의 통신, 특히 인터넷을 통한 통신에 관한 설명을 해보도록 할게요

> [!important] 앱이 인터넷을 통해 데이터를 주고 받는 과정을 이해하려면 먼저 ==**HTTP**==와 ==**REST API**== 라는 두 가지 중요한 개념을 알고 있어야 합니다!!

  

## 😃 HTTP

> HTTP는 **클라이언트 - 서버** 모델을 기반으로 하는 통신 규약입니다. 클라이언트는 데이터를 요청하고, 서버는 그 요청에 대한 응답을 제공합니다. HTTP는 웹 애플리케이션뿐만 아니라 모바일 애플리케이션에서 서버와의 통신을 관리하는 핵심 프로토콜입니다.

  

![[18-fT6K1o6nHiBRxKppcqOg.webp]]

  

### ==HTTP 요청(HTTP Requset)==

- **요청 라인**
    - 메서드, 요청 URL, HTTP 버전을 포함합니다.
- **헤더(Header)**
    - 요청에 대한 부가 정보를 포함합니다.
- **본문(Body)**
    
    - 주로 POST 요청에서 사용되며, 클라이언트가 서버에게 보낼 데이터를 담고 있습니다.
    
      
    

![[2.jpg]]

  

### ==HTTP 응답(Response)==

- **상태 코드**
    
    - 서버가 요청을 성공적으로 처리했는지, 또는 문제가 있었는지를 나타내는 3자리 숫자입니다.
    
    > [!important] ==**프로젝트를 진행 하시다가 꼭!! 문제점을 바로 알 수 있도록 상태 코드를 외우고 있기를 바라겠습니다.**==
    
    - **2XX**
        - 서버는 클라이언트의 요청을 확실히 이해했고, 성공적으로 이를 처리했음을 의미합니다.
    - **3XX**
        - 다른 리소스로 리다이렉트를 의미합니다. 클라이언트는 3XX 상태코드가 담긴 응답을 받았을 때 다른 리소스로 이동해야 합니다.
    - **4XX**
        - 클라이언트가 규격에 맞지 않는 데이터를 보냈을 경우 에러입니다==**. 서버 입장에서 볼 때 “니가 잘못했다” 클라이언트 입장에서 볼 떄는 “내가 잘못했나?” 입니다 ㅎㅎ 클라이언트가 잘못했습니다.**==
    - **5XX**
        - 클라이언트는 유효한 요청을 보냈지만 서버 측의 과실로 생긴 에러입니다. ==**서버 입장에서 볼때는 “내가 잘못했다”, 클라이언트 입장에서 볼 때는 “서버 똑바로 안하냐?”입니다. ㅎㅎ..**==

  

- **헤더(Header)**
    - 응답에 대한 부가 정보를 포함합니다.
- **본문(Body)**
    
    - 클라이언트가 요청한 데이터나 메시지가 여기에 담깁니다. JSON 형식의 데이터가 포함될 수 있습니다.
    
      
    

  

![[HTTP_Response.png]]

  

## 😁 REST API (Representational State Transfer)

> REST는 클라이언트와 서버가 상호직용하는 방식을 정의하는 아키텍처 스타일입니다. REST는 주로 `HTTP` 를 사용하여 통신하며, ==**RESTful API**==는 이 개념을 따르는 API 입니다. ==**RESTful API**==는 자원을 사용하여 클라이언트와 서버가 데이터를 주고받을 수 있는 일관된 인터페이스를 제공합니다.

> [!info] RESTful API란 무엇인가요? - RESTful API 설명 - AWS  
> RESTful API의 정의, 기업에서 RESTful API를 사용하는 방법과 이유, AWS에서 API Gateway를 사용하는 방법에 대해 알아보세요.  
> [https://aws.amazon.com/ko/what-is/restful-api/](https://aws.amazon.com/ko/what-is/restful-api/)  

  

![[/image 13.png|image 13.png]]

- **자원(Resource)**
    - API는 자원, 즉 서버에서 관리하는 데이터를 기반으로 합니다. 각 자원은 URI(Uniform Resource Identifier)로 고유하게 식별됩니다.
- **상태 없음(Stateless)**
    - 각 요청은 독립적이며, 서버는 이전 요청에 대한 정보를 기억하지 않습니다. 즉, 클라이언트는 모든 요청에 필요한 정보를 포함해야 합니다.
- **표현(Representation)**
    - 자원은 다양한 형식으로 표현될 수 있습니다.(JSON, XML) 클라이언트는 이 표현을 통해 자원에 접근하고 수정할 수 있습니다.

  

## 🙂 주요 HTTP 메서드

> HTTP 메서드는 서버와 통신할 때 어떤 작업을 할지 정의합니다. RESTful API에서 주로 사용하는 메서드는 **GET, POST, PUT, DELETE**입니다. 우리 워크북은 여기에 추가로 알면 좋은 PATCH까지 하여 설명하도록 하겠습니다.

  

> [!info] REST API 제대로 알고 사용하기 : NHN Cloud Meetup  
> REST API 제대로 알고 사용하기  
> [https://meetup.nhncloud.com/posts/92](https://meetup.nhncloud.com/posts/92)  

---

  

> [!info] JSONPlaceholder - Free Fake REST API  
> JSONPlaceholder is supported by the following companies and  
> [https://jsonplaceholder.typicode.com/](https://jsonplaceholder.typicode.com/)  

### ==**위 사이트는 API 테스트 연습해볼 수 있는 사이트입니다. 위 사이트의 API를 사용하여 아래 메서드를 진행보도록 하겠습니다.**==

  

### GET 메서드

- **목적**
    - 서버로부터 데이터를 조회할 때 사용합니다. 주로 읽기 작업에 사용됩니다.
    - **특징**
        - 요청 본문이 없으며, 필요한 정보는 URL에 쿼리 파라미터로 포함됩니다. 데이터를 서버에 전송하는 방식이 아니므로, 서버의 상태를 변경하지 않습니다.
    - **예시**
        
        - 사용자의 정보를 가져오는 API 요청을 할 때 GET 메서드를 사용할 수 있습니다.
        
        > [!important] ==**터미널에서 아래 명령어를 실행하여 확인할 수 있습니다.**==
        
        > [!important] ==**[Postman](https://www.postman.com)**====**을 설치하여 확인해보셔도 좋습니다!**==
        
        ```Shell
        curl -X GET https://jsonplaceholder.typicode.com/users/1
        ```
        
          
        

![[스크린샷_2024-10-01_오후_2.09.52.png]]

![[스크린샷_2024-10-01_오후_1.53.54.png]]

---

  

### POST 메서드

- **목적**
    - 서버에 새로운 데이터를 전송하거나 자원을 생성할 때 사용합니다. 주로 쓰기 작업에 사용됩니다.
- **특징**
    - POST 메서드는 데이터를 서버에 전송하기 위해 요청 본문에 데이터를 담습니다. 사용자의 로그인, 회원 가입, 파일 업로드 등 다양한 작업에서 주로 사용됩니다.
- **예시**
    
    - 로그인 요청을 보낼 때 POST 메서드를 사용합니다.
    
    > [!important] ==**터미널에서 아래 명령어를 실행하여 확인할 수 있습니다.**<br><br>====오른쪽 터미널 사진의== ==**빨간색 영역은 Response 데이터**== ==입니다.==
    
    > [!important] ==**[Postman](https://www.postman.com)**====**을 설치하여 확인해보셔도 좋습니다!**==
    
    ```Shell
    // 바디에 들어간 데이터의 값을 본인이 원하는 값으로 변경 후 하셔도 됩니다!
    
    
    curl -X POST https://jsonplaceholder.typicode.com/posts \
    -d '{
        "title": "Name",
        "body": "Je_ong",
        "userId": 100
    }'
    ```
    
    > [!important] Body에 유저 아이디를 100으로 해서 넣었습니다. 하지만 옆에 사진에 보이듯이 Response로 id는 101로 받았습니다. 즉, ==**서버에 제가 보낸 데이터는 101번 아이디로 저장되어 있습니다.는 것입니다**==. ==**서버에 존재하는 id 101번을 사용하여 아래 Delete 메서드를 진행하도록 하겠습니다.**==
    

  

![[스크린샷_2024-10-01_오후_2.16.23.png]]

![[스크린샷_2024-10-01_오후_2.13.31.png]]

---

  

### DELETE 메서드

- **목적**
    - 서버에서 특정 자원을 삭제할 때 사용되는 HTTP 메서드입니다. 주로 자원을 삭제하는 작업을 수헹하며, 해당 자원은 URI를 통해 지정됩니다.
- **특징**
    - DELETE 메서드는 동일한 요청을 여러 번 반복해서 보내더라도 같은 결과를 얻습니다. 즉, 동일한 자원에 대해 여러 번 DELETE 요청을 보내더라도 자원이 삭제된 이후의 요청은 효과가 없으며 동일한 응답을 반환해야 합니다.
- **예시**
    
    - 특정 사용자 계정을 삭제하는 API의 경우 사용됩니다.
    
    > [!important] ==**터미널에서 아래 명령어를 실행하여 확인할 수 있습니다.**<br><br>====오른쪽 터미널 사진의== ==**빨간색 영역은 Response 데이터**== ==입니다.==
    
    > [!important] ==**[Postman](https://www.postman.com)**====**을 설치하여 확인해보셔도 좋습니다!**==
    
    ```Shell
    curl -X DELETE https://jsonplaceholder.typicode.com/posts/101
    ```
    
      
    

![[스크린샷_2024-10-01_오후_2.37.40.png]]

![[스크린샷_2024-10-01_오후_2.40.59.png]]

  

---

  

### PUT 메서드

- **목적**
    - 서버에 이미 존재하는 특정 자원의 정보를 갱신하는 데 사용됩니다. 가령, 사용자의 프로필 정보를 수정하는 경우입니다.
    - 해당 자원이 서버에 존재하지 않을 경우, PUT 요청을 통해 자원을 새로 생성할 수 있습니다.
- **특징**
    
    - ==**PUT 메서드는 동일한 요청을 여러번 보내더라도 서버의 상태는 한 번 보낸 결과와 동일**==해야 합니다. 즉, 동일한 데이터를 여러 번 PUT 요청을 보내면 같은 결과가 나와야 합니다.
    - ==**PUT 요청은 보통 자원의 전체 데이터를 대체하는 방식으로 작동합니다. 즉,**== ==**자원의 일부만 수정하는 것이 아니라, 자원 전체를 수정할 때 사용됩니다.**==
    
    > [!important] ==**터미널에서 아래 명령어를 실행하여 확인할 수 있습니다.**==
    
    > [!important] ==**[Postman](https://www.postman.com)**====**을 설치하여 확인해보셔도 좋습니다!**==
    
    ```Shell
    // 101번은 지웠으니, 100번의 값을 수정해보도록 하겠습니다.
    // 아이디 값 100번이 아닌 값을 사용하여도 괜찮습니다.
    
    
    curl -X PUT https://jsonplaceholder.typicode.com/posts/100 \                               ✔  15:50:40 
    -d '{
        "title": "HAHA",
        "body": "Je_ong",
        "userId": 100
    }'
    ```
    

![[스크린샷_2024-10-01_오후_3.51.21.png]]

![[스크린샷_2024-10-01_오후_3.50.13.png]]

  

---

### PATCH 메서드

- **목적**
    - 자원의 전체 내용을 변경하는 PUT 메서드와 달리, ==**PATCH는 자원의 일부 속성만 업데이트할 수 있도록 설계되었습니다.**== RESTful API에서 자주 사용되며, 특히 자원의 일부만 수정해야 할 때 효율적인 방법입니다.
- **특징**
    
    - PATCH는 PUT과 달리 비대응성이 없습니다. 즉, ==**동일한 PATCH 요청을 여러 번 보내면 결과가 달라질 수 있습니다.**== 가령, PATCH 요청을 통해 자원의 특정 부분을 증분 업데이트하면, 동일한 요청이 여러 번 실행되면 자원의 상태가 계속 변할 수 있습니다.
    - 자원의 일부만 수정하는 데 사용되며, 전체 자원을 대체하지 않습니다!!! 따라서 ==**자원의 일부 속성만 변경하고 싶을 때 PUT보다 효율적입니다.**==
    
    ```Shell
    curl -X PATCH https://jsonplaceholder.typicode.com/posts/100 \
    -d '{
        "userId": 100,
        "id": 100,
        "title": "HAHA",
        "body": "Je_Je_Ong"
    }'
    ```
    

![[스크린샷_2024-10-01_오후_7.27.05.png]]

  

## PUT, PATCH, POST 메서드 비교

|   |   |   |
|---|---|---|
||특징|사용 예시|
|PUT|전체 자원 수정/대체|사용자 전체 프로필 수정|
|PATCH|일부 자원 수정|사용자 이메일만 수정|
|POST|새로운 자원 생성|새로운 사용자 계정 생성|

### 2️⃣ URLSession 소개

> `URLSession` 은 Swift에서 HTTP와 HTTPS를 통해 서버와 데이터를 주고받기 위한 API입니다. 이를 통해 네트워크 요청을 만들고 서버로부터 응답을 받아 데이터를 처리할 수 있습니다. 주로 `GET` , `POST` 와 같은 HTTP 메서드를 사용한 요청을 지원하며, 파일 다운로드, 업로드, 백그라운드 작업 등 다양한 네트워킹 작업을 처리할 수 있습니다.

## 😃 URLSession을 사용한 간단한 네트워크 요청

> `URLSession` 의 역할은 클라이언트와 서버 간에 네트워크 연결을 관리하고 데이터를 주고 받는 것입니다. 앱이 서버에서 데이터를 가져오거나, 데이터를 보내고자 할 때, 또는 파을일 다운로드하거나 업로드할 때 `URLSession` 을 사용합니다.

> [!important] 위의 ==**1. 네트워킹 기초**==에서 보여드린 주요 HTTP 메서드를 ==**URSession을 사용하여 처리해보도록 하겠습니다.**==

## GET Method

```Shell
let url = URL(string: "https://jsonplaceholder.typicode.com/posts/1")!
let task = URLSession.shared.dataTask(with: url) { data, response, error in
    if let error = error {
        print("Error: \(error)")
        return
    }

    if let httpResponse = response as? HTTPURLResponse {
        print("Status Code: \(httpResponse.statusCode)")
    }

    if let data = data {
        let responseString = String(data: data, encoding: .utf8)
        print("Response Data: \(responseString!)")
    }
}
task.resume()
```

  

![[스크린샷_2024-10-02_오전_10.03.05.png]]

## POST Method

```Swift
import UIKit

let url = URL(string: "https://jsonplaceholder.typicode.com/posts")!
var request = URLRequest(url: url)
request.httpMethod = "POST"

// 요청 본문에 전송할 데이터
let parameters: [String: Any] = [
    "title": "foo",
    "body": "bar",
    "userId": 1
]
request.httpBody = try? JSONSerialization.data(withJSONObject: parameters)
request.setValue("application/json", forHTTPHeaderField: "Content-Type")

let task = URLSession.shared.dataTask(with: request) { data, response, error in
    if let error = error {
        print("Error: \(error)")
        return
    }

    if let httpResponse = response as? HTTPURLResponse {
        print("Status Code: \(httpResponse.statusCode)")
    }

    if let data = data {
        let responseString = String(data: data, encoding: .utf8)
        print("Response Data: \(responseString!)")
    }
}
task.resume()
```

![[스크린샷_2024-10-02_오전_10.04.19.png]]

  

  

## DELETE Method

```Swift
import UIKit

let url = URL(string: "https://jsonplaceholder.typicode.com/posts/1")!
var request = URLRequest(url: url)
request.httpMethod = "DELETE"

let task = URLSession.shared.dataTask(with: request) { data, response, error in
    if let error = error {
        print("Error: \(error)")
        return
    }

    if let httpResponse = response as? HTTPURLResponse {
        print("Status Code: \(httpResponse.statusCode)")
    }

    if let data = data {
        let responseString = String(data: data, encoding: .utf8)
        print("Response Data: \(responseString!)")
    }
}
task.resume()
```

![[스크린샷_2024-10-02_오전_10.08.23.png]]

  

## PATCH Method

```Swift
import UIKit

let url = URL(string: "https://jsonplaceholder.typicode.com/posts/2")!
var request = URLRequest(url: url)
request.httpMethod = "PATCH"

// 요청 본문에 전송할 데이터
let parameters: [String: Any] = [
    "title": "JEJE",
]
request.httpBody = try? JSONSerialization.data(withJSONObject: parameters)
request.setValue("application/json", forHTTPHeaderField: "Content-Type")

let task = URLSession.shared.dataTask(with: request) { data, response, error in
    if let error = error {
        print("Error: \(error)")
        return
    }

    if let httpResponse = response as? HTTPURLResponse {
        print("Status Code: \(httpResponse.statusCode)")
    }

    if let data = data {
        let responseString = String(data: data, encoding: .utf8)
        print("Response Data: \(responseString!)")
    }
}
task.resume()
```

![[스크린샷_2024-10-02_오전_10.11.33.png]]

  

## PUT Method

```Swift
import UIKit

let url = URL(string: "https://jsonplaceholder.typicode.com/posts/100")!
var request = URLRequest(url: url)
request.httpMethod = "PUT"

// 요청 본문에 전송할 데이터
let parameters: [String: Any] = [
    "title": "JEJEONG",
    "body": "BABABA",
    "userId": 101
]
request.httpBody = try? JSONSerialization.data(withJSONObject: parameters)
request.setValue("application/json", forHTTPHeaderField: "Content-Type")

let task = URLSession.shared.dataTask(with: request) { data, response, error in
    if let error = error {
        print("Error: \(error)")
        return
    }

    if let httpResponse = response as? HTTPURLResponse {
        print("Status Code: \(httpResponse.statusCode)")
    }

    if let data = data {
        let responseString = String(data: data, encoding: .utf8)
        print("Response Data: \(responseString!)")
    }
}
task.resume()
```

![[스크린샷_2024-10-02_오전_10.16.35.png]]

  

## 🥲 비동기 네트워크 호출

> 비동기 네트워크 호출은 요청을 보낸 후 응답을 기다리는 동안 애플리케이션의 다른 작업이 중단되지 않도록 하는 방식입니다. ==**비동기 방식은 앱의 사용자 경험을 크게 향상시키는 중요한 개념으로, 네트워크 작업이 완료될 때까지 응답을 기다리는 것이 아니라, 동시에 다른 작업을 진행할 수 있습니다.**==

> [!important] 우리가 위에서 배운 `URLSession` 은 기본적으로 **비동기**적으로 동작합니다. UI 스레드가 차단되지 않는 것을 의미하며, 특히 네트워크 작업이 오래 걸릴 경우 앱이 멈추지 않고 정상적으로 작동하도록 보장합니다. 작업이 완료 되면 미리 정의된 콜백 함수를 통해 네트워크 작업의 결과를 처리할 수 있습니다.

  

### 비동기 호출 동작 방식은??!

1. **요청을 보냄**
    1. 클라이언트는 서버에 요청을 보내고 네트워크 작업을 시작하니다.
2. **다른 작업을 수행**
    1. 네트워크 응답을 기다리는 동안, 앱은 다른 작업을 계속할 수 있습니다. UI가 멈추지 않기 때문에 사용자는 앱을 계속 사용할 수 있습니다.
3. **응답 처리**
    1. 네트워크 작업이 완료되면, 응답 데이터는 콜백으로 전달되며 클라이언트는 그 데이터를 처리합니다.

  

### 비동기 호출을 더 쉽게 관리하는 방법

> ==**Swift 5.5부터 비동기 네트워크 호출을 더 쉽게 처리하기 위해 async/await이 도입**==되었습니다. 비동기 처리를 동기 코드처럼 작성할 수 있게 해주며, 콜백 헬 문제를 해결합니다.  
> 근데 우리 async/await 어디서 봤던거 같지 않나요?? 5주차 문법 워크북에서 Actor에 대해 공부했었죠?!  
> 즉, ==**Swift 언어로 네트워크 호출 관련 코드를 작성할 때 Actor를 이용해서 관리하면 내부 상태를 보호하면서 동시에 비동기 코드를 처리할 수 있습니다.**== 데이터는 여러 스레드에서 접근 할 수 있지만 안전하게 처리되도록 보장할 수 있습니다.

> [!important] ==**actor에 대해 다시 확인 하시고 싶으면 5주차 문법을 확인하고 오시면 되겠습니다!**==

> [!important] ==**GET Method의 예시 코드를 작성해서 진행했습니다. 추가로 더 연습해보고 싶으면 다른 HTTP Method를 작성해서 해볼 것을 추천드립니다.**==

```Swift
import UIKit
import Foundation

actor NetworkManager {
    var responseData: String?
    
    func fetchData() async {
        let url = URL(string: "https://jsonplaceholder.typicode.com/posts/1")!
        
        do {
            let (data, response) = try await URLSession.shared.data(from: url)
            
            if let httpResponse = response as? HTTPURLResponse {
                print("Status Code: \(httpResponse.statusCode)")
            }
            
            let responseString = String(data: data, encoding: .utf8)
            responseData = responseString
        } catch {
            print("Error: \(error)")
        }
    }
    
    func getResponseData() -> String? {
        return responseData
    }
}
```

```Swift
let networkManager = NetworkManager()

Task {
    await networkManager.fetchData()
    
    if let data = await networkManager.getResponseData() {
        print("Data: \(data)")
    } else {
        print("no data")
    }
}
```

![[스크린샷_2024-10-02_오전_10.48.29.png]]

  

## ❗️❗️ 다음으로~!!❗️❗️

서버와의 통신에서 중요한 것은 데이터를 주고받는 것입니다. 현대 웹/앱 서비스에서는 대부분의 데이터가 **JSON 형식으로 주고받기 때문에,** JSON 데이터를 처리하는 방법을 이해하는 것이 필수적입니다. ==**JSON의 구조**==와 이를 ==**Swift에서 파싱하는 방법**==**,** 그리고 ==**Codable 프로토콜**==을 활용해 JSON을 효율적으로 ==**인코딩하고 디코딩하는 방법**==에 대해 알아보겠습니다.

### 3️⃣ JSON 데이터 처리

> JSON은 경량 데이터 교환 형식으로, 읽고 쓰기가 간편하며 우리가 쉽게 이해할 수 있는 구조를 가지고 있습니다. 대부분의 웹/앱 API나 서버는 JSON 형식으로 데이터를 주고받습니다. Swift에서는 JSON 데이터를 쉽게 다룰 수 있는 여러 기능을 제공하며, 그중 ==**Codable 프로토콜**==을 사용하면 ==**데이터를 간편하게 인코딩 하고 디코딩 할 수 있습니다.**==

  

## 😃 JSON의 구조와 Swift에서 이를 파싱하는 방법

### JSON의 기본 구조

==**JSON은 키-값 쌍과 배열로 데이터를 표현합니다.**==

위의 목차 네트워킹 기초, URLSession 소개 부분을 학습 하시면서 아래 같은 형태의 JSON 데이터를 계속 보면서 여기까지 내려왔을 겁니다.

```Swift
{
    "name": "Jeong",
    "age": 28,
    "email": "UMC@UMC.com"
}
```

  

우리가 실제로 JSON을 파싱해서 활용하려면, ==**데이터를 적절한 Swift 구조체나 클래스로 변환해야 합니다.**== 즉, 이 데이터를 사용해 각종 컴포넌트들에 넣어서 앱에 보이도록 하려면 Swift 구조체나 클래스로 변환부터 해야 합니다.는 말입니다

  

**그럼 어떻게 파싱할까요??**

  

기본적으로 JSON 데이터를 Swift에서 처리하기 위해서는 JSONDecoder를 사용해 데이터를 파싱합니다. 이를 위해 Swift에서 해당 **JSON 데이터와 매핑할 구조체를 정의해야 합니다.**

  

## 😃 Codable 프로토콜을 활용한 JSON 인코딩 및 디코딩

> ==**Codable 프로토콜은 Encodable과 Decodable 프로토콜을 결합한 것**==으로, Swift에서 데이터를 손쉽게 JSON으로 인코딩하거나 디코딩할 수 있게 해줍니다. Codable을 사용하면 별도의 복잡한 파싱 코드를 작성할 필요 없이, Swift의 타입과 JSON을 쉽게 매핑할 수 있습니다.

  

### 구조체 정의 및 디코딩

위의 json 데이터를 파싱해서 출력 시켜보도록 하겠습니다.

**먼저, 위 json 데이터와 매핑할 구조체를 생성합니다.**

```Swift
struct User: Codable {
    let name: String
    let age: Int
    let email: String
}
```

  

서버에서 받은 json 데이터를 문자열로 가정하여 디코딩 하는 과정입니다.

```Swift
import UIKit
import Foundation

struct User: Codable {
    let name: String
    let age: Int
    let email: String
}

let jsonData = """
{
    "name": "Jeong",
    "age": 28,
    "email": "UMC@UMC.com"
}
""".data(using: .utf8)!

/* JSON 데이터를 User 구조체로 디코딩 */
do {
    let decoder = JSONDecoder()
    let user = try decoder.decode(User.self, from: jsonData)
    print("User name: \(user.name), Age: \(user.age), Email: \(user.email)")
} catch {
    print("Error: \(error)")
}
```

![[스크린샷_2024-10-02_오후_1.03.05.png]]

### JSON 인코딩

Swift 데이터를 JSON으로 변환하는 작업도 Codable 프로토콜을 통해 쉽게 할 수 있습니다.

```Swift
import Foundation
import UIKit

// Swift 객체를 JSON 데이터로 인코딩
struct User: Codable {
    let name: String
    let age: Int
    let email: String
}

let newUser = User(name: "JEONG", age: 28, email: "UMC@UMC.con")

do {
    let encoder = JSONEncoder()
    encoder.outputFormatting = .prettyPrinted
    let jsonData = try encoder.encode(newUser)
    
    if let jsonString = String(data: jsonData, encoding: .utf8) {
        print(jsonString)
    }
} catch {
    print("Error: \(error)")
}
```

![[스크린샷_2024-10-02_오후_1.07.10.png]]

### 실제 응답 데이터와 JSON 처리

실제 네트워크 응답에서 JSON 데이터를 처리하는 것은 매우 일반적인 작업입니다. **URLSession**과 **Codable**을 함께 사용하여 서버로부터 받은 JSON 응답 데이터를 디코딩합니다.

아래 사이트를 참고하여 API를 테스트 해보도록 하겠습니다.

> [!info] JSONPlaceholder - Free Fake REST API  
> JSONPlaceholder is supported by the following companies and  
> [https://jsonplaceholder.typicode.com/](https://jsonplaceholder.typicode.com/)  

  

1. **매핑할 구조체를 생성합니다.**

```Swift
import Foundation

struct Geo: Codable {
    let lat: String
    let lng: String
}

struct Address: Codable {
    let street: String
    let suite: String
    let city: String
    let zipcode: String
    let geo: Geo
}

struct Company: Codable {
    let name: String
    let catchPhrase: String
    let bs: String
}

struct User: Codable {
    let id: Int
    let name: String
    let username: String
    let email: String
    let address: Address
    let phone: String
    let website: String
    let company: Company
}
```

  

1. **actor로 정의된 NetworkManage를 생성합니다.**

```Swift
actor NetworkManager {
    private var userData: User?
    
    func fetchUserData() async {
        let url = URL(string: "https://jsonplaceholder.typicode.com/users/1")!
        
        do {
            let (data, response) = try await URLSession.shared.data(from: url)
            
            if let httpResponse = response as? HTTPURLResponse, httpResponse.statusCode == 200 {
                let decoder = JSONDecoder()
                let user = try decoder.decode(User.self, from: data)
                
                userData = user
                print("유저 데이터 저장 성공")
            } else {
                print("유저 데이터 저장 에러")
            }
        } catch {
            print("data Fetch Error: \(error)")
        }
    }
    
    // 저장된 사용자 데이터를 반환하는 메서드
    func getUserData() -> User? {
        return userData
    }
}
```

  

1. **인스턴스 생성 후, 네트워크 요청 실행**

```Swift
let networkManager = NetworkManager()


Task {

    await networkManager.fetchUserData()
   
    if let user = await networkManager.getUserData() {
        print("User Name: \(user.name)")
        print("Address: \(user.address.street), \(user.address.city)")
        print("Geo Location: \(user.address.geo.lat), \(user.address.geo.lng)")
        print("Company Name: \(user.company.name)")
    } else {
        print("no user data")
    }
}
```

  

![[스크린샷_2024-10-02_오후_1.54.39.png]]

  

## ❗️❗️ 다음으로~!!❗️❗️

**Codable**을 활용하여 JSON 데이터를 처리하는 방법을 알아보았습니다. 복잡한 네트워크 요청을 더욱 효율적으로 관리하고, 추가적인 기능을 제공하는 고급 네트워킹 라이브러리가 있습니다. Swift에서 많이 사용되는 ==**네트워킹 라이브러리인 Alamofire를 통해 네트워크 작업을 더 편리하게 처리하는 방법을 알아보겠습니다.**==

### 4️⃣ Alamofire 기초부터 심화까지

https://github.com/Alamofire/Alamofire

> Swift에 존재하는 HTTP 라이브러리로, 이 라이브러리는 다양한 특징의 HTTP method를 지원하고 있습니다. JSON, XML 그리고 네트워크 통신 상태를 모니터링 합니다. 하지만 때때로 ==OSI 7계층에서의 높은 레벨의 추상화가 필요로 합니다. 이에 대해선 다음주차 Moya를 통해 배우시게 될 것입니다.==

  

## 😃 Alamofire의 특징

### ==간편한 HTTP 요청 생성==

Alamofire는 간단한 직관적인 API를 제공하여 Get, Post, Put, Delete 등 HTTP 1.0 이상의 요청을 생성하고 실행할 수 있습니다.

### ==비동기 네트워킹==

Alamofire는 비동기 방식으로 네트워크 요청을 처리하며 클로저를 통해 응답과 오류를 처리할 수 있습니다. 이로 인해 메인 스레드의 블로킹을 피하고 사용자 인터페이스의 응답성을 유지할 수 있습니다.

  

### ==비동기 네트워킹==

URL 인코딩, JSON 인코딩 등 요청 데이터를 쉽게 인코딩할 수 있는 기능을 제공하며, 응답 데이터를 디코딩하는 것도 간편하게 처리할 수 있습니다.

  

### ==파일 업로드 및 다운로드==

대용량 파일 업로드 및 다운로드를 쉽게 구현할 수 있도록 지원합니다. 특히 백그라운드 다운로드와 업로드 기능을 제공하여 앱이 백그라운드로 전환되어도 작업을 지속할 수 있습니다.

  

### ==보안 기능==

Alamofire는 SSL 인증서 검증, HTTP 인증 등을 다양한 보안 기능을 지원하여 안전한 네트워크 통신을 구현할 수 있습니다.

  

![[스크린샷_2024-10-02_오후_6.21.07.png]]

  

## 📋 Alamofire 네트워킹

  

### GET

> 서버로부터 데이터를 가져오기 위해 사용합니다.

> 서버의 데이터를 조회하는데 사용되며, 서버의 상태나 데이터를 변경하지 않습니다.  
> 요청할 때 쿼리 파라미터를 URL에 포함하여 전송할 수 있습니다.  
> 캐시될 수 있으며, 일반적으로 안전하고 반복적으로 요청해도 서버 상태에 영향을 주지 않습니다.  

```Swift
private func apiGet() {
        AF.request("https://jsonplaceholder.typicode.com/todos/1").responseString { response in
            switch response.result {
            case .success(let response):
                self.apTextLabel.text = response
                print(response)
            case .failure(let error):
                self.apTextLabel.text = "Error: \(error)"
            }
        }
    }
```

  

![[스크린샷_2024-08-30_오후_3.04.18.png]]

![[스크린샷_2024-08-30_오후_3.04.43.png]]

  

### POST

> 서버에 데이터를 전송하여 새로운 리소스를 생성하거나 서버의 상태를 변경하기 위해 사용합니다.

> 요청 본문에 데이터를 포함하여 서버로 전송합니다.  
> 새로운 리소스를 생성하거나 서버의 상태에 변화를 일으킵니다.  

```Swift
 let param: [String: Any] = [
        "title": "fooText",
        "body": "barText",
        "userId": 122
    ]

 private func apiPost() {
        AF.request("https://jsonplaceholder.typicode.com/posts", method: .post, parameters: param, encoding: JSONEncoding.default).responseString { response in
            switch response.result {
            case .success(let response):
                self.apTextLabel.text = response
                print(response)
            case .failure(let error):
                self.apTextLabel.text = "Error: \(error)"
            }
        }
    }
```

  

![[스크린샷_2024-08-30_오후_3.11.48.png]]

![[스크린샷_2024-08-30_오후_3.12.44.png]]

### ==PATCH==

> 서버의 기존 리소스의 일부를 수정하기 위해 사용합니다.

> 요청 본문에 수정할 데이터만 포함하여 서버로 전송합니다.  
> ==**리소스 전체가 아닌, 일부 속성만 변경하고 싶을 때 사용합니다.(리소스 일부 변경)**==

```Swift
let param: [String: Any] = [
        "email": "newemail@example.com"
    ]
    
  private func apiPatch() {
        AF.request("https://jsonplaceholder.typicode.com/users/1", method: .patch, parameters: param, encoding: JSONEncoding.default).responseString { response in
            switch response.result {
            case .success(let response):
                self.apTextLabel.text = response
                print(response)
            case .failure(let error):
                self.apTextLabel.text = "Error: \(error)"
            }
        }
    }
```

  

![[스크린샷_2024-08-30_오후_3.23.53.png]]

![[스크린샷_2024-08-30_오후_3.23.35.png]]

### PUT

> 서버에 새로운 리소스를 생성하거나 기존 리소스를 대체하기 위해 사용합니다.

> 요청 본문에 리소스의 전체 표현을 포함하여 서버에 전송합니다.  
> 요청한 리소스가 존재하지 않으면 새로운 리소스를 생성합니다.  
> ==**요청한 리소스가 존재하면 해당 리소스를 요청 본문으로 완전히 대체합니다.**==

```Swift

  let param: [String: Any] = [
        "id": 1,
        "name": "John Doe",
        "username": "johndoe",
        "email": "johndoe@example.com"
    ]

private func apiPut() {
        AF.request("https://jsonplaceholder.typicode.com/users/1", method: .put, parameters: param, encoding: JSONEncoding.default).responseString { response in
            switch response.result {
            case .success(let response):
                self.apTextLabel.text = response
                print(response)
            case .failure(let error):
                self.apTextLabel.text = "Error: \(error)"
            }
        }
    }
```

  

![[스크린샷_2024-08-30_오후_3.19.33.png]]

![[스크린샷_2024-08-30_오후_3.20.02.png]]

  

## ❗️ 추가적인 HTTP 메소드

### DELETE

> 서버에 특정 리소스를 삭제할 때 사용합니다.

  

```Swift
AF.request("https://jsonplaceholder.typicode.com/posts/1", method: .delete)
    .response { response in
        if response.error == nil {
            print("리소스 삭제 성공")
        } else {
            print("리소스 삭제 실패: \(response.error?.localizedDescription ?? "Unknown error")")
        }
    }
```

  

  

  

### OPTIONS

> 서버에 지원하는 HTTP 메서드의 목록을 확인할 때 사용합니다. 주로 서버의 기능을 탐색하는 데 유용합니다.

```Swift
AF.request("https://jsonplaceholder.typicode.com/posts/1", method: .options)
    .response { response in
        if let headers = response.response?.allHeaderFields {
            print("지원되는 메서드: \(headers)")
        }
    }
```

  

  

### HEAD

> GET 요청과 유사하지만 응답 본문을 포함하지 않습니다. 주로 리소의 메타 데이터를 가져올 때 사용됩니다.

  

```Swift
AF.request("https://jsonplaceholder.typicode.com/posts/1", method: .head)
    .response { response in
        if let headers = response.response?.allHeaderFields {
            print("헤더 정보: \(headers)")
        }
    }
```

  

## ✍️ Request/Response

기본적인 틀 사용방법으로 아래 코드와 같습니다.

  

```Swift
let url = "https://example.com"

AF.request(url,
		   method: .get,
    	   parameters: nil,
    	   encoding: URLEncoding.default,
    	   headers: ["Content-Type":"application/json", "Accept":"application/json"])
	.validate(statusCode: 200..<300)
    .response { response in
    	
	/** 서버로부터 받은 데이터 활용 */
    switch response.result {
    case .success(let data):
		/** 정상적으로 reponse를 받은 경우 */
	case .failure(let error):
    	/** 그렇지 않은 경우 */
	}
}
```

  

`url` : 첫 번째 파라미터로 요청을 보낼 URL을 담습니다.

`method` : 어떤 request mthod를 사용할지 선택합니다. 기본값으로 .get으로 되어있어서 딱히 지정하지 않으면 get으로 요청을 보내게 됩니다.

`parameters` : POST 메소드와 같이 Request Body를 사용할 때 전달할 값을 담습니다. 위 예제 코드에서 봤듯이 파라미터 변수를 만들고 값을 넣어서 Request를 보낸것을 알 수 있습니다.

`Encoding` : 인코딩 방식을 정합니다.

**URLEncoding**

> 요청 파라미터를 URL의 쿼리 문자열로 인코딩하는 방식입니다. 일반적으로 Get 요청에서 사용되며,  
> 파라미터가 URL의 일부로 추가됩니다.  
> GET, DELETE와 같은 요청 메소드에서는 URL의 끝에 쿼리 파라미터로 추가됩니다.  
> POST, PUT과 같은 요청 메소드에서는 파라미터가 URL의 본문이 아닌 쿼리 파라미터로 추가될 수 있습니다.  

```Swift
AF.request("https://example.com",
           method: .get,
           parameters: ["key1": "value1", "key2": "value2"],
           encoding: URLEncoding.default)
```

**JSONEncoding**

> 요청 파라미터를 JSON 형식으로 인코딩하여 HTTP 요청의 본문에 포함시키는 방식입니다.  
> POST, PUT, PATCH 요청에서 주로 사용됩니다.  

```Swift
AF.request("https://example.com",
           method: .post,
           parameters: ["key1": "value1", "key2": "value2"],
           encoding: JSONEncoding.default)
```

  

`headers` : 부가적인 정보를 나타냅니다. 송/수신 데이터 타입을 나타냅니다. Contents-Type과 Accept를 헤더에 지정할 수 있습니다.

`validate`: 유효성 검사를 진행합니다. 요청 결과에 따라 처리되도록 할 수 있습니다.

**상태 코드 검증**

기본적으로 200번대 경우를 성공으로 간주합니다. 직접 지정하여 범위로 유효하도록 지정할 수 있습니다.

```Swift
AF.request("https://example.com/resource")
  .validate(statusCode: 200..<400)  // 200~399까지의 상태 코드를 성공으로 간주
  .response { response in
      // 처리 로직
  }
```

**콘텐츠 타입 검증**

서버에서 반환된 응답의 콘텐츠 타입이 요청 시 예상한 타입과 일치하는지 검증할 수 있습니다. 클라이언트가 JSON 데이터를 기대한다면 서버의 응답이 application/json 타입인지 확인합니다.

```Swift
AF.request("https://example.com/resource")
  .validate(contentType: ["application/json"])  // 응답의 콘텐츠 타입이 JSON인지 검증
  .response { response in
      // 처리 로직
  }
```

  

`response` : 응답의 성공, 실패에 따라 처리되도록 로직을 지정한다.

  

##  🙃 싱글톤 패턴으로 작성하는 Alamofire

> 싱글톤 패턴을 클래스의 인스턴스를 하나만 생성하고, 이를 전역에서 공유할 수 있도록 설계하는 디자인 패턴입니다. 애플리케이션에서 네트워킹, 데이터베이스 접근, 설정 관리와 같이 하나의 인스턴스로만 관리해야 하는 경우에 주로 사용됩니다.

## 싱글톤 패턴의 장점

- **중앙화된 인스턴스 관리**
    - 네트워킹 작업을 하나의 인스턴스에서 관리하여 코드의 일관성을 유지할 수 있습니다.
- **리소스 절약**
    - 동일한 인스턴스를 재사용하기 때문에 메모리 사용을 최소화하고, 불필요한 인스턴스 생성으로 인한 오버헤드를 줄입니다.
- **데이터 일광성 유지**
    - 전역적으로 동일한 인스턴스를 공유하기 때문에, 네트워크 요청에 대한 설정이나 상태를 일관되게관리할 수 있습니다.

## Alamofire에서의 싱글톤 패턴 사용

> Alamofire에서는 `Session` 을 사용하여 네트워크 요청을 처리합니다. 이 `Session` 인스턴스를 싱글톤으로 관리하면, 앱 전체에서 공통된 네트워킹 설정을 사용할 수 있습니다.

```Swift
class NetworkManager {
    static let shared = NetworkManager()
    
    private init() {}
    
    private let session: Session = {
        let configuration = URLSessionConfiguration.default
        configuration.timeoutIntervalForRequest = 30
        return Session(configuration: configuration)
    }()
    
    public func fetchPosts(completion: @escaping (Result<[Post], AFError>) -> Void) {
        let url = "https://example"
        
        session.request(url)
            .validate()
            .responseDecodable(of: [Post].self) { response in
                switch response.result {
                case .success(let posts):
                    completion(.success(posts))
                case .failure(let error):
                    completion(.failure(error))
                }
            }
    }
}
```

  

### 싱글톤 패턴의 활용

> 싱글톤 패턴을 사용하면 네트워킹 코드의 중복을 줄이고, 모든 네트워크 요청에 대해 동일한 설정과 인증 로직을 적용할 수 있습니다. 또한, 네트워크 연결 상태를 추적하거나, 공통된 오류 처리 로직을 추가할 때도 유용합니다.

> [!important]
> 
> 1. **인터셉터 활용**
>     1. 인증 토큰이 필요한 API의 경우, `RequestInterceptor` 를 사용하여 모든 요청에 자동으로 인증 헤더를 추가할 수 있습니다. 이를 통해 각 네트워크 요청에서 인증 로직을 반복적으로 작성할 필요가 없습니다.
> 2. **공통 설정 관리**
>     1. `Session` 의 설정을 중앙에서 관리하여, 타임아웃 시간, 캐시 정책, 리다이렉션 정책 등을 일관되게 적용 할 수 있습니다. 필요 시 설정을 변경하면, 앱, 전체에 바로 적용됩니다.
> 3. **상태 관리**
>     1. 네트워크 연결 상태를 추적하거나, 백그라운드에서 네트워크 작업을 수행할 때도 싱글톤 네트워크 매니저를 사용하면 중앙에서 모든 상태를 관리할 수 있습니다.

  

> Alamofire는 강력한 네트워킹 라이브러리로, 다양한 네트워크 작업을 효율적으로 처리리할 수 있는 여러 기능을 제공합니다. 싱글톤 패턴을 사용하여 기본적인 네트워크 요청을 관리하는 방법을 익혔다면, 이제 `Alamofire`가 제공하는 고급 기능들을 살펴보도록 하겠습니다.

  

## 😉 Alamofire의 주요 기능

## 1. Response Validation (응답 검증)

> 응답 검증은 서버에 반환된 HTTP 응답의 상태 코드나 콘텐츠 타입을 확인하여 요청이 성공했는지 판단하는 기능입니다. 기본적으로 `validation()` 메서드는 ==**200번대의 상태 코드나 JSON과 같은 컨텐츠 타입을 검증**==합니다. 이를 통해 클라이언트는 서버의 응답을 사전에 필터링하여 오류를 빠르게 감지하고 처리할 수 있습니다.

```Swift
AF.request("https://example.com")
	.validate(statusCode: 200..<300)
	.validate(contentType: ["application/json"])
	.responseJSON { response in
			switch response.self {
			case .success(let data):
					print("성공: \(data)")
			case .failure(let error):
					print("오류: \(error)")
			}
	}
```

  

## 2. Decoded Response Handling (응답 디코딩 처리)

> `Alamofire` 는 서버에서 받은 JSON 데이터를 Swift의 `Codable` 모델로 쉽게 디코딩할 수 있는 기능을 제공합니다. responseDecodable(of:) 메서드를 사용하면, JSON 데이터를 Swift 객체로 자동으로 변환하여 사용할 수 있습니다.

```Swift
struct User: Codable {
	let id: Int
	let name: String
	let email: String
	}
```

```Swift
AF.requset("https://example.com")
		.responseDecodable(of: User.self) { response in
			switch response.self {
			case .success(let data):
					print("성공: \(data)")
			case .failure(let error):
					print("오류: \(error)")
			}
	}
```

  

## 3. Multipart Form (멀티파트 폼)

> 파일 업로드를 포함한 복잡한 요청을 보낼 때 멀티파트 폼을 사용할 수 있습니다. `multipartFormData` 를 통해 텍스트 데이터와 파일을 함께 서버로 전송할 수 있습니다.

```Swift
AF.upload(multipartFormData: { multipartFormData in
			multipartFormData.append("Jeong".data(using: .utf8)!. withName: "name")
			multipartFormData.append(fileURL, whithName: "profileImage", fileName: "profile", mimType: "image/jpeg")
		}, to: "https://exapmle.com")
		.response { response in
				if response.error == nil {
						print("파일 업로드 성공")
						} else {
								print("파일 업로드 실패: \(response.error!)")
					}
		}
```

  

## 4. Response Retriers (응답 재시도)

> 네트워크 오류나 인증 오류와 같은 특정 상황에서 요청을 자동으로 재시도할 수 있습니다. `RequestRetrier` 프로토콜을 구현하여 재시도 로직을 정의할 수 있습니다.

```Swift
class RequstRetrier: RequestRetrier {
		func retry(_ request: Request, for session: Session, dueTo error: Error, completion: @escaping (RetryResult) -> Void) {
			if let response = request.task?.response as? HTTPURLResponse, response.statuscode == 401 {
					completion(.retry)
				} else {
					completion(.doNotRetry)
			}
		}
	}
```

  

## 5. Request Caching (요청 캐싱)

> Alamofire는 `URLCache` 를 통해 ==**HTTP 응답을 캐싱하여 네트워크 요청의 속도를 높이고**==, 서버 부하를 줄일 수 있습니다. `URLRequest.CachePolicy` 를 설정하여 캐싱 동작을 제어할 수 있습니다.

```Swift
let urlRequest = URLRequest(url: URL(string: "https://www.examples.com")!. cachePlicy: .returnCacheDataElseload)
AF.request(urlRequst)
	.response { response in
			print("캐시된 응답: \(response)
```

## 6. Session dispatchQueue

> Alamofire의 `Session` 은 네트워크 요청의 응답을 비동기로 처리할 때 사용할 디스패치 큐를 설정할 수 있습니다. 이를 통해 메인 스레드나 백그라운드 스레드에서 응답을 처리하도록 제어할 수 있습니다.

```Swift
let session = Session()
session.request("httpts://www.example.com")
```

  

## 8. RedirectHandler (리다이렉트 핸들링)

> HTTP 리다이렉트 요청을 처리하거나 방지할 수 있는 기능입니다. 리다이렉트가 발생했을 때 특정 조건에 따라 이를 허용하거나 거부할 수 있습니다.

  

**RedirectHandler**는 `task(_:willBeRedirectedTo:for:completion:)` 메서드를 통해 리다이렉트 요청을 제어합니다.

- **리다이렉트 허용**
    - 제공된 새로운 `URLRequest` 를 그대로 사용할 수 있습니다.
- **리다이렉트 수정**
    - 제공된 `URLRequest`를 수정하여 새로운 요청을 만들 수 있습니다.
- **리다이렉트 방지**
    - `nil`을 반환하여 리다이렉트 요청을 거부하고, 리다이렉트 응답 본문을 사용할 수 있습니다.

  

하지만 Alamofire는 ==**Reidrector**==**라는 구조체**를 제공하여 리다이렉트 제어를 더 쉽게 할 수 있도록 합니다. 이 타입은 `RedirectHandler` 프로토콜을 준수하도록 작성되었습니다.

```Swift
public enum Behavior {
    case follow
    case doNotFollow
    case modify((URLSessionTask, URLRequest, HTTPURLResponse) -> URLRequest?)
}
```

- **follow**
    - Redirect 요청을 전부 허용합니다.
- **doNotFollow**
    - Redirect 요청을 전부 거절합니다.
- **modify(using:)**
    - Redirect 요청을 사용자가 수정합니다.

  

```Swift
let director = Redirector(behavior: .doNotFollow)
let session = Session(RedirectHandler: redirector)

session.request("http://example.com")
	.response { response in
			print("리다이렉트되지 않습니다.")
		}
```

  

## 9. SSL 인증

> Alamofire에서 SSL 인증은 안전한 네트워크 통신을 위해 매우 중요합니다. SSL/TLS는 클라이언트와 서버 간의 데이터 전송을 암호화하여 제 3자가 데이터를 가로채거나 변조하지 못하도록 보호합니다. Alamofire는 기본적으로 iOS `URLSession` 과 `Security` 프레임워크를 사용하여 SSL 인증을 처리하며, 다양한 설정을 통해 SSL 인증서의 신뢰성 평가를 커스터마이즈할 수 있습니다.

  

> [!important] Alamofie는 `ServerTrustManager` 를 통해 서버의 SSL 인증서를 검증하는 로직을 세밀하게 제어할 수 있습니다. `ServerTrustManager` 는 서버의 인증서가 올바르게 서명되었는지, 특정 도메인에 대한 커스텀 검증 로직을 추가하는 데 사용됩니다.

- **ServerTrustManager**
    - 인증서 검증을 위한 평가자들을 구성하고 관리하는 클래스입니다.
    - 특정 도메인에 대해 다양한 검증 전략을 적용할 수 있도록 설정합니다.
- **ServerTrusetEvaluating 프로토콜**
    - 서버의 SSL 인증서를 평가하기 위해 사용합니다. Alamofire는 기본적으로 `DefaultTrustEvaluator`, `PinnedCertificatesTrustEvaluator`, 
    - `PublicKeysTrustEvaluator`와 같은 여러 기본 평가자를 제공합니다.

- `PinnedCertificatesTrustEvaluator`
    - 서버가 제시하는 인증서가 클라이언트 애플리케이션에 하드코딩된 인증서와 일치하는지 확인합니다. 이를 통해 MITM 공격을 방지할 수 있습니다.
- `PublicKeysTrustEvaluator`
    - 서버 인증서의 공개 키(Public Key)를 검증합니다. 인증서가 변경되더라도 동일한 공개 키를 사용할 경우 유효한 것으로 간주합니다.
- `DefaultTrustEvaluator`
    - 기본적인 시스템 인증서 신뢰 검증을 수행합니다.

```Swift
import Alamofire

let evaluator = PinnedCertificatesTrustEvaluator()
let severTrustManager = ServerTrustManager(evaluators: ["example.com": evaluator])
```

### 5️⃣ Alamofire 인증 관리

> ==**인증이 필요한 요청을 수행할 때는 인증 토큰을 서버에 전달하고, 해당 토큰이 만료되었을 때 자동으로 갱신하는 등의 작업이 필수적**==입니다. 그러나 이런 작업을 모든 네트워크 요청마다 수동으로 처리하는 것은 비효율적이며, 코드의 복잡성을 증가시킬 수 있습니다.

> Alamofire는 `AuthenticationInterceptor` 라는 강력한 도구를 제공합니다. 이 ==**인터셉터는 인증과 관련된 복잡한 로직을 단순화하여, 클라이언트 측에서 인증 토큰을 자동으로 관리하고, 만료 시 새로운 토큰을 갱신하는 과정을 자동화**==합니다. `AuthenticationInterceptor`, `Authenticator`와 `AuthenticationCredential` 을 구현하여 인증 로직을 구조화하고, 모든 네트워크 요청에 일관된 인증 처리를 적용할 수 있습니다.

## 😃 AuthenticationInterceptor란?

`AuthenticationInterceptor`는 Alamofire에서 인증 정보 관리하고, ==**필요한 경우 자동으로 인증 토큰을 갱신하는 기능을 제공**==합니다. 인증 로직이 필요한 요청마다 수동으로 처리하는 대신, 이 도구를 통해 인증 처리 과정을 일관되고 쉽게 유지할 수 있습니다.

  

> [!important]
> 
> - **인증 정보 추가**
>     - 서버에 요청을 보낼 때 필요한 인증 정보를 자동으로 추가
> - **토큰 만료 처리**
>     - 인증 토큰이 만료되었을 때, 새로운 토큰을 자동으로 요청
> - **재시도 로직**
>     - 만료된 토큰으로 인해 요청이 실패한 경우, 새로운 토큰을 사용하여 요청을 재시도

##  🙃 인증이 필요한 네트워크 요청 처리

> [!important] Alamofire의 인증 관리 기능은 프로젝트 초기뿐만 아니라 앱이 성장할 수록 ==**안전하고 효율적인 네트워크 통신을 구축하는 데 필수적인 도구**==입니다. 인증 토큰을 수동으로 관리하는 것은 코드를 복잡하게 만들 뿐만 아니라 보안상 취약점을 초래합니다.<br>여러분이 추후에 프로젝트를 진행하시면, 프로젝트가 복잡해지거나 외부 API 통합이 많아질 경우, 인증 로직을 체계적으로 관리하는 게 중요합니다. Alamofire의 <br>`AuthenticationInterceptor`와 같은 도구를 통해 이러한 인증 로직을 초기에 잘 설계해 두는 것이 매우 중요합니다.<br>==**이 기능을 반드시 참고하여 앱을 개발할 때 사용했으면 좋겠습니다!**==

  

![[스크린샷_2024-10-05_오후_5.14.15.png]]

  

  

## 1. 인증 토큰 처리

> 사용자가 로그인 하면 앱은 서버로부터 `accessToken` 을 받아 저장합니다. 이 토큰은 사용자의 모든 활동을 인증하는 데 사용되며, 일정 시간이 지나면 만료됩니다. 만료된 토큰으로 서버에 요청을 보낼 경우 `401 Unauthorized` 오류가 발생하고, 새로운 토큰을 발급받아야 합니다.

  

```Swift

import Alamofire

struct Credential: AuthenticationCredential { 
	let accessToken: String
	let expiration: Data
	
	// 토큰이 만료되기 전에 판단하여 x분 전에 갱신해야 됩니다.
	// 아래 코드는 5분으로 두어, 5분전에 갱신 되도록 했습니다.
	var requiresRefresh: Bool {
		return Date(timeIntervalSinceNow: 60 * 5) > expiration
}
```

## 2. Authenticator 인증 로직 처리

> `Authenticator` 프로콜을 구현하여 요청에 인증 정보를 추가하고, 토큰 만료 시 새로운 토큰을 발급받는 기능을 처리할 수 있습니다. 서버에서 401 오류를 반환했을 때 토큰을 갱신하고 다시 요청을 시도하는 로직도 자동으로 처리됩니다.

> [!important] 기본적으로 인증 토큰을 추가(apply), 토큰이 만료되었을 때 새로운 토큰을 발급(refresh)하고, 인증 오류가 발생하면 이를 감지하고 다시 요청을 시도합니다.

  

  

```Swift
class Authenticator: Authenticator {
	    
       // 요청에 토큰 추가
    func apply(_ credential: Credential, to urlRequest: inout URLRequest) {
        urlRequest.headers.add(.authorization(bearerToken: credential.accessToken))
    }

    // 토큰 갱신 로직
    func refresh(_ credential: Credential, for session: Session, completion: @escaping (Result<Credential, Error>) -> Void) {
        // 서버로부터 새로운 토큰 요청하는 부분 구현
        let newCredential = Credential(accessToken: "new_access_token", expiration: Date().addingTimeInterval(3600))
        completion(.success(newCredential))  // 새로운 토큰으로 업데이트
    }

    // 인증 실패(401 Unauthorized) 여부 확인
    func didRequest(_ urlRequest: URLRequest, with response: HTTPURLResponse, failDueToAuthenticationError error: Error) -> Bool {
        return response.statusCode == 401
    }

    // 요청이 인증되었는지 확인
    func isRequest(_ urlRequest: URLRequest, authenticatedWith credential: Credential) -> Bool {
        let bearerToken = HTTPHeader.authorization(bearerToken: credential.accessToken).value
        return urlRequest.headers["Authorization"] == bearerToken
    }
}
```

## 3. AuthenticationInterceptor와 Session을 통한 자동 처리

> Alamofire의 `AuthenticationInterceptor` 를 활용하면 위에서 구현한 `Authenticator` 와 `Credential` 을 사용하여 ==**네트워크 요청에서 인증과 갱신 로직을 자동으로 처리**==할 수 있습니다.

  

```Swift
let credential = Credential(accessToken: "initial_access_token", expiration: Date().addingTimeInterval(3600)) // 초기 토큰
let authenticator = Authenticator()
let authInterceptor = AuthenticationInterceptor(authenticator: authenticator, credential: credential)

let session = Session(interceptor: authInterceptor)

// 인증이 필요한 네트워크 요청
session.request("https://example.com/protected-endpoint")
    .validate()
    .responseJSON { response in
        switch response.result {
        case .success(let data):
            print("응답 데이터: \(data)")
        case .failure(let error):
            print("요청 실패: \(error)")
        }
    }
```

## 4. 작동 방식 설명

> [!important]
> 
> ### 1. 초기 인증 정보 설정(Credential)
> 
> 사용자가 처음 로그인하면 서버에서 인증 토큰(accessToken)을 발급받고, 이 토큰과 함께 토큰이 만료되는 시간(expiration)을 저장합니다. 이 정보는 `Credential` 구조체에서 관리되며, 이 구조체는 `AuthenticationCredential` 을 준수합니다.
> 
> ### 2. 네트워크 요청에 인증 정보 추가(apply 메서드)
> 
> 네트워크 요청이 만들어질 때마다, `Authenticator` 가 요청의 헤더에 `Authorization` 토큰을 자동으로 추가합니다. 이 때, `accessToken` 을 `Bearer` 토큰 형태로 전송합니다. 즉, ==**서버로 보내는 모든 요청에는 이 토큰이 포함되어 사용자의 신원을 인증합니다.**==
> 
> ### 3. 응답처리 및 인증 실패 감지(didRequest 메서드)
> 
> 서버는 요청을 받고 인증된 사용자만 접근할 수 있는 자원에 대해 응답을 반환합니다.
> 
> 만약 인증 ==**토큰이 만료된 경우**==, 서버는 `401 Unauthorized` 상태 코드를 반환합니다. 이 상태 코드는 `Authenticator`의 `didRequest` 메서드에서 감지되며, 이를 통해 토큰이 만료되었음을 인식합니다.
> 
> ### 4. 자동 토큰 갱신(refresh 메서드)
> 
> `Authenticator`는 토큰이 만료되었을 때 서버에 **새로운 토큰을 요청**합니다. 이 요청은 `refresh` 메서드를 통해 처리되며, 갱신된 토큰과 만료 시간은 다시 `Credential`에 저장됩니다. 이 과정은 비동기로 이루어지며, 서버가 새 토큰을 반환하면 기존의 만료된 토큰이 ==**자동으로 갱신**==됩니다.
> 
> ### 5. 요청 재시도
> 
> 새로운 토큰이 발급된 후, 실패했던 ==**요청이 자동으로 재시도**==됩니다.
> 
> ### 6. AuthenticationInterceptor와의 통합
> 
> `AuthenticationInterceptor` 는 세션 레벨에서 이 모든 과정을 관리합니다. 즉, 모든 네트워크 요청에서 자동으로 인증 토큰이 추가되며, 토큰이 만료되면 자동으로 갱신하고 재시도하는 과정을 자동화합

## 🔥 7주차 개념 점검

---

> [!important] URLSession을 사용하여 네트워킹을 처리할 때, URLSession이 어떤 역할을 하며, 이를 통해 네트워크 요청을 보낼 수 있는 기본적인 과정에 대해 설명하세요!

- **여기에 답을 적어주세요!**
    
    `URLSession` 의 역할은 클라이언트와 서버 간에 네트워크 연결을 관리하고 데이터를 주고 받는 것입니다. 앱이 서버에서 데이터를 가져오거나, 데이터를 보내고자 할 때, 또는 파일을 다운로드하거나 업로드할 때 `URLSession` 을 사용합니다.
    
    get - 서버로부터 정보 가져오기, post - 서버에 정보 전달, delete - 서버속 정보 삭제, patch - 서버속 정보 일부 수정
    

> [!important] JSON 데이터를 처리할 때, Swift에서 어떤 방법을 사용하여 데이터를 디코딩하고, 이 과정에서 필요한 프로토콜과 주요 메서드를 설명해주세요!

- **여기에 답을 적어주세요!**
    
    ==Codable 프로토콜은 Encodable과 Decodable 프로토콜을 결합한 것==으로, Swift에서 데이터를 손쉽게 JSON으로 인코딩하거나 디코딩할 수 있게 해줍니다. Codable을 사용하면 별도의 복잡한 파싱 코드를 작성할 필요 없이, Swift의 타입과 JSON을 쉽게 매핑할 수 있습니다. decode 메서드로 디코딩
    

> [!important] Alamofire는 URLSession을 기반으로 네트워킹을 간편하게 처리할 수 있게 해줍니다. Alamofire의 주요 기능 중 `responseJSON` 메서드를 사용하여 서버 응답을 처리하는 방법을 코드와 함께 설명하세요!

- **여기에 답을 적어주세요!**
    
    ```Swift
    AF.request("https://example.com/resource")
      .validate(contentType: ["application/json"])  // 응답의 콘텐츠 타입이 JSON인지 검증
      .response { response in
          // 처리 로직
      }
    ```
    

> [!important] Alamofire에서 `AuthenticationInterceptor` 를 활용한 인증 관리의 기본 흐름을 설명하고, 토큰 갱신이 자동으로 처리되는 과정에서 필요한 두 가지 주요 프로토콜에 대해 설명하세요!

- **여기에 답을 적어주세요!**
    
    1. 초기 인증 정보 설정(Credential)
    
    2. 네트워크 요청에 인증 정보 추가(apply 메서드)
    
    3. 응답처리 및 인증 실패 감지(didRequest 메서드)
    
    4. 자동 토큰 갱신(refresh 메서드)
    
    5. 요청 재시도
    
    6. AuthenticationInterceptor와의 통합
    
    - authenticator과 credential 프로토콜 → ==네트워크 요청에서 인증과 갱신 로직을 자동으로 처리==

## 📚 7주차 실습

---

> 실습 내용은 카카오톡 Daum 검색 API를 사용하여 앱 자체에서 검색해서 볼 수 있도록 하겠습니다.

> 아래 피그마 링크에 들어 오셔서 디자인을 확인해주시기 바랍니다.  
> ==**Option 키를 누르고, 프레임 위에 마우스를 올려 확인 하시면서 오토레이아웃 수치를 꼭!! 확인해주시기 바랍니다.**  
>   
> ====또한== ==`SnapKit`====을 적용하여 진행하도록 하겠습니다.==

[https://embed.figma.com/design/47IuhJxc7LFTwOYWtDgTdi/iOS-%EC%9B%8C%ED%81%AC%EB%B6%81?node-id=322-1594&t=TNYnLYCxfoZYM0Nn-1&embed-host=notion&footer=false&theme=system](https://embed.figma.com/design/47IuhJxc7LFTwOYWtDgTdi/iOS-%EC%9B%8C%ED%81%AC%EB%B6%81?node-id=322-1594&t=TNYnLYCxfoZYM0Nn-1&embed-host=notion&footer=false&theme=system)

### 1. SceneDelegate 설정

==**이 부분은 생략하도록 하겠습니다. 설정 방법을 모르시면 1주차 워크북을 다시 참고해주시기 바랍니다!**==

### 2. 분석

텍스트 필드를 사용해서 값을 넣고 검색 하기 버튼을 클릭하면, 연결된 Daum 검색 API를 통해 값을 받아와서 아래 타이틀과 컨텐츠에 띄우도록 하겠습니다.

- 상단에 값을 넣을 텍스트 필드 필요!
- 값을 API Request Param으로 전달할 검색하기 버튼 필요
- API를 통해 Response로 받아온 title과 contents 내용을 보일 UILabel 필요

### 3. 카카오톡 Daum 검색 API 등록하기

> [!info] Kakao Developers  
> 카카오 API를 활용하여 다양한 어플리케이션을 개발해보세요.  
> [https://developers.kakao.com/docs/latest/ko/daum-search/dev-guide](https://developers.kakao.com/docs/latest/ko/daum-search/dev-guide)  

이 사이트에 설명된 API를 사용하기 위해 먼저 애플리케이션을 등록해보도록 하겠습니다.

1. **상단에 애플리케이션 등록하기 버튼을 눌러주세요!**

그럼 옆에 사진처럼 애플리케이션을 등록할 수 있습니다.

애플리케이션에 대한 정보를 넣어주세요!

저는 옆에 처럼 하도록 하겠습니다.

  

  

![[스크린샷_2024-10-13_오후_5.08.00.png]]

![[스크린샷_2024-10-13_오후_5.07.37.png]]

1. **RestAPI 키 확인하기**

위 사이트의 문서를 읽어보면 헤더에 키 값을 넣도록 되어있습니다.

애플리케이션을 추가했기 때문에 개인의 REST API KEY를 갖고 있습니다.

이를 확인하고 헤더에 넣어서 테스트를 진행해보도록 하겠습니다.

등록한 애플리케이션에 들어가시면, 이렇게 Key가 나올 것입니다.

옆의 사진 Key를 사용하고 싶어도 안될꺼에요.. ㅎㅎ

이 워크북 다 만들고 애플리케이션을 삭제했기 때문에 존재하지 않는 Key입니다.

헤더에서 원하는 것은 RestAPIKey이기 때문에 옆에 앱 키 4개중에 두 번째 키를 복사해보도록 하겠습니다.

![[스크린샷_2024-10-13_오후_5.10.27.png]]

![[스크린샷_2024-10-13_오후_5.11.32.png]]

  

1. **Postman 테스트 해보기**

Postman을 실행하고 헤더 값에 위 사진처럼 넣어주세요

그리고, 문서에 보이듯이 쿼리 파라미터를 작성할 건데 필수에 해당하는 것과 페이지 값을 넣어서 해보도록 하겠습니다. 스스로 다른것도 같이 넣어서 실습을 진행해봐도 좋습니다!

그럼 오른쪽 세 번째 사진처럼 등장하게 됩니다.!!!

JSON의 형태가 어떻게 이루어져있는지 확인 되었으니, 이제 코드로 만들어보도록 하겠습니다.

![[스크린샷_2024-10-14_오후_6.06.23.png]]

![[스크린샷_2024-10-13_오후_5.13.23.png]]

![[스크린샷_2024-10-14_오후_6.08.19.png]]

  

### 4. 파일 및 폴더 생성

`ViewControllers` 폴더 내부에 ViewController.swift 파일을 생성해주세요

`Models` 폴더 내부에 Response 폴더를 생성 후, SearchModel.swift 파일을 생성합니다.

`Views` 폴더 내부에 APITestView.swift 파일을 생성합니다.

`Service` 폴더 내부에 APIClient.swift, AuthorizationInterceptor.swift 폴더를 생성합니다.

  

![[스크린샷_2024-10-14_오후_6.10.32.png]]

  

### 5. Model 작성하기

Get을 통해 받아오기 때문에 Response 데이터를 저장할 모델이 필요합니다.

Postman에서 받아온 JSON 형태를 받을 수 있도록 구현해줍니다.

  

변수명은 다르게 해서 사용해도 됩니다! 단!!!, 다르게 했으면 CodingKey를 정의하여 JSON에 있는 변수명과 일치할 수 있도록 합니다.

```Swift
struct SearchModel: Codable {
    let documents: [DetailDocument]
}

struct DetailDocument: Codable {
    let contents: String
    let datetime: String
    let title: String
    let url: String
}
```

```Swift
struct SearchModel: Codable {
    let documents: [DetailDocument]
}

struct DetailDocument: Codable {
    let contestText: String
    let date: String
    let titleText: String
    let urlText: String
    
    enum CodingKeys: String, CodingKey {
        case contestText = "contents"
        case date = "datetime"
        case titleText = "title"
        case urlText = "url"
    }
}
```

### 6. View 작성

중복되는 것은 함수로 구현하여 재사용할 수 있도록 합니다.

또한, 스택뷰를 사용하여 그룹으로 묶어 정리합니다.

이전에 해왔던 과제 참고 답안 코드를 작성하여 깃허브에 올려 볼 수 있도록 주소를 각 파트장님들에게 전달했었습니다.

제가 정리해두었던 깃 허브를 참고하여 코드를 보시면 쉽게 이해할 수 있을겁니다.

> [!info] GitHub - JEONG-J/UMC_KREAM_Reference: UMC 7기 KREAM 과제 참고 코드 구현  
> UMC 7기 KREAM 과제 참고 코드 구현.  
> [https://github.com/JEONG-J/UMC_KREAM_Reference](https://github.com/JEONG-J/UMC_KREAM_Reference)  

  

```Swift
//
//  APITestView.swift
//  7st
//
//  Created by 정의찬 on 10/13/24.
//

import UIKit
import SnapKit

class APITestView: UIView {
    
    override init(frame: CGRect) {
        super.init(frame: frame)
        self.backgroundColor = .white
        addStack()
        addComponents()
        constraints()
    }
    
    required init?(coder: NSCoder) {
        fatalError("init(coder:) has not been implemented")
    }
    
    private lazy var placeholderContainer: [NSAttributedString.Key: Any] = {
        var value = [NSAttributedString.Key: Any]()
        value[.foregroundColor] = UIColor.gray
        value[.font] = UIFont.systemFont(ofSize: 12)
        return value
    }()
    
    public lazy var searchTextField: UITextField = {
        let textfield = UITextField()
        textfield.attributedPlaceholder = NSAttributedString(string: "검색하고 싶은 것을 넣으세요!", attributes: placeholderContainer)
        textfield.leftViewMode = .always
        textfield.leftView = UIView(frame: CGRect(x: 0, y: 0, width: 14, height: 1))
        textfield.textColor = UIColor.black
        
        textfield.clipsToBounds = true
        textfield.layer.cornerRadius = 10
        textfield.layer.borderWidth = 2
        textfield.layer.borderColor = UIColor.black.cgColor
        return textfield
    }()
    
    public lazy var searchButton: UIButton = {
        let btn = UIButton()
        btn.setTitle("검색", for: .normal)
        btn.titleLabel?.font = UIFont.systemFont(ofSize: 12, weight: .regular)
        btn.backgroundColor = UIColor.lightGray
        btn.clipsToBounds = true
        btn.layer.cornerRadius = 8
        return btn
    }()
    
    private lazy var title: UILabel = makeTitleLabel("타이틀", font: UIFont.systemFont(ofSize: 20, weight: .bold))
    private lazy var contentsTitle: UILabel = makeTitleLabel("컨텐츠", font: UIFont.systemFont(ofSize: 20, weight: .bold))
    
    public lazy var responseTitle: UILabel = makeTitleLabel("이 부분에 title 값이 들어오도록 해주세요!", font: UIFont.systemFont(ofSize: 20, weight: .light))
    public lazy var responseContentsTitle: UILabel = makeTitleLabel("이 부분에 Contents 값이 들어오도록 해주세요!", font: UIFont.systemFont(ofSize: 20, weight: .light))
    
    /// 상단 텍스트 필드와 버튼 묶음 스택
    private lazy var inputTextStack: UIStackView = makeStack(axis: .horizontal, spacing: 21)
    
    /// Response title 스택
    private lazy var titleLabelStack: UIStackView = makeStack(axis: .vertical, spacing: 14)
    
    /// Response contents 스택
    private lazy var contentsLabelStack: UIStackView = makeStack(axis: .vertical, spacing: 14)
    
    private func makeTitleLabel(_ text: String, font: UIFont) -> UILabel {
        let label = UILabel()
        label.textAlignment = .center
        label.textColor = UIColor.black
        label.numberOfLines = 0
        return label
    }
    
    private func makeStack(axis: NSLayoutConstraint.Axis, spacing: CGFloat) -> UIStackView {
        let stack = UIStackView()
        stack.axis = axis
        stack.spacing = spacing
        stack.distribution = .fill
        return stack
    }
    
    private func addStack() {
        [searchTextField, searchButton].forEach{ inputTextStack.addArrangedSubview($0) }
        [title, responseTitle].forEach{ titleLabelStack.addArrangedSubview($0) }
        [contentsTitle, responseContentsTitle].forEach{ contentsLabelStack.addArrangedSubview($0) }
    }
    
    private func addComponents() {
        [inputTextStack, titleLabelStack, contentsLabelStack].forEach{ self.addSubview($0) }
    }
    
    private func constraints() {
        inputTextStack.snp.makeConstraints {
            $0.top.equalToSuperview().offset(94)
            $0.left.equalToSuperview().offset(26)
            $0.right.equalToSuperview().offset(-26)
            $0.height.equalTo(43)
        }
        
        searchTextField.snp.makeConstraints {
            $0.width.equalTo(262)
        }

        
        titleLabelStack.snp.makeConstraints {
            $0.top.equalTo(inputTextStack.snp.bottom).offset(91)
            $0.left.equalToSuperview().offset(18.5)
            $0.right.equalToSuperview().offset(-18.5)
            $0.height.lessThanOrEqualTo(110)
        }
        
        contentsLabelStack.snp.makeConstraints {
            $0.top.equalTo(titleLabelStack.snp.bottom).offset(91)
            $0.left.equalToSuperview().offset(18.5)
            $0.right.equalToSuperview().offset(-18.5)
            $0.height.greaterThanOrEqualTo(10)
        }
    }
}
```

  

### 7. API 연결하기

Alamofire를 통해 Daum 검색 API를 연결해보도록 하겠습니다!

> [!important] Alamofire를 패키지 추가합니다. snapKit 추가하듯이 하면 됩니다.!!
> 
> Alamofire 주소는 위 개념에 있습니다.

  

먼저!!, Intercepto부터 구현해보도록 하겠습니다!!

Interceptor에 대한 설명은 위 개념을 읽으면서 이해했다는 가정에 생략하겠습니다!

헤더에 Authorization을 자동으로 넣어서 Request 전달할 수 있도록 하기 위함입니다.

위에서 생성한 AuthorizationInterceptor.swift 파일에 코드를 작성해주세요

```Swift
//
//  AuthorizationInterceptor.swift
//  7st
//
//  Created by 정의찬 on 10/13/24.
//

import Foundation
import Alamofire

class AuthorizationInterceptor: RequestInterceptor {
    private let kakaoKey: String
    
    init(kakaoKey: String) {
        self.kakaoKey = kakaoKey
    }
    
    func adapt(_ urlRequest: URLRequest, for session: Session, completion: @escaping (Result<URLRequest, any Error>) -> Void) {
        var request = urlRequest
        request.setValue("KakaoAK \(kakaoKey)", forHTTPHeaderField: "Authorization")
        completion(.success(request))
    }
    
    func retry(_ request: Request, for session: Session, dueTo error: any Error, completion: @escaping (RetryResult) -> Void) {
        completion(.doNotRetry)
    }
    
}
```

  

그럼 이제 AuthorizationInterceptor를 사용하는 API 호출 함수를 구현해보도록 하겠습니다.

위에 생성한 APIClient.swift 파일에 작성하도록 하겠습니다!

==**다시 말씀드리지만, 제 API Key는 이제 존재하지 않기 때문에 사용이 안될겁니다 ^^..**==

**아래 코드 작성 방식은 제네릭하게 하여 Codable 프로토콜을 사용하는 Model을 전달 받을 수 있도록 했습니다. 또한 completion을 사용하여 성공, 실패 여부를 전달할 수 있도록 구현했습니다.**

> [!important] 아래 예제 코드는 Key값을 직접적으로 넣어서 사용했습니다. 그렇기 때문에 깃허브에 함부로 올리시면 안됩니다!!!!! 혹은 올리더라도 private로 안전하게 보호받는 레포짓인 경우 올리도록 해주세요!<br>원래는 Key값을 저렇게 대놓고 넣어서 쓰고, 깃허브에 올리지 않습니다. 민감한 데이터이기 때문입니다. 그럼 어떻게 하느냐?!!<br>
> 
> 아래 사이트처럼 하시면 됩니다! 본인이 깃허브에 올리실 경우라면 꼭 처리 후 올리도록 해주세요!!
> 
> 어떤 프로젝트를 하던 꼭!! 지켜주세요!!
> 
> > [!info] gitignore xcconfig ( api key가 git에 추가되지 않도록 하기)  
> > api key를 git에 노출시키지 않도록 하는 방법입니다.  
> > [https://ggasoon2.tistory.com/18](https://ggasoon2.tistory.com/18)  

```Swift
import Foundation
import Alamofire

final class APIClient {
    static let shared = APIClient()
    
    private let session: Session
    
    private init() {
        let interceptor = AuthorizationInterceptor(kakaoKey: "02f5417489f85ad3b023b1acfa9a83b1") // 본인의 API key를 넣어주세요!
        session = Session(interceptor: interceptor)
    }
    
    public func request<T: Codable>(
        _ url: String,
        method: HTTPMethod,
        parameters: Parameters? = nil,
        completion: @escaping (Result<T, Error>) -> Void) {
            session.request(url, method: method, parameters: parameters)
                .validate()
                .responseDecodable(of: T.self) { response in
                    switch response.result {
                    case .success(let value):
                        completion(.success(value))
                    case .failure(let error):
                        completion(.failure(error))
                    }
                }
   
```

### 8. ViewController 작성

View에서 작성한 텍스트필드의 값을 검색 버튼을 누르면 API 쿼리로 전달하여 값을 받은 후, 뷰가 다시 렌더링 될 수 있도록 해줍니다.

searchText() 함수를 통해 텍스트필드의 값을 검색함수로 넘겨줍니다.

search(query: String) 함수를 통해 전달 받은 텍스트르 쿼리로 사용하여 위에서 구현한 API 함수를 호출할 수 있도록 합니다.

만약 completion을 통해 성공을 전달받으면 뷰가 업데이트 될수 있도록 updateView(_ model: SearchModel) 함수를 실행합니다.

실패한다면, 왜 실패했는지 로고가 찍힐 수 있도록 합니다. 어렵죠…?

계속 코드 보면서 이해하시길 바랍니다.. 일부러 주석을 달지 않았습니다. 본인 스스로가 주석을 달면서 공부해보시기 바랍니다.

```Swift
import UIKit

class ViewController: UIViewController {

    override func viewDidLoad() {
        super.viewDidLoad()
        self.view = testView
    
    }
    
    private lazy var testView: APITestView = {
        let view = APITestView()
        view.searchButton.addTarget(self, action: \#selector(searchText), for: .touchUpInside)
        return view
    }()
    
    @objc private func searchText() {
        let query = testView.searchTextField.text ?? ""
        search(query: query)
    }
    
    private func search(query: String) {
        let url = "https://dapi.kakao.com/v2/search/web"
        let parameters: [String: Any] = ["query": query]
        
        APIClient.shared.request(url, method: .get, parameters: parameters) { (result: Result<SearchModel, Error>) in
            switch result {
            case .success(let response):
                self.updateView(response)
            case .failure(let error):
                print("네트워킹 오류: \(error)")
            }
            
        }
    }
    
    private func updateView(_ model: SearchModel) {
        testView.responseTitle.text = model.documents.first?.title
        testView.responseContentsTitle.text = model.documents.first?.contents
    }
}
```

### 9. 실행 결과화면

![[스크린샷_2024-10-14_오후_6.40.28.png]]

![[스크린샷_2024-10-14_오후_6.51.04.png]]

  

## 💻 7주차 과제

---

> [!important] **화면 구현에 필요한 레이아웃과 리소스는 아래 피그마를 참고해주세요!**
> 
>   
>   
> 
> **1주차 로그인 화면에 카카오 소셜 로그인 기능 넣기!!**  
>   
> 
> [https://embed.figma.com/design/47IuhJxc7LFTwOYWtDgTdi/iOS-%EC%9B%8C%ED%81%AC%EB%B6%81?node-id=13949-448&t=TNYnLYCxfoZYM0Nn-1&embed-host=notion&footer=false&theme=system](https://embed.figma.com/design/47IuhJxc7LFTwOYWtDgTdi/iOS-%EC%9B%8C%ED%81%AC%EB%B6%81?node-id=13949-448&t=TNYnLYCxfoZYM0Nn-1&embed-host=notion&footer=false&theme=system)

### 1. 카카오톡 API 애플리케이션 등록

> [!important] **실습 체크리스트**
> 
> - [x] 카카오톡 API 사이트에서 KREAM 애플리케이션 등록하기
>     - [x] [https://developers.kakao.com/docs/latest/ko/kakaologin/common](https://developers.kakao.com/docs/latest/ko/kakaologin/common) 접속해서 등록해주세요!
>     - [x] 문서 읽어보면서 이해하기 [https://developers.kakao.com/docs/latest/ko/kakaologin/ios](https://developers.kakao.com/docs/latest/ko/kakaologin/ios)
>         - [x] 이해하기, 활용하기, 설정하기, iOS 탭 읽어보면서 이해하기
> - [x] 닉네임 동의항목 허용으로 해주기
>     
>     ![[스크린샷_2024-10-14_오후_5.50.05.png]]
>     

### 2. 카카오톡 로그인 버튼에 카카오톡 API 연결하기

> [!important] **실습 체크리스트**
> 
> - [ ] 실습에서 연습했던 것처럼 파일 및 폴더를 생성하여 API 코드 작성하기
>     - [ ] Alamofire로 작성해주세요!
>     - [ ] 카카오톡 로그인 버튼을 누르면 카카오톡 로그인을 시도할 수 있도록 해주세요!
> - [x] 3주차 엑스트라 워크북에서 사용했던 Keychain 사용하기
>     - [x] 로그인 성공 시, 키체인에 토큰 값 + 닉네임 정보 담을 수 있도록 한다.

### 3. 로그인 후, 화면 연결

> [!important] **실습 체크리스트**
> 
> - [x] 카카오톡 로그인 성공 후, 탭바 컨트롤러로 연결되어 전환되도록 한다.
> - [x] 카카오톡 로그인 성공 후, 키체인에 등록된 닉네임 정보 값 사용하기
>     - [x] 마이페이지에서 유저 이름을 담는 Label에 카카오톡 닉네임 값으로 뜨도록 수정할 것!

### 4. 과제가 완성되었다면 깃허브 링크와 시연 영상을 첨부해주세요!

> [!important] **시연 영상 체크리스트**
> 
> - [x] `AutoLayout`이 잘 적용되어 있음을 확인할 수 있나요?
>     - [x] `iPhone 15 Pro`, `iPhone 13 mini` 시뮬레이터에서 테스트한 내용이 모두 들어가게 영상을 업로드해주세요.
> 
>   
> ==**체크리스트 항목을 모두 만족하는 영상만 업로드**==해주시길 바랍니다.

> **깃허브 링크 임베드**

> [!info] GitHub - TUK-UMC/7th_UMC_iOS at 쿠트_김의택  
> 7th UMC iOS.  
> [https://github.com/TUK-UMC/7th_UMC_iOS/tree/%EC%BF%A0%ED%8A%B8_%EA%B9%80%EC%9D%98%ED%83%9D](https://github.com/TUK-UMC/7th_UMC_iOS/tree/%EC%BF%A0%ED%8A%B8_%EA%B9%80%EC%9D%98%ED%83%9D)  

> **시연 영상 업로드** ==(영상 개수 제한 X)==

![[13.mp4]]

![[16.mp4]]

  

## 🤔 7주차 트러블 슈팅

---

## 📌 이번 주차에는 이런 내용을 학습했어요!

---

==워크북을 진행하며 스스로 공부해본 내용을 이곳에 자유 양식으로 정리해 보세요!  
주차마다 하나씩은 작성해주셔야 합니다.  
==

## ❓ 이런 질문이 있어요!

---

워크북을 진행하면서 궁금했던 점 또는 해결하지 못한 부분을 미리 작성하고 스터디에서 함께 논의해 보세요!  
해결하지 못한 질문이나 궁금한 점이 있습니다.면 언제든지 편하게 DM 주세요 🙋‍♀️  

  

---

Copyright © 2024 Lee Youjin All rights reserved.

Copyright © 2024 Jeong Euichan All rights reserved.