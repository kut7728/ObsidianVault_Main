---
설명: required 와 RouteSettings
상위 항목:
  - "[[인프런 강의]]"
---
> [!important] 한 페이지에서 다른 페이지로 값을 전달하는 두가지 방법

  

## 1. required 방법

Imperative Routing 이라고 부름

### 전달하는 페이지

```Dart
... 
  settingIconPressed() async {
    max = await Navigator.of(context)
        .push(MaterialPageRoute(builder: (BuildContext context) {
      return SettingScreen(prevMax: max);
    }));
  }
...
```

### 전달받는 페이지

```Dart
class SettingScreen extends StatefulWidget {
  final int prevMax;

  const SettingScreen({
    super.key,
    required this.prevMax,
  });

  @override
  State<SettingScreen> createState() => _SettingScreenState();
}
...
```

  

  

## 2. RouteSettings 방법

필요한 이유 : [[Named Routes]] 에서 Argument를 전달하기 위한 방법이다

### 전달하는 페이지

```Dart
OutlineButton(
	onPressed: (){
		Navigator.of(context).push(
			MaterialPageRoute(
				builder: (BuildContext context){
					return RouteTwoScreen();
				},
				settings: RouteSettings(
					arguments: 789,	
				),
			)
		)
	}
)
```

### 전달받는 페이지

```Dart
@override
widget build(BuildContext context) {
	/// ?는 전달받는 값이 없어 null 일 수도 있기 때문
	final arguments = ModalRoute.of(context)?.settings.arguments;
	
	return DefaultLayout(
		title: 'RouteTwoScreen',
		children: [
			Text(
				/// .toString() - 값이 없는 null 일때도 출력하기 위해
				arutments.toString(),
				textAlign: TextAlign.center,
			),
			OutlinedButton(...),
		]
	),
}
```