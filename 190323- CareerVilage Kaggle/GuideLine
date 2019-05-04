# Hypothesis
- 전문가 데이터(professionals.csv) professionals의 answers 로 professionals의 industry와 headline을 예측할 수 있다
- 이 문제는 Multi-Labeled Classification (Not multi-class classification)

# Work Flow
- professionals의 industry와 headline 데이터를 나름의 카테고리로 전처리한다. (2)
- Answer의 Text를 TF-idf(문장 내에 단어 가중치를 준다) & tokenizing(Reference 찾아보기로) → 하여 Answer의 명사만 뽑는다. (3)
- Answer의 author_id와 professinals_id를 mapping 해주고, 2번에서 전처리한 Answer의 Text를 Input data, 1번에서 전처리한 professionals의 카테고리를 target으로 하여 예측모델을 만든다. (4)
- 예측 모델로 professionals의 industry와 headline의 NA 값을 예측한다. (NA 값 처리 → Softmax(Classifier)) (5)
- Questions + tags(정규표현식으로 전처리)를 조합(어떻게 조합할지도 고민)하여 questions의 Text를 TF-idf(문장 내에 단어 가중치를 준다) & tokenizing 하여 키워드를 추출한다. (6)
- 추출된 키워드가 input, professionals의 industry와 headline이 target 값으로 하여 분류기를 만든다. (어떤 모델일지는 더 고민) (7)

# Expected Result
- Data → Model 1 → Model 2 → Output(Result)
- Model 1 : Answer를 Tokenizing 해주는 모델. 즉, 의미있는 키워드를 추출하는 모델
- Model 2 : 추출된 키워드를 통해 professional의 industry와 headline을 분류해주는 모델 → 결과적으로 industry, headline 분류를 통해 professional 몇 명을 추려내주는 모델

# 해결해야 할 문제
- 여러개의 answer중에 적절한 answer는? → 1대1인 것만 뽑아서 해보자. (1)

# 모델 향상을 위한 제안
- 우리가 전처리한 카테고리 내에서 professinals의 industry와 headline을 고를 수 있도록 항목을 추가

# 데이터 인사이트
- 1대多인 데이터가 양질의 데이터일 것이다.

# TeamMate
- 경욱/유리


## Idea 1: Questions-Answers 매칭하기
- Idea 1 : questions_title에 있는 명사만 tokenizing으로 뽑아내서 professional_industry와 연결짓기
- Idea 2 : questions_body에서 NER(개체명인식)을 통해 중요한 개체를 찾아서 TF-idf 돌리기 => 유사한 질문목록 

## Idea 2: Answers의 글에서 명사/동사 Hashtags를 뽑아서 전문가별 Hashtags 만들기
- 이후 Tags와 연계하여 새로운 Questions와 매칭
- 전문가의 위치(location)/산업(industry)에 따라 질문의 해시태그로 1차 분류

## Idea 3: Tags 상위를 띄워서 홈페이지에 올리기
- Idea: 태그들 top10으로 띄워서 웹페이지에서 해당 태그 누르면 자동으로 해당 top 질문-답변 볼 수 있게 하는 것은 어떨까?

## Idea 4: Groups의 특징을 파악해서 Questions의 Token과 상관관계 뽑기

## Idea 5: Professional과 Student의 상관관계 확인
- 오프라인 매칭(발전방향)
- 향후에 professional이랑 같은 위치인 사람들끼리 오프라인 매칭 시켜주는 것도 좋을 듯?
- data_join에 따라 태그가 어떻게 변화하는지 확인해보는 것도 좋을 듯
