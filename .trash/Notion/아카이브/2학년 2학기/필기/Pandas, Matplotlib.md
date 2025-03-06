---
강의 리스트:
  - "[[AI+X 머신러닝]]"
생성 일시: 2022-09-27
유형: 필기
주차:
  - 4주차
---
# Pandas

- 데이터 핸들링 모듈
- 한 열을 Series 라고 함
    
      
    
      
    

## DataFrame

```Python
(변수명) = pd.DataFrame( (채울 데이터), index = (행 이름), columns = (열 이름) )
```

  

```Python
# 처음부터 n개의 행을 보여준다. (디폴트 = 5)
(변수명).head(n)

# 뒤에서부터 n개의 행을 보여준다. (디폴트 = 5)
(변수명).tail(n)
```

```Python
# 데이터프레임의 행과 열을 바꿈
(변수명).T
```

```Python
# 특정 열 기준으로 정렬
(변수명).sort_values(by = ‘열 이름’, ascending = (True/False))
```

  

- 특정 위치의 데이터 변경

```Python
# 열 단위로 변경
df.[’열 이름’] = (변경할 값)

# 행 추가
df.loc[’행 이름’] = (추가할 값)
```

  

```Python
# 엑셀 파일 특정 부분 읽어오기
pd.read_excel(”경로”, header=’열 이름이 위치하는 행 번호 디폴트=0’, usecols=’열’)
```

  

## Matplotlib

```Python
plt.figure()    # figsize=(가로, 세로) 옵션으로 그래프 크기 조절 가능
plt.plot()      # plot()은 값을 이어서 선으로 표현, list형을 대상으로 일반적으로 사용
plt.show()

plt.grid()      # 그래프에 격자 추가

plt.title()     # 그래프에 제목 지정

plt.xlabel()    # 각각 x축과 y축에 이름 나타냄
plt.ylabel()
```

### subplot()

```Python
# 작은 그래프들을 일일히 설정해야함
plt.subplot(a, b, n)     # a행 X b행 으로 나누고 n번째에 그래프를 둔다
```

### subplots()

```Python
# 작은 그래프들을 한번에 설정가능
fig, axes = plt.subplots(nrows = a, ncols = b)
```