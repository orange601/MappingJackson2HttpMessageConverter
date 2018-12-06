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

