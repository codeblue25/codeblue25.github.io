---
layout: post
title: "Numpy 배열의 차원"
date: 2021-06-22T15:25:52-05:00
author: codeblue25
categories: Data&AI
---

<h3>Numpy 배열의 확장, 쌓기, 쪼개기</h3>

<h4>배열의 차원 확장</h4>

- 방법1
  - `arr[np.newaxis, :]` 행 방향으로 차원추가
  - `arr[:, np.newaxis]` 열 방향으로 차원 추가
- 방법2
  - `np.expand_dims(arr, axis = 0)` 행 방향으로 차원추가
  - `np.expand_dims(arr, axis = 1)` 열 방향으로 차원 추가
- 대괄호 겹이 많아진다 = 차원이 추가되었다

<h4>배열의 차원 쌓기</h4>

- 방법1
  - `np.hstack` 가로 방향으로 쌓기
  - `np.vstack` 세로 방향으로 쌓기
- 방법2
  - `np.concatenate(arr, axis = 1)` 가로 방향으로 쌓기
  - `np.concatenate(arr, axis = 0)` 세로 방향으로 쌓기

<h4>배열의 차원 쪼개기</h4>

- 쪼개기1: 몇등분으로 쪼갤 것인지를 지정할 수 있다.

  - `np.hsplit(arr, 2)` 가로 방향으로 2등분 쪼개기
  - `np.vsplit(arr, 3)` 세로 방향으로 3등분 쪼개기

- 쪼개기2: 쪼개는 지점을 지정할 수 있다.
  - `np.hsplit(arr,(2,5))` 가로 방향으로 2번째, 5번째 열에서 쪼개기
  - `np.vsplit(arr,(4, ))` 세로 방향으로 4번째 행에서 쪼개기
