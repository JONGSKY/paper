# Fast R-CNN

## Fast R-CNN이란

#### Fast R-CNN과 R-CNN 비교
  1) RoI (Region of Interest) 마다 CNN연산을 함으로써 속도저하 --> RoI pooling
  2) multi-stage pipelines으로써 모델을 한번에 학습시키지 못함 --> CNN 특징 추출부터 classification, bounding box regression까지 하나의 모델에서 학습
  
#### Fast R-CNN 

##### "CNN 특징 추출부터 classification, bounding box regression 까지 모두 하나의 모델에서 학습시키자!" 
  ![fAST-rNN](https://user-images.githubusercontent.com/40276516/79423991-79309500-7ffa-11ea-8c6f-ef0ee570b198.png)
  
  1-1. R-CNN에서와 마찬가지로 Selective Search를 통해 RoI를 찾는다.

  1-2. 전체 이미지를 CNN에 통과시켜 feature map을 추출한다.

  2. Selective Search로 찾았었던 RoI를 feature map크기에 맞춰서 projection시킨다.

  3. projection시킨 RoI에 대해 RoI Pooling을 진행하여 고정된 크기의 feature vector를 얻는다.

  4. feature vector는 FC layer를 통과한 뒤, 구 브랜치로 나뉘게 된다.

  5-1. 하나는 softmax를 통과하여 RoI에 대해 object classification을 한다.

  5-2. bounding box regression을 통해 selective search로 찾은 box의 위치를 조정한다. 

### Fast R-CNN 구조 살펴보기

![fast-rcnn](https://user-images.githubusercontent.com/40276516/79425258-64550100-7ffc-11ea-842c-55742c0d1d8b.png)

## RoI Pooling 이란

![roi-pooling](https://user-images.githubusercontent.com/40276516/79425472-b138d780-7ffc-11ea-88fd-3b7a9341387c.png)

  - Fast R-CNN에서 먼저 입력 이미지를 CNN에 통과시켜 feature map을 추출한다.
  - 그 후 이전에 미리 Selective search로 만들어놨던 RoI(=region proposal)을 feature map에 projection시킨다.
  - 위 그림의 가장 좌측 그림이 feature map이고 그 안에 hxw크기의 검은색 box가 투영된 RoI이다.

  (1) 미리 설정한 HxW크기로 만들어주기 위해서 (h/H) * (w/H) 크기만큼 grid를 RoI위에 만든다.
  
  (2) RoI를 grid크기로 split시킨 뒤 max pooling을 적용시켜 결국 각 grid 칸마다 하나의 값을 추출한다.
  
  - 위 작업을 통해 feature map에 투영했던 hxw크기의 RoI는 HxW크기의 고정된 feature vector로 변환된다.
  - "원래 이미지를 CNN에 통과시킨 후 나온 feature map에 이전에 생성한 RoI를 projection시키고
  - 이 RoI를 FC layer input 크기에 맞게 고정된 크기로 변형할 수가 있다"
  - 따라서 더이상 2000번의 CNN연산이 필요하지 않고 1번의 CNN연산으로 속도를 대폭 높일 수 있었다.
  
