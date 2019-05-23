# NCPI integration guide for publisher

### Getting Started

ADBC의 NCPI 캠페인을 진행하기 위해 포스트백을 연동합니다
추가로 귀사에서 사용될 링크 템플릿을 작성하여 ADBC 캠페인의 링크 발급시 사용되는 링크 형태를 미리 정의합니다 


### Prerequisites

방화벽이 설정되어 있다면 아래의 IP에 대해 오픈 정책을 추가합니다

```
13.209.187.209
13.209.170.146
```

# 1.Postback

- 앱 설치 그리고 이벤트에 대한 액션이 발생할때 호출될 포스트백 주소를 정의합니다
- http(s) 호출은 GET method를 사용합니다
- 아래 정의된 매크로 리스트를 참조하여 포스트백 주소를 작성해주세요


| Macro | 설명 | 예시 | 필수 | 인스톨 포스트백 지원 | 이벤트 포스트백 지원 |
| ------ | ------ | ------ | ------ | ------ | ------ |
| {sub1} | 트래킹 링크의 sub1 파라미터에 넣은 값. 일반적으로 Click ID를 전달받기 위해 사용 | aaaaaaaa-bbbb-cccc-dddd-eeeeeeeeeeee | ○ | ○ |  ○|
| {sub2} | 트래킹 링크의 sub2 파라미터에 넣은 값 |  |  | ○ |  ○|
| {sub3} | 트래킹 링크의 sub3 파라미터에 넣은 값 |  |  | ○ |  ○|
| {sub4} | 트래킹 링크의 sub4 파라미터에 넣은 값 |  |  | ○ |  ○|
| {sub5} | 트래킹 링크의 sub5 파라미터에 넣은 값 |  |  | ○ |  ○|
| {install_time} | 앱 설치가 된 시간 | 2019-05-20T19:00:00 |  | ○ |  |
| {event_time} | 이벤트가 발생한 시간 | 2019-05-20T19:30:00 |  |  | ○ |
| {event_name} | 이벤트명 | 2019-05-20T19:30:00 |  |  | ○ |
| {gaid} | Android 광고 식별 ID | 022db29c-d0e2-11e5-bb4c-60f81dca7676 |  | ○ |  ○|
| {idfa} | iOS idfa | 022db29c-d0e2-11e5-bb4c-60f81dca7676 |  | ○ |  ○|


- ###### 인스톨 포스트백 예시
```
http://install.publisher.com?click_id={sub1}&inst_date={install_time}&aid={gaid}&idfa={idfa}
```
- ###### 이벤트 포스트백 예시
```
http://event.publisher.com?click_id={sub1}&evt_date={event_time}&aid={gaid}&idfa={idfa}&evt_name={event_name}
```


# 2.Link template

adbc에서 귀사에게 링크를 발급할 때 어떤 형태로 파라미터를 추가할지 정의합니다

| Parameter | 설명 | 예시 | 필수 |
| ------ | ------ | ------ | ------ |
| sub1 | 포스트백으로 전달받을 값 1 (클릭ID) | aaaaaaaa-bbbb-cccc-dddd-eeeeeeeeeeee | ○ | 
| sub2 | 포스트백으로 전달받을 값 2 |  |  |
| sub3 | 포스트백으로 전달받을 값 3 |  |  |
| sub4 | 포스트백으로 전달받을 값 4 |  |  |
| sub5 | 포스트백으로 전달받을 값 5 |  |  |
| aff_id | 귀사의 매체 식별 값 | app12345_1234 | ○ | 

- ###### 링크 템플릿 예시
```
https://adbc.io?sub1={click_id}&aff_id={affiliate_id}
```

# 3.Test

위 1.Postback과 2.Link template를 정의하여 아래 메일로 전달주시면
검토 및 설정 후 테스트 캠페인을 전달드립니다

## Authors

* **CHOI BAWOO** - *Integration technical support* - [ADBC](https://adbc.co.kr)
bw@adbc.co.kr





