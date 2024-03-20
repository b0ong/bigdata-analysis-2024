## 9일차 실습
- 빅데이터 실습
    - OpenAPI 기반 크롤링 실습
    - 통계 분석 리뷰
    - 머신러닝 실습

### 빅데이터 실습
#### OpenAPI 기반 크롤링 실습
- [공동데이터포털](https://data.go.kr)
    - 국가 공곡기관에서 무료 제공하는 데이터 API서비스 포털
    - 한국관광공사 관광빅데이터 GW API 사용
    - http 프로토콜로 요청해야함. htpps로 요청하면 ssl 오류발생

    ```pythoh
        ## 반복문으로 처리
    year = 2023
    month = 12
    totalList = []

    for day in tqdm(range(1,32)):
        reqYmd = f'{year}{month}{day:02d}'
        data = getTouristDataService(reqYmd)
        if xmltodict.parse(data)['response']['body']['items'] == None: # 해당 날짜에 데이터가 없을 수 없음
            resList = []
        else:
            resList = xmltodict.parse(data)['response']['body']['items']['item']
            
        totalList = totalList + resList
    ```
    100%|██████████| 31/31 [01:21<00:00,  2.65s/it]

#### 통계 분석 리뷰
- 그래프를 사용한 기술 통계 분석
- 히트맵을 사용한 상관분석

#### 와인 품질 분석