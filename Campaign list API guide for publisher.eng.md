# Campaign list API guide for publisher

### Getting Started

Receive a list of campaigns provided by ADBC through API


# 1.Overview

- Recommend that you get updates every five minutes.
- method : GET
- domain : http://api.adbc.io/api/v1/campaigns
- parameter : token (mandatory), page (optional)
- Example : http://api.adbc.io/api/v1/campaigns?token={token}&page=1
- Request {token} value from adbc team



# 2.Response Interface

| Parameter | Description | example | notes  |
| ------ | ------ | ------ | ------ |
| result | result code | 200 | error code:501, 502, 503, 504 |
| message | cause of error | token is wrong. Require valid token. | error only |
| total_pages | total pages | 1 |  |
| current_page | current page | 1 |  |
| total_campaigns | total campaign count | 13 |  |
| campaigns_current_page | Number of campaigns on the current page | 10 |  |
| campaigns_per_page | Number of campaigns per page | 10 |  |
| campaigns.campaign_id | campaign ID | 11950 |  |
| campaigns.common_campaign_id | campaign group ID | 55071022 |  |
| campaigns.campaign_name_en | campaign name for eng | UsemapDefenseOnline_NCPI |  |
| campaigns.campaign_name_kr | campaign name for kor | 유즈맵디펜스온라인_NCPI |  |
| campaigns.description | description |  |  |
| campaigns.status | status of campaign | Active | Active, DayOff |
| campaigns.platform | target platform | Android | Android, iOS |
| campaigns.tracking_url | tracking URL | https://adbc.io/159750794/{pub_id} |  |
| campaigns.target_country | target country | kr |  |
| campaigns.price_krw | price for krw | 1200 | won |
| campaigns.price_usd | price for usd | 1 | USD |
| campaigns.price_type | type | CPI | CPI, CPA |
| campaigns.start_date | begin date | 2019-06-17T17:07:00+0900 |  |
| campaigns.end_date | end date | 2019-06-30T23:45:00+0900 |  |
| campaigns.daily_cap | daily capacity | 500 |  |
| campaigns.daily_remain_cap | remain capacity | 150 |  |
| campaigns.icon_link | icon image url |  |  |
| campaigns.guideline | guideline |  |  |
| campaigns.currency | currency | KRW |  |



## Authors

* **CHOI BAWOO** - *Integration technical support* - bw@adbc.co.kr





