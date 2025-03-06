---
강의 리스트:
  - "[[기계학습]]"
생성 일시: 2024-03-11
유형: 필기
주차:
  - 2주차
---
- 목차
    - [[#Pandas]]
        - [[#데이터 로드]]
        - [[#시리즈 혹은 데이터프레임 생성]]
        - [[#행, 열 발췌]]
            - [[#특정 열 발췌]]
            - [[#위, 아래 행 발췌]]
            - [[#인덱스로 특정 행 발췌]]
            - [[#조건으로 특정 행 발췌]]
        - [[#데이터 갯수 세기]]
            - [[#.count()]]
            - [[#.value_counts()]]
        - [[#정렬]]
            - [[#인덱스로 정렬 : .sort_index()]]
            - [[#데이터 값으로 정렬 ]]
        - [[#행/열 합계]]
        - [[#apply 변환]]
        - [[#NaN 값 메꾸기]]
        - [[#자료형 바꾸기]]
        - [[#Category 자료형]]
    - [[#Numpy]]
        - [[#ndArray 생성]]
        - [[#특정 값으로 배열 초기화]]
        - [[#배열 구조 바꾸기]]
        - [[#numpy의 슬라이싱]]
        - [[#numpy의 정수 인덱싱]]
            - [[#하나만 가져올 때]]
            - [[#두개 이상 가져올 때 (주의)]]
    - [[#Matplotlib]]
        - [[#라인 플롯 그리기]]

  

# Pandas

series, dataframe 등등 데이터 관리, 편집, 정리

  

### 데이터 로드

```Python
titanic = load_dataset("titanic")
```

  

### 시리즈 혹은 데이터프레임 생성

```Python
series = pd.Series([17000, 18000, 1000, 5000], 
											index=["피자", "치킨", "콜라", "맥주"])
											
values = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
index = ['one', 'two', 'three']
columns = ['A', 'B', 'C']

df = pd.DataFrame(values, index=index, columns=columns)
```

  

## 행, 열 발췌

### 특정 열 발췌

```Python
titanic[['sex', 'age', 'class', 'alive']]
titanic[['sex']]

titanic['sex']
```

- 겉 [대괄호] 는 리스트 인덱싱이라고 이해하면 되고
- 속 [대괄호] 의 경우는 데이터 프레임으로 뽑을 수 있게 해줌

  

### 위, 아래 행 발췌

```Python
titanic.head()
titanic.tail()
```

  

### 인덱스로 특정 행 발췌

```Python
df.loc[['a']]            # >> a라는 인덱스를 가진 행을 데이터프레임 형태로 출력
df.loc['a']              # >> a라는 인덱스를 가진 행을 날것의 데이터로 출력

df.loc['b':'c']          # >> b 부터 c 까지의 인덱스 행 데이터프레임으로 출력
							        	 #    이때는 속 [대괄호] 씌우면 에러

df.loc[['b', 'd']]       # >> 비순차적인 인덱스는 리스트로 호출

df.loc[1:3]              # >> 정수 인덱싱도 가능, 이 경우 슬라이싱 마지막 값을 포함

df.loc[1:3, ["A"]]       # >> A열의 1부터 3행을 데이터프레임으로 출력

df.loc[["a"], :]         # >> 모든 열의 a행을 데이터프레임으로 출력
```

- `.iloc()` 메소드는 정수를 받는 다는 점만 빼고 `.loc()` 과 동일

  

### 조건으로 특정 행 발췌

```Python
df.loc[df.A > 15]        # >> df 의 A열 중 조건을 만족하는 행을 출력

titanic.loc[(titanic['class'] == 'First') & (titanic.sex == 'female')]['age']
# class 열에 First, sex 열에 female 인 행들의 age 열을 출력
```

  

## 데이터 갯수 세기

### `.count()`

```Python
df.count()
```

- 데이터프레임에서는 각 열마다 갯수를 셈
- NaN 값은 세지 않음

  

### `.value_counts()`

```Python
sr.value_counts()

df['age'].value_counts()
```

- 각각의 값이 나온 횟수를 셈 ex) 나이 데이터라면 각 나이가 몇명인지 세줌
- 시리즈라면 그냥 사용하면 되지만
- 데이터프레임의 경우 각 열마다 적용해줘야 함

  

## 정렬

### 인덱스로 정렬 : `.sort_index()`

### 데이터 값으로 정렬

```Python
df.sort_values(by='age')
```

- NaN 값이 있다면 가장 마지막으로
- 기본은 오름차순, 내림차순으로 하려면 `.sort_values(ascending=False)`
- **데이터 프레임에서는 by 인수로 기준이 되는 열을 지정해줘야 함**
    - by 인수에 리스트를 넣으면 순서대로 기준이 됨 `by=[’age’, ‘pclass’]`

  

## 행/열 합계

```Python
df.sum()                              # >> sum은 axis=0 즉 열별 계산이 기본, 생략가능
df.loc["colTotal", :] = df.sum()      # >> 열별 합계를 df의 새로운 행 colTotal에 추가

df.sum(axis = 1)
df["new_rowsum"] = df.sum(axis = 1)   # >> 행별 합계를 df의 새로운열로 추가
```

  

## apply 변환

행이나 열에 반복하여 함수를 적용

```Python
df.apply(lambda x : x.max() - x.min())

df.apply(pd.value_counts)
```

- 적용은 열별이 기본 (axis=0, 생략가능), axis=1 로 행별 적용 가능

  

## NaN 값 메꾸기

```Python
df.fillna(0.0)
```

  

## 자료형 바꾸기

```Python
df['fruit'].astype('category')
```

  

## Category 자료형

```Python
titanic["adult/child"] = titanic.apply(lambda r: "adult" if r.age >= 20 else "child", axis=1)
```

  

---

  

# Numpy

수치 데이터 다루는 패키지

  

## ndArray 생성

```Python
vec = np.array([1, 2, 3, 4, 5])
# 축의 개수 1개, 크기 5

mat = np.array([[10, 20, 30], [ 60, 70, 80]])
# 축의 개수 2개, 크기 (2, 3)
```

- numpy 배열의 축의 개수(ndim)과 크기(shape)을 잘 숙지할 것
- name.ndim 과 name.shape 로 확인 가능

  

## 특정 값으로 배열 초기화

```Python
one_mat = np.ones((2, 3))
# 2, 3 매트릭스를 1로 채움

same_value_mat = np.full((2, 2), 7)
# 2, 2 매트릭스를 7로 채움

random_mat = np.random.random((2, 2))
# 임의의 값으로 채워진 2, 2 매트릭스 생성

range_vec = np.arange(1, 10, 2)
# 1 부터 9까지 2씩 증가하는 배열 생성
```

  

## 배열 구조 바꾸기

```Python
reshape_mat = np.array(np.arange(30).reshape((5, 6))
# 0부터 29의 벡터를 5행 6열 로 구성
```

  

## numpy의 슬라이싱

인덱싱으로 슬라이싱

```Python
reshape_mat[0, :]
# 0행의 모든 값 출력

reshape_mat[:, 1]
# 1열의 모든 행 값 출력
```

  

## numpy의 정수 인덱싱

특정한 값을 뽑아서 새로 배열을 만들고자 할때 사용

### 하나만 가져올 때

```Python
mat[1,0]
```

  

### 두개 이상 가져올 때 (주의)

```Python
mat[[1, 2], [1, 0]]
```

- [1, 2] 과 [1, 0] 의 값을 가져오는게 아니다!!!!
- 겉 [대괄호]에서 행, 열 임으로 속 [대괄호]에서 하나씩 꺼내온다는 개념
    - 즉 [1, 1] 과 [2, 0] 의 값을 가져오는 것

---

  

  

# Matplotlib

데이터를 차트나 플롯으로 시각화하는 패키지

보통 plt로 임포트해서 사용하는게 관례

  

## 라인 플롯 그리기

```Python
plt.title('test')
# 그래프의 제목

plt.plot([1, 2, 3, 4], [2, 4, 8, 6])
# x축과 y축의 값 기재
# 다른 라인을 추가하고 싶다면 같은 포맷으로 한 줄 더

plt.xlabel('hours')
plt.ylabel('score')
# 축 이름 삽입

plt.legend(['A student', 'B student'])
# 범례(라인 종류) 삽입

plt.show()
```