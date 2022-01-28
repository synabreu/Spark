## 2장 데이터 주입

##### 데이터 주입(Data Ingestion)은 서로 다른 운영 체제에서 데이터를 처리하고 데이터 분석에 도움이 되도록 데이터 웨어하우스나 데이터 레이크와 같은 중앙 위치로 이동하는 프로세스입니다. 데이터 분석 프로세스의 첫 번째 단계이며 데이터 엔지니어, 데이터 과학자 및 데이터 분석가가 비즈니스 분석을 생성하기 위해 데이터에 액세스, 처리 및 분석할 수 있는 중앙에서 액세스 가능한 영구 저장소를 만드는 데 필요합니다.

##### 따라서, 배치 및 실시간 처리를 위한 데이터 수집 엔진으로서 아파치 스파크의 기능을 소개합니다. 아파치 스파크에서 지원하는 다양한 데이터 소스와 스파크의 DataFrame 인터페이스를 사용하여 액세스하는 방법을 제시합니다.

##### 또한 아파치 스파크의 내장 기능을 사용하여 관계형 데이터베이스 관리 시스템(RDBMS)과 같은 외부 데이터 소스 및 아파치 카프카(Apache Kafka)와 같은 메시지 대기열의 데이터에 액세스하고, 이를 데이터 레이크에 수집하는 방법을 설명합니다. 또한, 정형, 비정형 및 반정형 파일 형식과 같은 다양한 데이터 저장 형식과 이들 간의 주요 차이점도 살펴봅니다. 구조적 스트리밍(Structured Streaming)이라는 스파크의 실시간 스트림 처리 엔진도 소개합니다. 배치 괄 처리와 실시간 스트림 처리를 사용하여 종단 간 데이터 수집 파이프라인을 만드는 방법을 설명합니다. 끝으로, 람다(Lambda) 아키텍처라고 하는 일괄 처리 및 스트림 처리를 통합하는 기술과 Apache Spark를 사용하여 구현하는 방법을 살펴봅니다.

##### 이 장에서는 Apache Spark를 사용하여 배치 처리 및 실시간 수집을 모두 수행하는 데 필요한 필수 기술에 대해 설명합니다. 또한 확장 가능하고 성능이 뛰어난 종단 간 빅 데이터 수집 파이프라인을 구축하는 데 필요한 지식과 도구를 습득합니다.

  - [2.1 기업 의사결정 지원 시스템 소개](https://github.com/synabreu/Spark/blob/main/Chapter02/Decision_Support_00.md)
  - [2.2 데이터 소스로 부터 데이터 주입](https://github.com/synabreu/Spark/blob/main/Chapter02/Data_Sources_00.md)
  - [2.3 데이터를 데이터 싱크 안에 주입](https://github.com/synabreu/Spark/blob/main/Chapter02/Data_Sinks_00.md)
  - [2.4 데이터 레이크에서 데이터 스토리지용 파일 포맷 사용하기](https://github.com/synabreu/Spark/blob/main/Chapter02/File_Formats_00.md)
  - [2.5 배치 및 실시간에서 데이터 주입 파이프라인 빌드하기](https://github.com/synabreu/Spark/blob/main/Chapter02/Ingestion_Pipelines_00.md)
  - [2.6 람다 아키텍처를 사용하여 배치 및 실시간 데이터 주입 통합하기](https://github.com/synabreu/Spark/blob/main/Chapter02/Lambda_Architecture_00.md)
