# nCPI integration guide for publisher

# 1.Postback

- Define Install, Event Postback URL
- method : GET
- timeout : 3000ms


| Macro | description | ex | mandatory | install | event |
| ------ | ------ | ------ | ------ | ------ | ------ |
| {sub1} | The first publisher passable parameter | aaaaaaaa-bbbb-cccc-dddd-eeeeeeeeeeee | ○ | ○ |  ○|
| {sub2} | The second publisher passable parameter |  |  | ○ |  ○|
| {sub3} | The third publisher passable parameter |  |  | ○ |  ○|
| {sub4} | The fourth publisher passable parameter |  |  | ○ |  ○|
| {sub5} | The fifth publisher passable parameter |  |  | ○ |  ○|
| {install_time} | installed time | 2019-05-20T19:00:00 |  | ○ |  |
| {event_time} | event time | 2019-05-20T19:30:00 |  |  | ○ |
| {event_name} | event name | 2019-05-20T19:30:00 |  |  | ○ |
| {gaid} | Google advertising identifier | 022db29c-d0e2-11e5-bb4c-60f81dca7676 |  | ○ |  ○|
| {idfa} | identifier for advertisers | 022db29c-d0e2-11e5-bb4c-60f81dca7676 |  | ○ |  ○|
| {cid} | adbc campaign ID | 11929 |  | ○ |  ○|
| {price} | payout | 1200.0 |  | ○ |  ○|
| {evt_price} | purchase price | 35000 |  |  |  ○|
| {evt_quantity} | purchase quantity | 3 |  |  |  ○|
| {evt_product_id} | product id | pid1111 |  |  |  ○|
| {evt_currency} | currency | krw |  |  |  ○|
| {purchase_info} | purchase info JSON format | {} |  |  |  ○|

- ###### install postback sample
```
http://install.publisher.com?click_id={sub1}&inst_date={install_time}&aid={gaid}&idfa={idfa}
```
- ###### event postback sample
```
http://event.publisher.com?click_id={sub1}&evt_date={event_time}&aid={gaid}&idfa={idfa}&evt_name={event_name}
```


# 2.Link template

define tracking url template

| Parameter | Description | Sample | Mandatory |
| ------ | ------ | ------ | ------ |
| sub1 | The first publisher passable macro (for click id) | aaaaaaaa-bbbb-cccc-dddd-eeeeeeeeeeee | ○ | 
| sub2 | The second publisher passable macro |  |  |
| sub3 | The third publisher passable macro |  |  |
| sub4 | The fourth publisher passable macro |  |  |
| sub5 | The fifth publisher passable macro |  |  |
| aff_id | sub-publisher's id | app12345_1234 | ○ |
| gaid | Google Advertising ID | 5195b3c1-0a6b-4c60-a8f2-1cc997e3dfc9 |  |
| idfa | Identifier for Advertising | 97CC2CBC-544A-4A08-99E0-C450A5D2D8DF |  | 
| ua | user agent | Mozilla/5.0 (Linux; Android 10; SM-G887N Build/QP1A.190711.020; wv) AppleWebKit/537.36 ... | ○ | 

- ###### sample for tracking url template
```
https://adbc.io?sub1={click_id}&aff_id={affiliate_id}&gaid={gaid}
```

# 3.Sign up

Go to [https://adbc.co.kr](https://adbc.co.kr) and signup  
Locate to Integration > Postback Configuration  
Fill the forms with your values 



Feel free to contact us at

## Authors

* **CHOI BAWOO** - *Integration technical support* - bw@adbc.co.kr





