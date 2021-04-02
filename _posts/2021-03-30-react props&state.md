---
layout: post
title:  "React Props와 State"
date:   2021-03-30T15:25:52-05:00
author: codeblue25
categories: React
---

[누구든지 하는 리액트](https://www.inflearn.com/course/react-velopert/questions?page=2)와 [생활코딩 React](https://www.youtube.com/watch?v=XMb0w3KMw00&list=PLuHgQVnccGMCRv6f8H9K5Xwsdyg4sFSdi)를 바탕으로 정리한 글입니다.<br />

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

<h3>State란?</h3>

* Props가 컴포넌트를 사용하는 입장에서 중요한 정보라면 State는 **컴포넌트 내부 구현**에 필요한 데이터들입니다.
<br />

<h4>State 사용하기1</h4>

* State를 사용하기 위해서는 먼저 값을 초기화 해야합니다.
  * 컴포넌트를 실행할 때, render()함수보다 먼저 실행되면서 컴포넌트를 초기화 시켜주고 싶은 코드는 constructor()함수 안에  `this.state = {}` 로 작성합니다.
  * ```jsx
        class App extends Component {
        constructor(props) {
            super(props);
            }
        }
        ```
  * 부모 컴포넌트에서 초기화한 State값은 (import한) 자식 컴포넌트의 Props값으로 줄 수 있습니다.
* ```jsx
    import React, { Component } from "react";
    import Subject from "./Subject";
    
    class App extends Component {
        constructor(props) {
        super(props);
        this.state = {
            subject: {title: "WEB", sub: "This is WWW!"}
        }
        }
        render() {
        return (
            <div className = "App">
            <Subject 
                title = {this.state.subject.title}
                sub = {this.state.subject.sub}>
            </Subject>
            </div>
        );
        }
    }
    
    export default App;
    ```
* App(부모 컴포넌트)에서 subject 값으로 객체를 설정합니다. 
  * ```jsx
        this.state = {
            subject: {title: "WEB", sub: "This is WWW!"}
        }
        ```
* import한 Subject(자식 컴포넌트)는 App의 상태를 Props로 전달 받습니다. 
  * ```jsx
        <Subject 
            title = {this.state.subject.title}
            sub = {this.state.subject.sub}>
        </Subject>
        ```
* 따라서 **부모 컴포넌트의 상태를 (import한) 자식 컴포넌트에 전달할 수 있습니다.**
<br />

<h4>State 사용하기2</h4>

* ```jsx
    import React, { Component } from "react";
    import Subject from "./Toc";
    
    class App extends Component {
        constructor(props) {
        super(props);
        this.state = {
            content: [
            {id: 1, title: "HTML", desc: "HTML is for Markup"},
            {id: 2, title: "CSS", desc: "CSS is for Design"},
            {id: 3, title: "JavaScript", desc: "JavaScript is for Interactive"}
            ]
        }
        }
        render() {
        return (
            <div className = "App">
            <Toc data = {this.state.content}></Toc>
            </div>
        );
        }
    }
    
    export default App;
    ```
* 여러 개의 state값을 생성하고 싶을 땐 배열[]을 사용합니다.
  * ```jsx
        class App extends Component {
        constructor(props) {
            super(props);
            this.state = {
            content: [
                {id: 1, title: "HTML", desc: "HTML is for Markup"},
                {id: 2, title: "CSS", desc: "CSS is for Design"},
                {id: 3, title: "JavaScript", desc: "JavaScript is for Interactive"}
            ]
            }
        }
        ```
* import한 Toc(자식 컴포넌트)는 App의 상태를 data라는 Props로 전달 받습니다. 
  * ```jsx
        <Toc data = {this.state.content}></Toc>
        ```
* Toc컴포넌트 내부엔  `this.props.data`  값을 가지게 됩니다. 이를 이용해서 목록을 생성할 수 있습니다.
  * 이처럼(반복문을 통해) 여러 개의 목록(Elements)을 자동으로 생성할 경우엔, **각 항목들마다 (식별자 역할을 하는) key라는 props를 가지고 있어야 합니다.**
  * ```jsx
        import React, { Component } from "react";
        
        class Toc extends Component {
        render() {
            var lists = []
            var data = this.props.data;
            var i = 0;
            while(i<data.length){
            lists.push(<li key = {data[i].id}><a href = {"/content/" + data[i].id}>{data[i].title}</a></li>)
            i += 1;
            }
            return(
            <nav>
                <ul>
                {lists}
                </ul>
            </nav>
            );
        }
        }
        
        export default Toc;
        ```
* 결과적으로 만약 자식 컴포넌트의 data변경이 생기면, **부모 컴포넌트의 State값으로 제어**할 수 있게 됩니다.