---
title: "Machine Learning study - 1"
author: explorersm11
date: 2024-05-05 19:02:00 +0900
categories: [MachineLeaning, Study]
tags: [python, til, machine_leaning]
render_with_liquid: false
---  

- 지도 학습 : 정답이 주어진 데이터를 먼저 학습한 뒤, 정답 예측
- 과적합(Over Fitting) : 학습 데이터에 과하게 최적화되어 실제 예측에는 성능이 과도하게 떨어짐
    - 교차 검증을 하여 데이터 편중을 막자!

## K-폴드 교차 검증
- K개의 데이터 폴드 세트를 만들어서 K번 만큼 각 폴더 세트에 학습과 검증 평가를 반복적으로 수행하는 방법

## Stratified K-Fold
- 불균형한 분포돌들 가진 레이블 데이터 집합을 위한 K-폴드 방식
    - 불균형 분포도 : 특정 레이블 값이 특이하게 많거나 적어서 값의 분포가 한 쪽으로 치우침
- 분류에서의 교차 검증은 Stratified K-Fold로 분할되어야 한다

## GridSearchCV
- 교차 검증, 최적의 하이퍼 파라미터 튜닝

## 데이터 전처리
- **레이블 인코딩** : 카테고리 피처 -> 코드형 숫자값
    ```python
    from sklearn.preprocessing import LableEncoder
    ```
    - 숫자 값의 크고 작음이 알고리즘에 영향을 줘서 특정 ML에서 예측 성능이 떨어진다.

- **원-핫 인코딩** : 형 형태의 피처의 고유 값 -> 열 형태의 차원 변환, 해당하는 컬럼에만 1, 나머지는 0으로 값 세팅
    ```python
    from sklearn.preprocessing import OneHotEncoder
    ```
    - 입력 값으로 2차원 데이터 필요
    - 변환 값을 다시 toarray() 메소드를 이용해서 변환해야 함
    - 판다스에 원 핫 인코딩을 더 쉽게 지원하는 API 존재 : `pd.get_dummies()`