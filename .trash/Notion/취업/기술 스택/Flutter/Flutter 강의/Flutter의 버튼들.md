---
설명: ElevatedButton, OutlinedButton, TextButton, 세가지 스타일링 방법
상위 항목:
  - "[[인프런 강의]]"
---
## styleFrom 스타일링

세 종류의 버튼은 사실상 모두 같은 위젯, 그저 기본 스타일이 첨가된 정도

```Dart
OutlinedButton(
	onpressed: (){}, 
	style: OutlinedButton.styleFrom(
		backgroundColor: Colors.blue,
		/// child 밑에 text 위젯으로도 설정할 수 있지만 버튼 내부에서도 가능
		textStyle: TextStyle(
			fontWeight: FontWeight.w700,
			fontSize: 20.0,
		),
	),
	child: Text('Outlined Button'),
)
```

### shape 파라미터

```Dart
shape: StadiumBorder()  // 세로로 늘린 원형 버튼

shape: RoundedRectangleBorder(   // 둥근 사각형 버튼
	borderRadius: BorderRadius.circular(
		32.0,
	)
)

shape: BeveledRectangleBorder(   // 양쪽으로 연필같은 버튼
	borderRadius: BorderRadius.circular(
		16.0,
	)
)

shape: ContinuousRectangleBorder(   // 더 부드럽게 둥근 사각형 버튼
	borderRadius: BorderRadius.circular(
		32.0,
	)
)
```

  

## Material State 스타일링

- hovered - 호버링 상태 (커서가 올라간 경우)
- focused - 포커스 됐을 때 (텍스트 필드 커서 깜빡거림)
- **pressed - 눌렸을 때**
- dragged - 드래그 됐을 때
- selected - 선택 됐을 때 (체크박스, 라디오 버튼)
- scrollUnder - 다른 컴포넌트 밑으로 스크롤링 됐을 때
- **disabled - 비활성화 됐을 때**
- error - 에러 상태일 때

  

### 1. MaterialStateProperty.all

```Dart
OutlinedButton(
	onpressed: (){}, 
	style: ButtonStyle(
		/// 모든 State에 대해 해당 스타일 적용
		backgroundColor: MaterialStateProperty.all(
			Colors.blue,)
	),
	child: Text('Outlined Button'),
)
```

  

### 2. MaterialStateProperty.resolveWith

```Dart
OutlinedButton(
	onpressed: (){}, 
	style: ButtonStyle(
		/// 특정 State에 대해 해당 스타일 적용
		backgroundColor: MaterialStateProperty.resolveWith(
			(state) {
				if (states.contains(MaterialState.pressed)) {
					return Colors.blue;
				}
				
				return Colors.white;
			},
		),
	),
	child: Text('Outlined Button'),
)
```