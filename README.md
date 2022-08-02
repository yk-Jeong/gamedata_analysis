# 🎮 gamedata analysis
비디오 게임 판매량 데이터 분석 프로젝트
>💭 **작업환경** `google colab`
>
>📅 **진행기간** 21.10.02 ~ 21.10.09

### 프로젝트 개요
게임을 좋아하는 내가 만약 게임 회사에 소속된 기획자라면? <br>
약 20년간 누적된 게임 데이터를 분석해서, **우리 회사가 다음 분기에 출시할 게임의 특징**을 정하고자 한다면?<br><br>
위와 같은 가정에서 해당 데이터를 분석하고, 그 과정에서 다음의 세 가지 질문에도 대답하고자 함


    1. 지역에 따라서 선호하는 게임 장르가 다를까?

    2. 연도별 게임의 트렌드가 존재할까?

    3. 출고량이 높은 게임은 어떤 특징을 가지고 있을까?


- 가설
  - 전세계 판매량/선호 장르 등의 패턴은 **북미 지역의 패턴**과 가장 유사할 것 ⇒ 🅾️
  - 모바일 하드웨어 시장의 성장으로 인해 **전통적인 비디오 게임 판매고는 하락하는 추세**일 것 ⇒ 🅾️
  
- 프로젝트의 목표
  - **신작 게임 기획 방향성 설정**을 위해 2010년대 초반까지의 비디오 게임 판매량 데이터를 분석
  - **지역별 판매 전략**을 수립하기 위해 전세계 각지의 판매 패턴을 비교

### 파일 설명
- **code.ipynb** 분석을 위해 작성한 전체 코드(`google colab`에서 작업)
- **presentation.pdf** 프레젠테이션을 위해 제작한 ppt의 pdf 버전



### 결과 요약
- **가설**: 
    - 전세계 판매 패턴은 북미 지역의 패턴과 가장 유사 → 기획 및 마케팅의 거시적인 포인트는 북미 지역의 패턴을 참고해 맞추는 것이 합리적
    - 휴대형/거치형/PC 중 휴대형 플랫폼으로 발매된 게임의 비중이 62.5%로 가장 높음 → 모바일 하드웨어 시장의 성장으로 인해 비디오 게임의 판매고가 하락한 결정적인 원인으로 판단됨
- **목표**: PC 기반의 멀티 플랫폼, 어드벤처 기반의 복합 장르 작품으로 기획 


---

### 데이터 세트의 특징
- 출처: [Video Game Sales](https://www.kaggle.com/datasets/gregorut/videogamesales), GREGORY SMITH, Kaggle
- 구성: 작품명, 플랫폼, 발매연도, 장르, 퍼블리셔, 미국 판매고, 유럽 판매고, 일본 판매고, 기타 지역 판매고

    ※데이터 세트 전처리 과정: <br>
    - 특성공학: 전세계 판매량 컬럼 추가, 플랫폼 컬럼 세분화(휴대형 콘솔/거치형 콘솔/PC)<br>
    - 판매고의 자릿수 변별 후 통일(K: 천 장thousands, M: 백만 장millions) <br>
    - 장르 결측치 재분류, 연도 결측치 수정(수작업)<br>
    그 외 결측치 제거, 대소문자 통일 등 기본적인 전처리 완료 



### 문제해결 과정

  - **상관계수 분석**<br>
  ![image](https://user-images.githubusercontent.com/90163856/182333117-720cd80c-4347-4aca-ac1f-f47ad0c13e1a.png)
  
  **북미와 유럽**의 판매량 추이가 각각 0.94, 0.90으로 **전세계 판매량 추이와 가장 높은 상관관계**를 가짐<br>
  **일본**에서의 판매량 추이는 타 지역 또는 전세계 판매량과 비교했을 때 **상대적으로 독립적인 경향성**

  - **지역별 선호 장르**<br>
  ![image](https://user-images.githubusercontent.com/90163856/182339055-a29be0e7-1b88-4342-a57e-27110c5d2660.png)

  **북미**에서는 플랫폼(점프), **유럽**에서는 플랫폼과 슈팅, **일본**에서는 롤 플레잉, **그 외 지역**에서는 슈팅 장르를 선호함 
  
  
  - **연도별 게임 트렌드**<br>
  ① 시대-장르 간 상관관계 ② 시대-플랫폼 간 상관관계로 나누어 분석함 
  
  ![image](https://user-images.githubusercontent.com/90163856/182343463-601f8985-5a97-41f2-936d-d7d16a48fd49.png)
  
  ![image](https://user-images.githubusercontent.com/90163856/182343564-66758db4-5bb9-4ab7-b64b-52ba8a111133.png)

  
  - **플랫폼별 비중**<br>
  ![image](https://user-images.githubusercontent.com/90163856/182342572-a7c12e37-0d17-4f9f-a69c-80d38c109f43.png)
  
  휴대형(handheld), 거치형(housing), PC 중 **휴대형**으로 발매된 소프트가 62.7%로 가장 높은 비중을 차지하고 있음


### 한계점과 보완 방안
#### 한계
- **데이터상의 한계**: 2015년도 이후 최신 데이터가 적음 
- **분석상의 한계**
  - 퍼블리셔 분석 미흡: 퍼블리셔(유통사)와 게임의 특성 간 상관관계를 고려하지 않고 분석을 진행하였음 
  - 결측치 처리의 한계: 중복 장르, 발매연도 결측치 등 수작업으로도 처리하지 못한 부분이 존재
  - 그루핑의 한계: 콘솔 플랫폼 각각의 특징이나 발매 시기상의 변수 등을 고려하지 않고 휴대형/거치형/PC로만 분류 

#### 보완방안
- 최신 데이터 추가: 원본 데이터를 제공한 vgchartz.com에서 2015년도 이후 데이터 수집 

<br>

---

### Update

- (2022.07.26~2022.08.02) 프로젝트 소개문 재작성

