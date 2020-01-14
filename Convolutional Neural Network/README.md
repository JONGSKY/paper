# Convolutional Neural Network (CNN)

## CNN이란

#### CNN의 정의
  - 심층 신경망의 한 종류로, 하나 또는 여러 개의 컨볼루션 레이어와 통합 레이어(pooling layer), 완전 연결 레이어(fully connected layer) 등으로 구성된 이미지 분석에 특화된 신경망입니다. 고양이의 시각과정에서 뇌의 시각 피질의 동작구조를 참고하여 1979년 쿠니히코 후쿠시마가 발표한 네오코그니트론(Neocojnitron)모델이 발전한 형태입니다.

#### CNN의 구조

![CNN_구조](https://user-images.githubusercontent.com/40276516/72335021-9d31c100-3701-11ea-9a36-7a57615ced41.png)

- convoltional filter와 pooling filter가 반복적으로 연결된 뒤에 적절한 사이즈, 특징을 알아내었을 때 최종적으로 fully connected layer로 연결하게 되고 그 후 classification(분류) 또는 다양한 연산을 수행하여 결과값을 얻게 됩니다.

  - Convolutional filter
![convolution_filter](https://user-images.githubusercontent.com/40276516/72339170-2e586600-3709-11ea-8bbb-e5bdcbdac211.png)
    - convolutional 필터를 적용하게 되면 예시 사진과같이 필터에 따라 이미지의 값들이 변경하게 됩니다.
    - 가로성분 필터를 이용하였을 때는 숫자 5의 가로가 강조되며 세로 또한 가로보다는 약하지만 강조가 됩니다.


  - Pooling filter
![5_pooling](https://user-images.githubusercontent.com/40276516/72340025-bb4fef00-370a-11ea-8e77-f9bb606a999a.png)
    - pooling 층은 앞선 특징들을 추출한 층들이 너무 크게 되면 연산량이 많아지고 복잡해지기 때문에 층을 단순화하고 사이즈를 축소해주는 층입니다.
    - 즉 연산량이 많아지고 복잡해지면 Overfitting이 일어나게 되는데 이를 방지하기 위한 층입니다.
  
  - pooling은 크게 3가지로 나눠집니다.
    1. max pooling (최대 풀링)
        - 일정한 크기(n*n)내에 있는 데이터의 값 중에서 가장 큰 값을 대푯값으로 설정합니다.
    2. mean pooling (평균 풀링)
        - 일정한 크기(n*n)내에 있는 데이터의 모든 값들의 평균을 대푯값으로 설정합니다.
    3. stochastic pooling (확률 풀링)
        - 일정한 크기(n*n)내에 있는 데이터들의 값들중 하나를 확률에 근거하여 대푯값으로 설정합니다.
![pooling](https://user-images.githubusercontent.com/40276516/72334985-9014d200-3701-11ea-9d49-a7e3f01af692.png)

  - Fully connected layer
![fully_connected_layer](https://user-images.githubusercontent.com/40276516/72340826-3534a800-370c-11ea-831e-6371f01a1eb0.png)
    - 
    
    
- Stride(스프라이드[보폭])
  - stride는 입력데이터에 필터를 씌울 때 이동할 간격을 조절하는 양을 의미합니다.
  - convolution filter가 합성곱 연산을 수행하기 위해 이동하는 일정한 이동량인 것입니다.

- Padding(패딩)
  - 레이어 외부에 일정한 값의 레이어를 덧대는 것을 의미합니다. 일반적으로는 상하좌우에 같은 크기와 값을 0으로 하는 패딩을 사용합니다.
  - 이미지 사이즈를 조정하는데에도 많이 쓰이며 바깥쪽에 대한 중요한 특징을 추출하는데도 도움이 됩니다.
![padding](https://user-images.githubusercontent.com/40276516/72336002-44632800-3703-11ea-8e5c-91d1dad1e14e.gif)


 
