---
layout: post
title: "[GoogleStudyJam] Introduction to Large Lanuage Models"
date: 2024-03-29 17:46:00 +0900
categories: TIL
---

## 정리

**수업의 목표 : LLM이란 무엇인가?**

### LLM이란?

- 사전 학습(pre-Trained) 된 다음 특정 목적을 위해 미세 조정(fine-tuned)할 수 있는 대규모 범용 언어 모델을 말한다.
  > fine-tuned : 기본적으로 이미 훈련된 모델을 특정 작업에 맞게 추가적으로 조정하거나 조정하는 것을 의미. 적은 date set을 사용해 다양한 분야의 특정 문제를 해결하도록 모델을 맞춤화 할 수 있다.
- LLM을 세 가지 특성으로 정리할 수 있다.
  - Large : 데이터의 양이 많다는 것이다. 페타바이트 규모의 큰 데이터를 사용한다. 또한 파라미터의 개수도 많다. HyperParameter라고도 한다. 매개변수는 기본적으로 기계가 모델 훈련을 통해 학습한 기억과 지식이다. 텍스트 예측과 같은 문제 해결에서 모델의 기술을 정의한다.
  - General Purpose(범용) : 모델이 일반적인 문제를 해결하기에 충분한 경우. 특정 도메인에 관계없이 인간 언어의 공통성을 의미한다. 자원이 제한되어 있기 때문에 범용성은 중요하다.
  - pre-Trained and fine-tuned (사전 훈련 및 미세 조정) : 대규모 데이터셋을 이용해 일반적인 목적을 위해 LLM을 사전교육한 다음 훨씬 작은 데이터셋을 이용해 특정 목표에 맞게 미세 조정하는 것을 의미한다. 특정 조직만이 거대한 데이터 셋, 파라미터를 가지고 LLM을 만들 수 있는 능력을 가지고 있다. → 각각 특화하려면 미세조정이 필요

### 사용 사례

- 단일 모델을 다양한 작업에 사용할 수 있다.
- 특정 문제를 해결하기 위해 fine-tuned 할 때 최소한의 학습 데이터가 필요하다. 거의 없어도 적절한 성능을 보여준다.
  - few-shot : 최소한의 데이터로 모델을 훈련시키는 것
  - zero-shot : 이전 훈련에서 명시적으로 가르쳐주지 않은 것들을 모델이 인식할 수 있다는 것
- 더 많은 데이터와 매개변수를 추가하면 대규모 언어 모델의 성능이 지속적으로 향상된다.

### LLM의 종류

- Generic language model(일반언어모델) : 훈련 데이터의 언어를 기반으로 다음 단어 예측 (자동완성)
- Instruction tuned(명령 모델) : 입력에 제공된 지침에 대한 응답을 예측하도록 학습된다.
- Dialog Tuned (응답 모델) : 대화형 응답을 하도록 훈련된다. 명령모델의 특별케이스로 채팅 봇에 대한 질문으로 구성된다. 더 긴 대화의 맥락에서 이루어질 것으로 예상되며 일반적으로 자연스러운 질문과 같은 문구에 더 잘 어울린다.

### Tuning

- 모델을 튜닝하면 모델이 수행할 작업의 예를 기반으로 모델 응답을 사용자가 정의할 수 있다. 본질적으로 새로운 데이터에 대해 모델을 교육해 모델을 새로운 도메인이나 사용자 지정 사용사례 집합에 적용시키는 프로세스이다.
- 자체 데이터셋을 가져와 LLM의 모든 가중치를 조정해 모델을 재교육하는 Fine tuning을 통해 모델을 추가로 튜닝할 수 있다. 이를 위해 대규모 교육 작업과 자체적으로 Fine tuning된 모델을 호스팅 해야 한다. →많은 비용, 현실적이지 않다.
- PETM(Parameter-Efficient Tuning Methods) : 모델을 복제하지 않고 사용자 정의 데이터를 기반으로 대규모 언어 모델을 튜닝하는 방법. 기본 모델은 변경되지 않고 추론 시 교체할 수 있는 소수의 추가 레이어가 조정된다.

## 오늘은 어땠냐면요

대학원생인 친구는 영어논문 해석을 AI에게 맞기곤 하는데 Chat GPT보다 claude에게 논문 해석을 시켰을 때 전문적인 영단어의 한글 번역이 자연스럽고, 저자가 의도한 미묘한 단어의 느낌까지도 잘 잡아준다고 말했다. 나도 Chat GPT를 애용하는데(무료로^^;;), IT지식이나 수학계산 등 이공계적인 질문을 했을 때는 답을 잘 하는데, 사자성어만 물어봐도 엉뚱한 대답을 하는 것을 자주 봤다. 오늘 LLM 강의를 들으니 클로드는 좀 더 인문사회학적인 prompt를 공부한 것이 아닌가! 하는 생각이 들었다 ㅎㅎ

claude와 chat GPT의 대답. chat GPT는 해당 사자성어에 대한 데이터가 없었는지 "가외"라는 부분을 한자 그대로 직역했다.
![image](https://github.com/pingu2017/comment/assets/115390100/b2d09658-9f0f-411c-bcd2-649599c54c75)

![image](https://github.com/pingu2017/comment/assets/115390100/3aac92ce-8647-4b82-b75a-5fddac4ea63e)

오늘은 100점 ~
![image](https://github.com/pingu2017/comment/assets/115390100/9e78eef6-2512-4d66-84ad-9eeba58377b4)