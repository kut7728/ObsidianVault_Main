
# 개요
로그에 출력값을 보여주는 두 함수를 비교해보자.
결론적으로 debugPrint가 더 타입적으로 명확하게 알려줌.


# 비교 분석

## 문자열 출력시

```swift
let value: String = "Green is Green" 

debugPrint(value) 
print(value) 

// "Green is Green" 
// Green is Green
```

`““` 이 붙어 문자열임을 확실하게 알 수 있는 debugPrint


## closed Range 출력시

```swift
debugPrint(1...10) 
print(1...10) 

// ClosedRange(1...10) 
// 1...10
```

