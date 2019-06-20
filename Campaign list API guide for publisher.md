# Campaign list API guide for publisher

### Getting Started

ADBC에서 제공하는 캠페인을  API를 통하여 확인합니다


# 1.기본 정보

- 5분마다 실데이터로 반영되므로 5분 주기로 업데이트 받는 것을 추천드립니다
- method : GET
- domain : http://api.adbc.io/api/v1/campaigns
- parameter : token (mandatory), page (optional)
- token은 발급 후 전달드립니다


# 2.응답 정보

| 파라미터명 | 설명 | 예시 | 비고  |
| ------ | ------ | ------ | ------ |
| result | 응답 결과 코드 | 200 | 에러 코드:501, 502, 503, 504 |
| message | 에러 사유 | token is wrong. Require valid token. | 에러 코드일 경우에만 기재 |
| total_pages | 총 페이지 수 | 1 |  |
| current_page | 현재 페이지 | 1 |  |
| total_campaigns | 총 캠페인 수 | 13 |  |
| campaigns_current_page | 현재 페이지의 캠페인 수 | 10 |  |
| campaigns_per_page | 페이지당 보여줄 수 있는 캠페인 수 | 10 |  |
| campaigns.campaign_id | 캠페인 고유번호 | 11950 | 같은 캠페인이어도 플랫폼별로 구분 |
| campaigns.common_campaign_id | 캠페인 고유번호 | 55071022 | 같은 캠페인이면 동일 |
| campaigns.campaign_name_en | 영문 캠페인명 | UsemapDefenseOnline_NCPI |  |
| campaigns.campaign_name_kr | 한글 캠페인명 | 유즈맵디펜스온라인_NCPI |  |
| campaigns.description | 앱설명 |  |  |
| campaigns.status | 캠페인의 집행 상태 | Active | 진행중:Active, 당일소진:DayOff |
| campaigns.platform | 타겟 플랫폼 | Android | Android, iOS |
| campaigns.tracking_url | 트래킹 URL | https://adbc.io/159750794/{매체고유번호} |  |
| campaigns.target_country | 타겟 국가 | kr |  |
| campaigns.price_krw | 단가 | 1200 | 원 단위 |
| campaigns.price_usd | 단가 | 1 | USD 단위 |
| campaigns.price_type | 수익형태 | CPI | CPI, CPA |
| campaigns.start_date | 시작일 | 2019-06-17T17:07:00+0900 |  |
| campaigns.end_date | 종료일 | 2019-06-30T23:45:00+0900 |  |
| campaigns.daily_cap | 일일 캡 | 500 |  |
| campaigns.daily_remain_cap | 당일 남은 캡 | 150 |  |
| campaigns.icon_link | 캠페인의 아이콘 이미지 링크 | http://static.adbc.io/AdImage/Campaign_3232/Ad_11950/C3232A11950IMG0_1560759358374.jpg" |  |
| campaigns.guideline | 가이드라인 |  |  |
| campaigns.currency | 재화단위 | KRW |  |
| campaigns.store_url | 스토어 링크 | https://play.google.com/store/apps/details?id=com.chuslab.usemap&hl=ko |  |
| campaigns.conversion | 전환 조건 | app open |  |
| campaigns.kpi | kpi | D+1 20% (soft) |  |
| campaigns.package_name | 캠페인의 패키지명 | com.chuslab.usemap |  |




## Authors

* **CHOI BAWOO** - *Integration technical support* - bw@adbc.co.kr





