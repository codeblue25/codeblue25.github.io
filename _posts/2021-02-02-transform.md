---
layout: post
title:  "CSS Transform"
date:   2021-02-02T15:25:52-05:00
author: codeblue25
categories: CSS
---

<h3>transform이란?</h3>

* 2차원 또는 3차원 공간에서 elements를 변형시킬 수 있습니다.
* 대표적으로 `scale()` `translate()` `rotate()` `skew()` 함수가 있습니다.
* **default 기준점은 elements 중앙입니다.** `transform-origin`으로 기준점을 바꿀 수 있습니다.
* 변형되기 전의 위치는 변하지 않기 때문에, **다른 elements에 영향을 미치지 않습니다.** <br />



<h4>scale(N)</h4>

* N만큼 배율로 사이즈를 조절합니다. (예: scale(2)는 사이즈가 두 배로 커집니다.)
* `scale(x, y)`로 쓸 경우, width값은 x만큼, height는 y만큼 사이즈를 조절합니다.
* <iframe height="265" style="width: 100%;" scrolling="no" title="LYbGVGy" src="https://codepen.io/codeblue25/embed/LYbGVGy?height=265&theme-id=dark&default-tab=html,result" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href='https://codepen.io/codeblue25/pen/LYbGVGy'>LYbGVGy</a> by CHOI SUN YOUNG
  (<a href='https://codepen.io/codeblue25'>@codeblue25</a>) on <a href='https://codepen.io'>CodePen</a>.


<h4>translate(x, y)</h4>

* x, y 값만큼 x축, y축 이동합니다.
* x 또는 y에만 값을 주고 싶을 땐 `translateX()` 또는 `translateY()`로 씁니다.
* <iframe height="265" style="width: 100%;" scrolling="no" title="bGBEdeO" src="https://codepen.io/codeblue25/embed/bGBEdeO?height=265&theme-id=dark&default-tab=css,result" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href='https://codepen.io/codeblue25/pen/bGBEdeO'>bGBEdeO</a> by CHOI SUN YOUNG
  (<a href='https://codepen.io/codeblue25'>@codeblue25</a>) on <a href='https://codepen.io'>CodePen</a>.
  

<h4>rotate(Ndeg)</h4>

* N만큼 각도로 회전합니다.
* deg 단위를 붙여서 사용합니다. (예: rotate(45deg)는 45도 회전합니다.)
* <iframe height="265" style="width: 100%;" scrolling="no" title="MWbKwbY" src="https://codepen.io/codeblue25/embed/MWbKwbY?height=265&theme-id=dark&default-tab=css,result" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href='https://codepen.io/codeblue25/pen/MWbKwbY'>MWbKwbY</a> by CHOI SUN YOUNG
  (<a href='https://codepen.io/codeblue25'>@codeblue25</a>) on <a href='https://codepen.io'>CodePen</a>.


<h4>skew(Ndeg)</h4>

* N만큼 각도로 비틉니다.
* 수직 방향으로 비틀고 싶을 땐 `skewY()`를 사용합니다.
* N값이 음수일 땐 반대 방향으로 비틀 수 있습니다.
* <iframe height="265" style="width: 100%;" scrolling="no" title="rNWxVjx" src="https://codepen.io/codeblue25/embed/rNWxVjx?height=265&theme-id=dark&default-tab=css,result" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href='https://codepen.io/codeblue25/pen/rNWxVjx'>rNWxVjx</a> by CHOI SUN YOUNG
  (<a href='https://codepen.io/codeblue25'>@codeblue25</a>) on <a href='https://codepen.io'>CodePen</a>.


<h4>transform-origin</h4>

* defualt로 중앙에 있는 기준점을 바꿀 수 있습니다.
* 깂으로 left, right, top, bottom 키워드를 이용할 수 있습니다.
* 숫자%로 값을 줄 수도 있습니다. 이 때 0% 0%는 좌측 상단(left top)을 뜻합니다.
* <iframe height="265" style="width: 100%;" scrolling="no" title="jOVPaaY" src="https://codepen.io/codeblue25/embed/jOVPaaY?height=265&theme-id=dark&default-tab=css,result" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href='https://codepen.io/codeblue25/pen/jOVPaaY'>jOVPaaY</a> by CHOI SUN YOUNG
  (<a href='https://codepen.io/codeblue25'>@codeblue25</a>) on <a href='https://codepen.io'>CodePen</a>.