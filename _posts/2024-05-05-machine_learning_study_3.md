---
title: "Machine Learning study - 4"
author: explorersm11
date: 2024-05-12 19:01:00 +0900
categories: [MachineLeaning, Study]
tags: [python, til, machine_leaning]
render_with_liquid: false
---  

# 분류(Classification)
학습 데이터로 주어진 데이터의 피처와 레이블 값을 머신러닝 알고리즘으로 학습해 모델을 생성하고, 생성된 모델에 새로운 데이터가 주어졌을 때 레이블 값을 예측하는 것.

## 결정트리
- 데이터에 있는 규칙을 학습을 통해 자동으로 찾아내어 트리 기반의 분류 규칙을 만든다.

    ![KakaoTalk_20240512_184701412](https://github.com/explorersm11/explorersm11/assets/145624456/fef2d005-943a-481e-9f6d-1ed604f11982)


- 많은 규칙이 있다는 것은 분류를 결정하는 방법이 복잡하다는 뜻 (트리의 depth 깊어짐 : 과적합)


- 최대한 **균일한** 데이터 세트를 구성할 수 있도록 분할하는 것이 필요


- 균일도 측정의 대표적인 방법
    - 엔트로피를 이용한 정보이득 지수
        - **엔트로피 : 데이터 집합의 혼잡도**
            - 서로 다른 값 = 엔트로피 높음
            - 서로 같은 값 = 엔트로피 낮음
        - **정보이득 지수 : 1에서 엔트로피 지수를 뺀 값** (1 - 엔트로피 지수)
        - 정보이득 지수가 높은 속성을 기준으로 분할한다.

    - 지니 계수
        - 경제학의 불평등 지수를 나타내는 계수
        - 0(평등) <--> 1(불평등)
        - 머신러닝에서는 지니 계수가 낮을수록 데이터의 균일도가 높음
        - 지니 계수가 낮은 속성을 기준으로 분할


- 사이킷런에서 DecisionTreeClassfier 또는 DecisionTreeRegressor로 구현


- 과정
    ![KakaoTalk_20240512_185459917](https://github.com/explorersm11/explorersm11/assets/145624456/73907d13-4264-495b-9642-5e05097b8cdf)


- **장점** : 알고리즘이 쉽고 직관적임
- **단점** : 과적합으로 정확도 떨어짐


- 트리의 크기를 사전에 제한하는 것이 성능 튜닝에 도움이 된다.


- Parameters
    - min_samples_split : 노드 분할 최소한의 샘플 데이터 수(과적합 제어)
    - min_samples_leaf : 분할이 될 경우 브런치 노드들이 가져야 할 최소한의 샘플 데이터 수
    - max_features : 최적의 분할을 위해 고려할 최대 피처 갯수
        - Default : None(전체)
    - max_depth : 트리의 최대 깊이
        - Default : None
    - max_leaf_nodes : 말단 노드의 최대 개수