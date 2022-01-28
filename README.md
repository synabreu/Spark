# Spark

##### 그 동안 Spark로 데이터 레이크 및 SparkML 머신러닝 프로젝트 했던 경험 노하우를 공유합니다.  
##### 먼저 아파치 스파크(Apache Spark)에 대해 알아보면, 빠르고 범용적인 클러스터 컴퓨팅 시스템을 말합니다. Java, Scala, Python, R의 고수준 API와 표준적인 실행 그래프를 지원하는 최적화된 엔진을 제공합니다. 또한 SQL과 같은 구조화된 데이터 처리를 위한 Spark SQL, 머신 러닝을 위한 MLlib, 그래프 처리를 위한 GraphX, 스파크 스트리밍을 포함한 고급 도구 셋등을 풍부하게 지원합니다.

***중요사항***
##### 소스 및 마크다운 문서에 대하여 Folks 나 Clone은 자유로나 만일 상용으로 사용하거나 다른 곳에 사용할 때는 반드시 관련된 레퍼런스를 꼭 해 주시기 바랍니다. 

### 1. 개요
#####  1) 스파크는 로컬 PC, Amazon EMR Custer 상에서 Notebook Instance 그리고 최근에 Spark on Kubernetes (EKS)에서 설치와 개발, 실행, 모니터링이 가능합니다.  
#####  2) 주의사항: 로컬 PC에서는 3가지 프레임워크 버전이 맞아야 합니다. 현재 저는 Anaconda 3 환경에서 Python 3.8 과 Java 8 version, 그리고 Spark 3.1.2 / Hadoop 2.7 버전을 사용하고 있습니다. 자세한 설치 가이드는 현재 작성 중에 있으니 완성되면 공유하도록 하겠습니다.
#####  3) 로컬 PC 시스템과 클라우드 실행 차이점: 로컬과 클라우드에서 Spark 실행은 거의 모두 동일하나 파일을 불러 올때 Path 와 불러올 때 함수가 차이가 납니다. 그외 RDD, SparkSQL, Spark DataFrame, SparkML (MLib)은 동일합니다.

#### 다음은 스파크에 관련한 내용에 대해 간단한 개요를 설명한 링크들입니다. 

- 0.1 스파크의 개요 및 구성요소
  - [0.1.1 스파크 아키텍처](https://github.com/synabreu/Spark/blob/main/Chapter00/Spark_Introduction_01.md)
  - [0.1.2 탄력적인 분산 데이터셋(RDD,Resilient Distrubuted Datasets)](https://github.com/synabreu/Spark/blob/main/Chapter00/Spark_Introduction_02.md)
  - [0.1.3 SQL, DataFrames 과 외부의 데이터셋](https://github.com/synabreu/Spark/blob/main/Chapter00/Spark_Introduction_03.md)
  - [0.1.4 구조적인 스트리밍](https://github.com/synabreu/Spark/blob/main/Chapter00/Spark_Introduction_04.md)
  - [0.1.5 스파크 스트리밍](https://github.com/synabreu/Spark/blob/main/Chapter00/Spark_Introduction_05.md)
  - [0.1.6 MLib(머신러닝)](https://github.com/synabreu/Spark/blob/main/Chapter00/Spark_Introduction_06.md)
  
- 1장 분산 컴퓨팅 개요
  - [1.1 분산 컴퓨팅 소개](https://github.com/synabreu/Spark/blob/main/Chapter01/Distributed_Computing_00.md) 
  - [1.2 Apache Spark를 사용한 분산 컴퓨팅](https://github.com/synabreu/Spark/blob/main/Chapter01/Apache_Spark_01.md)
  - [1.3 Spark SQL 및 DataFrames를 사용한 빅 데이터 처리](https://github.com/synabreu/Spark/blob/main/Chapter01/Spark_SQL_01.md)

- 2장 데이터 주입(https://github.com/synabreu/Spark/blob/main/Chapter02/Chapter02.md)
  - [2.1 기업 의사결정 지원 시스템 소개](https://github.com/synabreu/Spark/blob/main/Chapter02/Decision_Support_00.md)
  - [2.2 데이터 소스로 부터 데이터 주입](https://github.com/synabreu/Spark/blob/main/Chapter02/Data_Sources_00.md)
  - [2.3 데이터를 데이터 싱크 안에 주입](https://github.com/synabreu/Spark/blob/main/Chapter02/Data_Sinks_00.md)
  - [2.4 데이터 레이크에서 데이터 스토리지용 파일 포맷 사용하기](https://github.com/synabreu/Spark/blob/main/Chapter02/File_Formats_00.md)
  - [2.5 배치 및 실시간에서 데이터 주입 파이프라인 빌드하기](https://github.com/synabreu/Spark/blob/main/Chapter02/Ingestion_Pipelines_00.md)
  - [2.6 람다 아키텍처를 사용하여 배치 및 실시간 데이터 주입 통합하기](https://github.com/synabreu/Spark/blob/main/Chapter02/Lambda_Architecture_00.md)











