# R-CNN 

## R-CNN이란

#### R-CNN 정의
  - R-CNN은 Image classification을 수행하는 CNN과 이미지에서 물체가 존재할 영역을 제안해주는 region proposal 알고리즘을 연결하여 높은 성능의 object detection을 수행할 수 있음을 제시해 준 논문입니다. R-CNN의 목표는 하나의 이미지에서 주요 객체들을 박스(Bounding box)로 표현하여 정확히 식별(identify)하는 것에 있습니다.
  
#### R-CNN의 구조
![0sdj6skdrqyzpo6oh](https://user-images.githubusercontent.com/40276516/77990900-7b89c280-735d-11ea-838b-64817fbed988.png)
1. 이미지를 입력값(input)으로 받습니다.
2. 이미지로부터 약 2000개 가량의 region proposal을 추출함 (Selective search[1] 활용) 
3. 각 region proposal 영역을 이미지로부터 잘라내고(cropping) 동일한 크기로 만든 후(warping), CNN을 활용해 feature 추출
4. 각 region proposal feature에 대한 classification을 수행



### 참고
- [1] Selective Search for Object Recognition, J. R. R. Uijings et al, IJCV13.
- [R-CNN(Regions with CNN features) 논문 리뷰](https://jaehyeongan.github.io/2019/10/10/R-CNN/)
