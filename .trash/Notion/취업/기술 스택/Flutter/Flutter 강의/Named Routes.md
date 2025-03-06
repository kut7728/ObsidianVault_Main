---
설명: Declarative Routing - 페이지에 이름 붙여서 사용하기
상위 항목:
  - "[[인프런 강의]]"
---
> [!important] Declarative Routing - 페이지(라우트) 이동 할때 지정해 놓은 라우트 이름을 활용해 이동하는 방법

  

### main.dart

```Dart
void main(){
	runApp(
		MaterialApp(
			initialRoute: '/',
			routes: {
				/// key : 라우트의 이름, 
				/// value : builder -> 이동하고 싶은 라우트
				'/': (BuildContext context) => HomeScreen(),
				'/one': (BuildContext context) => RouteOneScreen(),
				'/two': (BuildContext context) => RouteTwoScreen(),
				'/three': (BuildContext context) => RouteThreeScreen(),
			}
		)
	)
}
```

### 다른 페이지

```Dart
...
OutlinedButton(
	onPressed: (){
		Navigator.of(context).pushNamed(
			'/three'
			arguments: 111,
		);
	},
	child: Text('push Route Three'),
)
```