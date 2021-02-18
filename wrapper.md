## 레퍼(wrapper)란?
### jQuery(엘리먼트 오브젝트 | 'CSS스타일 선택자')
jQuery()부분이 레퍼, 인자로 전달된 요소들에 jQuery의 기능성을 부가해서 반환

## 레퍼의 안전한 사용
$(엘리먼트)와 jQuery(엘리먼트)는 같은 의미이지만 $를 사용하는 다른 라이브러리들과의 충돌을 고려하여 다음과 같은 방법을 사용한다.
```html
<script type="text/javascript">
  // $ 대신 jQuery를 사용
  jQuery('body').html('hello world');
</script>
```
```html
<script type="text/javascript">
  // $를 함수의 지역변수로 선언해서 외부에 있을지도 모르는 타 라이브러리의 $와의 충돌 예방
  (function($) {
    $('body').html('hello world');
  }) (jQuery)
</script>
```

## 제어 대상을 지정하는 방법
- jQuery(selector, [context])
- jQuery(element)
### 예제 1. jQuery(selector, [context])
```html
<html>
  <body>
    <ul>
      <li>test2</li>
    </ul>
    <ul class="foo">
      <li>test</li>
    </ul>
    <script type="text/javascript" src="https://ajax.googleapis.com/ajax/libs/jquery/1.6.2/jquery.min.js"></script>
    <script type="text/javascript">
      (function($) {
        $('ul.foo').click(function() {
          $('li', this).css('background-color','red');
        });
      }) (jQuery)
    </script>
  </body>
</html>
```
[코드](https://github.com/LAH1203/Study_jQuery/blob/main/%EC%A0%9C%EC%96%B4%EB%8C%80%EC%83%81%EC%A7%80%EC%A0%95_%EC%98%88%EC%A0%9C1.html)

### 예제 2. jQuery(element)
```html
<html>
  <body>
    <script type="text/javascript" src="https://ajax.googleapis.com/ajax/libs/jquery/1.6.2/jquery.min.js"></script>
    <script type="text/javascript">
      jQuery(document.body).css( "background-color", "black" )
    </script>
  </body>
</html>
```
[코드](https://github.com/LAH1203/Study_jQuery/blob/main/%EC%A0%9C%EC%96%B4%EB%8C%80%EC%83%81%EC%A7%80%EC%A0%95_%EC%98%88%EC%A0%9C2.html)
