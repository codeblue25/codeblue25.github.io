---
layout: post
title: "ANN (인공신경망) 이론"
date: 2021-07-07T15:25:52-05:00
author: codeblue25
categories: Deep_learning
---

<h3>ANN (artificial neural network)</h3>

- 생물학의 신경망에서 파생된 학습 알고리즘
  - 생물학의 신경세포(뉴런)을 수학적으로 모델링 한 것이 인공신경망의 뉴런 모델
- 뉴럴 네트워크: 크게 입력층, 은닉층, 출력층으로 구성
- 출력층에서 나온 **예측값과 실제값의 오차( = 손실함수 값 = SSE )**가 0에 수렴할수록 이상적인 알고리즘

---

<h3>주요 용어 정리</h3>

- 원-핫 벡터: 범주형 요소, 즉 수치로 표현되지 않는 요소를 0과 1로 이루어진 변수로 변환해주는 표현 방식

  - 예시: gender를 원-핫 벡터로 표현

  - ```python
            F  M
    female  1  0
    male    0  1
    ```

  - female은 [1, 0] male은 [0, 1]

- Adam: 예측값과 실제값의 오차가 작아지도록 학습률을 epoch 돌 때마다 경신시키는 함수
- epoch: 데이터를 학습시키는 한 차례, 즉 epoch = 4면 학습을 4회 실행
- 순전파 (forward propagation): 입력값과 파라미터를 넣고 손실함수값을 계산하는 함수
- 역전파 (back propagation): 순전파를 통해 도출된 손실함수값을 줄이기 위해, 순전파 계산을 역행하며 손실기울기를 계산하는 함수
- 경사하강법: 순전파와 역전파를 반복하며 손실함수값이 최소화 되는 방향으로 이동하는 기법

---

<h3>경사하강법 구현식</h3>

```python
import numpy as np

x             = np.asarray([580, 700, 810, 840])
y_label_total = np.asarray([374, 385, 375, 401])

input_cnt  = 1
output_cnt = 1

RND_STD  = 1
RND_MEAN = 0

def main_execute(x,y, epoch_count, report ,lr = 0.001):
    model_init()
    sse_row, theta_0_row, theta_1_row = run_train(x,y, epoch_count, report ,lr)

    return sse_row, theta_0_row, theta_1_row
```

- 입력값은 x, y_label_total이다. 이 때 두 array는 랜덤한 수로 이루어져 있다.
- `input_cnt` / `output_cnt` / `RND_STD` / `RND_MEAN` : 표준정규분포를 위한 변수
  - 사용 예시: `np.random.normal(0, 1, size=5000)` = 평균이 0, 표준편차가 1인 정규분포에서 데이터 5000개 생성
- main_execute 함수는 model_init() 함수와 run_train() 함수로 구성되어 있다.
  - run_train함수는 forward_neuralnet() 함수, forward_postproc() 함수 back_propagation() 함수로 구성되어 있다.

---

```python
def model_init():
    global theta_0, theta_1
    theta_0 = np.random.normal(RND_MEAN, RND_STD, size = [output_cnt])
    theta_1 = np.random.normal(RND_MEAN, RND_STD, size = [input_cnt, output_cnt])

def run_train(x,y, epoch_count, report ,lr):
    print("Initial theta_0 : {}".format(theta_0))
    print("Initial theta_1 : {}".format(theta_1))
    sse_row = []
    theta_0_row, theta_1_row = [], []

    for epoch in range(epoch_count):
        y_hat = forward_neuralnet(x)
        sse   = forward_postproc(y_hat, y_label_total)
        sse_row.append(sse)

        back_propagation(y_hat, lr)

        theta_0_row.append(theta_0)
        theta_1_row.append(theta_1)

        if report > 0 and epoch % report == 0:
            print("Epoch - {}".format(epoch+1))
            print("SSE : {}".format(sse))

    print("==============================")
    print("Final SSE : {}".format(sse))

    return sse_row, theta_0_row, theta_1_row
```

- model_init() 함수를 통해 표준정규분포로 모델링 한다.
- run_train() 함수를 통해 순전파, 역전파 연산을 한다.
  - 순전파 출력값을 y_hat 변수로 생성한다.
  - y_hat과 lr(학습률)을 넣어서 역전파 계산을 한다.
  - y_hat과 입력값(y_label_total)을 비교하여 손실함수값을 구할 수 있다.

---

```python
def forward_neuralnet(input_x):
    y_hat = theta_0 + theta_1 * input_x

    return y_hat

def forward_postproc(output, y):
    diff   = output - y
    square = np.square(diff)
    sse    = 1/2 * (np.sum(square))

    return sse

def back_propagation(y_hat, lr):
    global theta_0, theta_1
    theta_0 = theta_0 - lr * (np.sum(y_hat - y_label_total))
    theta_1 = theta_1 - lr * (np.sum(y_hat - y_label_total) * x)

sse_row, theta_0_row, theta_1_row = main_execute(x = x,
                                                 y = y_label_total,
                                                 epoch_count = 10,
                                                 report = 3,
                                                 lr = 0.0000001)
```

- forward_neuralnet() 함수는 순전파 계산한다.
  - y = ax + b를 세타(θ)로 표현한 식
- forward_postproc() 함수는 손실함수값을 계산한다.
  - 예측값과 실제값의 차이를 제곱하여 2로 나눈 것이 SSE이다.
- back_propagation() 함수는 순전파의 출력값과 학습률을 이용하여 역전파 계산한다.
- report: epoch가 커짐에 따라 출력값이 너무 많아지는 것을 우려해서, report 값의 주기로 출력값을 보여준다.
