
<br>

# 개요

클린 아키텍처란 다음 사진처럼 앱 아키텍쳐를 구성한 것
![[Pasted image 20250305195550.png]]
- 최외곽의 원은 구체적인 상세 정보를 담음, 안쪽으로 갈수록 추상화되고, 고수준의 정책을 캡슐화 한다.
- 소스코드는 안쪽을 향해서만 의존할 수 있다.^[[[Solid Programming]]]
- 내부의 원은 외부의 원에 대해 전혀 알지 못한다.
	- 특히 외부의 원에서 선언된 어떠한 이름을 내부의 원에서 참조해서는 안된다
- ==외부의 원의 어떠한 것도 내부의 원에 영향을 줘서는 안된다.==

# 원들에 대한 설명

![[1__HxTmyiDQNCfACBZle67rw.webp]]
## 1️⃣ Entities

- 비즈니스 모델
- 메서드를 갖는 객체 / 데이터 구조 / 함수의 집합

## 2️⃣ Use Cases

- 시스템의 모든 유스케이스를 캡슐화하고 구현한다
- 엔티티로부터의 혹은 엔티티에서의 데이터 흐름을 조합한다.


## 3️⃣ Controllers, Gateway, Presenters (Interface Adapter)

- 유스케이스, 엔티티에서 사용하던 타입에서 외부의 기능에 용이한 타입으로 데이터를 변환
- Coordinator, ViewModel, ViewController 등이 해당됨

## 4️⃣ Devices, Web, UI, DB, External Interfaces

-  데이터베이스나, 웹 프레임워크 등 프레임워크나 도구들로 구성됨
- Network, CoreData 등이 해당됨


# 레이어에 대한 설명
![[Pasted image 20250305195550.png]]
### 1️⃣ Presentation Layer

UI + Presenters
- UI (ViewControllers / Views) 와 Presenters (ViewModel) 이 해당됨
- ViewModel은 하나이상의 UseCases를 실행하기 때문에 Presentation Layer는 Domain Layer에 의존 함


### 2️⃣ Domain Layer

Entities + Use Cases
- 다른 레이어들에게 어떠한 영향도 받지 않음


### 3️⃣ Data Repository Layer

DB + API
- Repository 프로토콜의 구현체 (Repository Implementations)와 Data Sources들이 해당됨
- Repository는 다른 Data Sources (DB, API)로부터의  데이터를 처리하는 책임이 있음
- Data Layer에는 API응답으로 받은 JSON 데이터를 Domain Layer에 있는 모델로 변환하는 작업이 들어있음


# 데이터 플로우
1. View(UI) 에서 ViewModel(Presenter)의 메소드를 호출
2. ViewModel은 UseCase를 실행
3. UseCase는 Repository로부터 데이터를 조합
4. Repository는 Network 또는 DB에서 데이터를 처리해서 가져옴
5. 데이터는 다시 View(UI)로 넘어가 화면을 구성함

# 계층을 나누는 장점
### 소스코드 전반을 쉽게 장악 할 수 있다
- 모듈, 패키지, 폴더의 구성이 자연스럽계 계층별로 트리구조를 이루기 때문에
- 다른 개발자, 혹은 내가 다시 들여볼때 이해가 빠르다.
- 특히 특정 계층에 대한 수정이 다른 계층에 거의 영향을 주지 않기 때문에
- 수정이 빠르고 간편해진다.



# 참고
##### 정리글
[\[Clean Architecture\] iOS Clean Architecture + MVVM 개념과 예제](https://eunjin3786.tistory.com/207?category=837198)
[Clean Architecture는 모바일 개발을 어떻게 도와주는가? - (1) 경계선: 계층 나누기](https://medium.com/@justfaceit/clean-architecture%EB%8A%94-%EB%AA%A8%EB%B0%94%EC%9D%BC-%EA%B0%9C%EB%B0%9C%EC%9D%84-%EC%96%B4%EB%96%BB%EA%B2%8C-%EB%8F%84%EC%99%80%EC%A3%BC%EB%8A%94%EA%B0%80-1-%EA%B2%BD%EA%B3%84%EC%84%A0-%EA%B3%84%EC%B8%B5%EC%9D%84-%EC%A0%95%EC%9D%98%ED%95%B4%EC%A4%80%EB%8B%A4-b77496744616)

##### 레포지터리
[GitHub - DroidKaigi/conference-app-2018: The Official Conference App for DroidKaigi 2018 Tokyo](https://github.com/DroidKaigi/conference-app-2018) → 간소화 클린 아키텍처