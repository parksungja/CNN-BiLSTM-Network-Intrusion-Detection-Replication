# **Efficient CNN-BiLSTM Model Replication for Network Intrusion Detection**

## **Project Overview**
이 저장소에는 Jay Sinha의 연구 프로젝트를 재현한 내용이 포함되어 있습니다. 본 연구에서는 NSL-KDD 및 UNSW-NB15 데이터셋을 활용하여 네트워크 침입 탐지를 위한 효율적인 CNN-BiLSTM 모델을 구현하였습니다. 이 재현 작업은 동일한 데이터셋에서 모델을 재실행하여 결과를 검증하고 연구 과정에 대한 통찰력을 얻기 위해 수행되었습니다. 본 프로젝트는 머신러닝 연구 방법론을 탐구하고, 연구 과정을 이해하며, 결과를 분석하기 위해 수행되었습니다.


## **Datasets Used**

- **NSL-KDD**: 네트워크 침입 탐지 시스템(NIDS)을 위해 중복성을 줄이고 훈련/테스트 세트를 개선한 KDDCup'99 데이터셋의 정제된 버전.
- **UNSW-NB15**: 모델의 견고성을 테스트하기 위해 사용되는, 보다 다양한 공격 범주를 포함하는 포괄적인 데이터셋.

## **Methodologies**

- **Data Preparation**:
  - **Normalization**: 데이터를 [0,1] 범위로 재조정하기 위해 최소-최대 정규화(Min-Max Normalization)를 적용합니다.
  - **One-Hot Encoding**: 범주형 변수를 인코딩하여 모델이 데이터 순서를 잘못 해석하는 것을 방지하기 위해 사용됩니다.
  - **Oversampling**: UNSW-NB15 데이터셋에 적용되어 특히 웜(Worms) 및 퍼저(Fuzzers)와 같은 범주에서 발생하는 클래스 불균형 문제를 처리합니다.
  - **Stratified K-Fold Cross Validation**: 견고한 매개변수 조정 및 분류를 보장합니다.



- **Model Architecture**:
  이 모델은 1차원 컨볼루션 신경망(1-D CNN)과 다중 양방향 LSTM(Bi-LSTM) 레이어를 통합하며, 리셰이프(Reshape) 및 배치 정규화(Batch Normalization) 레이어를 포함하여 특징 추출을 최적화하고 과적합을 줄입니다.
  - **1-D CNN Layers**: 공간적 특징 추출을 위해 사용됩니다.
  - **BiLSTM Layers**: 데이터 내 시간적 의존성을 포착하기 위해 사용됩니다.
  - **Batch Normalization and Max Pooling**: 과적합을 방지하고 모델 성능을 최적화하기 위해 사용됩니다.
  - **Dropout Layer**: 과적합 위험을 추가로 줄이기 위해 통합되었습니다.
  - **Fully Connected Dense Layer**: 최종 예측을 위한 출력 레이어로 사용됨.



## **Evaluation Metrics**

- **Accuracy (ACC)**
- **Detection Rate (DR)**
- **False Positive Rate (FPR)**
- **F1-Score**
- **ROC-AUC Curve**

## **Results**

### **Binary Classification:**
- **NSL-KDD**:
  - **Accuracy**: 99.03% on average
  - **Highest Accuracy**: 99.42%
  - **Detection Rate**: 98.02%
  - **False Positive Rate**: 0.24%

- **UNSW-NB15**:
  - **Accuracy**: 91.95% on average
  - **Highest Accuracy**: 92.71%
  - **Detection Rate**: 93.36%
  - **False Positive Rate**: 7.23%

### **Multi-class Classification:**
- **NSL-KDD**:
  - **Accuracy**: 99.02% on average
  - **Highest Accuracy**: 99.62%
  - **F1-Score**: 0.96

- **UNSW-NB15**:
  - **Accuracy**: 81.9% on average
  - **F1-Score**: 0.53
  - **Discrepancy**: 원본 연구는 92.51%의 검출률과 0.74의 F1 점수를 보고했으며, 이는 본 재현 연구 결과와의 유의미한 차이를 시사한다.

## **Learning and Insights**

본 연구는 데이터 준비, 모델 훈련, 결과 분석을 포함한 머신러닝 연구 프로세스에 대한 이해를 심화하기 위해 수행되었습니다. 특히 UNSW-NB15 다중 분류 결과에서 관찰된 불일치는 연구에서 엄격한 실험과 검증의 중요성을 부각시킵니다. 이 경험은 복잡한 모델의 재현성 문제와 데이터셋 특성 및 모델 튜닝에 따른 결과 변동 가능성에 대한 귀중한 통찰력을 제공했습니다.

## **Resources**

- **Colab Notebook NSL-KDD**: [Link to Colab Notebook]( https://colab.research.google.com/drive/1Ryte-kEg1aOQDYcl_xF-veaJOPcAh1et?usp=sharing)  
- **Colab Notebook UNSW-NB15**: [Link to Colab Notebook]( https://colab.research.google.com/drive/1cD-A-ToovakbDmrzdCf-1TXyQD86hF-n?usp=sharing)  

- **Datasets**:
  - [NSL-KDD Dataset](https://drive.google.com/drive/folders/1oXg_AxHPREXxL-jsX6gj5hSsjIrV6l4c?usp=sharing)
  - [UNSW-NB15 Dataset](https://drive.google.com/drive/folders/1QzqHQFLDzERSL9fBP0rDsCzjKVhK0YTT?usp=sharing)
- **Project Summary PDF**: [Link to PDF Summary](https://drive.google.com/file/d/1ek4QS35fSlhIva2OOt1PPOrn-f_b27gR/view?usp=sharing)
