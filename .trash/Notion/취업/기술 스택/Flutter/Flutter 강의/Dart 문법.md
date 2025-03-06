---
설명: 변수, 함수, 클래스
상위 항목:
  - "[[인프런 강의]]"
---
> [!info] DartPad  
> An online Dart editor with support for console and Flutter apps.  
> [https://dartpad.dev/](https://dartpad.dev/)  

- 목차
    
    - [[#변수]]
        - [[#타입]]
        - [[#변수명 규칙]]
        - [[#리스트]]
        - [[#맵]]
    - [[#문법]]
        - [[#반복문 for]]
        - [[#반복문 while 과 do-while]]
        - [[#조건문 Switch]]
        - [[#상태지정자 enum]]
    - [[#함수]]
        - [[#일반 함수]]
        - [[#화살표 함수]]
        - [[#함수를 변수처럼 사용하는 Typedef]]
    - [[#클래스]]
        - [[#클래스의 구성요소]]
        - [[#클래스의 객체(Instance) 생성]]
        - [[#상속(Extends)]]
        - [[#Private 옵션]]
        - [[#Static 옵션]]
        - [[#인터페이스]]
        - [[#제너릭 (Generic)]]
    
    ---
    

  

## 변수

### 타입

```Dart
var a = 1; // 처음 담기는 값에 따라 타입 정해짐, 이후 값을 바꿔도 타입은 불변!
dynamic a' = 2;  // 담기는 값에 따라 타입 달라짐

const b = "Hello World"; // 한번 담긴 값은 변경 불가능
final c; // 아무 값 없이 생성 후, 값이 담기면 변경 불가능

String d = "what?"; // 문자열 변수
String? e = null; // 문자열 + null 가능
print(e!) // null이 가능한 변수에 ! 씌우면 -> 현재 null 이 아니라는 뜻
```

### 변수명 규칙

1. `영문 / _ / $ / 숫자` 사용
2. `숫자` 로 시작 불가능
3. 카멜케이스

### 리스트

```Dart
List names = ['daniel', 'chris', 'david'];

names.add('luigi');
names.remove('luigi');
names.add(39);  
// 일반 리스트에는 다른 타입도 저장 가능!
// List<int> names 같이 리스트의 타입을 지정할 수 있다.
```

### 맵

```Dart
Map<String, String> dictionary = {
	'Harry Potter' : '해리포터',
	'Ron Weasley' : '론 위즐리',
};
```

---

  

## 문법

### 반복문 for

```Dart
void main() {
	for (int i = 0; i < 5; i++) {
		print("hello ${i+1}');
	}
}
```

### 반복문 while 과 do-while

```Dart
int total = 0;

while(total < 10) {
	total += 1;
}

do {
	total += 1;
} while(total < 10);
```

### 조건문 Switch

```Dart
int number = 3;

switch (number % 3) {
	case 0:
		print("나머지가 0입니다');
		break;
	case 1:
		print("나머지가 1입니다');
		break;
	default:
		print("나머지가 2입니다.');
		break;
}
```

- 각 케이스의 끝에 break 해줘야 함

### 상태지정자 enum

```Dart
enum Status {
	approved,
	pending,
	rejected,
}

void main() {
	Status status = Status.approved;
	
	if(status == Status.approved) {
		print("approved");
	} else if(status == Status.pending) {
		print("pending");
	} else {
		print("rejected");
	}
}
```

- 클래스처럼 사용
- 다른 개발자에게 어떤 상태가 존재하는지 알릴수 있음

---

  

## 함수

### 일반 함수

```Dart
void main() {
  addNumbers(10, 20, 30);
}

addNumbers(int x, int y, int z) {
  int sum = x + y + z;
  
  print("x : $x");
  print("y : $y");
  print("z : $z");
}
```

- 함수 인풋을 선언하는 것은 parameter, 함수의 인풋 값은 argument 라고 명명
- 위 경우처럼 인풋 순서가 중요한 파라미터를 positional parameter 라고 함
- named parameter
    
    - 이름이 정해져 있어 순서가 중요하지 않은 parameter
    - optional parameter를 사용하려면 required만 제거하면 됨
    
    ```Dart
    void main () {
    	addNumbers(y: 20, x: 10, z: 30);
    }
    
    addNumber({
    	required int x,
    	required int y,
    	int z = 30,
    }) {
    	int sum = x + y + z;
    ```
    
- optional parameter
    
    - parameter중 제공되지 않아도 무방한 parameter
    - 함수 인풋값에 값을 적지 않아도 오류가 생기지 않음  
        → 값을 적지 않으면 null임으로 null허용 타입 써야함  
        → 혹은 기본값을 지정  
        
    
    ```Dart
    addNumbers(int x, [int? y, int z = 30]) {
    	...
    }
    ```
    

### 화살표 함수

```Dart
say() {
	return "hello";
}

arrowSay() => "hello";
```

- 둘은 같은 함수

### 함수를 변수처럼 사용하는 Typedef

- 코드
    
    ```Dart
    void main() {
    	int result = calculate(30, 40, 50, add);
    	print(result1);
    	
    	int result2 = calculate(40, 20, 60, subtract);
    	print(result2);
    }
    
    typedef Operation = int Function(int x, int y, int z);
    // 이런 형태(signature라고 부름)의 함수들을 Operation이라는 타입의 변수처럼 사용 가능
    
    int add(int x, int y, int z) => x + y + z;
    int subtract(int x, int y, int z) => x - y - z;
    int calculate(int x, int y, int z, Operation operation){
    	return operation(x, y, z);
    }
    ```
    

---

  

## 클래스

: 변수와 함수를 모아둔 툴

> [!important] 클래스의 이름은 대문자로 시작함

### 클래스의 구성요소

- 속성(Property) : 클래스 속 변수
    - 왠만한 상황에서는 immutable하게 프로그래밍 하기 위해 final로 변수 선언
- 메소드 : 클래스 속 함수
- 생성자(Constructor) : 클래스 이름과 동일한 함수
    - 클래스의 객체(Instance)를 생성할때마다 실행되는 함수

```Dart
class Bread {
  final String? content;   // null을 허용하지 않는 타입이어서 ? 붙여야 함
  final int? count;
  
  Bread(String name, int count) {  // 생성자
    this.content = name;  // this 붙여야 미리 선언한 변수에 담을 수 있음
    this.count = count;
  }
  
  Bread(this.content, this.count);  // 이것도 똑같은 생성자
  
  String breadStatement() {
    return "${this.content} 는 ${this.count}개 남아있습니다.";
  }
}
```

### 클래스의 객체(Instance) 생성

```Dart
void main() {
  Bread bread = Bread('팥빵', 14);
  print(bread.breadStatement());
}
>> 팥빵 는 14개 남아있습니다.
```

### 상속(Extends)

```Dart
class DailyBread extends Bread {
  
  DailyBread(String name, int count) : super(name, count);
  
  void newStatement() {
    print("$content $count개는 오늘 만들어진 빵입니다.");
  }
}
```

- 자식 클래스 생성자의 `super`은 부모 클래스의 생성자를 활용하게 해주는 문법

### Private 옵션

```Dart
class _Bread {
  final String? content;   // null을 허용하지 않는 타입이어서 ? 붙여야 함
  final int? count;
  
  _Bread(this.content, this.count);  // 이것도 똑같은 생성자
  
  String breadStatement() {
    return "${this.content} 는 ${this.count}개 남아있습니다.";
  }
}
```

- class 구현시와 인스턴스 선언시 모두 클래스 앞에 `_ 언더스코어` 붙여주면 됨
- 해당 파일에서만 사용 가능한 클래스
- 클래스 뿐만 아니라 변수나 함수에도 부여 가능

### Static 옵션

```Dart
void main() {
	Employee uitaek = Employee('uitaek');
	Employee seulgi = Employee('seulgi');
	
	Employee.building = "오투타워";
	
	Employee.workerBuilding();
}

class Employee {
	static String? building;
	String worker;
	
	Employee(this.worker);
	
	void introduce() {
		print("저는 ${this.worker}입니다. ${this.building}에서 근무하고 있죠.");
	}
	
	static void workerBuilding() {
		print("제 근무지는 ${this.building}입니다.");
	}
}
```

- Employee 클래스의 worker 속성은 인스턴스에 귀속되어 인스턴스마다 다르지만  
    building 속성은 static 옵션을 통해 클래스에 귀속되어 모든 인스턴스가 동일하다.  
    
- 클래스에 귀속되는 속성과 메소드들은 클래스로 직접 호출한다.

### 인터페이스

```Dart
abstract class IdolInterface {
	String name;
	
	IdolInterface(this.name);
	
	void sayName(){}
}

class BoyGroup implements IdolInterface{
	String name;
	
	BoyGroup(this.name);
	
	void sayName() {}
}
```

- 클래스의 구조를 통일시키도록 강제하는 기능
- implement 하는 인터페이스의 시그니쳐를 동일하게 따라해야 오류 안생김
- 인터페이스로 인스턴스 생성을 금지하기 위해 `abstract` 옵션 부여

### 제너릭 (Generic)

타입조차도 인풋으로 입력받고 싶을 때 사용

```Dart
void main() {
	Lecture<String> lecture1 = Lecture('123', 'lecture1');
	Lecture<int> lecture2 = Lecture(123, 'lecture2');
}

class Lecture<T> {
	final T id;
	final String name;
	
	Lecture(this.id, this.name);
}
```

---