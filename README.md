# EEG 기반 우울증 분류

## 목차
  - [프로젝트 기본 정보](#프로젝트-기본-정보)
  - [프로젝트 개요](#프로젝트-개요)
  - [프로젝트 설명](#프로젝트-설명)
  - [분석 결과](#분석-결과)
  - [기대 효과](#기대-효과)
  - [Lesson & Learned](#lesson--learned)

## 프로젝트 기본 정보
- 프로젝트 이름: EEG 기반 우울증 분류
- 프로젝트 기간: 2025.07.20 ~ (진행중)
- 사용 언어: Python


## 프로젝트 개요
- 우울증은 전 세계적으로 영향을 미치는 주요 정신 건강 질환으로, 조기 진단이 매우 중요
- 기존 진단은 자가 보고와 전문가 면담에 의존해 객관성과 정량성이 부족하다는 한계 존재
- 이에 따라 EEG(뇌파) 신호를 활용한 자동화된 우울증 분류 연구가 주목받고 있음.
- 따라서 EEG(뇌파) 신호를 활용한 자동 분류 모델을 제안하고자 함.


## 프로젝트 설명
- 건강한 사람과 우울증 환자의 EEG 데이터를 활용하여 Transformer 기반 분류 모델 구현
- Stratified K-Fold 교차검증으로 모델 일반화 평가


## 분석 결과
### 로그 변환 전, 후 비교
- 샘플 피처(AB.C.alpha.r.O1)에 대한 로그 변환 전, 후 비교
<img width="1469" height="436" alt="log before_after" src="https://github.com/user-attachments/assets/01278a1e-bb56-417f-ac83-628490cb97ac" />

### 2. 학습 설정
- Stratifed k-fold cross validation (k=5)
- 클래스 가중치

###  3. 모델 구성
사용 모델: Transformer 기반 이진 분류 모델
입력: 정제된 EEG feature 벡터
출력: 우울증 / 건강 분류
<img width="1310" height="283" alt="Model architecture" src="https://github.com/user-attachments/assets/a6df24d6-ab37-4854-baff-7ee602c72c55" />

### 결론
- Transformer 모델은 정확도 81.37%, F1 점수 80.32%, 정밀도 82.36%, 그리고 재현율 81.37% 달성
- 우울증 분류의 재현율은 81%였으며, 일부 경우 오분류 발생
- ROC AUC가 0.826이므로 모델의 분류 성능 개선 필요
<img width="1124" height="311" alt="result" src="https://github.com/user-attachments/assets/69f8a364-1ec6-48d4-97ae-369c1f4233f4" />


## 기대 효과
- 우울증 조기 진단을 통한 악화 예방
- 객관적인 진단 가능

  
## Lesson & Learned
- 도메인 및 EEG 데이터에 대한 이해 부족으로 한계 발생
- 건강한 집단과 우울증 집단의 차이를 비교할 수 있도록 그래프 시각화 추가
- 데이터 누수 문제 해결 필요
- 피처 그룹 기준 학습 필요
- 향후 절대 대역 파워 데이터만을 활용하여 다양한 머신러닝 모델에 적용 후 분류 성능 비교 및 검증 예정
- PCA 적용과 미적용 차이 비교 필요
- 기존 연구에 비해 성능이 낮기 때문에 다른 전처리 방법(PCA 등) 및 모델 튜닝과 같은 추가 개선이 필요
