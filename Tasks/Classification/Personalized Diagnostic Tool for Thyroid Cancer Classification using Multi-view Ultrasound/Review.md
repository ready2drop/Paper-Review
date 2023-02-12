# Personalized Diagnostic Tool for Thyroid Cancer Classification using Multi-view Ultrasound


#### Accepted by MICCAI 2022
#### Official code : None
###### Cite as : Huang, Han, et al. "Personalized Diagnostic Tool for Thyroid Cancer Classification Using Multi-view Ultrasound." Medical Image Computing and Computer Assisted Intervention–MICCAI 2022: 25th International Conference, Singapore, September 18–22, 2022, Proceedings, Part III. Cham: Springer Nature Switzerland, 2022.
###### Index : *Thyroid Cancer*, *Ultrasound*, *Multi-view*, *Classification*
------


### Abstract
> Over the past decades, the incidence of thyroid cancer has been increasing globally. Accurate and early diagnosis allows timely treatment and helps to avoid over-diagnosis. Clinically, a nodule is commonly evaluated from both transverse and longitudinal views using thyroid ultrasound. However, the appearance of the thyroid gland and lesions can vary dramatically across individuals. Identifying key diagnostic information from both views requires specialized expertise. Furthermore, finding an optimal way to integrate multi-view information also relies on the experience of clinicians and adds further difficulty to accurate diagnosis. To address these, we propose a personalized diagnostic tool that can customize its decision-making process for different patients. It consists of a multi-view classification module for feature extraction and a personalized weighting allocation network that generates optimal weighting for different views. It is also equipped with a self-supervised view-aware contrastive loss to further improve the model robustness towards different patient groups. Experimental results show that the proposed framework can better utilize multi-view information and outperform the competing methods.

> 지난 수십년간 갑상선 암의 발병률은 전세계적으로 증가로 조기 진단의 필요성이 대두됨. 갑상선의 해부학적 특징상 개인별 병변의 크기와 모양은 크게 다르므로 본 논문에서는 갑상선의 가로, 세로 방향의 multi-view 초음파 사진을 사용하여 결절 평가를 하고자 함. 특징 추출을 위한 multi-view classification으로 최적의 가중치 생성하는 네트워크 제안하고 모델 견고성을 향상 시키기 위해 self-supervised view-aware contrastive loss 적용하였음. 그 결과 ACC=83.29%, SEN=89.97%, SPE=70.31%, PRE=85.49% and F1-score=87.67% 의 성능을 보임
--------
### Introduction

#### Dataset
![img_1](https://user-images.githubusercontent.com/89971553/218296978-686b7cef-bb3d-4159-87a2-9bfd60b66b46.jpg)
- Each set contains a pair of multi-view (a transverse and a longitudinal views) US images
- Data augmentation : scaling, rotation, flipping, and mixup

#### Training and Inference
- We use the AdamW optimizer with a learning rate of 5e-4
- The weight decay is set to 0.05. 
- We randomly split the dataset at the patient level into 7:1:2 for training, validation, and test

#### Model Architectures
![img_2](https://user-images.githubusercontent.com/89971553/218296986-074771e7-6885-455c-aae6-b90e6eb451b1.jpg)
- MVC model(Multi-view classification)
- The feature extraction Backbone : Swin-transformer 
- (ft,fl)은 Personalized Weighting allocation network(PAWN)으로 보내져 output이 Wt, Wl
- Multiview data에 대한 contrastive loss equipped with view awareness 적용
- generate view-specific decisions(Pred) 을 생성하기 위해 다층퍼셉트론(MLP) 통과 
- Benign or Malignant (Binary classification)

---------
### Result
![img_3](https://user-images.githubusercontent.com/89971553/218296996-ab2979bd-6bd5-4c44-beb3-73e7ac1a4bc3.jpg)
- MVMT, AADNN are trained only using transverse or longitudinal view, MVMT higher ACC and PRE. It might be caused by its larger size with greater modeling capacity. 
- The AW3M model scored higher F1-score, displaying a balanced performance
- AdaMML model proposed to analyze multi-modal data for video classification and learns to discard modalities to improve accuracy.


--------
### Contribution
- Longitudinal view help to promote diagnosis accuracy than transverse view
- 병변의 편차가 크기때문에 Multiview data에 대한 contrastive loss equipped with view awareness 적용
-PAWN과 VACL design이 향후 multi-view or multimodal problems in future applications 적용 가능할 것




--------
### Conclusion
- Multi-view US를 활용한 갑상선암 진단을 위한 맞춤형 진단 도구로 본 논문에서 제안한 MVC model without the PWAN and VACL이 단일 시점 모델과 다중시점 모델 sota보다 가장 유망한 성능 달성
- 추후 초음파 진단 분류 task에서 multi view로 분석하는 것이 단일 view 보다 정확도 향상 기대 

