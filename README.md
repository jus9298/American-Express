# American-Express

대회 - [링크](https://www.kaggle.com/competitions/amex-default-prediction/overview)

base model 만들기 - class link[링크](https://ldjwj.github.io/ML_Basic_Class/part03_ml/part03_pro_kaggle/amex_01_basemodel_xgbm_2208.html)

연습/데이터 분석 노트북 - [링크](https://www.kaggle.com/code/jus9298/4th-base/edit)

제출 노트북 - [링크](https://www.kaggle.com/code/jus9298/4th-comp/edit)

---

## Overview

### Description

* 세계 최대 결제카드 발행사인 아메리칸 익스프레스의 고객 신용거래 채무 불이행 예측

### Evaluation

* 평가지표 M = 정규화된 지니계수 G 와 기본비율 4% D 의 평균
* 4%의 기본비율은 예측의 가장 높은 4%에서의 positive 레이블의 백분율(%). 민감도/호출 통계에 해당.
* G와 D에서 negative 레이블은 다운샘플림을 위해 20 가중치 조정됨
* 최댓값은 1.0
* 이 metric의 계산을 위한 파이썬 코드는 노트북에 제공됨
* Submission file : 테스트 셋에 있는 고객 아이디에 대해 타겟 값의 확률을 예측해야 함. 파일은 다음과 같은 헤더와 포멧을 포함한다.
* customer_ID,prediction

  00000469ba...,0.01
  
  00001bf2e7...,0.22
  
  0000210045...,0.98
  210046.
  etc.

---

## Data Description

고객의 월별 프로필을 바탕으로 향후 신용카드 잔액 등을 갚지 않을 확률을 예측.
타겟 바이너리 변수는 최근 신용카드 내역 이후 18개월간 사용을 관찰하며, 고객이 가장 최근의 내역서 날짜 이후 120일 이내에 만기 금액을 지불하지 않으면 채무 불이행으로 간주한다.

데이터셋은 각 내역 날짜에 각 고객의 프로필 특성을 종합한 것이 포함되어 있다. 
득성은 익명화, 정규화되었으며 다음과 같은 일반적인 카테고리로 분류된다.

* D_* = 연체 변수 (Delinquency variables)
* S_* = 지출 변수 (Spend variables) 
* P_* = 지급 변수 (Payment variables)
* B_* = 균형 변수 (Balance variables)
* R_* = 위험 변수 (Risk variables)

(*다음과 같은 범주형 피쳐. ['B_30', 'B_38', 'D_114', 'D_116', 'D_117', 'D_120', 'D_126', 'D_63', 'D_64', 'D_66', 'D_68'])

### 참가자가 각각의 고객 아이디에 대해 예측할 것 : 미래의 채무 불이행 가능성 (target=1)

negative class는 5%로 이 데이터셋에 대해 다운샘플링되어 scoring metric에서 가중치20

### Files

* train_data.csv - 각 고객 아이디의 여러 내역 날짜를 가지고 있는 훈련 데이터

  컬럼 : customer_ID, S_2(날짜) - 월별 명세서 (Monthly Statement date)

* test_data.csv - 해당하는 테스트 데이터 

* train_labels.csv - 각 고객 아이디에 대한 타겟 레이블

  컬럼 : customer_ID, target값(0과 1로 분류됨.)
  
* sample_submission.csv - 올바른 형식의 샘플 제출파일

  컬럼 : customer_ID, prediction(0인 상태.)

___

## Discussion

Feature 'S_2' (Monthly Statement date): initial analysis and engineering
 - [링크](https://www.kaggle.com/competitions/amex-default-prediction/discussion/329467)



https://www.kaggle.com/competitions/amex-default-prediction/discussion/328565
https://www.kaggle.com/code/swimmy/tuffline-amex-anotherfeaturelgbm

___

train_data 16.39GB
  
test_data 32.82GB
  
train_labels 30.75MB
  
sample_submission 61.95MB
  
### 총 50.32 GB

## 데이터 사이즈 줄이기




