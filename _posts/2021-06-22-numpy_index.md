---
layout: post
title: "Numpy 배열의 속성과 인덱싱"
date: 2021-06-22T15:25:52-05:00
author: codeblue25
categories: Data&AI
---

<h4>Numpy 배열 속성</h4>

- `arr.size` : 원소의 개수
- `arr.shape` : 배열의 모양 -> (행, 열) 형식으로 출력
- `arr.ndim` : 배열 차원의 수
- ```python
  import numpy as np

  arr = np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9]])
  arr.size # 결과값: 9
  arr.shape # 결과값: (3, 3)
  arr.ndim # 결과값: 2
  ```

---

- `arr.reshape` : 배열의 모양을 바꿀 수 있다.
  - 배열의 모양을 지정할 때, 한 쪽이 공백(-1)이어도 자동으로 축의 크기를 유추하여 배열 모양 생성 가능하다.
  - reshape할 때 order 옵션으로 가로 세로 방향을 지정할 수 있다.
  - reshape해도 메모리 공간을 공유하는 동일 객체이기 때문에, copy본을 떠서 만들어야 독립된 객체를 생성한 것이다.
- ```python
  arr = np.arange(12)
  arr.reshape(2, 6)
  # 결과값: array([[ 0,  1,  2,  3,  4,  5],
  #               [ 6,  7,  8,  9, 10, 11]])

  arr = arr.reshape(3, -1)
  arr
  # 결과값: array([[ 0,  1,  2,  3],
  #       		[ 4,  5,  6,  7],
  #       		[ 8,  9, 10, 11]])

  arr = np.array([1, 2, 3, 4])
  arr.reshape((2,2),order='C')
  # 결과값: array([[2, 5],
  #       		[1, 3]])  -> 'C'는 가로 방향
  a.reshape((2,2),order='F')
  # 결과값: array([[2, 1],
  #       		[5, 3]])  -> 'F'는 세로 방향
  ```

---

<h4>fancy indexing</h4>

- 1차원 배열은 python의 list와 비슷해보인다.
- ```python
  arr = np.array([1, 2, 3, 4, 5])
  a[2] # 결과값: 3
  a[-1] # 결과값: 5
  a[:] # 결과값: array([1, 2, 3, 4, 5])
  ```
- 2차원 이상의 배열도 슬라이싱 가능하다.
  - 슬라이싱 기본: [x:y] x**이상**, y**미만**
- ```python
  arr = np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9]])
  arr
  # 결과값: array([[1, 2, 3],
  #       		[4, 5, 6],
  #       		[7, 8, 9]])
  ```

- ```python
  arr[1]
  # 결과값: array([4, 5, 6]) -> 1번째 행 반환
  arr[:2]
  # 결과값: array([[1, 2, 3],
  #       		[4, 5, 6]]) -> 0이상 2미만 행 반환

  arr[[0, 2]]
  # 결과값: array([[1, 2, 3],
  #       		[7, 8, 9]]) -> 0번째, 2번째 행 반환
  arr[0, 2]
  # 결과값: 3 -> 0번째행, 2번째 열 원소 반환
  ```

---

<h4>bool 배열과 fancy indexing</h4>
