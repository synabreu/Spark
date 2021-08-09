# Spark

#### 그 동안 Spark로 데이터 레이크 및 SparkML 머신러닝 프로젝트했던 경험 노하우와 소스파일, 설치 방법등을 공개합니다. 
#### 먼저 아파치 스파크(Apache Spark)에 대해 알아보면, 빠르고 범용적인 클러스터 컴퓨팅 시스템을 말합니다. Java, Scala, Python, R의 고수준 API와 표준적인 실행 그래프를 지원하는 최적화된 엔진을 제공합니다. 또한 SQL과 같은 구조화된 데이터 처리를 위한 Spark SQL, 머신 러닝을 위한 MLlib, 그래프 처리를 위한 GraphX, 스파크 스트리밍을 포함한 고급 도구 셋등을 풍부하게 지원합니다.

## 1. 개요
####  1) 스파크는 로컬 PC, Amazon EMR Custer 상에서 Notebook Instance 그리고 최근에 Spark on Kubernetes (EKS)에서 설치와 개발, 실행, 모니터링이 가능합니다.  
####  2) 주의사항: 로컬 PC에서는 3가지 프레임워크 버전이 맞아야 합니다. 현재 저는 Anaconda 3 환경에서 Python 3.8 과 Java 8 version, 그리고 Spark 3.1.2 / Hadoop 2.7 버전을 사용하고 있습니다. 자세한 설치 가이드는 현재 작성 중에 있으니 완성되면 공유하도록 하겠습니다.
####  3) 로컬 PC 시스템과 클라우드 실행 차이점: 로컬과 클라우드에서 Spark 실행은 거의 모두 동일하나 파일을 불러 올때 Path 와 불러올 때 함수가 차이가 납니다. 그외 RDD, SparkSQL, Spark DataFrame, SparkML (MLib)은 동일합니다.
####  


