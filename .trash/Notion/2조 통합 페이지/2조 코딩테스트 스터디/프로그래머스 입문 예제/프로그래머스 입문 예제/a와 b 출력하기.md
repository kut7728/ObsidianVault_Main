---
차수: Day1
생성일자: Invalid date
소요 시간: 3분?
작성자: 이규현
해결여부: 해결
---
```Swift
import Foundation

let n = readLine()!.components(separatedBy: [" "]).map { Int($0)! }
let (a, b) = (n[0], n[1])

print("a = \(a)")
print("b = \(b)")
```

  

  

해설

초기 코드가 print(a+b)라고 되있어서 조금 헤메다가 아닌걸 깨닫고 바로 작성했다

print("a = \(a)")  
print("b = \(b)")  

a 값은 a값을 불러와서 출력하고 b값은 b를 불러와서 출력하면된다