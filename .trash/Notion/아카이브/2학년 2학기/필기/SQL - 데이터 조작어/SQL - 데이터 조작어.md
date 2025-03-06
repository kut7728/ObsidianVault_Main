---
강의 리스트:
  - "[[데이터베이스]]"
생성 일시: 2022-11-11
유형: 필기
주차:
  - 7주차
  - 9주차
---
# INSERT : 데이터 삽입문

### INSERT  
INTO 고객(고객아이디, 고객이름, 나이, 등급, 적립금)  
VALUES (’tomato’, ‘정은심’, 35, ‘gold’, 4000);  

  

  

# SELECT : 데이터 검색

### ⑥ SELECT [ ALL | DISTINCT ] 속성, [산술식] [AS 별명]

- ALL : 해당 속성의 모든 값을 반환  
    DISTINCT : 해당 속성의 중복 값을 제거하여 반환  
    
- 테이블의 모든 속성 출력시 리스트 말고 * 사용 가능
- 산술식 : 연산자와 상수를 속성값에 적용해서 출력 가능  
    문자열 함수 : 속성값을 특정 형태로 출력 가능 ex) SELECT LEFT(제품명, 2) → 제품명 속성의 속성값을 왼쪽에서 2글자만 출력하기  
    
    ![[/Untitled 48.png|Untitled 48.png]]
    
- AS : 속성의 이름을 바꿔서 출력

### CASE WHEN

: 속성값을 조건에 따라 다르게 출력하고 싶을 때 사용

```SQL
SELECT 속성, CASE WHEN 조건1 THEN 결과1
								WHEN 조건2 THEN 결과2
								...
								ELSE 결과n
								END [AS 별명]
```

- 조건에 맞는 경우 카운팅하기
    
    sum(case when ‘조건’ then 1 else 0 end)
    

### RANK

- RANK() : 동점은 공동순위, 차순위는 동점수 만큼 건너 뜀
- DENSE_RANK() : 동점은 공동순위, 차순위는 바로 다음 수
- ROW_NUMBER() : 동점이어도 튜플 순서로 순위 나눔
- 랭크 n위 까지 출력 → where절에서 rnk between 1 and n

```SQL
SELECT 속성,
				RANK() OVER (PARTITION BY 속성
													ORDER BY 속성 DESC) [AS 별명]
```

### DATEDIFF()

: DATEDIFF(’기준 날짜’, 비교할 날짜)

### ① FROM 테이블, [AS 별명]

: 검색하고 싶은 속성이 있는 테이블 나열

- AS 로 별명을 붙여 간결하게 만들 수 있다 → Join 시에 유용

### ② [ WHERE 조건 ]

: 비교 연산자, 논리 연산자를 이용하여 검색 조건 제시

- 문자, 날짜 값은 ‘ ‘ 로 묶어서 표현
- 파이썬과 비교연산자 표현 다름 → 같다( = ), 다르다 ( <> )
    
    ```SQL
    WHERE 단가 BETWEEN 2000 AND 3000;
    
    WHERE 수량 >= 2000 AND 수량 <= 3000;
    
    WHERE 주문고객 IN ('apple', 'melon');
    ```
    

### LIKE ‘ 조건 ‘ 키워드

: 조건에 일치하는 속성값 검색

- % : 문자 종류 및 개수 미정
- _ : 종류 상관없는 문자 한칸

```SQL
WHERE 속성 LIKE '데이터%'    \#데이터로 시작하는 문자열
WHERE 속성 LIKE '데이터___'  \#데이터로 시작하는 6글자 문자열
WHERE 속성 LIKE '__한%'     \#세번째 글자가 '한'인 문자열
```

### NULL

: 속성값에 NULL 여부로 검색

- IS NULL : 속성값이 NULL 인 것 찾기
- IS NOT NULL : 속성값이 NULL이 아닌 것 찾기

```SQL
WHERE 속성 IS NULL;
WHERE 속성 IS NOT NULL;
```

### ③ [ GROUP BY 속성, [HAVING 조건] ]

: 특정 속성의 값이 같은 튜플을 모아 그룹을 만들고, 그룹별로 검색

- 그룹을 나누는 기준이 된 속성을 SELECT 절에도 작성하는 것이 좋음
- HAVING절에서 집계함수 사용 가능
    
    ```SQL
    SELECT 등급, COUNT(*) AS 고객수, AVG(적립금) AS 평균적립금
    FROM 고객
    GROUP BY 등급 HAVING AVG(적립금) >= 1000;
    ```
    

### ④ [ ORDER BY 속성, [ASC | DESC] ]

: 원하는 속성을 기준으로 정렬

- ASC : 오름차순 (기본)  
    DESC : 내림차순  
    
- 여러 기준 , 로 나열가능. 앞에 것 부터 적용 → 최종 오더는 맨 뒤에 기준

### ⑤ [ LIMIT 숫자 [ OFFSET 숫자 ] ];

: 출력할 튜플 수를 제한

- OFFSET : 앞에서부터 숫자 만큼 튜플 제외하고 출력

  

## 집계 함수

: 특정 속성 값을 통계적으로 계산한 결과 출력

- ==WHERE에서 사용 불가!  
    SELECT절이나 HAVING절에서만 사용 가능  
    ==
- count() : 속성값의 갯수 반환, DISTINCT로 중복없이 세기 가능
- max() : 속성값중 최댓값 반환 ↔ min()
- sum() : 속성값의 합계 반환
- floor() : 내림 함수, 소수점 삭제 ex) floor(AGE/10)*10 → 나이대로 출력
    
    ```SQL
    \#집계함수 내 CASE WHEN 구문
    SELECT SUM(CASE WHEN 직업='학생' THEN 1 ELSE 0 END) 학생수,
    			 SUM(CASE WHEN 직업='회사원' THEN 1 ELSE 0 END) 회사원수
    FROM 고객db.고객;
     
    ```
    

  

  

  

# 테이블끼리 연계 : Join

: 여러개의 테이블 연결하여 데이터 검색하기

- 조인 속성 : 테이블간의 연결고리 역할을 하는 속성

### 문제상황을 토대로 Join검색 수행하기

1. 속성 뽑아내기
2. 사용할 Table 정하기
3. Table을 서로 연결 가능한지 고려, 안된다면 간접적으로라도 가능한 다른 Table 추가해서 연결

## FROM에 나열하여 적기

: 나열된 테이블 모든 튜플을 이어적고 그중에서 조건에 맞춰 걸러내는 방법

```SQL
SELECT 제품.제품명
FROM 제품, 주문
WHERE 주문.주문고객 = 'banana' AND 제품.제품번호 = 주문.주문제품;

# 제품T, 주문T를 전부 이어적고 나열한 다음 
# 제품번호와 주문번호의 속성값이 같은 튜플 중(JOIN속성)
# 주문고객이 'banana'인 튜플 걸러내서 출력
```

  

## Join 구문 따로 적기

```SQL
SELECT 제품.제품명
FROM 주문
	INNER JOIN 제품
	on 주문.주문제품 = 제품.제품번호
WHERE ~ ;
```

### INNER JOIN

: 테이블 A와 B가 서로 연결되는 경우만 남김

### LEFT JOIN

: A의 튜플이 메인, 매치되는 B의 튜플이 없다면 B 위치는 NULL

### RIGHT JOIN

: B의 튜플이 메인, 매치되는 A의 튜플이 없다면 A 위치는 NULL

### FULL JOIN

: 모든 A와 B의 튜플 살리기, 매칭 안되는 부분은 NULL

# 쿼리끼리 연계 : Subquery (부속질의문)

: Select문(상위질의문)속 또다른 Select문(부속질의문)을 포함하는 질의

- 부속질의문은 (괄호)로 묶어서 작성, ORDER BY 절 사용 불가
- 단일 행 부속질의문 : 하나의 행만 결과로 반환  
    다중 행 부속질의문 : 여러 행을 결과로 반환  
    
- 부속질의문의 결과로 상위질의문을 수행
- 부속질의문과 상위질의문 연결은 비교연산자(=, <>, ≤, ≥) 사용  
    but 다중 행 부속질의문은 불가  
    
    ```SQL
    SELECT 제품명, 단가
    FROM 제품
    WHERE 제조업체 = (SELECT 제조업체
    								FROM 제품
    								WHERE 제품명='달콤비스킷');
    
    # 결과적으로 WHERE 제조업체 = '한빛제과' 가 됨
    ```
    
- 다중 행 부속질의문의 경우 다음의 연산자 사용
    - IN : 결과 값 중 일치하는 것이 있는 경우 참
        
        ```SQL
        SELECT 제품명, 제조업체
        FROM 제품
        WHERE 제품번호 IN (SELECT 주문제품
        								 FROM 주문
        								 WHERE 주문고객='banana');
        
        # 결과적으로 WHERE 제품번호 IN ('p01', 'p04', 'p05')
        ```
        
    - NOT IN : 결과 값 중 일치하는 것이 없을 때 참
    - EXISTS : 결과 값이 하나라도 존재하면 참
        
        ```SQL
        SELECT 고객이름
        FROM 고객
        WHERE EXISTS (SELECT *
        							FROM 주문
        							WHERE 주문일자='2013-03-15'
        							AND 주문.주문고객=고객.고객아이디);
        ```
        
        > [!important] 부속질의문의 FROM에 주문과 더불어 고객도 불러야 하는게 아닌가?
        > 
        >   
        > JOIN문 아님??  
        > 
        > → 고객 추가하고 전체 코드 돌리니 모든 고객이름 다 나옴
        
    - NOT EXISTS : 결과 값이 하나도 존재하지 않으면 참
    - ALL : 결과 값 모두와 비교한 결과가 참이면 만족
        
        ```SQL
        SELECT 제품명, 단가, 제조업체
        FROM 제품
        WHERE 단가 ALL (SELECT 단가
        							 FROM 제품
        							 WHERE 제조업체='대한식품');
        ```
        
    - ANY, SOME : 결과 값 중 하나라도 비교한 결과가 참이면 만족