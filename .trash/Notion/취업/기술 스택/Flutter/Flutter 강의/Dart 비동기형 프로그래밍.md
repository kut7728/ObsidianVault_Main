---
설명: async, Future, Stream
상위 항목:
  - "[[인프런 강의]]"
하위 항목:
  - "[[Stream]]"
---
### Future 키워드

```Dart
Future<String> name = Future.value('user2');
Future<int> number = Future.value(2);
```

- Future 키워드를 붙여줘야 밑에서 배울 async를 위한 키워드들을 사용할 수 있다.

  

### Future.delayed 메소드

```Dart
Future.delayed(Duration(seconds: 2), () {
	print('Delay 끝');
};
```

- 2개의 파라미터 받음
    - Duration - 지연할 기간
    - 지연시간이 지난 후 실행할 함수

  

### await

```Dart
void addNumbers(int number1, int number2) async {
	print('adding : $number1 + $number2');
	
	await Future.delayed(Duration(seconds: 2). (){
		print('add complete : $number1 + $number2 = ${number1 + number2}');
	});
	
	print('Function ended : $number1 + $number2');
}
```

- Future 값들을 리턴해주는 변수만 `await` 가능 - void도 `Future<void>`로 Future값으로 만들 수 있다
- 함수의 파라미터와 body 사이에 `async` 키워드 넣고 오래걸릴 함수에 `await` 키워드를 삽입
- `await` 키워드 이후의 코드들은 `await` 함수가 끝난 다음에 실행