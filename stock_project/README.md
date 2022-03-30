# kiwoom_project

- 프로젝트 구조
    + folders
        + old_file : 테스트 용도로 썼던 노트북을 모아두었다.
        + test : 테스트 용도로 썼던 파이썬 파일을 모아두었다.
        + stock_project : 주가데이터 프로젝트의 핵심 파일
            + stock_data : raw data files
                + daily_data : 일간 주가데이터를 가져오려고 만들었으나 테스트만 하고 사용하지 않았다.
                + min_data : 형륜씨가 가져온 분봉데이터
                + stock_article0301_0531 : 찬우씨가 가져온 주가 뉴스 데이터
                
                모델에 쓸 raw 데이터이다. 이 데이터들을 기반으로 모델을 제작했다.
            + get_news_data : 찬우씨가 제작한 news 데이터를 가져오는 파이썬 파일
            + get_stock_data : 형륜씨가 제작한 키움증권에서 데이터를 가져오는 부분을 제작한 파일들이 존재
                + kiwoom_api : kiwoom 증권 api를 파이썬으로 wrapping해주는 패키지가 존재
            + newstock : news.py라는 파일이 안에 존재. 이 안에 Newstock이라는 클래스로 raw file들을 preprocessing하고 불러오기 쉽게 도와주는 라이브러리가 있다.
            + jupyter notebooks
                1. labeling_1 : 분단위 데이터를 최종적으로 어떻게 labeling할지를 연구한 노트북 lableing을 하기 위해서 percentage로 나눠보고, 기울기로도 나눠보았다.(결과는 없음. labeling을 해보기만 했다.)
                2. Untitled : konlpy를 실험해본 노트북
                3. Untitled1 : 삼성전자 주식데이터(뉴스+주가)를 가지고 뉴스 데이터를 countervectorizing을 한 뒤, MultinomialNB모델링을 해보았고, '상승', '하락'이라는 단어가 들어있는 경우 두 집합의 평균과 분산으로 t-test를 해보았다. 또한 contingency table을 만들어 보았다.
                4. bert_model : bert model를 기존 뉴스데이터에 시도하려다가 중도에 멈추었다. (완성이 되지 않음)
                5. NB_model : MultinomialNB + Counter vectorizer + 시간순으로 train/test set을 나누었다.
                6. NB_pipline : NB_model에서의 구조를 그대로 하되 sklearn pipeline을 써보았다.
                7. tf-idf : NB_pipeline에서 만든 pipeline을 가지고 삼성전자 주식에 대해서 tf-idf와 countervectorizer를 Grid Search를 통해서 비교해 보았다.
                8. Tfidf_keywords : tf-idf를 하고난 후, 임의의 문장과 가장 유사한 문장을 cos-similarity로 찾아보았다.
                9. NB_Test_All_v1 : 1개의 주식에 대해서 기존의 NB모델을 이용해서 ROC curve와 Confusion Matrix를 만들었다.
                10. NB_Test_All_v2 : 모든 주식에 대해서 NB모델을 사용하여 ROC와 Confusion Matrix를 출력했다.
                11. NB_Test_All_slope : NB모델을 동일하게 하되, Label을 뉴스 발행시점으로부터 60분간의 기울기의 상승, 하락을 예측하도록 했다.
                12. NB_Slope_2 : NB_Test_All_slope와 동일한 방식이나 vectorizer를 tf-idf를 사용했다.
                13. konlpy : kkma 라이브러리를 이용하여 모든 뉴스를 단어단위로 쪼개고, 품사정보를 각 단어에 추가했으며, 그 정보가 추가된 단어들을 이용하여 Word2Vec 라이브러리를 이용하여 vectorizer를 학습시켰다.
                    - tagged_all_kkma.pickle : 품사정보와 단어정보가 들어있는 파이썬 객체
                    - joined_all_kkma.pickle : 품사정보와 단어정보가 '_'로 joined된 파이썬 객체
                    - word2vec_all.model : 품사정보와 단어정보를 가지고 word2vec를 학습시킨 모델 파이썬 객체.
                14. '오르_VV'라는 단어+품사 vector와 가장 비슷한 단어 벡터들이 들어있는 뉴스들을 MultinomialNB 모델로 label은 변동성을 측정하는 것으로 모델을 만들어 보았다.

            
