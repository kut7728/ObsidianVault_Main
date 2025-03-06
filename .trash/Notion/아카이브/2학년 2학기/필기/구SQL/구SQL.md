---
강의 리스트:
  - "[[데이터베이스]]"
생성 일시: 2022-10-14
유형: 필기
주차:
  - 6주차
  - 7주차
---
# SQL의 분류

## 데이터 정의어

- 테이블을 생성하고 변경, 제거하는 기능

  

### CREATE TABLE : 테이블 생성

![[/Untitled 34.png|Untitled 34.png]]

- **NOT NULL** : 속성이 NULL값을 허용하지 않는다는 키워드
- **DEFAULT** : 속성의 기본 값을 지정하는 키워드
- 데이터 타입
    - INT : 정수
    - CHAR(n) : 길이 n인 고정 길이 문자열
    - VARCHART(n) : 최대길이가 n인 가변 길이의 문자열
    - FLOAT(n) : 길이가 n인 부동소수점 실수
    - REAL : 부동소수점 실수
- **FOREIGN KEY** : 외래키를 지정하는 키워드
    - ON UPDATE 옵션 : 참조되는 테이블에서 튜플 변경 시 처리 방법 지정
        
        ![[/Untitled 1 11.png|Untitled 1 11.png]]
        

  

- EX)
    
    ![[/Untitled 2 9.png|Untitled 2 9.png]]
    
      
    

### ALTER TABLE : 테이블 변경

- 속성 추가
    
    ![[/Untitled 3 7.png|Untitled 3 7.png]]
    
- 속성 삭제
    
    ![[/Untitled 4 6.png|Untitled 4 6.png]]
    
    - CASCADE : 삭제할 속성과 관련된 제약조건이나 참조하는 다른 속성 함께 삭제
    - RESTRICT: 관련된 속성이 존재시 삭제 거부
- 제약 조건 추가
    
    ![[/Untitled 5 5.png|Untitled 5 5.png]]
    
- 제약 조건 삭제
    
    ![[/Untitled 6 5.png|Untitled 6 5.png]]
    
- 테이블 삭제
    
    ![[/Untitled 7 4.png|Untitled 7 4.png]]
    
      
    

## 데이터 조작어

### INSERT : 데이터 삽입문

![[/Untitled 8 3.png|Untitled 8 3.png]]

  

### SELECT : 데이터 검색

![[/Untitled 9 3.png|Untitled 9 3.png]]

- 속성 리스트의 순서는 바뀌어도 무방
- ‘ * ‘ 사용하여 모든 속성을 확인가능  
    ex) SELECT * FROM 고객;  
    
- **ALL** : 해당 속성의 모든 값 반환 (중복 허용)
- **DISTINCT** : 해당 속성의 중복 값을 제거하여 결과 반환

  

- **WHERE** : 속성에 조건을 붙여 만족하는 값만 반환
- **ORDER BY**
    - 오름차순(기본) : ASC | 내림차순 : DESC
    - 속성을 여러개로 했다면 첫번째 속성이 최종 오더가 되도록 뒤에서부터 적용
- **산술식** : 속성에 산술 연산자 (+, -, *, /) 와 상수로 값 변경 가능

- **문자열 함수**
    
    ![[/Untitled 10 3.png|Untitled 10 3.png]]
    
      
    

- **AS 바꿀_이름;** : 속성이름을 바꿔서 출력 가능, 바꿀이름에 공백있을시 따옴표로 묶어줘야 함
    
    > [!important] **속성이름은 문자열이 되버리는 따옴표 쓰면 안되는거 아니었남?**
    > 
    > - ㅇㅇ : 속성이름에 ‘모시깽’ 하면 한 열이 전부 모시깽으로 나옴
    > - 하지만 바꿀이름에는 문자열 넣어도 ㅇㅋ
    >     - 공백있는 이름 따옴표로 안묶으면 신택스 에러 뜸
    >     - ` ` 이놈은 써보고 싶은데 ₩로 떠서 못해봄
    
- **LIMIT 출력할_행_갯수 [OFFSET 제외할_행_갯수];** : 샘플로 몇개의 행만 뽑아보기, OFFSET은 앞에서부터 제외시키기

  

### CASE WHEN

조건에 따라 결과 출력

![[/Untitled 11 3.png|Untitled 11 3.png]]

## 데이터 제어어