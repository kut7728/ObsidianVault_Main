---
설명: 여러 데이터를 입력받아 각각의 함수를 적용한 결과를 반환
---
```Swift
map(function, iterable)
```

  

> 예시 1

```Swift
a, b, c, d, e = map(int, ['1', '2', '3', '4', '5'])

// a=1 a=2 a=3 a=4 a=5
```

  

> 예시 2

```Swift
result = map(int, ['1', '2', '3', '4', '5'])

print(result)  //map([1, 2, 3, 4, 5])
```

- `map` 의 결과를 바로 출력하는 `map` 객체로 나옴
- `list()`로 변환해줘야 함

  

### 2차원 배열의 min, max 구하기

```Swift
x = [[1,0,-30,6,5],
			[3,4,7,8,1],
			[3,2,6,7,1],
			[-1,2,3,6,8],
			[99,1,2,3,6,8]]

print(max(map(max, x))) # 최대값 99
print(min(map(min, x))) # 최소값 -30
print(min(map(max, x))) # 내부 배열의 최대 값들 중에서 가장 작은 값 6
print(max(map(min, x))) # 내부 배열의 최소 값들 중에서 가장 큰 값 1
print(sum(map(sum, x))) # 2차원 배열의 모든 값의 합
```