---
layout: post
title:  "JavaScript Interactive"
date:   2021-03-15T15:25:52-05:00
author: codeblue25
categories: JavaScript
---

<h1>스크롤(Scroll) 이벤트</h1>

<h2>관련 속성, 메소드</h2>

1. `pageXOffset` ,  `pageYOffset`
2. `offsetTop` ,  `offsetLeft`
3. `getBoundingClientRect()`

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

