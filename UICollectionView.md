#UIKit #UIKit-View 

# 개요
- 데이터 항목의 정렬된 컬렉션을 관리하고 커스텀한 레이아웃을 사용해 표시하는 객체
- 스크롤 뷰 상속함
- 리스크 뿐만 아니라 슬라이드같은 다양한 방식으로 표현 가능 ([[UITableView]]와 다른 점)

# 기능 구현

![[CleanShot 2025-03-09 at 23.54.21@2x.png]]
## 1️⃣ UICollectionViewDataSource
- 프로토콜
- 섹션이 몇개인지, 섹션속에 셀이 몇개인지
- 컬렉션 뷰로 보여지는 컨텐츠들을 관리하는 객체

### 1. numberOfItemsInSection
- 지정된 섹션에 표시할 셀의 갯수를 묻는 메서드

### 2. CellForItemAt
- 뷰의 지정된 위치에 표시할 셀을 요청하는 메서드

## 2️⃣ UICollectionViewLayout
- 컬렉션 뷰의 시각적인 설정 담당
### Cell
- 컬렉션 뷰의 컨텐츠를 표시

### Supplementary View
- 컬렉션 뷰의 섹션에 대한 정보 표시
- 헤더, 푸터 → 필수 구현 요소 아님

### Decorative View
- 컬렉션 뷰의 배경을 꾸미는 용도

## 3️⃣ UICollectionViewFlowLayout
- 컬렉션 뷰의 셀들의 배치를 담당하는 객체
	- 하나의 열에 몇개를 배치할지
	- 슬라이드처럼 가로로 보기에 적합하게 배치할지 등등
- 셀 간의 거리 뿐만 아니라 섹션 내부의 패딩도 설정 가능

### 구현 순서
1. FlowLayout 객체를 작성하고 컬렉션 뷰에 할당
2. ==셀의 Width, Height 설정==
3. 셀의 좌우 최소간격, 상하 최소 간격을 설정
4. 섹션에 header, footer가 있다면 이들의 크기 설정
5. 레이아웃의 스크롤 방향 설정

## 4️⃣ UICollectionViewDelegate
- 컨텐츠의 표현, 사용자와의 상호작용 관리 → cell 선택시 세부 뷰로 페이지 이동 등에 사용
- 필수 구현 요소 아님

# 커스텀 컬렉션 뷰 : Compositional Layout

![[CleanShot 2025-03-10 at 00.05.19@2x.png]]

## 1️⃣ size
1. Absolute : 절대적인 사이즈를 지정하는 방식
2. Estimate : 시스템 글꼴 크기런타임시에 