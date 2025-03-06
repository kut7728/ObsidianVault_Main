---
설명: pushNamed, pushReplacement, pushNamedAndRemoveUntil…
상위 항목:
  - "[[인프런 강의]]"
---
### push

```Dart
...
OutlinedButton(
	onPressed: (){
		Navigator.of(context).push(
			MaterialPageRoute(
				builder: (BuildContext context){
					return RoutethreeScreen();
				},
			),
		);
	},
	child: Text('push Route Three'),
)
```

- Navigator 스택에 부르고자 하는 페이지를 push

### pushNamed

```Dart
...
OutlinedButton(
	onPressed: (){
		Navigator.of(context).pushNamed(
			'/three',
			arguments: 111,
		);
	},
	child: Text('push Route Three'),
)
```

- Navigator 스택에 부르고자 하는 페이지를 별명으로 push

  

### pushReplacement

```Dart
...
OutlinedButton(
	onPressed: (){
		Navigator.of(context).pushReplacement(
			MaterialPageRoute(
				builder: (BuildContext context){
					return RoutethreeScreen();
				},
			),
		);
	},
	child: Text('push Route Three'),
)
```

- Navigator 스택에 마지막 페이지를 삭제하고 부르고자 하는 페이지를 push

### pushReplacementNamed

```Dart
...
OutlinedButton(
	onPressed: (){
		Navigator.of(context).pushReplacementNamed(
			'/three',
			arguments: 111,
		);
	},
	child: Text('push Route Three'),
)
```

- Navigator 스택에 마지막 페이지를 삭제하고 부르고자 하는 페이지 별명으로 push

  

  

### pushNamedAndRemoveUntil

> [!important] named 라우트를 push 하고, 라우트 스택의 마지막부터 조건문이 true가 나올때까지 라우트 삭제
> 
>   
>   
> **라우트 스택에는 namedPush를 했을때만 이름이 남음**

```Dart
...
OutlinedButton(
	onPressed: (){
		Navigator.of(context).pushNamedAndRemoveUntil(
			'/three',
			/// 조건에 따라 homescreen 라우트를 제외한 나머지 라우트는 삭제됨
			/// 따라서 push했던 threescreen에서 pop버튼 누르면 homescreen으로 돌아옴
			(route){
				return route.settings.name == '/';
			},
			arguments: 111,
		);
	},
	child: Text('push Route Three'),
)
```

  

### maybePop

> [!important] 라우트 스택에 라우트가 없으면 pop 시키지 않음

  

### canPop

```Dart
print(Navigator.of(context).canPop());
```

- 해당 페이지에서 뒤로가기 가능한지 boolean 값을 반환함

  

### PopScope()

```Dart
@override
  Widget build(BuildContext context) {
    return PopScope(
      canPop: false,
      child: DefaultLayout(
        title: 'HomeScreen',
        children: [...]
```

- 시스템에서 제공하는 pop(오른쪽으로 스와이프, 백버튼)을 막아버림