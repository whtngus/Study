# 9. 추천 시스템(Recommendations)

## 1. 추천 시스템의 개요와 배경

> 추천 시스템의 유형

```
추천시스템은 크게 2가지 유형으로 나뉨

    - 콘텐츠 기반 필터링(Content based filtering)
추천시스템의 초반기에 자주 사용
    
    - 협업 필터링(Collaborative Filltering)
1. 최근접 이웃(Nearest Neighbor) 협업 필터링
추천시스템의 초반기에 자주 사용

2. 잠재 요인Latent Factor) 협업 필터링
넷프릭스 추천 시스템 경연 대회에서 행렬 분해 기법을 이용한 잠재 요인 협업 필터링 기반의 
추천시스템이 우승하면서 많이 사용하기 시작
```

## 2. 콘텐츠 기반 필터링 추천 시스템

```
사용자가 특정한 아이템을 매우 선호하는 경우, 그 아이템과 비슷한 콘텐츠를 가진 다른 아이템을 추천하는 방식.
ex)
A 사용자가 특정 영화에 높은 평점을 준 경우,
그 영화와 장르, 출연 배우, 감독, 영화 키워드 등의 몬텐츠와 유사한 다른 영화를 추천해주는 방식
```

## 3. 최근접 이웃 협업 필터링

```
사용자가 아이템에 매긴 평점 정보나 구매 이력같은 행동 양식(User Behavior)만을 
기반으로 추천을 수행하는 것이 협업 필터(Collaborative Filtering)링 방식.

협업 필터링의 주요 목표는 사용자(아이템 평점 매트릭스)와 같은 축적된 사용자 행동 데이터를 기반으로
사용자가 아직 평가하지 않은 아이템을 예측 평가(Predicted Rating)하는 것.

협업 필터링 방식은 최근접 이웃 방식과가 잠재 요인방식으로 나뉜다.
```

> 최근접 이웃 협업 필터링 설명

```
최근접 이웃 협업 필터링은 메모리(Memory) 협업 필터링이라고도 하며, 일반적으로 사용자 기반과 아이템 기반으로 나눌 수 있다.

    - 사용자 기반(User-User)
당신과 비슷한 고객들이 다음 상품도 구매했습니다.
특정 사용자와 유사한 다른 사용자를 TOP-N으로 선정해 이 사용자가 좋아하는 아이템을 추천하는 방식
    - 아이템 기반(Item-Item)
이 상품을 선택한 다른 고객들은 다음 상품도 구매했습니다.
사용자들이 그 아이템을 좋아/싫어 하는지의 평가 척도가 유사한 아이템을 추천하는 기준이 되는 알고리즘
일반적으로 사용자 기반보다는 아이템 기반 협업 필터링이 정확도가 더 높다. -> 주로 코사인 유사도 사용
(비슷한 영화를 좋아한다고 해서 사람들이 비슷한 취향이라고 확실할 수 없기 때문)
```

## 4. 잠재 요인 협업 필터링

> 잠재 요인 협업 필터링 설명

```
사용자(아이템 평점 매트릭스)속에 숨어 있는 잠재 요인을 추출해 추천 예측을 할 수 있게하는 기법

대규모 다차원 행렬을 SVD와 같은 차원 감소 기법으로 분해하는 과정에서 잠재 요인을 추출한다.
-> 이러한 기법을 행렬 분해(Matrix Factorization)이라고 한다.

잠재 요인이 어떤건지 명확히 정의는 불가능.

잠재요인을 기반으로 다차원 희소 행렬인 사용자-아이템 행렬 데이터를 저차원 밀집 행렬의 사용자-잠재요인 행렬과, 아이템-잠재요인의 전치행렬로 분해할 수 있다.
```

> 행렬 분해의 이해

```
행렬 분해는 다차원의 매트릭스를 저차원 매트릭스로 분해하는 기법
대표적으로 SVD(Singular Vector Decomposition), NMF(Non_Negative Matrix Factorization)등이 있다.
```

> SGD와 ALS(Alternating Least Squares)

```
행렬 분해는 주로 SVD 방식을 이용하지만 NaN값이 없는 행렬에만 적용이 가능하다.
평점이 되지 않은 많은 널값이 있는 영화 평점의 경우 일반적인 SVD로 분해할수가 없다.
이러한 경우 SVD나 ALS방식을 이용해 SVD를 수행한다.

p, q : 행렬분해를 통해 얻은 저차원의 밀집 행렬
SGD 절차
1. P와 Q를 임의의 값을 가진 행렬로 설정
2. P와 Q.T값을 곱해 예측 R행렬을 계산하고 예측 R 행렬과 실제 R 행렬에 해당하는 오류 값을 계산
3. 이 오류 값을 최소화할 수 있도록 P,Q 행렬을 적절한 값으로 업데이트
4. 오류값을 최소화 하기 위한 반복 업데이트를 진행하여 P,Q를 근사화
(학습시 오버피팅을 피하기 위에 L2 규제 적용)
```














