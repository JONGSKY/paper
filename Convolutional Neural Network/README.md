# Convolutional Neural Network (CNN)

- CNN이란
  - 심층 신경망의 한 종류로, 하나 또는 여러 개의 컨볼루션 레이어와 통합 레이어(pooling layer), 완전 연결 레이어(fully connected layer) 등으로 구성된 이미지 분석에 특화된 신경망입니다. 고양이의 시각과정에서 뇌의 시각 피질의 동작구조를 참고하여 1979년 쿠니히코 후쿠시마가 발표한 네오코그니트론(Neocojnitron)모델이 발전한 형태입니다.

- CNN의 구조
![CNN_구조](https://user-images.githubusercontent.com/40276516/72335021-9d31c100-3701-11ea-9a36-7a57615ced41.png)

- Pooling 층
  - pooling 층은 앞선 특징들을 추출한 층들이 너무 크게 되면 연산량이 많아지고 복잡해지기 때문에 층을 단순화하고 사이즈를 축소해주는 층입니다.
  - 즉 연산량이 많아지고 복잡해지면 Overfitting이 일어나게 되는데 이를 방지하기 위한 층입니다.
![pooling](https://user-images.githubusercontent.com/40276516/72334985-9014d200-3701-11ea-9d49-a7e3f01af692.png)

- 