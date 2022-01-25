### 0.1.2 탄력적인 분산 데이터셋(RDD, Resilient Distrubuted Datasets)

##### RDD에 대해 좀더 자세히 설명하자면, Spark는 병렬로 작동할 수 있는 내결함성(fault-torelance) 콜렉션으로 탄력적인 분산 데이터셋(RDD) 중심으로 합니다. RDD를 생성하는 두 가지 방법이 있습니다. 드라이버 프로그램에서 기존 컬렉션을 병렬화하거나 공유 파일 시스템인 HDFS, HBase 또는 Hadoop InputFormat을 제공하는 모든 데이터 소스와 같은 외부 스토리지 시스템의 데이터셋을 참조하는 것입니다.
