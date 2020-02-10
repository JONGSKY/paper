# LeNet-5

+ 내 맘대로 한줄 요약 : 

## LeNet-5이란
  - LeNet은 우편번호와 수표의 필기체를 인식하기 위해 개발되었습니다. CNN 모델을 최초로 개발한 사람은 프랑스 출신의 Yann LeCun이며, 1989년 “Backpropagation applied to handwritten zip code recognition” 논문을 통해 최초로 CNN을 사용하였고, 1998년 LeNet이라는 Network를 소개하였습니다. 이후 LeNet-1, LeNet-2, ... 등 최종 버전인 LeNet-5가 나오게 되었습니다.

#### LeNet-5의 구조

![lenet5_구조](https://user-images.githubusercontent.com/40276516/74128881-98d5c680-4c21-11ea-9d33-cdde723ea337.png)

  - LeNet5는 총 7개의 Layer로 구성되어있습니다. 3개의 Convoltuion Layer, 2개의 Sub-Sampling Layer, 1개의 Fully-Connected Layer 그리고 최종 출력 Layer로 이루어져 있습니다.

  1) C1 layer : Convolution Layer로 32*32 사이즈의 데이터를 5*5 Filter 6개를 사용해 Convolution 합니다. 그 결과로 28*28 사이즈의 Feature map을 6개 만들어 냅니다.
Parameter수 : 5*5 filter 6개, bias 6개 = 5*5*6 + 6 = 156

  2) S2 layer : Sub-Sampling Layer로 6장의 28*28 Feature map에 대해 2*2 필터(stride:2)로 서브샘플링 해줍니다. 이때 pooling은 average pooling을 시행하도록 합니다. 따라서 14*14 size를 6개를 만들게 됩니다.
 
 3) C3 layer : Convolution Layer로 14*14 사이즈의 데이터를 5*5 filter 16개를 사용해 Convolution 합니다. 




### ※ 참고자료 ※
- 영상
  - 
- 글
  - [LeNet-5의 구조](https://bskyvision.com/418)
  - [CNN-LeNet](https://reniew.github.io/07/)
