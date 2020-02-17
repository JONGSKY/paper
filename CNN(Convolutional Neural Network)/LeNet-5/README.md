# LeNet-5

+ 내 맘대로 한줄 요약 : 아직 공부중

## LeNet-5이란
  - LeNet은 우편번호와 수표의 필기체를 인식하기 위해 개발되었습니다. CNN 모델을 최초로 개발한 사람은 프랑스 출신의 Yann LeCun이며, 1989년 “Backpropagation applied to handwritten zip code recognition” 논문을 통해 최초로 CNN을 사용하였고, 1998년 LeNet이라는 Network를 소개하였습니다. 이후 LeNet-1, LeNet-2, ... 등 최종 버전인 LeNet-5가 나오게 되었습니다.

#### LeNet-5의 구조

![lenet5_구조](https://user-images.githubusercontent.com/40276516/74128881-98d5c680-4c21-11ea-9d33-cdde723ea337.png)

  - LeNet5는 총 7개의 Layer로 구성되어있습니다. 3개의 Convoltuion Layer, 2개의 Sub-Sampling Layer, 1개의 Fully-Connected Layer 그리고 최종 출력 Layer로 이루어져 있습니다.

##### LeNet-5 구조설명

  1) C1 layer : Convolution Layer로 32*32 사이즈의 데이터를 5 * 5 Filter 6개를 사용해 Convolution 합니다. 그 결과로 28 * 28 사이즈의 Feature map을 6개 만들어 냅니다.
- Parameter수 : 5 * 5 filter 6개, bias 6개 = 5 * 5 * 6 + 6 = 156 개

 2) S2 layer : Sub-Sampling Layer로 6장의 28 * 28 Feature map에 대해 2*2 필터(stride:2)로 서브샘플링 해줍니다. 이때 pooling은 average pooling을 시행하도록 합니다. 따라서 14 * 1 size 6장으로 만들게 됩니다.
 
 3) C3 layer : Convolution Layer로 14 * 14 사이즈의 데이터를 5 * 5 filter 16개를 사용해 Convolution 합니다. 그 결과로 10 * 10 사이즈의 Feature map을 16개 만들어 냅니다. 이때 일반적으로 수행하는 것이 아니라 6 * 16인 96개의 Feature map이 만들어져야 하지만 모든 map을 연결 하는 것이 아니라 아래의 table과 같이 선택적으로 연결시켜 network의 symmetry(대칭)한 성질을 없애려고 합니다. 최종적으로 Global Feature를 얻기 위해 다음과 같이 연결시키도록 합니다.
 
![C3_layer](https://user-images.githubusercontent.com/40276516/74229884-9bf6b280-4d06-11ea-95a3-49da55dbb0a4.png)

- Parameter수 : 456+606+303+151 = 총 1516 개

  1) (5 * 5 * 3 + 1) * 6 = 456
  2) (5 * 5 * 4 + 1) * 6 = 606
  3) (5 * 5 * 4 + 1) * 3 = 303
  4) (5 * 5 * 6 + 1) * 1 = 151


 4) S4 layer : Sub-Sampling Layer로 16장의 10 * 10 Feature map에 대해 2 * 2 필터(stride:2)로 서브샘플링 해줍니다. 이때 pooling은 average pooling을 시행하도록 합니다. 따라서 5 * 5 size 16장으로 바뀌게 됩니다.
  
  
 5) C5 layer : FC(Fully connected) layer로 5 * 5 * 16 filter 120개를 사용해 Convolution 합니다. 그 결과로 1 * 1 Feature map이 120개 만들어지게 됩니다.
 
 - Parameter 수 : (5 * 5 * 16 + 1) * 120 = 48120
 
 6) F6 layer : FC layer로 1 * 1 * 120 data를 84개의 unit에 연결시켜 1 * 1 * 84개의 data로 만듭니다.
 
 - Parameter 수 : (120 + 1 ) * 84 = 10164

 7) Output layer : 10개의 Euclidean radial basis function(RBF) 유닛들로 구성되어있습니다. 각각의 F6 layer의 84개 유닛으로부터 인풋을 받게 되고 최종적으로 이미지가 속한 클래스를 알려주게 됩니다.
 
 - 총 Parameter 수는 : 156(C1) + 1516(C3) + 48120(C5) + 10164(F6) = 60000 개 입니다.

## 그림으로 Layer 해석해보기

![그림_1](https://user-images.githubusercontent.com/40276516/74237490-057ebd00-4d17-11ea-8aa2-492d33ad60b8.png)
![그림_2](https://user-images.githubusercontent.com/40276516/74237492-06afea00-4d17-11ea-8589-7558454bdcf1.png)

[PDF파일로 보기](https://github.com/JONGSKY/paper/files/4185671/Untitled_20200211_172225.PDF)


### ※ 참고자료 ※
- 글
  - [LeNet-5의 구조](https://bskyvision.com/418)
  - [CNN-LeNet](https://reniew.github.io/07/)
  - [라온피플 머신러닝 아카데미](https://m.blog.naver.com/PostView.nhn?blogId=laonple&logNo=220648539191&proxyReferer=https%3A%2F%2Fwww.google.com%2F)
