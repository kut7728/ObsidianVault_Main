---
설명: 날짜를 표현하는 클래스
상위 항목:
  - "[[인프런 강의]]"
---
## DateTime()

```Dart
// 프로그램이 실행되는 런타임 기준 시간
void main() {
	final date = DateTime(
		1992, 11, 12, 1, 23, 25);
}

// UTC 기준 시간
void main() {
	final date = DateTime.utc(
		1992, 11, 12, 1, 23, 25);
}
```

- 년, 월, 일, 시, 분, 초, 밀리초 순서
- 년도는 필수입력, 나머지는 옵셔널(월, 일은 기본값 1, 나머지는 0)

### 현재시간

```Dart
void main() {
	final date = DateTime.now();
}
```

### DateTime.add() / DateTime.subtract()

```Dart
print(date.add(duration));
```

- duration 만큼의 기간을 date에서 더하고 빼기

### DateTime.isAfter() / DateTime.isBefore() - 시간 비교

```Dart
print(date1.isAfter(date2));
```

### DateTime.toUtc / DateTime.toLocal() - 시간 기준 변경

---

## Duration()

```Dart
void main() {
	final duration = Duration(
		days: 1,
		hours: 2,
		minutes: 3,
		seconds: 4,
		milliseconds: 1,
		microseconds: 2);
}
```

- 날, 시, 분, 초, 밀리초 순서, named parameter로 입력
- 입력되지 않은 값은 0으로 초기화