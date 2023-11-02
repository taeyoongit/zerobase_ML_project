# 강남구 위치 기반 시설 밀집도 분석

### 📖 Introduction

- 문제 인식: 서울 최고 상권인 강남 지역의 상가 공실률 증가
- 목표: 비지도 학습으로 강남구 시설 밀집도를 분석하여 부동산과 도시개발에 대한 인사이트 제공

### 📝 Result

![](https://velog.velcdn.com/images/hsty94/post/21240a99-a481-4f06-a92e-1fd4b42e7f38/image.png)

- 밀도 레벨을 구분하여 시설 밀집도가 높은 곳과 낮은 곳을 다섯 단계로 구분.

### 🤖 Modeling

#### (1) 폴리곤 바운더리 활용하여 강남구 내 랜덤 좌표 추출

- 강남구 내 850개에서 950개의 랜덤 좌표를 사용
- 폴리곤 바운더리로 랜덤 좌표 중 강, 산 부분을 제외

#### (2) 랜덤 좌표 기준 반경 500m 내 시설별 개수 추출, 전처리

- 랜덤 좌표를 기준으로 반경 500m 내 편의시설별 개수를 추출
- 위경도를 제외한 좌표별 시설 개수를 피처로 사용

#### (3) 군집화(KMeans)

- 클러스터 5개로 나누었을 때가 가장 적절하다 판단.

#### (4) 클러스터별 밀도 레벨 구분 – 평균값, 중위값 활용

- 평균값과 중위값을 기준으로 밀도가 높은 클러스터를 선별


### 💡 EDA & Insight

#### (1) 밀도 레벨별 특성

- 밀도 레벨 4: 상업 집중 지역
- 밀도 레벨 3: 상권과 가까운 지하철역, 대로변
- 밀도 레벨 2: 학동역 주변, 상권과 조금 떨어진 지역
- 밀도 레벨 1: 압구정과 청담의 주거 지역
	     청담역, 선릉과 정릉 주변
	     주거 집중 지역 근처 지하철역   
- 밀도 레벨 0: 주거 집중 지역

#### (2) 강남구 인구 대비 시설 수의 군집화

- 강남역 주변: 밀도 감소
- 수서역 주변: 밀도 증가

#### (3)  지하철역의 밀도 레벨과 주변 시설, 승객 수

- 지하철역 승객 수가 높을 수록 밀도 레벨이 높은 경향


>### 🪅 Toy service
>
>(1) 특정 좌표 입력하면 밀도 레벨과 근거리 시설 출력
>
>(2) 지하철역 주변 밀도 레벨과 근거리 시설 출력
>
>➡️ 특정 좌표와 지하철역 주변 밀도 레벨과 시설 수로 부동산, 도시 개발을 위한 정보 제공

