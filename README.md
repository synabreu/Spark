# Spark

#### 그 동안 Spark로 데이터 레이크 및 SparkML 머신러닝 프로젝트했던 경험 노하우와 소스파일, 설치 방법등을 공개합니다. 

####  1. 개요: Spark는 로컬 PC, Amazon EMR Custer 상에서 Notebook Instance 그리고 최근에 Spark on Kubernetes (EKS)에서 설치와 개발, 실행, 모니터링이 가능합니다.  
####  2. 주의사항: 로컬 PC에서는 3가지 프레임워크가 맞아야 합니다. 현재 저는 Anaconda 3 환경에서 Python 3.8 과 Java 8 version, 그리고 Spark 3.1.2 / Hadoop 2.7 버전을 사용하고 있습니다.
####  3. 로컬과 클라우드 실행 차이점: 로컬과 클라우드에서 Spark 실행은 거의 모두 동일하나 파일을 불러 올때 Path 와 불러올 때 함수가 차이가 납니다. 그외 RDD, SparkSQL, Spark DataFrame, SparkML (MLib)은 동일합니다.
####  
