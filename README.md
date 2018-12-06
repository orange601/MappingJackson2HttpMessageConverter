# MappingJackson2HttpMessageConverter란 뭘까?

ajax 통신시 자동으로 json 처리

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

만약 MappingJackson2HttpMessageConverter을 하지 않으면 

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

[출처] http://yookeun.github.io/java/2014/11/21/spring-json/


