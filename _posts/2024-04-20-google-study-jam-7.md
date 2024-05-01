---
layout: post
title: "[GoogleStudyJam] Attention Mechanism"
date: 2024-04-20 12:32:00 +0900
categories: TIL
---

### 정리

- 예를 들어 영어문장을 프랑스어로 번역하고자 한다면.
  - 번역을 개선하기 위해 encoder, decoder에 Attention Mechanism을 추가할 수 있다. 신경망이 입력 시퀀스의 특정 부분에 집중할 수 있도록 하는 기술이다. 이것은 입력 시퀀스의 다른 부분에 가중치를 할당하고 가장 중요한 부분이 가장 높은 가중치를 받음으로써 수행된다. 입력 시퀀스의 가중치 합은 신경망의 다음 계층에 대한 입력으로 사용된다.
  - 모델은 한 번에 하나의 단어를 입력받아 hidden state를 업데이트하고 다음 단계로 전달한다. 최종 hidden state만 처리를 위해 디코더로 전달된다.
- attention medel 이 traditional model과 다른점

  - 인코더가 더 많은 데이터를 디코더에게 전달한다 : 최종hidden state만 전달하는 것이 아니라 인코더는 모든 hidden state를 전달한다. 이는 디코더에게 더 많은 context를 제공한다. 디코더는 모든 hidden state 정보를 사용하여 문장을 번역한다.
  - 디코더는 output을 생성하기 전에 추가적인 단계를 거친다. 입력에서 가장 관련성이 높은 부분에 초점을 맞추기 위해 디코더는 다음을 수행한다.

    1. 수신한 인코더의 set of hidden state 를 확인한다. 각 encoder hidden state는 입력된 문장의 특정 단어와 관련된 것이다.
    2. 각 hidden state에 점수를 준다
    3. 각 hidden state의 softmax점수를 곱한다.

> softmax score란? <br>
> Softmax score는 입력된 값들을 확률 분포로 변환하는 함수의 결과를 나타냅니다. 주로 다중 클래스 분류 문제에서 출력층에서 사용됩니다. Softmax 함수는 각 클래스에 대한 점수(일반적으로 로짓 또는 선형 출력)를 입력으로 받아 이를 확률 값으로 변환합니다. Softmax 함수는 입력된 점수들을 모든 클래스 점수의 지수화된 값의 합으로 나누어 각 클래스에 속할 확률을 계산합니다. 이렇게 하면 각 클래스에 대한 확률 분포를 얻을 수 있습니다. 이 때, Softmax 함수의 출력은 0과 1 사이의 값을 가지며, 모든 클래스에 대한 확률의 합은 1이 됩니다.
> 따라서 Softmax score는 다중 클래스 분류 문제에서 각 클래스에 대한 예측 확률을 나타내는 값으로 이해할 수 있습니다.

> Hidden State란? <br>
> "Hidden state(은닉 상태)"는 주어진 모델이 내부적으로 유지하는 상태를 가리킵니다. 이것은 순환 신경망(Recurrent Neural Network, RNN)이나 장단기 메모리(Long Short-Term Memory, LSTM), 그리고 변형된 형태의 모델에서 자주 사용됩니다.
> Hidden state는 현재 입력과 이전 입력에 대한 정보를 담고 있으며, 이전 단계의 hidden state에 영향을 받습니다. 이것은 모델이 입력 시퀀스를 처리하면서 내부적으로 상태를 갱신하고 유지하면서 정보를 "기억"한다고 생각할 수 있습니다.
> 예를 들어, RNN은 각 시간 단계에서 현재 입력과 이전 시간 단계의 hidden state를 사용하여 새로운 hidden state를 계산합니다. 이를 통해 RNN은 시퀀스 데이터를 처리하면서 이전 정보를 기억하고 현재 입력과 함께 사용하여 다음 단계의 출력을 생성할 수 있습니다.
> Hidden state는 주로 모델의 내부 상태를 나타내는데 사용되며, 주어진 시퀀스 데이터를 처리하는 동안 모델이 어떤 정보를 보유하고 있는지를 이해하는 데 도움을 줍니다. 따라서 hidden state는 모델의 학습 및 추론 과정에서 중요한 역할을 합니다.

### 오늘은 어땠냐면요

![스크린샷 2024-04-20 121706](https://github.com/pingu2017/comment/assets/115390100/228eec30-b63b-4583-8e69-6ddda9813fde)

파파고 등 번역 서비스를 정말 잘 이용하면서도 AI는 어떻게 번역이 가능할까? 라는 의문을 가져본 적은 없던것 같다. (워낙 전지전능하시니..)
이번 파트는 짧아서 encoder-decoder에 대해 정확히 이해하진 못했지만 단어에 문법적 가중치를 두어 순서를 정한다는 것이 흥미로웠다. 다음 파트에서 더 상세한 설명이 있길래 기대중!