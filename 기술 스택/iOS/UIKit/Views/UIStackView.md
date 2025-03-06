#UIKit #UIKit-View #UIKit-AutoLayout 

## 개요
- ==열 또는 행에 View들의 묶음을 배치할 수 있는 뷰==
- 뷰들을 묶음으로서 오토레이아웃을 남발하는 사태를 방지할 수 있음

## StackView의 속성들 ???
### 1. Axis : 스택 뷰의 방향 결정 (가로, 세로)
### 2. Distribution : 스택 뷰 속 뷰들의 사이즈를 어떻게 분배할지 결정하는 속성
1. Fill 옵션
	- 가능한 공간을 모두 채우도록 내부 뷰들을 조정
	- 각 뷰의 hugging / compression registing priority 에 따라 압축, 팽창하게 됨^[[[AutoLayout]]]
2. Fill Proportionally 옵션
	- 각 뷰의 비율을 유지하면서 내부 공간을 꽉 채움
3. Equal Spacing 옵션
	- 서브 뷰들 사이의 간격을 일정하게 설정
4. Equal Centering 옵션
	- 서브 뷰들의 중앙점간의 길이를 동일하게 맞춰서 설정
### 3. Alignment : 스택뷰 속 뷰들을 어떤식으로 정렬할지 결정하는 속성
1. Fill 옵션
	- 스택뷰가 Horizontal 일 경우, 서브뷰 위아래 공간을 채우기 위해 뷰들을 늘림
	- 스택뷰가 Vertical 일 경우, 서브뷰 좌우 공간을 채우기 위해 뷰들을 늘림
2. Leading 옵션 : Leading에 붙여서 정렬
3. Top 옵션 : 스택뷰 위로 붙여서 정렬
4. First BaseLine 옵션
5. Center 옵션
6. Last BaseLine 옵션

### 4. Spacing : 스택뷰 속 뷰들의 간격을 조정하는 속성
