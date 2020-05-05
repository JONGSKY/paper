# 논문 구현


- Image 처리 관련 논문
  - Image Classification - CIFAR 10 , ImageNet
    - [CNN(Convolutional Neural Network)](https://github.com/JONGSKY/paper/tree/master/CNN(Convolutional%20Neural%20Network))
      - [LeNet-5](https://github.com/JONGSKY/paper/tree/master/CNN(Convolutional%20Neural%20Network)/LeNet-5)
      - [AlexNet](https://github.com/JONGSKY/paper/tree/master/CNN(Convolutional%20Neural%20Network)/AlexNet)
      - VGGNet
      - GoogLeNet (Inception V2)
      - ResNet(https://arxiv.org/pdf/1512.03385v1.pdf)
      - EfficientNet
  - Image Detection - COCODataset 
![fig4_paper_trend_2019](https://user-images.githubusercontent.com/40276516/77990083-598f4080-735b-11ea-81ee-0249acb7bebd.png)
![detecter](https://user-images.githubusercontent.com/40276516/78026753-2074c180-7397-11ea-9db4-78fbfd9ffbc2.png)

    - [이미지 라벨링](https://hoya012.github.io/blog/Tutorials-of-Object-Detection-Using-Deep-Learning-labeling/)
    - [이호성](https://hoya012.github.io/blog/Tutorials-of-Object-Detection-Using-Deep-Learning-what-is-object-detection/)
    - [R-CNN](https://github.com/JONGSKY/paper/tree/master/R-CNN), [Fast R-CNN](https://github.com/JONGSKY/paper/tree/master/Fast_R-CNN), [Faster R-CNN](https://github.com/JONGSKY/paper/tree/master/Faster_R-CNN)
    - YoLo v1,v2,v3
    - SSD
  - Image Segmentation
    - [FCN](https://github.com/JONGSKY/paper/tree/master/FCN)
    - SANet
  - Image Generation
    - [GAN](https://papers.nips.cc/paper/5423-generative-adversarial-nets.pdf)
    - WGAN
    - BEGAN
    - StyleGAN

- Text 처리 관련 논문
  - Text Classification
  - Text Summarization
  - Machine Translation
  - Natural Language Understanding - Chatbot
- Text to Image , Image to Text


## 논문의 종류 
- 논문은 크게 Conference paper와 Journal paper가 있습니다.
- Conference(학회)는 학술대회장에 많은 사람이 모여 각자의 연구(논문)를 발표하며 교류하는 행사를 말하고 여름, 겨울마다 가는 정보과학회 학술대회라고 생각하시면 됩니다.
- Journal(저널, 학술지)는 마치 여러 편의 논문으로 구성되는 하나의 책이라고 볼 수 있습니다. 특정 장소에 모이거나 발표를 하지 않습니다.
- Conference paper는 적은 분량(보통 8장 이내)으로, 자신의 연구를 간략하게 발표하고 공유하는 목적을 두고 있습니다. 때문에 Journal에 비해 상대적으로 트랜디하고 동향을 파악하는데 좋을 듯 합니다.
- Journal paper는 분량이 많고(10장 이상), 보다 풍부한 실험과 분석으로 자신의 연구를 디테일한 부분까지 마감하기에 상당한 노력이 들어가고 때문에 Conference paper보다 더 높은 가치를 갖습니다. 다만 작성하는데 많은 시간이 소요되기에 최신 트랜드를 반영하기 어렵습니다. 컴퓨터 분야는 아니지만 한 번쯤은 들어봤을 Nature, Science 등이 Journal에 속합니다.
- 다른 분야에 비해 트랜드의 흐름이 빠른 컴퓨터공학 분야에서는 Journal 만큼 Conference paper를 인정하기도 합니다.
- 보통은 Conference에 자신의 연구를 발표하고 이에 대해 연구와 실험, 분석 등을 보강하여 Journal에 투고합니다.

[출처사이트](https://github.com/HYU-AILAB/ai-seminar/wiki/%EB%85%BC%EB%AC%B8-%EC%84%A0%EC%A0%95-%EB%B0%8F-%EC%9D%BD%EB%8A%94-%EB%B0%A9%EB%B2%95).

## 논문 읽는 법

- 논문의 구조는 대부분 아래와 같습니다.
  1. 나는 이런 문제를 풀거야 (abstract)
  2. 사실 이 문제는 이런 동기에서 연구가 시작된건데 (introduction)
  3. 관련해서 이런저런 접근들이 있었지 (related works)
  4. 난 이런 새로운 방식으로 접근해보려고 하는데 (method)
  5. 정말 이게 잘 먹히는지 실험도 해봤어 (experiment)
  6. 이를 통해 이런 사실도 알아냈지만 한계점도 있지 (discussion)
  7. 마지막으로 귀찮은 너를 위해 요약 (conclusion)
- 논문에서 가장 중요한 부분은 Abstract(초록) 파트입니다. 논문 한 편을 다 압축해서 하이라이트만 서술해놓은 부분입니다.
- Conclusion(결론), Introduction(서론)이 그 다음으로 중요하고, 여기까지 읽으면서 전체적인 논문의 흐름을 파악합니다.
- Method(방법)과 Experiment(실험)을 읽으면서 디테일한 부분들을 이해하고 채워나갑니다.

[출처사이트](https://github.com/HYU-AILAB/ai-seminar/wiki/%EB%85%BC%EB%AC%B8-%EC%84%A0%EC%A0%95-%EB%B0%8F-%EC%9D%BD%EB%8A%94-%EB%B0%A9%EB%B2%95).

