# MappingJackson2HttpMessageConverter란 뭘까?

[출처] http://yookeun.github.io/java/2014/11/21/spring-json/

ajax 통신시 spring이 자동으로 json 처리

````javascript
var param = {
    "name": "홍길동",
    "age": 22    
};

$.ajax({
    type: 'POST',
    dataType: 'JSON',
    data: param,
    url:  'test/testing/select',
    error: function() {
    	//에러처리
    },                
    success: function(returnJSON) {
    	//성공처리
	}    
}):
````

만약 MappingJackson2HttpMessageConverter을 설정 하지 않으면 수동으로 변환 후 호출하면된다.

````javascript
// JavaScript Code
var param = {
    "name": "홍길동",
    "age": 22    
};

$.ajax({
    type: 'POST',
    dataType: 'JSON',
    data:  JSON.stringify(search),
    contentType:"application/json; charset=UTF-8",
    url:  'test/testing/select',
    error: function() {
        //에러처리
    },                
    success: function(returnJSON) {
    	//성공처리
	}    
}):
````


jackson-core Dependency 추가

xml 설정 like this..
````xml
	<annotation-driven>
		<message-converters register-defaults="true">
			<beans:bean class="org.springframework.http.converter.json.MappingJackson2HttpMessageConverter">
				<beans:property name="supportedMediaTypes" value="text/plain;charset=utf-8" />
			</beans:bean>
		</message-converters>
	</annotation-driven>
````




설명

출처: http://victorydntmd.tistory.com/172 [victolee]

**MessageConverter란?**

HTTP 프로토콜에서 메시지는 문자열을 통해 전송 됩니다.

MessageConvert는 HTTP 통신에서 일반 문자열이 아닌 XML 이나 JSON으로 통신하기 위해 사용됩니다.

**JSON을 전달하는 이유?**

브라우저에서 XML을 조작하는 것은 JS인데 굳이 XML으로 전달하여 다시 JS로 파싱 할 필요가 없음을 깨닫게 되었습니다.

그래서 JS 객체 형식으로 전달하는 JSON을 사용하게 되었죠.

브라우저 내에 XMLHttpRequest라는 내장 브라우저가 존재하여 Ajax 통신이 가능한데, 

XML로 데이터를 전송하는 것은 비효율적이므로 JSON으로 데이터를 주고 받는다





