---
설명: 일정 시간 후에 무언가를 실행하게 함
상위 항목:
  - "[[전자액자 프로젝트]]"
---
> [!important] 특정 시간이 지난 뒤 한번 또는 주기적으로 무언가를 실행하도록 함
> 
>   
>   
> 플러터에 기본 제공되는 dart:async 패키지 불러와서 사용  

  

### 단일실행

```Dart
import 'dart:saync';

Timer(
	Duration(seconds: 1),
	() {
		print('1초 뒤에 실행!');
	);
}
```

  

### 반복실행

```Dart
import 'dart:saync';

int number = 0;

Timer.periodic(
	Duration(seconds: 1),
	(Timer timer) {
		number ++;
		print('1초 뒤에 실행!');
		
		if (number == 3) {
			timer.cancel();
	);
}
```