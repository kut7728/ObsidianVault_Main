---
강의 리스트:
  - "[[데이터분석과 시각화]]"
생성 일시: 2022-09-15
유형: 필기
주차:
  - 2주차
---
## R 제거 방법

제어판에서 R studio → R 제거 → 탐색기의 R과 R pro 폴더 삭제

  

## 데이터 타입

- 수치형
    - 실수형 (Double) : 소수점(실수) 값
    - 정수형 (Integer) : 정수값
- 논리형 (Logical) :TRUE / FALSE 값
- 문자형 (Character) : 문자열 값
- 복소수형 (Float) : 실수와 허수 값
- 특수형태
    - NULL : 존재하지 않는 객체 지정시 사용
    - N/A : 결측치(Missing Value) 의미
    - NaN : 수학적으로 계산 불가능한 수

### 데이터 타입 변환 함수

as.double(), as.integer()…

- 변환시킨 다음 다시 할당 해 줘야 함
    
    ```R
    x1 <- 3
    typeof(x1) >> double
    
    as.integer(x1)
    typeof(x1) >> double
    
    x1 <- as.integer(x1)
    typeof(x1) >> integer
    ```
    

  

## 데이터 구조

- Scala 구조 (기본) : 변수 하나에 값 하나
- Vector 구조 : 변수하나에 같은 데이터 타입 여러개 → 행렬
    - c()
        
        ```R
        v1 <- c(3, 11, 5)
        v1 <- c("Kim", "Lee", "Park")
        ```
        
    - seq()
        
        ```R
        v2 <- seq(from = 1, to = 9, by = 2)
        v2                                        >> 1 3 5 7 9
        ```
        
    - rep()
        
        ```R
        v3 <- rep("a", times = 4)
        v3                                         >> a a a a
        v4 <- rep("b", each = 5)
        v4                                         >> b b b b b
        ```
        
        ```R
        v3 <- rep(c("a", "b"), times = 3)
        v3                                         >> a b a b a b
        v4 <- rep(c("c", "d"), each = 3)
        v4                                         >> c c c d d d
        ```
        
        ```R
        v3 <- rep(c("a", "b"), times = 2, each = 3)
        v3                                         >> a a a b b b a a a b b b
        ```
        
        ```R
        v3 <- rep(c("a", "b"), times = c(2, 5))
        v3                                         >> a a b b b b b
        ```
        
- Factor 구조 : 명목형 데이터(코드화 가능한 데이터)를 값으로 저장 ex) 성별, 혈액형
- Matrix 구조 : Vector의 2차원 배열
- Data frames 구조 : 다양한 타입의 데이터를 속성 별로 저장 가능
- List 구조 : 다양한 데이터 구조 저장 가능

  

## 기타 함수 및 기능

- names() 함수 : 데이터에 별명 붙이기
    
    ```R
    v1 <- c(10, 20, 30)
    names(v1) <- c("Kim", "Lee", "Park")
    v1                                         >> Kim Lee Park
                                                   10  20  30
    ```
    

- ‘ : ‘ - 연속적인 범위 표현
- ‘ , ‘ - 비연속적인 범위 표현