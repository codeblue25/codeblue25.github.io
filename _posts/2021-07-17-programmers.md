---
layout: post
title: "[프로그래머스 / Python] Level 2 기능개발"
date: 2021-07-17T15:25:52-05:00
author: codeblue25
categories: Algorithm
---

<h2>문제</h2>

프로그래머스 팀에서는 기능 개선 작업을 수행 중입니다. 각 기능은 진도가 100%일 때 서비스에 반영할 수 있습니다.<br />
또, 각 기능의 개발속도는 모두 다르기 때문에 뒤에 있는 기능이 앞에 있는 기능보다 먼저 개발될 수 있고, 이때 뒤에 있는 기능은 앞에 있는 기능이 배포될 때 함께 배포됩니다.<br />
먼저 배포되어야 하는 순서대로 작업의 진도가 적힌 정수 배열 progresses와 각 작업의 개발 속도가 적힌 정수 배열 speeds가 주어질 때 각 배포마다 몇 개의 기능이 배포되는지를 return 하도록 solution 함수를 완성하세요.

<h2>제한사항</h2>

- 작업의 개수(progresses, speeds배열의 길이)는 100개 이하입니다.
- 작업 진도는 100 미만의 자연수입니다.
- 작업 속도는 100 이하의 자연수입니다.
- 배포는 하루에 한 번만 할 수 있으며, 하루의 끝에 이루어진다고 가정합니다. 예를 들어 진도율이 95%인 작업의 개발 속도가 하루에 4%라면 배포는 - 2일 뒤에 이루어집니다.

<h3>🔹나의 풀이</h3>

```python
def solution(progresses, speeds):
    lst = []
    for i in range(len(progresses)):
        count = 1
        while True:
            if progresses[i] + speeds[i] >= 100:
                break
            else:
                count += 1
                progresses[i] += speeds[i]
        lst.append(count)

    stage = []
    counts = 0
    answer = []
    for i in lst:
        stage.append(i)
        if len(stage) == 1:
            counts += 1

        elif stage[0] >= stage[1]:
            counts += 1
            stage.pop()

        elif stage[0] < stage[1]:
            answer.append(counts)
            stage.remove(stage[0])
            counts = 1
    answer.append(counts)

    return answer
```
