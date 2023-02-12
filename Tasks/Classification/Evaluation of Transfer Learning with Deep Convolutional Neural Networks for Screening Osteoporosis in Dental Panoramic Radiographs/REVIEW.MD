
# Evaluation of Transfer Learning with Deep Convolutional Neural Networks for Screening Osteoporosis in Dental Panoramic Radiographs


#### Accepted by MDPI 2020
#### Official code : None
###### Cite as : Lee KS, Jung SK, Ryu JJ, Shin SW, Choi J. Evaluation of Transfer Learning with Deep Convolutional Neural Networks for Screening Osteoporosis in Dental Panoramic Radiographs. J Clin Med. 2020 Feb 1;9(2):392. doi: 10.3390/jcm9020392. PMID: 32024114; PMCID: PMC7074309.
###### Index : *Osteoporosis*, *Dental panoramic radiographs*, *Deeplearning*, *Classification*
------


### Abstract
> Dental panoramic radiographs (DPRs) provide information required to potentially evaluate bone density changes through a textural and morphological feature analysis on a mandible. This study aims to evaluate the discriminating performance of deep convolutional neural networks (CNNs), employed with various transfer learning strategies, on the classification of specific features of osteoporosis in DPRs. For objective labeling, we collected a dataset containing 680 images from different patients who underwent both skeletal bone mineral density and digital panoramic radiographic examinations at the Korea University Ansan Hospital between 2009 and 2018. Four study groups were used to evaluate the impact of various transfer learning strategies on deep CNN models as follows: a basic CNN model with three convolutional layers (CNN3), visual geometry group deep CNN model (VGG-16), transfer learning model from VGG-16 (VGG-16_TF), and fine-tuning with the transfer learning model (VGG-16_TF_FT). The best performing model achieved an overall area under the receiver operating characteristic of 0.858. In this study, transfer learning and fine-tuning improved the performance of a deep CNN for screening osteoporosis in DPR images. In addition, using the gradient-weighted class activation mapping technique, a visual interpretation of the best performing deep CNN model indicated that the model relied on image features in the lower left and right border of the mandibular. This result suggests that deep learning-based assessment of DPR images could be useful and reliable in the automated screening of osteoporosis patients.

> 치과 파노라마 방사선 사진(DPR)은 하악골의 질감 및 형태적 특징 분석으로 잠재적인 골밀도 변화를 평가하는데 필요한 정보를 제공함. 따라서 본 논문에서는 DPR에서 전이학습과 CNN의 식별 성능으로 골다공증의 분류 평가를 목표
가장 성능이 좋은 모델은 0.858 AUC의 성능을 보임 DPR 이미지의 딥러닝 기반 평가가 골다공증 환자의 automated screeening에 유용하고 신뢰할 수 있음을 시사

--------
### Introduction

#### Dataset
![img4](https://user-images.githubusercontent.com/89971553/218298030-2cd00ca5-8816-492e-8833-994ddb3876ac.jpg)
680 panoramic radiograph images from 680 different patients who  simultaneously underwent skeletal BMD examinations and digital panoramic radiography evaluations within four months

![img1](https://user-images.githubusercontent.com/89971553/218298049-c70dac6e-2ee9-4ea4-949d-af9ef31ec653.jpg)
Downsampled to a uniform size of 1200 × 630
- ROI : lower part of the mandible (700 × 140 pixels)

#### Training and Inference
![img3](https://user-images.githubusercontent.com/89971553/218298591-eff61bef-bc59-4b90-b631-accedf0dfbbf.jpg)
- 5-fold cross validation to evaluate the model training(80:20) while avoiding overfitting or bias
- The CNN models of this study were trained using a cross-entropy loss function

#### Model Architectures
![img2](https://user-images.githubusercontent.com/89971553/218298629-251fc02b-02d0-47ae-9c3f-2a3e21e791a1.jpg)
- CNN
  - Widely adopted and recognized as state-of-the-art in both general and medical image classification tasks
- VGG16-TR(transfer learning)
- VGG16-TR(transfer learning)-FT(Fine tuning)
  - two transfer learning version models (VGG16-TR and VGG16-TR-FT) employed pre-trained weights using the “ImageNet”

#### Model Performance

---------
### Result
![img5](https://user-images.githubusercontent.com/89971553/218298829-f33ed933-a9c5-4f81-9dcd-4cab6f35b22c.jpg) 
![img8](https://user-images.githubusercontent.com/89971553/218298783-55836eec-ac83-4776-851d-767e3319795b.jpg)
- Best predictive model : VGG16-TR-TF
  - AUC 0.858 Sensitivity 0.900 Specificity 0.815 Accuracy 0.840

#### Class activation mapping(Grad-CAM)
<img src = https://user-images.githubusercontent.com/89971553/218298908-c2eb6d4b-6e6a-4b14-a8f6-0126570f7591.jpg width = 50% height = 50% >
<img src = https://user-images.githubusercontent.com/89971553/218298911-697fa178-e0b3-4ad7-8373-48ff5e58a8ef.jpg width = 50% height = 50% >

- Model : VGG16-TR-TF
   - Correct prediction : region showing the strong lower boundary of the mandible cortical bone and the dense texture around its “periphery” was extracted as the main image feature of the classification
   - Wrong prediction : central region of the mandible or the ghost images of the hyoid bone was extracted as the main image feature


--------
### Contribution
- DPR은 치열 및 턱의 인접 구조를 평가하기 위해 일반적으로 수행되지만 골다공증 및 경동맥 석회화와 같은 전신 질환을 선별하기 위해 DPR을 기반으로 하는 임상 보조 진단(CAD) 시스템이 제안되었음
- 모델의 Transfer learning과 Fine tuning이 골다공증 스크리닝 성능 향상에 도움을 줌
- Grad-CAM 기법 활용 DPR 영상에서 골다공증 선별에 주요 임상적인 부위 특징 규명




--------
### Conclusion
- 요추 x-ray가 아닌 DPR 이미지를 사용하여 딥러닝 기반 골다공증을 선별하는데 효율적인 솔루션 제시
- DPR 영상에서 하악골 하연의 좌우 중앙으로 해면골 조직이 치밀하지 않을 때 주요 특징으로서 분류


