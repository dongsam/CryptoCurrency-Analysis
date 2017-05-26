# Coin-Trends: CryptoCurrency Analysis with Python

## Abstract

최근 비트코인, 이더리움 등이 급등하며 가상화폐 시장이 뜨겁다. 
주식의 경우 해당 기업의 매출 등 재무제표를 통한 기본적 분석으로 기업의 내재가치를 평가한다면, 가상화폐의 가치는 무엇으로, 어떻게 평가할 수 있을까?

본 발표에서는 가상화폐에 대한 기술적 분석과 더불어 텍스트마이닝(뉴스, 커뮤니티)을 통한 심리분석, 오픈소스 분석을 통한 가치 평가로 트렌드를 추정하고 나아가 머신러닝을 활용한 포트폴리오 구성과 백테스팅까지 파이썬으로 개발한 경험에 대해 다룬다.


## Detailed description

{CryptoCurrency, 가상화폐, 암호화폐}(이하 코인) 는 블록체인, 암호학 기술에 근거하여 발행, 거래되는 통화이다. 
보통 거래소에서 거래되는 코인의 경우 누구나 거래에 참여할 수 있는 Public Blockchain 이며, 그 중 대부분은 Github 등에서 오픈소스로서 공개적으로 개발되어간다. 

주식시장에서 경제학자들이 경제학에 기반하여 주식, 회사의 가치를 평가하며 부를 축적했다면
코인시장은 컴퓨터공학자, 암호학자, 개발자들이 코인을 분석하고, 개발하며, 가치를 평가, 창조해 나갈 수 있는 매력적인 시장이라고 볼 수 있다.

본 발표에서는 파이썬으로 코인의 가치 평가 시스템을 개발한 경험에 대해 다루며
자세하게는 기술적 분석, 텍스트마이닝을 통한 심리분석, 오픈소스 분석을 통한 가치 평가, 시스템 트레이딩을 위한 포트폴리오 구성과 백테스팅에 대한 내용을 포함한다.

#### 발표를 듣기 위해 어떤 사전 지식이 필요한가요?

- 파이썬의 기본 문법, 패키지 활용 능력
- 주식 or 코인 시장의 거래 구조에 대한 기초적인 이해
- 머신러닝, 데이터 분석에 대한 기초적인 이해와 경험

#### 청중이 이 발표를 듣고 얻게 되는 것은 무엇인가요?

- 개발자스럽고, 개발자답게 코인의 가치를 평가하는 접근방법
- 파이썬을 통한 웹 크롤링, 텍스트마이닝, 머신러닝, 최적화, 백테스팅을 아우르는 Case Study

### [Research Concept PPT](https://goo.gl/uz1gZC)

### 목차
- Background _[ 가상화폐 시장 및 블록체인 개념에 대한 간략한 설명 ]_ (5분)
    + 블록체인 개념
        * 비트코인[BTC]
        * 라이트코인[LTC]
        * 이더리움[ETH]
        * 리플[XRP]
    + 주식 시장과의 차이점
    + 가상화폐 시장의 특징

- 기술적 분석 (7분)
    + API를 통한 시세, 거래 데이터 가져오기
        * 코인 거래소 소개(제공 API 관점)
            - 해외
                + [Poloniex](http://poloniex.com)
                + [Bitfinex](https://www.bitfinex.com)
                + [Kraken](https://www.kraken.com/)
            - 국내 
                + [빗썸](http://bithumb.com)
                + [코인원](https://coinone.co.kr)
                + [코빗](https://www.korbit.co.kr)
    
    + 거래소, 국가별 시세 차익 분석(arbitrage)
    + 자금 이동 및 추세 분석
        * Price
        * Volume
        * Transaction
        * Momentum
        
- 심리적 분석 [텍스트마이닝, 빈도분석, 오피니언마이닝] (10분)
    + 제한
        * only English

    + 웹 크롤링
        * 대상
            - 코인 리스트
            - 코인 전문 뉴스
            - 코인 전문 블로그, 공식 블로그
            - 코인 관련 커뮤니티
            - 코인 관련 채팅

        * RSS 기반 크롤링
        * WebSocket, WAMP 기반 크롤링
            + [autobahn-python](https://github.com/crossbario/autobahn-python)
        * 크롤링 대상 수집
            - 뉴스, RSS feed 리스트
        * 스케줄링 및 자동화

    + 텍스트 전처리
        * 본문, 제목, 날짜 추출
        * 코인에 대한 동의어 처리
        * 형태소 분석, Stemming
        * [NLTK](http://www.nltk.org/)

    + 텍스트마이닝
        * NER, CRF
        * 키워드 추출

    + 빈도 분석
        * 코인 언급량 변화 추이 분석
    
    + 오피니언마이닝
        * 뉴스 등 글에 대한 긍부정 감정분석
        * 긍부정 사전 구축
            - [SentiWordNet](http://sentiwordnet.isti.cnr.it/)
        * 태깅 및 학습
        * 호재, 악재 판단 및 정확도 검증
    + Word2Vec, Doc2vec, [Gensim](https://radimrehurek.com/gensim/)

- 오픈소스 분석 (7분)
    + 코인별 Github Repository 들의 Activity 활성도 분석 
        * Commits
        * Issues
        * Pull requests
        * Contributors
        * Wiki
    
    + 소스코드 레벨 분석
        * 정적 분석(Static Analysis)
        * 잠재적 취약점 분석
        * 코드 퀄리티 분석
    
    + 텍스트 레벨 분석
        + commit message
        + comments
        + Improvement Proposals
    
    + 블록체인 분석 접근
        * Bitcoin: over 100GB
        * Ethereum: over 30GB
        
- 시스템 트레이딩으로 가기까지 (7분)
    
    + 시그널 발생, 포트폴리오 구성
        * 머신러닝적 접근
            - Collaborative Filtering, Minhash
            - RNN, LSTM

    + 백테스팅(Backtesting)
        * 수익률, 정확도 추정, 평가
        * [zipline](https://github.com/quantopian/zipline)

- 결론 (4분)


### Reference
- Garcia, D., & Schweitzer, F. (2015, June 4). Social signals and algorithmic trading of Bitcoin. arXiv.org. http://doi.org/10.1098/rsos.150288
- Kaminski, J. (2014, June 30). Nowcasting the Bitcoin Market with Twitter Signals. arXiv.org.
- Matta, M., Lunesu, I., & Marchesi, M. (2015). Bitcoin Spread Prediction Using Social And Web Search Media
. UMAP Workshops.
- [finector report](http://finector.com/report/)