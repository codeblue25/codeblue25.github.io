---
layout: post
title:  "React Props와 State"
date:   2021-03-30T15:25:52-05:00
author: codeblue25
categories: React
---

[누구든지 하는 리액트: 초심자를 위한 react 핵심 강좌](https://www.inflearn.com/course/react-velopert/questions?page=2)를 바탕으로 정리한 글입니다.<br />

<h3>Props란?</h3>

* 부모 컴포넌트가 자식 컴포넌트에게 **값을 전달**할 때 사용합니다.
* HTML의 속성처럼 **JSX의 속성**으로 사용합니다. (속성(Propertis)의 줄임말)
* 컴포넌트 render할 때 특정 값을 설정해주는 방식입니다.
<br />

<h4>예시 : 자식 컴포넌트 만들기</h4>

* ```jsx
    import React, { Component } from "react";

    class Subject extends Component {
        render() {
        return (
            <header>
            <h1>{this.props.title}</h1>
            {this.props.sub}
            </header>
        );
        }
    }

    export default Subject;
    ```
* Subject 라는 자식 컴포넌트를 생성합니다.
* Subject 컴포넌트 내에서 `this.props.` 키워드를 통해 h1태그의 title 속성과 sub 속성을 지정했습니다.
<br />

<h4>예시 : 부모 컴포넌트 만들기</h4>

* ```jsx
    import React, { Component } from "react";
    import Subject from "./Subject";

    class App extends Component {
    render() {
        return (
        <div className = "App">
            <Subject title = "WEB" sub = "world wide web!"></Subject>
            <Subject title = "React" sub = "for UI!"></Subject>
        </div>
        );
        }
    }

    export default App;
    ```
* App 이라는 부모 컴포넌트에 Subject 자식 컴포넌트를 import합니다.
* App 컴포넌트 내에서 값을 작성함으로서 Props를 전달합니다.

-----