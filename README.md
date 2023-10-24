# 교통인구 통계 및 공연 예매 데이터 기반 지역 클러스터링
🏆 제2회 공연예술(KOPIS) 빅데이터 공모전 장려상 🏆
2022.08 ~ 2022.10

---

# 1. 연구배경

![image](https://github.com/eunjiiiiii/Regional_Clustering_From_Performance_Market/assets/47842737/2b80936f-85ef-461b-8119-406368670ecc)

2022년 kopis 상반기 동향 분석 보고서 통계에 따르면, 코로나19로 타격이 컸던 티켓 판매가 점차 회복세를 넘어 성장세를 보이고 있는 것을 알 수 있었습니다.<br>

![image](https://github.com/eunjiiiiii/Regional_Clustering_From_Performance_Market/assets/47842737/5bc707c3-b17e-4190-99b5-c2016a9edab3)

하지만 이렇게 성장세를 보임에도 불구하고, 여전히 공연이 서울에 집중되어 있고, 예술인들 조차도 서울에 편중되어 있는 상황입니다.<br>
공연시장의 지속적인 성장을 위해서 데이터 분석을 기반으로 서울과 그 외 지역 간의 불균형을 해소할 수 있는 해결방안을 찾아나가야 한다고 판단했습니다.<br>

# 2. 분석 프로세스

![image](https://github.com/eunjiiiiii/Regional_Clustering_From_Performance_Market/assets/47842737/829f5ee1-3385-4843-8054-dab28c27d9af)

- 활용 데이터
  - 인구 데이터
  - 시군구 경계 데이터
  - 교통 데이터
  - KOPIS 공연예매 데이터

# 3. 데이터 탐색

데이터 전처리에 앞서 지역별 데이터 시각화를 통해 공연 예매 특성을 알아보았습니다.

![image](https://github.com/eunjiiiiii/Regional_Clustering_From_Performance_Market/assets/47842737/82de6c1b-0cb7-4a43-a08c-ab33ff3aba57)

#### 장르명

![image](https://github.com/eunjiiiiii/Regional_Clustering_From_Performance_Market/assets/47842737/2b1f1702-e353-47a4-908c-5173ec2b1bff)

서울과 그 외 지역의 구별 공연장수가 현저한 차이를 보이고 있습니다. 서울은 뮤지컬 비율이 압도적으로 높았고, 그 외 지역은 유사한 분포를 보였습니다.


#### 좌석수

![image](https://github.com/eunjiiiiii/Regional_Clustering_From_Performance_Market/assets/47842737/74490a47-e969-4b41-98a3-2d66644c3020)

전라도의 경우에는 다른 지역에 비해 좌석수의 분포가 넓게 나타났고, 제주도나 충청도의 경우 소규모 공연장들로 이루어져 있습니다.


#### 시설특성

![image](https://github.com/eunjiiiiii/Regional_Clustering_From_Performance_Market/assets/47842737/754320b7-3eed-447b-9b6b-a3462385e01b)

뿐만 아니라 각 지역별로 시설 특성에 따른 분포도 확인할 수 있었습니다. 
- 서울 : 민간(대학로 외) > 민간(대학로) > 공공(문화예관)
- 경기도 : 대부분 공공시설
- 경상도 : 민간시설 > 공공시설 (2.5배)
- 전라도 : 민간시설 > 공공시설 (미세한 차이)
- 충청도 : 대부부 민간시설
- 제주도 : 민간시설 X

편의시설이나 주차시설 여부에 따른 지역별 분포도 확인할 수 있었습니다. 

#### 편의시설 여부
![image](https://github.com/eunjiiiiii/Regional_Clustering_From_Performance_Market/assets/47842737/fd81b21c-a887-4340-a4f6-dfcc7eb43c9e)

- 서울 : 값이 눈에 띄게 큼
  -> 서울의 공연장 수가 다른 지역을 압도하기 때문
- 서울 외 지역 : 편의시설끼리 유의미한 경향성 X
  -> 시도라는 큰 단위로 분석했기 때문이라고 판단.
  
#### 주차시설 여부

![image](https://github.com/eunjiiiiii/Regional_Clustering_From_Performance_Market/assets/47842737/81c20dfe-a7e6-4a84-b7d2-bb3982b18ea7)

- 분포 : 주차시설 자체 여부 <-> 주차시설 공영 여부
- 편의시설 여부 변수들과 유사한 결과

#### 장애인 시설 여부

![image](https://github.com/eunjiiiiii/Regional_Clustering_From_Performance_Market/assets/47842737/ea50d64c-26f4-4235-bf12-12670276cfaf)

편의시설 여부 변수들과 유사한 결과를 보였습니다.

#### 장애인석

![image](https://github.com/eunjiiiiii/Regional_Clustering_From_Performance_Market/assets/47842737/bd97dfec-75e9-4f71-b1f3-e338b24af06b)

대부분의 지역이 장애인석을 갖췄으며, 충청도, 강원도는 장애인석이 없는 비율이 있는 비율보다 많았습니다. 

#### 성별

![image](https://github.com/eunjiiiiii/Regional_Clustering_From_Performance_Market/assets/47842737/e3bf2aed-8461-488e-8088-dbbbf56458e0)

성별의 값이 0인 것은 결측치를 의미합니다. 결측치의 비율이 많고 대체할 적합한 방법이 없다고 판단되어 성별 변수를 삭제하였습니다.

#### 연령

![image](https://github.com/eunjiiiiii/Regional_Clustering_From_Performance_Market/assets/47842737/7fb026eb-77af-4fa6-bbac-5b165f421cec)

연령의 값이 0000인 것은 결측치를 의미합니다. 이 역시 결측치 비율이 많고 대체할 적합한 방법이 없다고 판단되어 삭제했습니다.

# 4. 데이터 전처리

kopis데이터의 공연장 주소가 도로명주소로 되어있기 때문에, 이를 시군구코드로 변환하는 작업을 수행했습니다.
GEOSERVICE-WEB을 통해 공연장의 위경도 값을 구하고, QGIS를 활용하여 시군구 레이어를 생성합니다. 공연장의 위경도와 시군구 레이터의 교차 영역을 계산하여 각 공연장이 속해 있는 행정동코드 컬럼을 생성했습니다.

![image](https://github.com/eunjiiiiii/Regional_Clustering_From_Performance_Market/assets/47842737/c072b776-5fb4-441d-8e8d-d28bcd596c9f)

뿐만 아니라, 전국 도시철도,버스정류장 데이터의 경우에도 결측치를 같은 방식으로 처리했습니다.

![image](https://github.com/eunjiiiiii/Regional_Clustering_From_Performance_Market/assets/47842737/e4db5a42-bd83-4acc-bfaf-90eb238042ad)

KOPIS 예매데이터에서 공연장 시설과 관련된 편의시설, 장애인시설, 주차시설의 경우 존재 여부에 따라 1,0 으로 나누고, 현재 연도와 개관연도의 차이를 가지고 노후화정도 컬럼을 만들었습니다. 이를 클러스터링하여 공연장 특성 파생변수를 생성하여 공연장 테이블로 만들었습니다.

![image](https://github.com/eunjiiiiii/Regional_Clustering_From_Performance_Market/assets/47842737/b3589e87-3674-4fd8-b456-6665cd2c3ae7)

최종적으로 지역 클러스터링을 위해, 서울내에 속한 데이터는 제외하였습니다. 그리고 공연장 테이블과 해당 지역의 교통과 인구 통계 테이블을 결합하였습니다. 

![image](https://github.com/eunjiiiiii/Regional_Clustering_From_Performance_Market/assets/47842737/a0b11c3a-0e13-4ab3-9c1d-59b8ff9e4997)


# 5. 모델링

## 1) 공연 클러스터링
공연장 관련 변수 클러스터링 결과, 세가지 집단으로 나눌 수 있었습니다. hall_1은 소규모 민간공연장이 주로 분포해 있었고, hall_2는 공공기관의 특성을 띄고 있었습니다. 마지막으로 hall_3는 주로 대규모 공연장 특성을 보였습니다. 

![image](https://github.com/eunjiiiiii/Regional_Clustering_From_Performance_Market/assets/47842737/000b62f0-3704-429f-9ed1-7a636da4c71a)


## 2) 지역 클러스터링
최종적으로 공연장 파생변수와 연령대별 인구수, 여성인구비율, 경제활동참가율, 대중교통 밀도변수를 가지고 클러스터링을 진행하였고, 각 그래프는 다섯가지 집단의 분포를 나타내고 있습니다.

![image](https://github.com/eunjiiiiii/Regional_Clustering_From_Performance_Market/assets/47842737/7f44546b-d1e0-4a4c-8aea-2936986b987e)


![image](https://github.com/eunjiiiiii/Regional_Clustering_From_Performance_Market/assets/47842737/8c6056c5-147d-4298-9ecf-b45b02eda6fc)

