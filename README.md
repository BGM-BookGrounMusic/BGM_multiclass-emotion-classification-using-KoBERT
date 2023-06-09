# BGM_multiclass-emotion-classification-using-KoBERT

## 0.KoBERT란?

[KoBERT](https://github.com/SKTBrain/KoBERT) SKT Brain에서 배포한 한국어 버전의 자연어 처리 모델이다. KoBERT를 이해하기 위해서는 먼저 BERT 모델이 무엇인지 알아야 한다. 

- BERT(Bidirectional Encoder Representations from Transformers)는 2018년에 구글이 공개한 사전 훈련된 모델이다. 해당 모델은 방대한 양의 데이터(약 33억개 단어)로 먼저 학습(pretrain)되어 있고, 자신의 사용 목적에 따라 파인튜닝(finetuning)이 가능하다는 점에서 많은 인기를 얻었다.
- KoBERT는 그러한 BERT 모델에서 한국어 데이터를 추가로 학습시킨 모델로, 한국어 위키에서 5백만개의 문장과 54백만개의 단어를 학습시킨 모델이다. 따라서 한국어 버전의 BERT라고도 할 수 있다.

첫 포스트로는 그러한 KoBERT모델을 통해 텍스트에 담긴 7개의 감정을 분류하는 다중감성분류모델을 구현하고자 한다.

## 1. 프로젝트 설명

내가 현재 학교에서 진행하고 있는 프로젝트는 다음과 같다.

- Screen OCR을 통해 소설 텍스트 데이터 수집 및 전처리
- **KoBERT를 이용해 텍스트를 다중감성으로 분류**
- **문단별로 감성 퍼센트 데이터를 분석하여 주된 감성 파악**
- 파악된 감성과 매치되는 음악 데이터를 연결하여 유저에게 제공
- 소설을 읽으며 감성이 달라질때마다 적절하게 음악을 자동으로 변경

나는 해당 프로젝트에서 분석의 핵심이 되는 NLP, 즉 KoBERT를 이용한 자연어 처리 파트를 맡아 진행하고 있다. 이를 위해 첫 포스트는 KoBERT를 이용해, 한국어 대화 문장을 7가지의 감정(기쁨, 슬픔, 놀람, 분노, 공포, 혐오, 중립)으로 분류하는 모델을 학습시키려고 한다.

약 8만건의 한국어 말뭉치를 바탕으로 감성분석 모델을 만들었다. 먼저 토큰화, 정수 인코딩, 패딩 등의 과정으로 데이터를 전처리하고, 주어진 텍스트를 문장 단위로 분류하는 코드가 존재한다. KoBert를 이용한 다중감성분류 모델을 이용해 7가지의 세부 감성을 분석할 수 있다.(행복, 중립, 공포, 놀람, 분노, 슬픔, 혐오)


이번에 소개할 코드는 SKT Brain에서 제공하는 [KoBERT 깃허브](https://github.com/SKTBrain/KoBERT)에 있는 [naver_review_classifications_pytorch_kobert](https://colab.research.google.com/github/SKTBrain/KoBERT/blob/master/scripts/NSMC/naver_review_classifications_pytorch_kobert.ipynb#scrollTo=yyU73n1og6ed)를 바탕으로 작성했다.

구체적인 코드 설명은 하단의 블로그에 라인별로 있으니 이를 참고하면 된다. 

https://velog.io/@fhflwhwl5/Python-KoBERT-7%EA%B0%80%EC%A7%80-%EA%B0%90%EC%A0%95%EC%9D%98-%EB%8B%A4%EC%A4%91%EA%B0%90%EC%84%B1%EB%B6%84%EB%A5%98%EB%AA%A8%EB%8D%B8-%EA%B5%AC%ED%98%84%ED%95%98%EA%B8%B0

