# Start-SageMaker
이 자습서에서는 Amazon SageMaker를 사용하여 기계 학습(ML) 모델을 구축, 훈련 및 배포하는 방법을 알려드립니다. 이 실습에서는 일반적으로 사용하는 XGBoost ML 알고리즘을 사용합니다. Amazon SageMaker는 개발자와 데이터 과학자가 대규모로 기계 학습 모델을 구축, 훈련 및 배포할 수 있는 완전 관리형 모듈식 기계 학습 서비스입니다.

일반적으로 기계 학습 모델을 개념화에서부터 프로덕션까지 진행시키는 작업은 복잡하고 시간이 오래 걸립니다. 모델을 훈련하기 위한 대량의 데이터를 관리하고, 훈련에 가장 적합한 알고리즘을 선택하고, 훈련하는 도중에 컴퓨팅 용량을 관리하고, 나중에는 모델을 프로덕션 환경에 배포해야 합니다. Amazon SageMaker는 기계 학습 모델을 훨씬 간편하게 구축 및 배포함으로써 이러한 복잡성을 낮춥니다. 다양한 옵션 중에서 적절한 알고리즘과 프레임워크를 선택하고 나면, Amazon SageMaker가 모델을 페타바이트 규모로 훈련하기 위한 모든 기본 인프라를 관리하고 프로덕션에 배포합니다.

이 자습서에서는 은행에서 일하는 기계 학습 개발자라고 가정합니다. 여러분은 고객이 예금 증서(CD)에 등록할지 예측하는 기계 학습 모델 개발 요청을 받았습니다. 모델은 고객 인구 통계 정보, 마케팅 행사에 대한 반응, 외부 요소에 대한 정보가 포함된 마케팅 데이터 세트로 훈련됩니다.

데이터 세트는 여러분의 편의에 따라 레이블이 표시되었고, 데이터 세트에 있는 열은 고객이 은행에서 제안하는 상품에 등록했는지 여부를 나타냅니다. 이 데이터 세트 버전은 어바인 소재의 University of California에서 큐레이션한 기계 학습 리포지토리에서 공개 제공됩니다. 이 자습서에서는 데이터에 레이블이 표시되어 있으므로 지도형 기계 학습 모델을 구현합니다. (데이터 세트에 레이블이 표시되지 않았을 때 비지도형 학습이 발생합니다.)
이 자습서 개요

노트북 인스턴스 생성
데이터 준비
데이터에서 학습하도록 모델 훈련
모델 배포
기계 학습 모델의 성능 평가
 
이 자습서에서 생성되고 사용된 리소스는 AWS 프리 티어에 해당합니다. 7단계를 완료하고 리소스를 종료해야 합니다. 2개월 이상 계정에서 이 리소스가 활성화되어 있으면 계정에 0.50 USD 미만의 비용이 청구됩니다.


# 1단계. Amazon SageMaker 콘솔 열기
## Amazon SageMaker 콘솔로 이동합니다.
여기를 클릭하면 AWS Management Console이 새 창에서 열리므로 이 단계별 안내서를 계속 열어 놓을 수 있습니다. 검색창에 SageMaker를 입력하고 Amazon SageMaker를 선택해서 서비스 콘솔을 엽니다.

![image](https://d1.awsstatic.com/tmt/build-train-deploy-machine-learning-model-sagemaker/build-train-deploy-machine-learning-model-sagemaker-1.dc780f9c52f4be8442c3ffdb735606bb51ca6e5d.png)

# 2단계. Amazon SageMaker 노트북 인스턴스 생성
## 이 단계에서는 Amazon SageMaker 노트북 인스턴스를 생성합니다. 

### 2a. Amazon SageMaker 대시보드에서 노트북 인스턴스를 선택합니다. 

![image](https://d1.awsstatic.com/tmt/build-train-deploy-machine-learning-model-sagemaker/build-train-deploy-machine-learning-model-sagemaker-2a.11efeb24074ebbfea5a13b30b6365ef830f29fd2.png)
