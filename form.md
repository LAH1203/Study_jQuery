## 폼(form)
- 서버로 데이터를 전송하기 위한 수단
- Query는 폼을 제어하는데 필요한 이벤트와 메소드를 제공
- [jQuery 폼 API 문서](https://api.jquery.com/category/forms/)
### 예제1. .focus(), .blur(), .change(), .select()
- 위의 함수들은 밑의 예제를 직접 해보면 쉽게 파악할 수 있다.
```html
<!DOCTYPE html>
<html>
    <head>
        <style>
            span {
            }
        </style>
        <script src="http://code.jquery.com/jquery-latest.js"></script>
    </head>
    <body>
        <p>
            <input type="text" />
            <span></span>
        </p>
        <script>
            $("input").focus( function () {
                $(this).next("span").html('focus');
            }).blur( function() {
                $(this).next("span").html('blur');
            }).change(function(e){
                alert('change!! '+$(e.target).val());
            }).select(function(){
                $(this).next('span').html('select');
            });
        </script>
    </body>
</html>
```

### 예제2. .submit(), .val()
- submit()은 말그대로 '전송'이다. 내가 입력한 정보를 서버를 통해 다른 곳에 보내고 싶을 때 사용할 수 있다.
- val()은 이전에 했던 [엘리먼트 제어](https://github.com/LAH1203/Study_jQuery/blob/main/%EC%97%98%EB%A6%AC%EB%A8%BC%ED%8A%B8%20%EC%A0%9C%EC%96%B4.md)에서 봤다시피 값을 읽어오는 역할을 한다.
```html
<!DOCTYPE html>
<html>
    <head>
        <style>
            p {
                margin:0;
                color:blue;
            }
            div, p {
                margin-left:10px;
            }
            span {
                color:red;
            }
        </style>
        <script src="http://code.jquery.com/jquery-latest.js"></script>
    </head>
    <body>
        <p>
            Type 'correct' to validate.
        </p>
        <form action="javascript:alert('success!');">
            <div>
                <input type="text" />
 
                <input type="submit" />
            </div>
        </form>
        <span></span>
        <script>
            $("form").submit( function() {
                if ($("input:first").val() == "correct") {
                    $("span").text("Validated...").show();
                    return true;
                }
                $("span").text("Not valid!").show().fadeOut(1000);
                return false;
            });
        </script>
    </body>
</html>
```
