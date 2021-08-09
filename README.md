# Spark

#### 그 동안 Spark로 데이터 레이크 및 SparkML 머신러닝 프로젝트했던 경험 노하우와 소스파일, 설치 방법등을 공개했습니다.
####  PC의 로컬 (저는 맥을 현재 사용하고 있습니다.) 이나 Amazon EMR Cluster 에서 Notebook Instances 에서 실행하고, 또한 최근에 Spark on Kubernetes (EKS) 에서 설치해 보았습니다.
####  로컬 PC에서는 3가지 프레임워크가 맞아야 합니다. 현재 저는 Anaconda 3 환경에서 Python 3.8 과 Java 8 version, 그리고 Spark 3.1.2 / Hadoop 2.7 버전을 사용하고 있습니다.
####  로컬과 클라우드에서 Spark 실행은 거의 모두 동일하나 파일을 불러 올때 Path 와 불러올 때 함수가 차이가 납니다. 그외 RDD, SparkSQL, Spark DataFrame, SparkML (MLib)은 동일합니다.
####  
