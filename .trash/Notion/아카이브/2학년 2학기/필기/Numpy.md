---
강의 리스트:
  - "[[인공지능과 머신러닝의 이해]]"
생성 일시: 2022-11-03
유형: 필기
주차:
  - 9주차
---
# Numpy

### 2차원 리스트

: 리스트의 리스트

  

### arange(start, stop, step)

start 부터 stop-1까지 step 간격으로 배열 만들기

### np.linspace(start, stop, step)

start 부터 stop-1이 아닌 stop 까지 총 step 갯수의 수들 생성

### .reshape()

메소드, 배열을 변경, 인수로 -1을 넣을경우 데이터 개수에 맞춰 알아서 배열을 만들어줌  
ex) 데이터 12개 짜리 arr1 → arr1.reshape(6, -1) → 6,2 배열로 변경됨  

---

  

  

### np.random.seed(번호)

처음 도출된 랜덤 값을 seed 번호로 고정하고 동일 값을 재사용

### np.random.rand(배열)

난수 생성 함수, 배열 만큼의 난수를 채워 줌

> [!important] **어떤 범위에 있는 난수 생성 법**
> 
> a = 시작 값; b = 끝 값
> 
> (b-a) * np.random.rand(갯수) + a

### np.random.randint(start, stop, [size=n | (행렬)])

start부터 stop-1 까지의 숫자 중에서 size 만큼 정수 채우기

---

  

  

### np.random.randn(갯수 | (행렬))

정규분포를 따르는 난수 생성 (평균값 = 0, 표준편차 = 1)

> [!important] **특정 평균값과 표준편차를 따르는 난수 생성**
> 
> m = 평균값; sigma = 표준편차
> 
> m + sigma * np.random.randn(5)