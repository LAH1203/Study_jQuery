## Chain이란?
jQuery의 메소드들은 반환값으로 자기 자신을 반환해야 한다는 규칙을 갖고 있다. 이를 이용하면 한 번 선택한 대상에 대해서 연속적인 제어를 할 수 있다.
### 예제 1. jQuery를 이용해서 코딩하는 경우
```html
<html>
    <body>
        <a id="tutorial" href="http://jquery.com" target="_self">jQuery</a>
        <script type="text/javascript" src="https://ajax.googleapis.com/ajax/libs/jquery/1.6.2/jquery.min.js"></script>
        <script type="text/javascript">
            jQuery('#tutorial').attr('href', 'http://jquery.org').attr('target', '_blank').css('color', 'red');
        </script>
    </body>
</html>
```
### 예제 2. Javascript의 DOM을 이용해서 코딩하는 경우
```html
<html>
     <body>
         <a id="tutorial" href="http://jquery.com" target="_self">jQuery</a>
         <script type="text/javascript">
             var tutorial = document.getElementById('tutorial');
             tutorial.setAttribute('href', 'http://jquery.org');
             tutorial.setAttribute('target', '_blank');
             tutorial.style.color = 'red';
         </script>
     </body>
 </html>
 ```
 
 ## Chain의 장점
 - 코드가 간결해진다.
 - 사람의 언어와 유사해 사고의 자연스러운 과정과 일치한다.<sub>(체인이 이 점에서 많이 편리한 것 같다.)</sub>
 
 ## 탐색(Traversing)
 - chain의 대상을 바꿔서 체인을 계속 연장시킬 수 있는 방법
 - https://api.jquery.com/category/traversing/
 - (조금 오래되긴 했지만) [taeyo.net의 jQuery traverse 강좌](http://www.taeyo.net/columns/View.aspx?SEQ=375&PSEQ=29&IDX=1)
 - 너무 복잡한 chain은 오히려 코드의 가독성을 떨어뜨릴 수도 있기 때문에 적당량만 사용하는 것이 좋다.
 ### 예제 3. traversing을 이용하여 chain 안에서 대상을 움직이는 경우
 ```html
 <html>
    <body>
        <ul class="first">
            <li class="foo"> list item 1 </li>
            <li> list item 2 </li>
            <li class="bar"> list item 3 </li>
        </ul>
        <ul class="second">
            <li class="foo"> list item 1 </li>
            <li> list item 2 </li>
            <li class="bar"> list item 3 </li>
        </ul>
        <script type="text/javascript" src="https://ajax.googleapis.com/ajax/libs/jquery/1.6.2/jquery.min.js"></script>
        <script type="text/javascript">$('ul.first').find('.foo').css('background-color', 'red').end().find('.bar').css('background-color', 'green');</script>
    </body>
</html>
```
