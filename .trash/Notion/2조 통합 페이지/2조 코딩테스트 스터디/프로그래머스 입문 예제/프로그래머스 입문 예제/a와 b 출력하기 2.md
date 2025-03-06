---
차수: Day1
생성일자: Invalid date
소요 시간: 1분
작성자: 한인탁
해결여부: 해결
구분(입문|기초): 기초
---
[https://school.programmers.co.kr/learn/courses/30/lessons/181951](https://school.programmers.co.kr/learn/courses/30/lessons/181951)

### **문제 설명**

정수 `a`와 `b`가 주어집니다. 각 수를 입력받아 입출력 예와 같은 형식으로 출력하는 코드를 작성해 보세요.

  

```Swift
import Foundation

let n = readLine()!.components(separatedBy: [" "]).map { Int($0)! }
let (a, b) = (n[0], n[1])

print("a = \(a)")
print("b = \(b)")
```

  

.components(separatedBy: [" "])

문자열 기준으로 쪼개서(여기서는 공백기준) 배열로 저장 해준다.