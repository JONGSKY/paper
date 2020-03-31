# R-CNN 

## R-CNN이란
![Picture1](https://user-images.githubusercontent.com/40276516/78000057-a16b9300-736e-11ea-9b79-055670fc7e6e.png)
#### R-CNN 정의
  - R-CNN은 Image classification을 수행하는 CNN과 이미지에서 물체가 존재할 영역을 제안해주는 region proposal 알고리즘을 연결하여 높은 성능의 object detection을 수행할 수 있음을 제시해 준 논문입니다. R-CNN의 목표는 하나의 이미지에서 주요 객체들을 박스(Bounding box)로 표현하여 정확히 식별(identify)하는 것에 있습니다.
  
#### R-CNN의 구조
![0sdj6skdrqyzpo6oh](https://user-images.githubusercontent.com/40276516/77990900-7b89c280-735d-11ea-838b-64817fbed988.png)
1. 이미지를 입력값(input)으로 받습니다.
2. 이미지로부터 약 2000개 가량의 region proposal을 추출합니다. (Selective search[1] 활용) 
3. 각 region proposal 영역을 이미지로부터 잘라내고(cropping) 동일한 크기로 만든 후(warping), CNN을 활용해 feature 추출합니다.
4. 각 region proposal feature에 대한 classification을 진행하여 결과를 도출합니다.

#### R-CNN의 구조 파악
  - R-CNN은 2-stage Detector로서 전체 Task를 두 가지 단계로 나누어 진행합니다.
    1. Region Proposal (물체의 위치를 찾는 일)
    2. Region Classification (물체를 분류하는 일)
    - 이 두 Task를 행하기 위한 구조 총 3가지 모듈
    -  ===>
1. Region Proposal - 카테고리와 무관하게 물체의 영역을 찾는 모듈
2. CNN - 각각의 영역으로부터 고정된 크기의 Feature Vector를 뽑아내는 Large Convolutional Neural Network
3. SVM - Classification 을 위한 선형 지도학습 모델 Support Vector Machine(SVM)

##### 1. Region Proposal (영역 찾기)
![region](https://user-images.githubusercontent.com/40276516/78004195-bfd48d00-7374-11ea-8306-95816929da1b.png)

- Region Proposal 단계에서 Selective Search라는 알고리즘을 이용하였습니다.
- Selective Search 알고리즘은 Segmentation 분야에 많이 쓰이는 알고리즘이며 다양한 전략으로 물체의 위치를 파악할 수 있도록 하는 알고리즘 입니다.
- [Selective Search 논문](http://www.huppelen.nl/publications/selectiveSearchDraft.pdf)

##### 2. CNN (Convolutional Neural Network)
![2CNN](https://user-images.githubusercontent.com/40276516/78004295-e0044c00-7374-11ea-8fab-c17237948c95.png)

- 앞선 Selectvie Search를 통해 생성된 2000개의 224*224 Pixel Size로 Warping된 이미지를 각각 CNN에 넣어 줍니다.
![figure](https://user-images.githubusercontent.com/40276516/78004714-720c5480-7375-11ea-9bdc-c46784044b4e.png)
- 위 사진은 224*224 사이즈로 Warping된 VOC2007 tarin 이미지들 입니다.
- 여기서 CNN은 AlexNet의 구조를 거의 그대로 가져다 썼으며, object detetion용으로 마지막 부분만 조금 수정하였습니다.
![alexnet 구조](https://user-images.githubusercontent.com/40276516/78006126-89e4d800-7377-11ea-8265-14752529e0d0.png)
- 위 사진은 AlexNet의 구조입니다.

##### 3. CNN (Convolutional Neural Network)
![svm](https://user-images.githubusercontent.com/40276516/78004340-f14d5880-7374-11ea-8f77-d697b9a30851.png)
- CNN 모델로부터 Feature가 추출이 되고 Training Label이 적용되고 나면, Linear SVM을 이용하여 classification을 진행합니다. (Category-Specific Linear SVMs)
- 여기서 R-CNN은 classifier로 softmax를 쓰지않고 SVM을 사용한 이유는
- VOC2007 데이터셋 기준으로 Sofxmax를 사용했을 때 mAP값이 54.2%에서 50.9%로 떨어졌다고 합니다.


### R-CNN의 단점 및 결론
- R-CNN은 Object Detection 방법들에 비해 굉장히 뛰어난 성능을 보여준것은 분명하지만 다음과 같은 단점들이 있습니다.

1. 오래걸린다.
  - Selective Search에서 뽑아낸 2000개의 이미지들을 CNN모델에 다 돌려서 오래걸립니다.
  - 또한 Selective Search가 CPU를 사용하는 알고리즘이기 때문에 오래걸립니다.

2. 복잡하다.
  - R-CNN은 Multi-Stage Training을 수행하여 CNN, SVM, Bounding Box Regression까지 총 3가지 모델을 필요로 합니다.

3. Back Propagation이 안된다.
  - R-CNN은 Multi-Stage Training을 수행하기 때문에 SVM, Bounding Box Regression에서 학습한 결과가 CNN을 업데이트 시키지 못합니다.

- R-CNN은 최초로 Object Detection에 Deep Learning 방법인 CNN을 적용시켰다는 점과
- 이후 2-stage detector들의 구조에 막대한 영향을 미쳤다는 점에서 의미가 큰 논문입니다.

### 참고
- [1] Selective Search for Object Recognition, J. R. R. Uijings et al, IJCV13.
- [R-CNN(Regions with CNN features) 논문 리뷰](https://jaehyeongan.github.io/2019/10/10/R-CNN/)
- [Object Detection 논문 흐름 및 리뷰](https://nuggy875.tistory.com/20)
