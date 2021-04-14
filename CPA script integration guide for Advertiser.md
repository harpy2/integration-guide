# CPA script integration guide for Advertiser

### Getting Started

> **사전예약/가입/상담신청/구입** 등 광고주의 프로모션 웹페이지와 스크립트 연동을 위한 가이드입니다 


### Prerequisites

> 1.광고주는 스크립트 연동을 위해 웹페이지를 소유하고 수정권한이 있어야합니다  
> 2.스크립트를 불러올 때 동적 호출은 지원되지 않습니다 (예시 : ajax를 통해 페이지를 로드하여 스크립트가 호출되는 경우)

# 1.Setup

> 아래의 javascript code를 head tag 내에 위치하도록 합니다


```
<script type="text/javascript">
	const ADBC_JS_DEBUG = false;
	eval(function(p,a,c,k,e,r){e=function(c){return(c<a?'':e(parseInt(c/a)))+((c=c%a)>35?String.fromCharCode(c+29):c.toString(36))};if(!''.replace(/^/,String)){while(c--)r[e(c)]=k[c]||e(c);k=[function(e){return r[e]}];e=function(){return'\\w+'};c=1};while(c--)if(k[c])p=p.replace(new RegExp('\\b'+e(c)+'\\b','g'),k[c]);return p}('e 1;e k=w;e 5=f.n(\'5\');5.o=\'x://y.1.z/1.A.B.C\';5.D=p;5.E=7(){k=p};7 g(2,3){4(!k){4(h)i.j(\'1::q::F G H 5\');I(7(){3==="8"?1.8(2):1.9(2)},J)}K{l=L();4(l==c){6=\'1::r::l s c\';4(h)i.j(6);d 6}4(2==c&&3=="9"){6=\'1::r::m s c\';4(h)i.j(6);d 6}4(2==c)2="";e b=f.n(\'M\');b.o=3==="8"?t.g(2):t.9(2);f.u("N")[0].v(b);4(h)i.j(\'1::q::O(\'+2+\')\');d"P"}}1={8:7(a){3="8";d g(a,3)},9:7(m){3="9";d g(m,3)}};f.u(\'Q\')[0].v(5);',53,53,'|adbc|val|type|if|script|errorMsg|function|post|event|||undefined|return|let|document|postback|ADBC_JS_DEBUG|console|log|isLoaded|clk_id|event_name|createElement|src|true|info|error|is|ADBC_URL|getElementsByTagName|appendChild|false|https|static|io|v2|min|js|async|onload|wait|for|loading|setTimeout|2000|else|getClkIdFromCookie|img|body|POSTBACK_FIRED_WITH_|success|head'.split('|'),0,{}))
</script>
```


# 2.Postback

> 사용자가 가입/신청/구매 등의 액션을 한 경우 아래의 코드를 실행합니다 


```

adbc.post(identifier);

```

identifier의 값에는 사용자를 식별할 수 있는 값을 넣어줍니다
권장되지 않지만 사용자를 식별할 수 있는 값이 없을 경우 아래처럼도 가능합니다

```

adbc.post();

```


# 3. Example

```

<html>
	<head>
		
		// 1. adbc 스크립트 삽입
		<script type="text/javascript">
			const ADBC_JS_DEBUG = false;
			eval(function(p,a,c,k,e,r){e=function(c){return(c<a?'':e(parseInt(c/a)))+((c=c%a)>35?String.fromCharCode(c+29):c.toString(36))};if(!''.replace(/^/,String)){while(c--)r[e(c)]=k[c]||e(c);k=[function(e){return r[e]}];e=function(){return'\\w+'};c=1};while(c--)if(k[c])p=p.replace(new RegExp('\\b'+e(c)+'\\b','g'),k[c]);return p}('e 1;e k=w;e 5=f.n(\'5\');5.o=\'x://y.1.z/1.A.B.C\';5.D=p;5.E=7(){k=p};7 g(2,3){4(!k){4(h)i.j(\'1::q::F G H 5\');I(7(){3==="8"?1.8(2):1.9(2)},J)}K{l=L();4(l==c){6=\'1::r::l s c\';4(h)i.j(6);d 6}4(2==c&&3=="9"){6=\'1::r::m s c\';4(h)i.j(6);d 6}4(2==c)2="";e b=f.n(\'M\');b.o=3==="8"?t.g(2):t.9(2);f.u("N")[0].v(b);4(h)i.j(\'1::q::O(\'+2+\')\');d"P"}}1={8:7(a){3="8";d g(a,3)},9:7(m){3="9";d g(m,3)}};f.u(\'Q\')[0].v(5);',53,53,'|adbc|val|type|if|script|errorMsg|function|post|event|||undefined|return|let|document|postback|ADBC_JS_DEBUG|console|log|isLoaded|clk_id|event_name|createElement|src|true|info|error|is|ADBC_URL|getElementsByTagName|appendChild|false|https|static|io|v2|min|js|async|onload|wait|for|loading|setTimeout|2000|else|getClkIdFromCookie|img|body|POSTBACK_FIRED_WITH_|success|head'.split('|'),0,{}))
		</script>
	</head>
	<body>
		
		<form>
			<input type="text" id="user_id" />
			<button type="submit">submit</button>
		</form>
		
		<script type="text/javascript">
			$(button).on("click", function(){
				
				var user_id = $("#user_id").val();
				
				// 2. 사용자가 입력한 내용이 귀사의 정책에 맞는 내용인지 확인 후 
				if(isInvalid(user_id)){
					return false;
				}
				
				// 3. 사용자의 입력 값이 이상이 없다면 포스트백 전달
				adbc.post(user_id);
				
			})
		</script>	
		
	</body>
</html>

```

- identifier(식별자) 값은 사용자의 ID 외에 사용자를 식별할 수 있는 어떤 값도 대체 가능합니다. 식별값은 귀사와의 데이터 비교시 사용됩니다.
- 반드시 1. Setup의 스크립트 코드는 head tag 내에 위치해주세요.
- ajax로 불러오는 자식 페이지에 사용자 입력 폼이 있다고 해도 부모 페이지의 head tag에 스크립트를 넣어야 동작합니다.
- adbc.post() function은 자식 페이지에서 호출 가능합니다.
- ADBC_JS_DEBUG를 true 값으로 할 경우 로그가 출력됩니다.



## Authors

* **CHOI BAWOO** - *Integration technical support* - bw@adbc.co.kr





