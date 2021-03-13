---
layout: post
title:  "CSS Animation"
date:   2021-02-08T15:25:52-05:00
author: codeblue25
categories: CSS
---

<h3>animation이란?</h3>



<h4>name과 @keyframes</h4>

* `animation-name` : 함수처럼 animation의 이름을 만들고 적용하고 싶은 곳에 씁니다.
* `@keyframes` : 애니메이션의 내용을 적습니다.
* ```css
  @keyframes /*name*/{
      from{
          /*시작 부분에 적용할 CSS 속성*/
      }
      to{
          /*끝 부분에 적용할 CSS 속성*/
      }
  }
  ```
* `@keyframes`의 로직은 (from to 대신) 0% 100%로도 쓸 수 있고, 더욱 디테일한 컨드롤을 할 수 있습니다.


<h4>duration</h4>

* animation이 재생되는 시간을 정합니다.
* s(1초) 또는 ms(0.001초) 단위를 사용합니다.
* ```css
  animation-duration: 1s;
  ```


<h4>timing-function</h4>

* 변화하는 속도를 정합니다. (생략 가능합니다.)
* 대표적으로 ease-in, ease-out, ease-in-out, cubic-bezier()이 있습니다.
* ```css
  animation-timing-function: linear;
  ```


<h4>delay</h4>

* 변화를 지연시킵니다. (생략 가능합니다.)
* s(1초) 또는 ms(0.001초) 단위와 사용하며, 해당 시간 뒤에 animation이 실행됩니다.
* ```css
  animation-delay: 0s;
  ``` 


<h4>iteration-count</h4>

* ''되풀이 하다''는 뜻으로, animaion이 실행되는 횟수를 정합니다.
* ```css
  animation-iteration-count: infinite; /*무한으로 실행*/
  ```


<h4>direction</h4>

* animation이 진행되는 방향을 뜻합니다. (생략 가능합니다.)
* ```css
  animation-direction: alternate; /*번갈아가며 실행*/
  animation-direction: reverse; /*시작점과 끝점이 바뀌어서 실행*/
  ```


<h4>fill-mode</h4>

* ```css
  animation-fill-mode: forwards; /*끝점에 머물러 있음*/
  ```


<h4>play-state</h4>

* animation의 진행 상태를 뜻합니다. 기본 값은 `running`입니다.
* ```css
  animation-play-state: paused /*ani 실행을 정지*/
  ```

<h3>+) Animation Event</h3>

* `animationend` ,  `animationstart`
  * 애니메이션이 끝날 때, 시작할 때 이벤트가 실행됩니다.
* `animationiteration`
  * 애니메이션이 반복될 때마다 이벤트가 실행됩니다.
* <iframe height="265" style="width: 100%;" scrolling="no" title="animation event" src="https://codepen.io/codeblue25/embed/zYoeygj?height=265&theme-id=dark&default-tab=js,result" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href='https://codepen.io/codeblue25/pen/zYoeygj'>animation event</a> by CHOI SUN YOUNG
  (<a href='https://codepen.io/codeblue25'>@codeblue25</a>) on <a href='https://codepen.io'>CodePen</a>.