---
layout: post
title: "Matplotlib 기초 및 꾸미기"
date: 2021-06-23T15:25:52-05:00
author: codeblue25
categories: Data&AI
---

<h4>Matplotlib</h4>

- 리스트, 튜플, numpy 배열, pandas 시리즈 등등 **관계없이 사용 가능**
- ```python
  import matplotlib.pyplot as plt #서브모듈 pyplot을 plt라는 이름으로 import한다
  import numpy as np
  %matplotlib inline # 셀 안에서 시각화가 잘 보이게 해주는 magic command
  plt.show() # 시각화 결과값을 볼 수 있다.
  ```
- 종류엔 bar chart, histogram, pie chart, box plot, line plot, scatter plot 등이 있다.

<h4>Bar chart 막대그래프</h4>

- labling이 가능한 차트이기 때문에, label이랑 값이 매치되어야한다.
- 실험자료를 표현할 때
- ```python
  x = ["Q1", "Q2", "Q3", "Q4"]
  y = [502, 430, 276, 642]
  plt.show()
  ```
- 다양한 옵션이 있다.
- ```python
  plt.bar(x, y, color = "red") # 그래프 색
  plt.bar(x, y, alpha = 0.6) # 그래프 투명도 정도
  plt.title("Bar chart") # 그래프 제목
  plt.xlabel("Q") # x축 라벨
  plt.ylabel("P") # y축 라벨
  ```

<h4>Histogram 히스토그램</h4>

- 도수 분포를 나타낸 그림
- 하나의 수치형 확률 변수를 표현
- bins만큼 항목을 나누고 축적된 분포를 나타낸다.
- bins 막대 개수, density = False면 실제 도수, True면 상대 도수
- ```python
  x = np.random.randn(10000)
  plt.hist(x, bins=20, density=True) # density=True이면 상대적인 값으로 나타낸다. 이 때 그래프의 총 면적은 1이다.
  ```

<h4>Pie chart 원형 그래프</h4>

- 직접적인 값이 아닌 **상대적인 비율**을 나타내는 그래프
- 특징은 Bar chart와 유사하다.
- ```python
  x = [502, 430, 276, 642]
  y = ["Q1", "Q2", "Q3", "Q4"]
  plt.pie(x, labels = y, autopct = "%0.1f %%")
  # autopct로 비율 출력 커스터마이징 가능하다.
  # "%0.1f %%"는 소수점 1자리 수 + "%" 를 의미한다.
  ```

<h4>Box plot 상자 그림</h4>

- 분위수를 나타내는 그림
- 정상범위와 정상범위를 벗어나는 외상치를 나타낸다.
- vert=False면 가로로 상자그림

<h4>Line plot 꺾은선 그래프</h4>

- 대표적인 커스터마이징 옵션: linewidth, linestyle
- :점선
- -실선
- -. 점선+실선
- xlim, ylim : x축, y축 범위 제한

<h4>Scatter plot 산점도</h4>

- 대표적인 커스터마이징 옵션: marker(o, s, p, d, ^, v, ....), markersize
- 컬러 옵션은 color가 아니라 c로 표시

---

메소드는 set없음. plt.메소드

함수는 set있음. axes.set\_함수

<h4>그리드 추가</h4>

- 그래프 배경에 격자형 선
- `plt.grid(True)`
- `axis` 옵션 따로 설정 안하면 가로 세로 선 둘다 표시
- `axis = "x"` 는 x축 눈금 따라서 세로 선 표현
- `axis = "y"` 는 y축 눈금 따라서 가로 선 표현
- 객체지향적 시각화에도 적용할 수 있다.

<h4>X축, Y축 눈금 조절</h4>

- `xticks()`, `yticks()`
- 매개변수에 원하는 눈금 표현

<h4>투명도 조절</h4>

- 그래프가 겹칠 때, 겹쳐진 부분을 표현하기 위해 필요한 옵션
- `plt.hist(x, bins=100, color='blue', density=True, alpha=0.3)`

<h4>해상도와 크기 조절</h4>

- 해상도를 나타내는 단위는 DPI(Dot per Inch)
- 해상도가 높아지면 그래프는 더 선명해진다.
- 해상도와 크기는 반비례 관계를 가진다.

<h4>폰트 변경(한글 사용)</h4>

- 다양한 폰트를 사용하기 위해 모듈을 import해와야 한다.
- ```python
    from matplotlib.font_manager import fontManager
  ```

- Jupyter에서는 `fontManager.ttflist` 메소드를 통해 폰트 종류를 확인할 수 있다.
- ```python
    fnames = [(f.name, f.style) for f in fontManager.ttflist]
    fnames.sort()
    fnames
  ```

- 한글을 사용하고 싶을 땐,
- ```python
    plt.rc('font', family = "Malgun Gothic")
    plt.rc('axes', unicode_minus=False)
  ```
