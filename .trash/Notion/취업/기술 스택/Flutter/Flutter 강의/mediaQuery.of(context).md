---
설명: 사용중인 기기의 화면 크기 정보를 가져오는 위젯
상위 항목:
  - "[[데이트날짜앱 프로젝트]]"
---
> [!important] 현재 실행중인 기기의 화면 정보를 가져오는 클래스

  

### 예시

```Dart
SizedBox(
	width: MediaQuery.of(context).size.width
)
```

- 사용중인 기기의 가로 정보를 가져옴 → double.infinity와 다를게 없어 보이지만
- `MediaQuery.of(context).size.width /3` 이런식으로 화면의 특정 크기 만큼만 할당하는게 가능