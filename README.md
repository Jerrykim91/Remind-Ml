# Remind project

- 이번 프로젝트의 실패 원인은
1. 데이터에 대한 이해도가 낮았다.
2. 날씨가 배추가격에 영향을 미친다고 생각했고 무작정 아무 데이터나 가지고 와서 작업한 점이다.         
이 두 가지가 큰 것으로 판단된다.

- 그래서 다시 프로젝트 정리 겸 작업을 시작하고자 한다.
본 파일은 [이전 프로젝트](https://github.com/euskate/mp02)에서 확인 가능하다.

- 원래 작업의 핵심적인 목적은 일정한 기간 아니 특정한 기간에 사람들이 얼마나 금액을 올리는지 확인하고자 함이다. 
- 특히 명절 때 폭등하는 과일의 금액은 자연재해로 인한 금액 상승이 아닌 특정한 기간이기 때문에 누군가 의도적으로 금액을 올려 팔아서라고 생각되었기 때문이다.

---

**본 프로젝트는 github의 프로젝트 보드로 전체적인 스케줄이 관리되고 있다.**      

---

# 프로젝트 단계

## Step 1. 연구목표 설정

- 농산물의 시세를 예측하고자 한다.
    - 배추가격을 분석해 보고 작업 진행 어느 정도 예측이 나오면 이전에 진행한 무 가격 예측으로 넘어가도록 진행단계를 생각 중이다.

- 연구 목표 설정 이유 :     
    - 핵심적인 목적은 일정한 기간 아니 특정한 기간에 사람들이 얼마나 금액을 올리는지 확인하고자 한다.
    - 특히 명절 때 폭등하는 과일 금액은 평범한 금액 상승이 아닐 거라는 생각이 들었었다.
    - 단합으로 인한 금액 상승일 거라는 생각이 들었고, 이를 확인하고자 이 프로젝트를 구상하였다.
    - 아무래도 명절이라는 특정한 기간이기 때문에 누군가 의도적으로 금액을 올려 팔아서라고 생각되었기 때문이다.

- 전체적인 이미지구상
    - 내가 그려낼 최종 산출물을 상상해본다.
    - 그 상상을 기반으로 어떤 데이터가 필요할지 상상한다.
        - 배추 금액 데이터, 데이터의 날짜에 따른 날씨 데이터

---

## Step 2. 데이터 수집/확보


- 자료를 어디서 구할 수 있는지 파악하고 자료를 수집한다.
    - [KAMIS 농산물 유통 정보](https://www.kamis.or.kr/customer/main/main.do)
        - [조사기준](https://www.kamis.or.kr/customer/price/knowhow/knowhow.do?action=standardList)
    - [날씨/아직]()


- 수집과정에서 데이터를 확인했을 것, 이를 기반으로 데이터를 어떻게 재정리해서 데이터분석을 할지 생각한다.

    - 농산물 데이터
        - KAMIS 농산물 유통 정보에서 데이터는 도매, 소매 소, 도매데이터를 CSV로 다운로드받을 수 있다.
            - 소매와 도매의 차이를 확실하게 아는 것이 필요하다.[관련정보](https://modestmind.tistory.com/140)
               - 일반적인 상품의 유통과정은 생산자 -> 도매상 -> 소매상 -> 소비자 
               - 소매는 최종 소비자에게 판매하는 행위를 소매
               - 도매는 소매를 제외한 모든 판매를 도매

        - 대분류(도매, 소매)에서 원하는 상품을 검색해보면 상품 등급별로 데이터를 가지고 올 수 있다.
            - 이 등급이 무엇을 의미하는지 알 필요가 있다고 생각한다. 하지만 우선순위가 급한 것은 아니다.

    - 날씨 데이터
        - 미정


- 실전:
- 프로토타입구현:

---

## Step 3. 데이터 준비 - 전처리

- 데이터 파악 후 카테고리 정리한다.
    - 이 데이터를 어떻게 활용할지 생각해보고 카테고리를 나눈다.
    - 어떻게 생겼는지 어떻게 이 데이터를 표현할지 구상한다.

- 훈련용 데이터와 학습용 데이터를 75:25로 나눈다.



### Step 3.1 데이터 파악 - 수집 전 어느 정도 구조 파악이 필요

- 농산물 데이터 형태

    - 대형마트, 전통시장 등에서 소비자에게 판매하는 가격을 제공
    - 농산물 특성상 크기와 색상 등이 다양하고 저장 기간, 기후변화에 따라 동일 등급에도 다소 차이가 있을 수 있음
    - **평년은 5년간(올해 제외) 해당일에 대한 최곳값과 최솟값을 제외한 3년 평균값**

    - **전통시장**
        - 경동, 영등포, 부전, 동구, 현대, 양동, 역전, 지동, 중앙, 육거리, 남부, 상남, 신정, 동문시장

 ~~조사단위가 중량이 아닌 품목(포기, 개, 마리 등)은 kg 단위 환산이 제공되지 않음.~~



### Step 3.2 데이터 구조 설계

- 데이터 설계
    - 배추 종류 4가지 
        - 1
        - 2
        - 3
        - 4

    - 소매와 도매 분리
        - 도매 
            - 지역 
                - 서울, 부산, 대구, 광주 ,대전 
            - 10kg 단위
            - 시장 분리 없음 

        - 소매 
            - 지역 
                - 전국구
            - 포기 단위  
            - 시장 분리 있음 
            - 소매 기준 
                - 대형마트와 전통시장으로 카테고리 분리
                    - 대형마트
                    - 전통시장 
                - 각 카테고리 평균
        - 소매강 도매랑 비교하는 부분이 필요할수도 있음 
        

    - 상품과 중품 분리[조사기준](https://www.kamis.or.kr/customer/price/knowhow/knowhow.do?action=standardList)
        - 상품
            - 상품 먼저 진행 
        - 중품

    - 지역별 평균



- 날씨 데이터 형태
    -

- 데이터 -> 최소, 최대, 표준편차, 변동 계수, 진폭계수


---

## Step 4. 데이터 분석	- 탐색적 분석(EDA)

- 탐색적 분석 EDA를 이용
    - 막대차트
    - 선형차트


---

## Step 5. 데이터 모델링 구축

- 데이터 모델링 구축
    - 알고리즘 선택
    - 학습
    - 예측
    - 성능평가
    - 모델 덤프

---

## Step 6. 시스템 통합

- 웹서비스구축
    - 장고를 이용하거나 플라스크를 이용해 진행할 예정이다.

---

