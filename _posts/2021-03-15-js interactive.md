---
layout: post
title:  "JavaScript Interactive"
date:   2021-03-15T15:25:52-05:00
author: codeblue25
categories: JavaScript
---

<h1>1. 스크롤(Scroll) 이벤트</h1>

<h4>관련 속성, 메소드</h4>

1. `pageXOffset` ,  `pageYOffset`
2. `offsetTop` ,  `offsetLeft`
3. `getBoundingClientRect()`

<br/>

<h3>pageXOffset , pageYOffset</h3>

* 브라우저 크기에서 가로로, 세로로 **얼마나 스크롤 되었는지**를 'px'로 나타내는 속성입니다.
  * 이 때 기준은 **좌측, 상단**입니다.

<br/>

<h3>offsetTop , offsetLeft</h3>

* 브라우저에서 **오브젝트의 위치**를 'px'로 나타내는 속성입니다.
  * 이 때 기준은 **좌측, 상단**입니다.
  * 단, **처음 위치**만을 값으로 취합니다. 따라서 스크롤함에 따라 변화를 감지해서 값이 변하지 않습니다. 

<br/>

<h3>getBoundingClientRect()</h3>

* 브라우저에서 **오브젝트의 위치와 크기**를 'px'로 나타내는 객체를 반환하는 **메소드**입니다.
  * 이 때 기준은 **좌측, 상단**입니다.
* 가로 상 위치는  `getBoundingClientRect().left`  , 세로 상 위치는 `getBoundingClientRect().top`으로 알 수 있습니다.
  * 스크롤 함에 따라 오브젝트를 기준으로 위치 변화를 감지해서 값이 변합니다.
    * **오브젝트가** 브라우저의 상단 **아래**에 있을 땐  `getBoundingClientRect().top`  > 0
    * 브라우저의 상단에 **닿을 땐**  `getBoundingClientRect().top`  = 0
    * 브라우저의 상단 **위**에 있을 땐  `getBoundingClientRect().top`  < 0

---

<h1>2. 타이밍 이벤트</h1>

<h4>관련 속성, 메소드</h4>

1. `setTimeout`
2. `setInterval`
3. `requestAnimationFrame`

<br/>

<h3>setTimeout()</h3>

* 의도적으로 함수 실행 **시간을 지연**시키는 함수입니다.
* 1번만 실행됩니다.
* 첫 번째 매개변수는 함수이고 두 번째 매개변수는 초(이 때 단위는 ms)입니다. (예시  :  `setTimeout(function(){}, 3000)` )
* 실행 시키면 (보통) **1씩 숫자값을 리턴**합니다. 이 값을 `clearTimeout()` 매개변수로 이용하면 `setTimeout()` 을 취소시킬 수 있습니다.
* ```javascript
  let timeId = setTimeout(sample, 3000);
  clearTimeout(timeId);
  /*3초 경과되기 전에 함수 실행을 취소시켰음*/
  ```

<br/>

<h3>setInterval()</h3>

* 함수 실행을 일정 **시간 간격으로 반복**하는 함수입니다.
* 첫 번째 매개변수는 함수이고 두 번째 매개변수는 초(이 때 단위는 ms)입니다.
* 실행 시키면 리턴하는 숫자값을 `clearInterval()` 매개변수로 이용하면 `setInterval()` 을 취소시킬 수 있습니다.

<br/>

<h3>requestAnimationFrame()</h3>

* `setInterval()` 을 보완한 함수로써, 프레임 누락이 없고 더 매끄럽게 함수를 실행합니다. (초당 60회 반복)
* 1번만 실행됩니다. 단, **재귀**적으로 호출하면  `setInterval()` 처럼 사용할 수 있습니다.
* ```javascript
  function sample(){
      console.log("sample!");
      let timeId = requestAnimationFrame(sample); /*2. requestAnimationFrame 함수를 실행시키는데,
      실행시 호출하는 함수가 sample함수*/
  }
  sample(); /*1. sample 함수 호출*/ /*3. 다시 sample 함수 호출을 반복*/
  ```
* 실행 시키면 리턴하는 숫자값을 `cancelAnimationFrame()` 매개변수로 이용하면 `requestAnimationFrame()` 을 취소시킬 수 있습니다.
* 또는 조건문과 함께 사용해서 제어할 수 있습니다.
* ```javascript
  let n = 0;
  function counter(){
      n++;
      if(n > 200){
          return;
      }
      console.log(n);
      let timeId = requestAnimationFrame(counter);
  }
  counter();
  ```