# DACON: [도배 하자 유형 분류 AI 경진대회](https://dacon.io/competitions/official/236082/overview/description)
<img alt="Html" src ="https://img.shields.io/badge/dacon Final rank-Top 6%25-lightblue?style=for-the-badge"/>

#### 총 19가지의 도배 하자 유형을 분류하는 AI 모델을 개발 (23.04.10 - 23.05.22) - 길다영, 김준용

##### 📊 [PUBLIC] 57/1028 (상위 10%) 점수: 0.65692
##### 📊 [PRIVATE] 55/1028 (상위 10%) 점수: 0.66688

<br><br>

### K-Fold, Ensemble, CutMix 사용
- DACON 다른 대회에서 좋은 성적을 냈던 Image Classfication 코드를 주어진 Dataset에 맞도록 수정하여 훈련. <br>
  - *DACON 작물 병해 분류 AI 경진대회: [수달이팀, Private 4위(점수:0.99769)](https://dacon.io/competitions/official/235842/codeshare/3657)*

- efficientnet_v2_l 모델 사용, Optimizer 변경, Scheduler 추가
```
self.model = models.efficientnet_v2_l(pretrained=True)
optimizer = torch.optim.AdamW(model.parameters(), lr=CFG["LEARNING_RATE"])
scheduler = lr_scheduler.CosineAnnealingLR(optimizer, T_max=10)
```

<br>

### 불균형 Class 해소 위해 Data Augmentation 진행
- DACON 다른 대회에서 좋은 성적을 냈던 코드를 주어진 Dataset에 맞도록 수정하여 데이터 불균형 해소함. <br>
  - *월간 데이콘 Computer Vision 이상치 탐지 알고리즘 경진대회: [[Private 5위, 0.89376] 데이터 증강](https://dacon.io/en/competitions/official/235894/codeshare/4946?page=1&dtype=recent)*

- image개수가 90개 이하인 class들만 적용해서 data augmentation 진행함.


<br>

### Hyperparameters
```
CFG = {
    'IMG_SIZE':224,
    'EPOCHS':100,
    'LEARNING_RATE':2e-4,
    'BATCH_SIZE':32,
    'SEED':100,
    'FOLD' : 5,
}
```
<br>

### Transform
- Train dataset에만 RandomCrop(), RandomHorizontalFlip(), RandomPerspective() 적용

<br>

### 아쉬운 점
- 시간이 부족해 Data Aaugmentataion된 데이터셋으로 Image Classification을 돌리지 못함.

- Data Augmentation 데이터셋 이용해 epoch 300으로 모델 훈련 시, 더 좋은 성능 보일 거라 예상. 


