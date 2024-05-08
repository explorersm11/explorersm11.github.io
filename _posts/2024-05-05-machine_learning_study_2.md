---
title: "Machine Learning study - 2"
author: explorersm11
date: 2024-05-06 19:21:00 +0900
categories: [MachineLeaning, Study]
tags: [python, til, machine_leaning]
render_with_liquid: false
---  

# 이진 분류에서 중요한 성능 평가 지표(Evaluation Metric)
## 1. 정확도(Accuracy) : `accuracy_score()`
- 실제 데이터와 예측 데이터가 얼마나 같은지 판단
- 정확도 = 예측 결과가 동일한 데이터 수 / 전체 예측 데이터 수
- 불균형한 레이블 데이터 세트에서는 성능 수치로 사용되면 안된다.
    - 여러가지 분류 지표와 함께 적용하여 모델 성능 평가!
        
&nbsp;

## 2. 오차행렬(Confusion Matrix) : `confusion_matrix()`
- 학습된 분류 모델이 예측하면서 얼마나 헷갈리고 있는지도 함께 보여주는 지표
<table border>
    <tr>
        <td></td>
        <td>nagative (0)</td>
        <td>positive (1)</td>
    </tr>
    <tr>
        <td>nagative (0)</td>
        <td align="center">TN</td>
        <td align="center">FP</td>
    </tr>
    <tr>
        <td>positive (1)</td>
        <td align="center">FN</td>
        <td align="center">TP</td>
    </tr>
</table>

- TN: 예측 부정, 실제 부정
- FP: 예측 긍정, 실제 부정
- FN: 예측 부정, 실제 긍정
- TP: 예측 긍정, 실제 긍정

- 정확도 = 예측값과 실제값이 동일한 건수 / 전체 데이터 건수<br>
　　　　　TN + TP / TN + FP + FN + TP

- 불균형한 이진 분류 데이터 세트에서는 positive 데이터 건수가 매우 작다.
    - 예측 정확도가 nagative > positive  ->  모델 신뢰도 떨어짐

&nbsp;

## 3. 정밀도, 재현율 : `precision_score(), recall_score()`
- positive 데이터 세트의 예측 성능에 좀 더 초점을 맞춤
- 정밀도 = **예측을 positive**로 한 대상
    - TP / (FP + TP)
- 재현율 = **실제 값이 positive**인 대상
    - TP / (FN + TP)
- 재현율이 중요한 경우: 실제 positive 데이터를 nagative로 잘못 판단한 경우
    - ex) 환자가 암에 걸렸는데 음성으로 판단
- 가장 좋은 성능 평가는 재현윩돠 정밀도 모두 높은 수치를 얻는 것!

- `predict_proba()` : 테스트 피처 레코드의 개별 클래스 예측 확률을 다차원 배열로 반환
    - predict() 메소드는 predict_proba() 메소드에 기반해 생성된 API
        - 분류 결정 임계값보다 큰 값이 들어있는 컬럼의 위치를 받아서 최종적으로 예측하는 API

- `precision_recall_curve()`
    - parameters
        - y_test : 실제 클래스 값 배열
        - proba_predict : positive 컬럼의 예측 확률 배열

    - return
        - 정밀도 배열
        - 재현율 배열

- 임계값의 변경을 재현윩돠 정밀도의 수치를 상호 보완할 수 있는 수준에서 적용되어야 한다.
    - 단순히 하나의 성능 평가 지표 수치를 높이기 위한 수단으로 사용하면 안됨

&nbsp;
    
## 4. F1 Score : `f1_score()`
- 정밀도와 재현율을 결합한 지표
- 정밀도와 재현울의 수치가 어느 한 쪽으로 치우치지 않는 수치를 나타낼 때 상대적으로 높은 값을 가짐
- F1 Score = (정밀도 * 재현율) / (정밀도 + 재현율) * 2
