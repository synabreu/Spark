### 1.3.1 Spark DataFrame으로 데이터 변환

##### 아파치 스파크 1.3부터 스파크 SQL 엔진이 RDD API 위에 계층으로 추가되고, 스파크의 모든 컴포넌트로 확장되어 개발자에게 더욱 사용하기 쉽고 친숙한 API를 제공합니다. 수년에 걸쳐 스파크 SQL 엔진과 해당 DataFrame 및 SQL API는 더욱 강력해졌으며, 일반적으로 스파크를 사용하기 위한 사실상의 권장하는 표준이 되었습니다. 모든 데이터 처리 요구 사항에 대해 DataFrame 동작이나 스파크 SQL 문을 독점적으로 사용할 것이며 RDD API를 거의 사용하지 않을 것입니다.

##### 스파크의 DataFrame을 판다스(Pandas)의 DataFrame 또는 행과 명명된 열이 있는 관계형 데이터베이스 테이블로 있다면, 유일한 차이점은 스파크의 DataFrame이 단일 시스템 대신 여러 시스템의 메모리에 상주한다는 것입니다. 다음 다이어그램은 3개의 워커 머신에 분산된 3개의 열이 있는 스파크의 DataFrame을 보여줍니다.

##### Figure 1.4 ­ A distributed DataFrame

##### Spark DataFrame은 행과 명명된 열로 구성된 RDD와 같은 변경할 수 없는 데이터 구조이기도 합니다. 여기서 각 개별 열은 모든 유형이 될 수 있습니다. 또한 DataFrame에는 데이터를 조작할 수 있는 오퍼레이(operation)이 포함되어 있으며, 일반적으로 이러한 오퍼레이션 집합을 **도메인 지정 언어(DSL, Domain Specific Language)**이라고 합니다. Spark DataFrame 작업은 두 가지 주요 범주, 즉 변환 및 액션으로 그룹화할 수 있습니다.

##### RDD API를 통해 DataFrames 또는 Spark SQL을 사용할 때의 한 가지 이점은 스파크 SQL 엔진에 Catalyst라는 내장 쿼리 최적화 프로그램이 함께 제공된다는 것입니다. 이 Catalyst 옵티마이저는 데이터에 대한 사용 가능한 통계와 함께 사용자 코드를 분석하여 쿼리에 대한 최상의 실행 계획을 생성합니다. 이 쿼리 계획은 Executor의 자바 JVM 내에서 기본적으로 실행되는 자바 바이트코드로 추가 변환됩니다. 이것은 사용된 프로그래밍 언어와 관계없이 발생하므로 스칼라, 자바, 파이썬, R 또는 SQL을 사용하여 작성되었는지 여부에 관계없이 대부분의 경우 스파크 SQL 엔진을 통해 처리된 모든 코드의 성능이 동일합니다.

  - ##### **Transformations:** DataFrame의 데이터를 조작하여 다른 DataFrame을 생성하는 DataFrame에서 수행되는 오퍼레이션입니다. Transformation의 몇 가지 예는 ***read, select, where, filter, join*** 및 ***groupBy***입니다.
  - ##### **Actions:** 실제로 결과가 계산되어 콘솔에 인쇄되거나 더 실질적으로 저장 위치에 다시 기록되도록 하는 오퍼레이션을 말합니다. 이러한 오퍼레이션의 몇 가지 예에는 ***write, count*** 및 ***show***가 있습니다.
  - ##### **Lazy evaluation:** Spark Transformation은 lazy evaluation 입니다. 즉, Transformation이 선언되는 즉시 평가되지 않으며 액션이 호출될 때까지 데이터가 메모리에 표시되지 않습니다. 이는 액션이 호출될 때까지 Spark 옵티마이저가 모든 Transformation을 평가하고 코드에서 최상의 성능과 효율성을 얻기 위해 가장 최적의 실행 계획을 생성할 수 있는 기회를 제공하기 때문에 몇 가지 이점이 있습니다. Spark의 Catalyst 옵티마이저와 결합된 Lazy Evaluation의 장점은 데이터 변환 논리를 표현하는 데만 집중할 수 있고, 코드에서 최고의 성능과 효율성을 얻기 위해 변환을 특정 순서로 정렬하는 것에 대해 너무 많이 걱정할 필요가 없다는 것입니다. 이렇게 하면 태스크의 생산성을 높이고 새 프레임워크의 복잡성으로 인해 당황하지 않을 수 있습니다.

***중요 사항***
##### Pandas DataFrames와 비교하여 Spark DataFrames는 선언되는 즉시 메모리에 표시되지 않습니다. 액션이 호출될 때만 메모리에 나타납니다. 마찬가지로 DataFrame 오퍼레이션은 Spark의 Catalyst 옵티마이저가 최상의 실행 계획을 생성하고 때로는 몇 가지 작업을 단일 단위로 결합하기 때문에 지정한 순서대로 실행될 필요는 없습니다.

##### 이전에 RDD API를 사용하여 구현한 단어 수 예제를 가져와 DataFrame DSL을 사용하여 구현해 보겠습니다.

~~~
from pyspark.sql.functions import split, explode
linesDf = spark.read.text("/databricks-datasets/README.md") 
wordListDf = linesDf.select(split("value", " ").alias("words")) wordsDf = wordListDf.select(explode("words").alias("word")) 
wordCountDf = wordsDf.groupBy("word").count() 
wordCountDf.show() 
wordCountDf.write.csv("/tmp/wordcounts.csv") 
~~~

##### 위의 소스 코드 조각 모음은 다음과 같이 설명할 수 있습니다. 

  - ##### 1. 먼저 PySpark SQL 함수 라이브러리에서 몇 가지 함수 중에 split 과 explode 컴포넌트를 import 해서 가져옵니다.
  - ##### 2. 그런 다음 StringType 행의 DataFrame을 생성하는 SparkSession read.text() 메서드를 사용하여 텍스트를 읽습니다.
  - ##### 3. 그런 다음 split() 함수를 사용하여 모든 줄을 개별 단어로 분리합니다. 결과는 실제로 단어 목록인 값이라는 단일 열이 있는 DataFrame입니다.
  - ##### 4. 그런 다음, explode() 함수를 사용하여 각 행의 단어 목록을 별도의 행에 있는 모든 단어로 분리합니다. 그 결과는 word 레이블이 지정된 열이 있는 DataFrame입니다.
  - ##### 5. 이제 드디어 단어를 셀 준비가 되었습니다. 따라서 단어 열을 기준으로 단어를 그룹화하고 각 단어의 개별 발생 횟수를 계산합니다. 최종 결과는 두 열, 즉 실제 단어와 해당 개수의 DataFrame입니다.
  - ##### 6. show() 함수를 사용하여 결과의 표본을 볼 수 있으며, 마지막으로 write() 함수를 사용하여 결과를 영구 저장소에 저장할 수 있습니다.

##### 위의 소스 코드에서 show() 또는 write() 함수가 액션입니다. select() 및 groupBy()를 포함한 다른 모든 함수는 Transformation 이며 Spark job을 action은 아닙니다. 

***알림*** 
##### read() 함수는 Transformation 이지만 때때로 실제로 스파크 잡(job)을 action 한다는 것을 알 수 있습니다. 그 이유는 특정 구조화 및 반정형 구데이터 형식의 경우, 스파크가 기본 파일에서 스키마 정보를 추론하고 이를 수행하기 위해 실제 파일의 작은 하위 집합을 처리하기 때문입니다.
