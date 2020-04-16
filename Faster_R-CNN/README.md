# Faster R-CNN

## Faster R-CNN이란

#### Faster R-CNN 소개
![img](https://user-images.githubusercontent.com/40276516/79421875-b72bba00-7ff6-11ea-8421-890f59578a5a.png)

  - RPN + Fast R-CNN
  - R-CNN에서는 3가지 모듈 (region proposal, classification, bounding box regression)을 각각 따로따로 수행한다.
  - (1)region proposal 추출 → 각 region proposal별로 CNN 연산 → (2)classification, (3)bounding box regression
  - Fast R-CNN에서는 region proposal을 CNN level로 통과시켜 classification, bounding box regression을 하나로 묶었다.
  - (1)region proposal 추출 → 전체 image CNN 연산 → RoI projection, RoI Pooling → (2)classification, bounding box regression
  
#### Faster R-CNN과 Fast R-CNN의 비교
  - Selective search는 cpu에서 돌아가기 때문에 느리다는 단점이 있다.
  - 따라서 Region proposal 생성하는 네트워크도 gpu에 넣기 위해서 Conv layer에서 생성하도록 하자는게 아이디어이다.
  
