# **참여 여부 검토 중! / 참여 여부 검토 중! / 참여 여부 검토 중!**

</br>

## **1. 대회 요약**
- **주제:** H&M Personalized Fashion Recommendations
- **문제:** 상품 선택의 폭이 너무 넓으면 고객이 관심을 가질만한 것이나 찾고 있는 것을 빨리 찾지 못할 수 있다. 이는 궁극적으로 고객의 구매 포기를 유발한다.
- **목표:** 제품 추천 시스템을 구축하여 고객이 올바른 선택을 할 수 있도록 함으로써 쇼핑 경험을 향상시키고, 반품을 줄인다.
- **문제 유형:** Train data의 마지막 기간 이후 7일 동안 각 고객이 구매할 상품을 예측한다.
  - 7일의 기간 동안 구매하지 않은 고객은 예측 대상에서 제외되며, 인당 최대 12개의 구매 상품을 예측한다.
- **데이터:** 상품 유형, 고객 연령, 상품 설명 텍스트, 성품 이미지, 고객의 구매 이력
  - 정형, 텍스트, 이미지 데이터를 모두 제공한다. 즉, NLP, CV 등 모든 기술을 적용해서 성능을 높여야 한다. (H&M에서도 언급)
  - Public leaderboard에서는 전체 Test Data를 1%만을 사용하여 Score를 산정한다. 즉, Private에서 등수가 뒤집힐 수 있다.
  - 참고로 최근 대회에서는 Test Data를 5%만을 사용했었는데, 1800등이 1등까지 올라간 사례가 있었다.

</br>

## **2. 데이터 세부 - 폴더 별**
- **images/:** a folder of images corresponding to each article_id
  - not all article_id values have a corresponding image. -> 중요 !!!!! 잘못 매칭된 것이 있는지 확인해야 함 !!!!!!!!!!!!!!!
- **articles.csv:** detailed metadata for each article_id available for purchase
- **customers.csv:** metadata for each customer_id in dataset
- **sample_submission.csv:** a sample submission file in the correct format
- **transactions_train.csv:** the training data, consisting of the purchases each customer for each date, as well as additional information.
  - Duplicate rows correspond to multiple purchases of the same item. -> 중요 !!!!! 전처리시 주의해야 함 !!!!!!!!!!

NOTE: You must make predictions for all customer_id values found in the sample submission. All customers who made purchases during the test period are scored, regardless of whether they had purchase history in the training data. -> 중요 !!!!! Test 데이터에는 Train 데이터에는 없는 customer_id가 있을 수 있다. 때문에 customer_id 기반의 모델 구축은 적절하지 않다.
