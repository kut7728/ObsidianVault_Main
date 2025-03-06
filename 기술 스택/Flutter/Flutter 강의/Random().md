---
설명: 난수를 생성해주는 클래스
상위 항목:
  - "[[랜덤숫자 생성기 프로젝트]]"
---
```Dart
generateRandomNumber() {
    final rand = Random();
    final Set<int> newNumber = {};

    while (newNumber.length < 3) {
      final randomNumber = rand.nextInt(maxNumber);

      newNumber.add(randomNumber);
    }

    setState(() {
      numbers = newNumber.toList();
    });
  }
```

- `.nextInt` - 범위는 0 부터 max를 포함하지 않는 정수