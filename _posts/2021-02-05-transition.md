---
layout: post
title:  "CSS Transition"
date:   2021-02-05T15:25:52-05:00
author: codeblue25
categories: CSS
---

<h3>transition이란?</h3>

* 값이 **숫자**로 표현되는 속성에 변화가 있을 때, 중간과정을 애니메이션으로 만들어줍니다.
* transition을 사용하기 위해서는 `property` `duration` `time-function` `delay`를 선언해야합니다. 
* transform과 함께 사용하면 다양한 애니메이션 표현이 가능합니다.


<h4>property</h4>

* 어떤 CSS 속성에 변화를 줄 것인지 정합니다. (예: font-size, background-color)
* 두 가지 이상의 속성에 변화를 주고 싶을 땐 all이라고 선언합니다. 또는 콤마(,)로 개별 선언이 가능합니다.
* ```css
  transition: font-size 1s ease-out, background-color 2s ease-in-out 1s;
  ```

  
<h4>duration</h4>

* 재생 시간(경과 시간)을 뜻합니다.
* s(1초) 또는 ms(0.001초) 단위를 사용합니다.


<h4>time-function</h4>

* 변화하는 속도를 정합니다. (생략 가능합니다.)
* 대표적으로 ease-in, ease-out, ease-in-out, cubic-bezier()이 있습니다.

  
<h4>delay</h4>

* 변화를 지연시킵니다. (생략 가능합니다.)
* s(1초) 또는 ms(0.001초) 단위와 사용하며, 해당 시간 뒤에 변화가 생깁니다.

<br />
<iframe height="265" style="width: 100%;" scrolling="no" title="eYBJVpY" src="https://codepen.io/codeblue25/embed/eYBJVpY?height=265&theme-id=dark&default-tab=css,result" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href='https://codepen.io/codeblue25/pen/eYBJVpY'>eYBJVpY</a> by CHOI SUN YOUNG
  (<a href='https://codepen.io/codeblue25'>@codeblue25</a>) on <a href='https://codepen.io'>CodePen</a>.