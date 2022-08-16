# American-Express

대회 - [링크](https://www.kaggle.com/competitions/amex-default-prediction/overview)

base model 만들기 - class link[링크](https://ldjwj.github.io/ML_Basic_Class/part03_ml/part03_pro_kaggle/amex_01_basemodel_xgbm_2208.html)

연습/데이터 분석 노트북 - [링크](https://www.kaggle.com/code/jus9298/4th-base/edit)

제출 노트북 - [링크](https://www.kaggle.com/code/jus9298/4th-comp/edit)

---

##Overview

#Description

* 세계 최대 결제카드 발행사인 아메리칸 익스프레스의 고객 신용거래 채무 불이행 예측

#Evaluation

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
etc.

---

##Data Description

The objective of this competition is to predict the probability that a customer does not pay back their credit card balance amount in the future based on their monthly customer profile. The target binary variable is calculated by observing 18 months performance window after the latest credit card statement, and if the customer does not pay due amount in 120 days after their latest statement date it is considered a default event.

The dataset contains aggregated profile features for each customer at each statement date. Features are anonymized and normalized, and fall into the following general categories:

D_* = Delinquency variables
S_* = Spend variables
P_* = Payment variables
B_* = Balance variables
R_* = Risk variables
with the following features being categorical:

['B_30', 'B_38', 'D_114', 'D_116', 'D_117', 'D_120', 'D_126', 'D_63', 'D_64', 'D_66', 'D_68']

Your task is to predict, for each customer_ID, the probability of a future payment default (target = 1).

Note that the negative class has been subsampled for this dataset at 5%, and thus receives a 20x weighting in the scoring metric.

Files
train_data.csv - training data with multiple statement dates per customer_ID
train_labels.csv - target label for each customer_ID
test_data.csv - corresponding test data; your objective is to predict the target label for each customer_ID
sample_submission.csv - a sample submission file in the correct format
kaggle competitions download -c amex-default-prediction
Use the Kaggle API to download the dataset.
https://github.com/Kaggle/kaggle-api
