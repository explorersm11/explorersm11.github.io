---
title: "test"
author: explorersm11
date: 2024-05-11 17:29:00 +0900
categories: [Python, Study]
tags: [python, til]
render_with_liquid: false
---  

## 1. 모든 행, 열 출력 설정 : `pd.set_opstion()`
```python
pd.set_option("display.max_rows", None)
pd.set_option("display.max_columns", None)
pd.reset_option("all") # 모든 설정 초기화
```

<br>
    
## 2. 데이터 프레임 가로 병합 : `pd.merge()`

```python
pd.merge(dataframe_1, dataframe_2, how = "left || right", on = "기준 컬럼")
```

<br>

## 3. 데이터 프레임 세로 병합 : `pd.concat()`

```python
pd.concat([dataframe_1, dataframe_2])
```
- 인덱스 중복이 발생하기 때문에 설정 파라미터인 **ignore_index = True** 입력
- 두 데이터의 컬럼(변수)명이 같아야 함
    - 만약, 변수명이 다르다면 **pd.rename()**으로 동일하게 변경 후 진행

<br>

## 4. 파생 변수 추가 함수 : `DataFrame.assign()`

```python
test.assign("파생 변수명" = test["a"] + test["b"])
# 데이터 프레임 명을 반복 입력해야 하는 상황이 생김

test.assign("파생 변수명" = lambda x: x["a"] + x["b"])
# 람다식 사용해서 코드 간결화
# x = test 
```
- 파생 변수를 ","로 구분하여 여러 개 한 번에 추가 가능

<br>

## 5. 데이터 프레임에서 컬럼 하나만 추출하면 시리즈 형태로 반환된다.
- 데이터 프레임 형태를 유지하려면 대괄호로 한 번 더 감싸줌
    ```python
    dataframe["test"] # Series
    dataframe[["test"]] # DataFrame
    dataframe.test # Series
    ```
- 대괄호 대신 "."으로 추출해도 되지만, 시리즈 형태로만 추출된다.

<br>

## 6. 다차원 배열이나 리스트를 데이터 프레임으로 변환하면 Columns 파라미터로 컬럼명 지정 가능

<br>

## 7. 데이터 프레임 조건 검색
```python
dataframe.query("test > 50") # query()
dataframe[dataframe["test"] > 50] # boolean indexing
dataframe.loc[dataframe["test"] > 50] # loc
```

<br>

## 8. 사분위수
- **1사 분위수(Q1)** : 하위 25% 값
- **2사 분위수(Q2)** : 하위 50% 값 (중앙값)
- **3사 분위수(Q3)** : 하위 75% 값
- **아랫 수염** : 0% ~ 25%
- **윗 수염** : 75% ~ 100%
- **극단치 경계** : Q1, Q3 밖 1.5 IQR 내 최대값
- **극단치** : Q1, Q3 밖 1.5 iQR을 벗어난 값
- **IQR(Inter Quartile Range, 사분위 범위)** : Q1과 Q3의 거리