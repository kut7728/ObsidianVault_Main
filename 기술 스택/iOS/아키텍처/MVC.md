# 개요
Model - View - Controller

![[CleanShot 2025-03-06 at 14.36.32@2x.png]]

# 단점
## 1. 너무 비대해지는 ViewController

- 날짜 데이터 포맷터와 같은 애매한 코드들을 VC에 넣다보니 VC가 너무 비대해지는 문제점
- MVC는 사실 Massive View Controller 라고 풍자하기도 함

## 2. ViewController와  View가 너무 친한 애플의 MVC 패턴

- 애플의 MVC패턴은 기존의 그것과는 다르다.
- ViewController가 View의 라이프 사이클에 관여하기 때문에 둘을 분리하기 어렵다.
	→ 앱 테스트하기 어려움
