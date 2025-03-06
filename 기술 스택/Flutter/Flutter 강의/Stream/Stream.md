---
설명: 값을 순서대로 제공받는 stream
상위 항목:
  - "[[Dart 비동기형 프로그래밍]]"
---
![[Assets/image 16.png|image 16.png]]

### Stream 기본 개념

```Dart
import 'dart:async';

void main() {
	final controller = StreamController();   // streamcontroller 인스턴스 생성
	final stream = controller.stream;   // stream 생성
	
	// stream에 빨대 하나 설치, 빨대를 통해 데이터 받고(val), 데이터 넣어서 함수 실행
	final streamListener1 = stream.listen((val){   
		print('Listener1 : $val');            
	});
	
	controller.sink.add(1);    // stream에 데이터 띄우기, 여러개 띄우면 차례대로 들어감
	controller.sink.add(2);
}


>>> Listener1 : 1
>>> Listener1 : 2
```

  

### Stream에 Listener 여러개 선언하기 - BroadcastStream

```Dart
import 'dart:async';

void main() {
	final controller = StreamController();   // streamcontroller 인스턴스 생성
	final stream = controller.stream.asBroadcastStream();   // BroadcastStream 생성
	
	// stream에 빨대 1번 설치, 빨대를 통해 데이터 받고(val), 데이터 넣어서 함수 실행
	final streamListener1 = stream.listen((val){   
		print('Listener1 : $val');            
	});
	
	// stream에 빨대 2번 설치, 빨대로 받은 데이터 바로 가공 가능
	final streamListener2 = stream.where((val) => val % 2 == 0).listen((val){   
		print('Listener2 : $val');            
	});
	
	controller.sink.add(1);    // stream에 데이터 띄우기, 여러개 띄우면 차례대로 들어감
	controller.sink.add(2);
}


>>> Listener1 : 1
>>> Listener2 : 1  where로 가공해서 출력 안됨
>>> Listener1 : 2
>>> Listener2 : 2
```

  

### Stream을 출력하는 함수

```Dart
import 'dart:async';

void main() {
	calculate(1).listen((val){   // stream에 빨대 꽂기
		print('calculate(1) : $val');
	});
}

// stream에는 async* 사용해야함
stream<int> calculate(int number) async* {   // stream을 생성하는 함수
	for(int i=0; i < 5; i++) {
		yield i * number;   //stream에 값을 띄워주는 yield
	}
}

>>> calculate(1) : 0
>>> calculate(1) : 1
>>> calculate(1) : 2
>>> calculate(1) : 3
>>> calculate(1) : 4
```

  

### Stream 을 순차적으로 진행시키는 방법

```Dart
import 'dart:async';

void main() {
	playAllStream().listen((val) {
		print(val);
	});
}

Stream<int> playAllStream()async* {
	yield* calculate(1);    // yield* 을 통해 이 stream이 다 끝난 후에 다음 stream 보냄
	yield* calculate(1000);
}

Stream<int> calculate(int number) async* {
	for(int i = 0; i < 5; i++){
		yield i * number;   
		
		// async* 에서 Future 기능 사용하는 법 - await을 사용하면 됨
		await Future.dealayed(Duration(seconds: 1));
	}
}
```