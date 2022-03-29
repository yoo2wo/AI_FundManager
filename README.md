# AI_FundManager
> [팀프로젝트] 인공 신경망과 강화학습을 통한 실시간 주식매매 프로그램 (Tensorflow, Keras, 키움 openAPI, PyQT) (20년 10월  - 20년 12월)

## 프로젝트 소개
주제 : 강화학습과 인공신경망을 통한 실시간 주식 매매 프로그램

## 개발 환경
- Python, Tensorflow, Keras, PyQt
- 키움 open APi 
- 강화학습 투자 시물레이션 RLTrader 오픈소스 사용

## 인공신경망
- 논물을 참고해 LSTM 신경망 결정

  <img src="https://user-images.githubusercontent.com/51395712/160520571-788d2c5e-b0b9-4dd8-9f6c-06077fdd7b79.png" width=50%>
    
    > 관련 논문 “Deep Robust Reinforcement Learning for Practical Algorithmic Trading(2019, August)”
- 시계열의 특성을 고려 일주일(5일) 정도의 데이터를 한번의 예측에 사용 (LSTM의 step 5로 설정)
- LSTM 레이어를 네겹으로 설정햇고 Dropout과 배치 정규화를 실시

## 학습 데이터
- 종목의 시가, 종가, 고가, 저가, 거래량
- 환율, kospi, 국채 가격
- 위 데이터들을 정규화를 위해 비율 데이터로 학습

## 수익률 비교

<img src="https://user-images.githubusercontent.com/51395712/160521516-26286f2a-c03c-4f19-a302-1e29e97251b3.png" width=70%>
<img src="https://user-images.githubusercontent.com/51395712/160521549-828a0191-c6d8-4919-bfb5-ed9f4c27eb06.png" width=70%>

## 시나리오
1. 자동매매전 투자 학습, 모델생성
  <img src="https://user-images.githubusercontent.com/51395712/160522397-8dd44f4e-50d5-4079-a181-03bf49b8894f.png" width=70%>


2. 자동매매 프로그램 UI
  <img src="https://user-images.githubusercontent.com/51395712/160522896-40a5cff8-9d58-4c33-8a2c-7c78e3f58a9a.png" width=70%>

- 로그인으로 키움 연동
- 종목코드 가져오기로 종목별 코드 조회

3. 종목 데이터 얻기
  - 당일 주식의 매매를 판단하기 위해 데이터 얻기
  - 종목 코드 입력후 데이터 얻기를 하면 api 를 통해 학습데이터가 .csv 형식으로 저장
  
 4. 모델활용 후 매매시작![스크린샷 2022-03-29 오전 11 58 26](https://user-images.githubusercontent.com/51395712/160524117-2a72549d-2272-4e3b-ab40-5183c8eb1014.png)

 - 모델 활용 으로 저장된 거래량을 이용하여 키움 api에 매매 요청
