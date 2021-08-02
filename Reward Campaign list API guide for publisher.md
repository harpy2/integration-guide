# Reward-CPC Campaign API guide for publisher

***

## Campaign list API

### Getting Started
ADBC에서 제공하는 리워드 캠페인을 API를 통하여 확인합니다 \
Campaign list API 연동이 필요 없을 경우, \
아래 [Reward campaign link and click postback](#reward-campaign-link-and-click-postback) 항목으로 이동해주세요

# 1.기본 정보

- 5분마다 실데이터로 반영되므로 5분 주기로 업데이트 받는 것을 추천드립니다
  - **클라이언트에서 직접 호출 금지. 서버에서 요청 후 캐싱하여 사용하여야합니다**
- method : GET
- domain : http://api.adbc.io/api/v1/reward/campaigns
- parameter : token (mandatory), page (optional)
- 요청 예시 : http://api.adbc.io/api/v1/reward/campaigns?token={token}&page=1
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
| campaigns.click_cap | 일일 캡 | 500 |  |
| campaigns.click_remain_cap | 당일 남은 캡 | 150 |  |
| campaigns.frequency | 디바이스당 노출 제한 | 5 |  |
| campaigns.img_link | 소재 이미지 링크 |  |  |
| campaigns.guideline | 가이드라인 |  |  |
| campaigns.currency | 재화단위 | KRW |  |



***

## Reward campaign link and click postback

### Getting Started
reward campaign api를 통해 캠페인 리스트를 확인 후
홍보하고 싶은 캠페인의 링크를 생성합니다
campaign api의 campaigns.tracking_url을 기준으로 cpb 파라미터에 추가 매크로를 넣어 포스트백을 받을 수 있습니다

### 지원 가능한 파라미터


| 파라미터 | 설명 | 예시 | 비고  | 필수 |
| ------ | ------ | ------ | ------ | ------ |
| cpb | 포스트백 받을 주소 | https%3A%2F%2Fpostback.test.com | encoded URL | |
| gaid | 구글 광고ID | a669b5d0-f29d-11eb-9a03-0242ac130003 | 안드로이드일 경우 | O |
| idfa | 애플 IDFA | a669b5d0-f29d-11eb-9a03-0242ac130003 | 아이폰일 경우 | O |

### 예시


귀사의 포스트백 주소가 https://postback.test.com 이라고 가정했을 때,

    https://adbc.io/{캠페인번호}/{매체고유번호}?cpb=https%3A%2F%2Fpostback.test.com&gaid=a669b5d0-f29d-11eb-9a03-0242ac130003

와 같이 귀사의 포스트백 주소를 URL encoding 후 cpb 파라미터에 넣습니다 


포스트백에 아래의 값을 추가하여 캠페인번호, GAID, IDFA 등의 값을 전달받을 수 있습니다

| 매크로명 | 설명 | 예시 | 비고  |
| ------ | ------ | ------ | ------ |
| {cid} | 캠페인번호 | 13228 | ADBC의 캠페인 번호 |
| {gaid} | 구글 광고 ID |  | 클릭 링크의 gaid 파라미터에 넣은 값 |
| {idfa} | 애플 광고 ID |  | 클릭 링크의 idfa 파라미터에 넣은 값 |



**최종 링크 예시)** 

    https://adbc.io/{캠페인번호}/{매체고유번호}?cpb=https%3A%2F%2Fpostback.test.com%3Fcampaign_id%3D%7Bcid%7D%26google_id%3D%7Bgaid%7D&gaid=a669b5d0-f29d-11eb-9a03-0242ac130003


## Authors

* **CHOI BAWOO** - *Integration technical support* - bw@adbc.co.kr





