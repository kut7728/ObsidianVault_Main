---
설명: 컨테이너의 속성중 그라데이션 설정하기
상위 항목:
  - "[[Video Player 프로젝트]]"
---
> [!important] Container 위젯에서 구현 가능

  

### RadialGradient - 원형 그라데이션

```Dart
Container(
  decoration: BoxDecoration(
    gradient: RadialGradient(
      center: Alignment.bottomLeft,  // 원의 중심 위치
      radius: 2,   // 원의 반지름
      colors: [
        Colors.red,
        Colors.green,
      ],
    ),
  ),
)
```

  

### LinearGradient - 선형 그라데이션

```Dart
Container(
  decoration: BoxDecoration(
    gradient: LinearGradient(
      begin: Alignment.topCenter,   // 그라데이션 시작 지점
      end: Alignment.bottomCenter,   // 종료 시점
      stops: [   // 색깔 하이라이트(섞이지 않은 원색)의 위치, 색의 갯수만큼 실수 지정
        0,
        0.9,
      ],
      colors: [
        Colors.green,
        Colors.red,
      ],
    ),
  ),
)
```