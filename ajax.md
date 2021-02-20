## ajax란?
- Asynchronous Javascript and XML의 약자
- 자바스크립트를 이용해서 비동기식으로 서버와 통신하는데, 이 때 XML을 사용한다는 뜻이다.
  - 다만 꼭 XML일 필요는 없다. json을 더 많이 사용하기도 한다.
- [비동기식 vs 동기식](https://private.tistory.com/24)
  - 참고로, 내가 공부했던 Node.js는 기본적으로 비동기를 지원한다. 그러나 동기식을 사용해야 할 때가 있다. 그럴 때는 동기식을 지원하는 모듈을 설치하여 사용하였다. 내가 나중에 어떤 것을 사용할지는 모르겠지만, 그럴 때는 꼭 다른 방식을 지원하는지 알아보자! 안 그러면 Node.js를 처음 할 때처럼 왜 오류나는지도 모르고 엄청 헤맬 것 같다ㅜㅜ
  
## $.ajax(settings)
- jQuery를 이용한 ajax 통신의 가장 기본적인 API
- 주요 속성
  - data : 서버에 전송할 데이터. key/value 형식의 객체
  - dataType : 서버가 리턴하는 데이터 타입(xml, json, script, html)
  - type : 서버로 전송하는 데이터의 타입(GET, POST)
  - url : 데이터를 전송할 url
  - success : ajax 통신에 성공했을 때 호출될 이벤트 핸들러
<br>

***밑의 예제들은 말그대로 예제이고 제대로 작동은 되지 않으므로 어떤 식으로 사용되는지만 파악하도록 하자!***

### 예제1-1. 웹페이지
```html
<!DOCTYPE html>
<html>
    <head>
        <script src="http://code.jquery.com/jquery-latest.js"></script>
    </head>
    <body>
        <div id="result"></div>
        <input type="text" id="msg" />
        <input type="button" value="get result" id="getResult" />
        <script>
            $('#getResult').click( function() {
                $('#result').html('');
                $.ajax({
                    url:'http://opentutorials.org/example/jquery/example.jquery.ajax.php',
                    dataType:'json',
                    type:'POST',
                    data:{'msg':$('#msg').val()},
                    success:function(result){
                        if(result['result']==true){
                          $('#result').html(result['msg']);
                        }
                    }
                });
            })
        </script>
    </body>
</html>
```
### 예제1-2. 서버 쪽 로직
```
<?
echo json_encode(array('result'=>true, 'msg'=>$_REQUEST['msg']));
?>
```
