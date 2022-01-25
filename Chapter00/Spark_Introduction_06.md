### 0.1.6 MLib (머신러닝)

##### MLlib는 Spark의 머신러닝(ML) 라이브러리입니다. 이 라이브러리의 목표는 실용적인 머신러닝을 확장 가능하고 쉽게 만드는 것입니다. 고수준에서 다음과 같은 도구를 제공합니다.

##### * ML 알고리즘: 분류, 회귀, 클러스터링 및 협업 필터링과 같은 일반적인 학습 알고리즘
##### * 피쳐: 피쳐 추출, 변환, 차원 축소 및 선택
##### * 파이프라인: ML 파이프라인을 구성, 평가 및 튜닝하기 위한 도구
##### * 지속성: 알고리즘, 모델 및 파이프라인 저장 및 로드
##### * 유틸리티: 선형 대수학, 통계, 데이터 처리 등

##### MLlib의 RDD 기반 API는 이제 유지관리 모드에 있습니다. Spark 2.0부터 spark.mllib 패키지의 RDD 기반 API가 유지 관리 모드에 들어갔습니다. Spark용 기본 Machine Learning API는 이제 spark.ml 패키지의 DataFrame 기반 API입니다. 그 이유는 MLlib는 버그 수정과 함께 spark.mllib에서 RDD 기반 API를 계속 지원하기 때문입니다. 따라서 더 이상 MLlib는 RDD 기반 API에 새로운 기능을 추가하지 않습니다.참고로 Spark 2.x 릴리스에서 MLlib는 DataFrames 기반 API에 기능을 추가하여 RDD 기반 API와 기능 패리티에 유사합니다.

#### 1) MLlib가 DataFrame 기반 API로 전환하는 이유는 무엇입니까?

##### DataFrame은 RDD보다 사용자 친화적인 API를 제공합니다. DataFrames의 많은 이점에는 Spark Datasources, SQL/DataFrame 질의, Tungsten 및 Catalyst 최적화, 언어 간 균일한 API 등이 있습니다.
MLlib용 DataFrame 기반 API는 ML 알고리즘과 여러 언어에서 균일한 API를 제공합니다. DataFrame은 실용적인 ML 파이프라인, 특히 기능 변환을 용이하게 합니다.  

#### 2) "스파크 ML"이란 무엇입니까?

##### "Spark ML"은 공식 명칭은 아니지만 가끔 MLlib DataFrame 기반 API를 지칭하는 데 사용됩니다. 이는 주로 DataFrame 기반 API에서 사용하는 org.apache.spark.ml Scala 패키지 이름과 초기에 파이프라인 개념을 강조하기 위해 사용한 "Spark ML Pipelines" 용어 때문입니다.

#### 3) MLlib가 더 이상 사용되지 않습니까?

##### 그렇지 않습니다. MLlib에는 RDD 기반 API와 DataFrame 기반 API가 모두 포함되어 있습니다. RDD 기반 API는 이제 유지관리 모드만 사용하고 더 이상 최신 API도 더 이상 사용되지 않으며 MLlib도 전체적으로 사용되지 않을 뿐입니다. 



