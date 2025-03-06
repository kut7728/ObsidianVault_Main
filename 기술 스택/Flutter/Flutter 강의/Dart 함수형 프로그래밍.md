---
설명: 형변환, map(), where(), reduce()
상위 항목:
  - "[[인프런 강의]]"
---
### 형 변환

리스트로 변환 - `.toList()`

세트로 변환 - `.toSet()`

  

### `map()` : 훑으면서 함수 적용

리스트

```Dart
final newBlackPink = blackPink.map((x) {
	return '블랙핑크 $x';
});

final newBlackPink = blackPink.map((x) => '블랙핑크 $x');
```

- iterable한 blackPink 리스트를 훑으면서 `map()` 함수에 인풋한 함수 적용

  

맵

```Dart
Map<String, String> harryPotter = {
	'Harry Potter' : '해리 포터',
	'Ron Weasley' : '론 위즐리',
	'Hermione Granger' : '헤르미온느 그레인저'
};

final result = harryPotter.map(
	(key, value) => MapEntry(
		'Harry Potter Character $key',
		'해리포터 캐릭터 $value',
	),
};
```

  

세트

```Dart
Set blackPinkSet = {'로제', '지수', '제니', '리사'};

final newSet = blackPinkSet.map((x) => '블랙핑크 $x').toSet();
```

  

### `where()` : 훑으면서 조건에 참이면 보존, 거짓이면 삭제(필터링)

```Dart
List<Map<String, String>> people = [
  {'name': '로제', 'group': '블랙핑크'},
  {'name': '지수', 'group': '블랙핑크'},
  {'name': 'RM', 'group': 'BTS'},
  {'name': '뷔', 'group': 'BTS'},
];

final blackPink = people.where((x) => x['group'] == '블랙핑크');
```

  

### `reduce()` : 훑으면서 순차대로 무언가 실시

```Dart
List<String> words = ['안녕하세요', '저는', '김의택입니다'];

final sentence = words.reduce((prev, next) => prev + next);

// 안녕하세요 저는 김의택입니다
```

- prev에는 최초에만 리스트의 첫번째 항목이 들어가고, 그 이후부터는 return 값이 들어감
- next에는 계속 리스트의 다음 항목이 들어감
- `reduce()`의 리턴값의 타입이 실행되는 리스트의 항목의 타입과 같아야함

  

### `fold()` : 리턴값이 지정되는 reduce()

```Dart
final name = listname.fold<int>(0, (prev, next) => prev + next);
```

- 0 은 최초로 prev에 들어갈 항목

  

### `cascading operator` : 두개의 리스트를 풀어서 넣어줌

```Dart
List<int> even = [1, 3, 5, 7];
List<int> odd = [2, 4, 6, 8];

print([odd, even]);  //[[1, 3, 5, 7], [2, 4, 6, 8]]
print([...odd, ...even]); [1 ,3 ,5, 7, 2, 4, 6, 8]
```