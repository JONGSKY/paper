# Convolutional Neural Network (CNN)

+ 내 맘대로 한줄 요약 : 각각의 특징들을 이용해 강조하고(Convolutional) 다시 강조된 것을 다시 사이즈 조정하고(Pooling) 이후 연산하고(Fully connected) 이후에 분류(softmax) 또는 다양한 결과값을 얻는다. 

## CNN이란

#### CNN의 정의
  - 심층 신경망의 한 종류로, 하나 또는 여러 개의 컨볼루션 레이어와 통합 레이어(pooling layer), 완전 연결 레이어(fully connected layer) 등으로 구성된 이미지 분석에 특화된 신경망입니다. 고양이의 시각과정에서 뇌의 시각 피질의 동작구조를 참고하여 1979년 쿠니히코 후쿠시마가 발표한 네오코그니트론(Neocojnitron)모델이 발전한 형태입니다.

#### CNN의 구조

![CNN_구조](https://user-images.githubusercontent.com/40276516/72335021-9d31c100-3701-11ea-9a36-7a57615ced41.png)

- convolutional filter와 pooling filter가 반복적으로 연결된 뒤에 적절한 사이즈, 특징을 알아내었을 때 최종적으로 fully connected layer로 연결하게 되고 그 후 classification(분류) 또는 다양한 연산을 수행하여 결과값을 얻게 됩니다.

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
    - 완전 연결층에서 weight(가중치)와 bias(스칼라값)들의 연산을 거쳐서 classification 이나 다양한 

#### 필요용어 정리
- Stride(스프라이드[보폭])
  - stride는 입력데이터에 필터를 씌울 때 이동할 간격을 조절하는 양을 의미합니다.
  - convolution filter가 합성곱 연산을 수행하기 위해 이동하는 일정한 이동량인 것입니다.

- Padding(패딩)
  - 레이어 외부에 일정한 값의 레이어를 덧대는 것을 의미합니다. 일반적으로는 상하좌우에 같은 크기와 값을 0으로 하는 패딩을 사용합니다.
  - 이미지 사이즈를 조정하는데에도 많이 쓰이며 바깥쪽에 대한 중요한 특징을 추출하는데도 도움이 됩니다.
![padding](https://user-images.githubusercontent.com/40276516/72336002-44632800-3703-11ea-8e5c-91d1dad1e14e.gif)

- Forward pass (순방향 패스)
  - 파라미터를 사용하여 입력부터 출력까지의 각 계층의 weight를 계산하는 과정을 거치는 것을 순방향 패스(forward pass)라고 합니다.

- Backward pass (역방향 패스)
  - forward pass를 반대로 거슬러 올라가며 다시 한번 계산 과정을 거쳐 기존의 weight를 수정하는 것을 역방향 패스(backward pass)라고 합니다.
  
- Epoch
  - 전체 데이터 셋에 대해 (forward pass + backward pass) 과정이 완료되면 한 번의 epoch가 진행했다고 할 수 있습니다.
  - epochs가 너무 작으면 underfitting이 일어날 수 있고 너무 크면 overfitting이 발생할 수 있습니다.
  - 따라서 적당한 epoch값을 설정해야 underfitting과 overfitting을 방지할 수 있습니다.

- Batch Size
  - 한 번에 처리하는 사진의 장 수를 말합니다.

- Iteration
  - 1회 학습하는 것을 의미합니다. 
  - 만약 총 데이터가 100개인데 batch_size가 10이면 1 iteration당 10개 데이터를 학습합니다.
  - 그래서 10 iterations를 하게되면 1 Epoch가 되게 됩니다.
  
![word](https://user-images.githubusercontent.com/40276516/72598817-eaa56c80-3953-11ea-8ef1-eb9211a07ead.png)

### ※ 참고자료 ※
- 영상
  - [십분딥러닝_CNN_1](https://www.youtube.com/watch?v=P9gDMUDRgGk)
  - [십분딥러닝_CNN_2](https://www.youtube.com/watch?v=_qH1K98W8aE)
- 글
  - [합성곱신경망_학습알고리즘](https://untitledtblog.tistory.com/150)
  - [Pooling이란](https://medium.com/@hobinjeong/cnn%EC%97%90%EC%84%9C-pooling%EC%9D%B4%EB%9E%80-c4e01aa83c83)
  - [CNN_이론](https://everyday-deeplearning.tistory.com/entry/%ED%8C%8C%EC%9D%B4%EC%8D%AC%EC%9C%BC%EB%A1%9C-%EB%94%A5%EB%9F%AC%EB%8B%9D%ED%95%98%EA%B8%B0-CNNConvolution-Neural-Network)
  - [텐서플로우로 배우는 딥러닝](https://www.slideshare.net/w0ong/ss-82372826)
  
