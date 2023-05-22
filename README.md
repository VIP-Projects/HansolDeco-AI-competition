# DACON: [도배 하자 유형 분류 AI 경진대회](https://dacon.io/competitions/official/236082/overview/description)

#### 총 19가지의 도배 하자 유형을 분류하는 AI 모델을 개발 (23.04.10 - 23.05.22) 
#### 📊 [PUBLIC] 57/1028 (상위 10%) 점수: 0.65692
#### 📊 [PRIVATE] 55/1028 (상위 10%) 점수: 0.66688

<br><br>

### K-Fold, Ensemble, CutMix 사용
- DACON 다른 대회에서 좋은 성적을 냈던 Image Classfication 코드를 주어진 Dataset에 맞도록 수정하여 훈련. <br>
  - [DACON 작물 병해 분류 AI 경진대회](https://dacon.io/competitions/official/235842/codeshare/3657): 수달이팀, Private 4위(점수:0.99769)
  
- Optimizer: torch.optim.AdamW(model.parameters(), lr=2e-4)
- Scheduler 추가: lr_scheduler.CosineAnnealingLR(optimizer, T_max=10)

<br>

### 불균형 class 해소 위해 Data Augmentation 진행
- DACON 다른 대회에서 좋은 성적을 냈던 코드를 주어진 Dataset에 맞도록 수정하여 데이터 불균형 해소함. <br>
  - [월간 데이콘 Computer Vision 이상치 탐지 알고리즘 경진대회](https://dacon.io/en/competitions/official/235894/codeshare/4946?page=1&dtype=recent): [Private 5위, 0.89376] 데이터 증강

- image개수가 90개 이하인 class들만 적용해서 data augmentation 진행함.


<br>

### Hyperparameters

'IMG_SIZE'|'EPOCHS'|'LEARNING_RATE'|'BATCH_SIZE'|'SEED'|'FOLD'
--|--|--|--|--|--
224|100|2e-4|32|100|5



