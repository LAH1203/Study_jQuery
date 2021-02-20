## 이벤트(event)란?
- 시스템에서 일어나는 사건을 의미
- Javascript나 jQuery에게 이벤트란, 브라우저에서 일어나는 사건을 의미
  - 클릭, 마우스 이동, 타이핑, 페이지 로딩 등
- 이벤트가 발생했을 때 작동할 로직을 시스템에게 미리 알려두면 해당 이벤트 발생 시 시스템이 그 로직을 호출
- 이벤트에 대한 기본적인 내용은 자바스크립트의 이벤트를 참고하면 좋다.

## jQuery의 이벤트
- 크로스브라우징의 문제를 해결해줌
- bind로 이벤트 핸들러를 설치하고, unbind로 제거([예제1](#예제1-bind-unbind-trigger를-이용한-이벤트의-설치-제거-호출))
  - 강의가 예전 버전이라 최근 버전에서는 bind, unbind를 제공하지 않고, on, off를 제공한다고 한다.([예제1 바뀐 버전](#예제1-바뀐-버전))
- 이벤트 헬퍼([예제2](#예제2-이벤트-헬퍼))
  - trigger로 이벤트 핸들러를 강제로 실행
  - click, ready와 같이 다양한 이벤트 헬퍼(helper)를 제공
- live를 이용하면 현재 존재하지 않는 엘리먼트에 이벤트 핸들러를 설치할 수 있음([예제3](#예제3-live를-이용하면-존재하지-않는-엘리먼트에-대해서-이벤트를-설치할-수-있다))
  - bind와 마찬가지로 현재는 live 대신 통합 메소드인 on을 사용한다고 한다. 바뀐 버전은 [예제1 바뀐 버전](#예제1-바뀐-버전)과 동일하다.

### 예제1. bind, unbind, trigger를 이용한 이벤트의 설치, 제거, 호출
```html
<html>
    <head>
        <script type="text/javascript" src="https://ajax.googleapis.com/ajax/libs/jquery/1.6.2/jquery.min.js"></script>
        <script type="text/javascript">
            function clickHandler(e){
                alert('thank you');
            }
            $(document).bind('ready', function(){
                 $('#click_me').bind('click', clickHandler);
                 $('#remove_event').bind('click', function(e){
                     $('#click_me').unbind('click', clickHandler);
                 });
                 $('#trigger_event').bind('click', function(e){
                     $('#click_me').trigger('click');
                 });
             })
        </script>
    </head>
    <body>
        <input id="click_me" type="button" value="click me" />
        <input id="remove_event" type="button" value="unbind" />
        <input id="trigger_event" type="button" value="trigger" />
    </body>
</html>
```

### 예제1 바뀐 버전
```html
<html>
    <head>
        <script type="text/javascript" src="https://code.jquery.com/jquery-3.5.1.min.js"></script>
        <script type="text/javascript">
            function clickHandler(e){
                alert('thank you');
            }
            $(document).ready(function(){
                 $('#click_me').on('click', clickHandler);
                 $('#remove_event').on('click', function(e){
                     $('#click_me').off('click', clickHandler);
                 });
                 $('#trigger_event').on('click', function(e){
                     $('#click_me').trigger('click');
                 });
             });
        </script>
    </head>
    <body>
        <input id="click_me" type="button" value="click me" />
        <input id="remove_event" type="button" value="unbind" />
        <input id="trigger_event" type="button" value="trigger" />
    </body>
</html>
```

### 예제2. 이벤트 헬퍼
```html
<html>
    <head>
        <script type="text/javascript" src="https://code.jquery.com/jquery-3.5.1.min.js"></script>
        <script type="text/javascript">
            function clickHandler(e){
                alert('thank you');
            }
            $(document).ready(function(){
                 $('#click_me').click(clickHandler);
                 $('#remove_event').click(function(e){
                     $('#click_me').off('click', clickHandler);
                 });
                 $('#trigger_event').click(function(e){
                     $('#click_me').trigger('click');
                 });
             })
        </script>
    </head>
    <body>
        <input id="click_me" type="button" value="click me" />
        <input id="remove_event" type="button" value="unbind" />
        <input id="trigger_event" type="button" value="trigger" />
    </body>
</html>
```

### 예제3. live를 이용하면 존재하지 않는 엘리먼트에 대해서 이벤트를 설치할 수 있다.
```html
<html>
    <head>
        <script type="text/javascript" src="https://ajax.googleapis.com/ajax/libs/jquery/1.6.2/jquery.min.js"></script>
        <script type="text/javascript">
            function clickHandler(e) {
                alert('thank you');
            }
            $('#click_me').live('click', clickHandler);
            $('#remove_event').live('click', function(e) {
                $('#click_me').die('click', clickHandler);
            });
            $('#trigger_event').live('click', function(e) {
                $('#click_me').trigger('click');
            });
        </script>
    </head>
    <body>
        <input id="click_me" type="button" value="click me" />
    <input id="remove_event" type="button" value="unbind" />
    <input id="trigger_event" type="button" value="trigger" />
    </body>
</html>
```
