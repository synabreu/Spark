### 1.2.5 스파크 시작하기

##### 지금까지 RDD라고 하는 아파치 스파크의 핵심 데이터 구조, RDD를 조작하는 데 사용되는 고차 함수라고 하는 함수 및 아파치 스파크 클러스터의 구성 요소에 대해 배웠습니다. 고차 함수를 사용하는 방법에 대한 몇 가지 코드 조각도 보았습니다. 그렇다면, 이 절에서는 지식을 실제 사용에 적용하고 PySpark라는 스파크의 Python API를 사용하여 단어 수 계산 애플리케이션을 만드는 첫 번째 아파치 스파크 프로그램을 작성합니다. 그러나 먼저 시작하려면 몇 가지 사항이 필요합니다.

  - ##### 아파치 스파크 클러스터
  - ##### 데이터세트
  - ##### 단어 수 응용 프로그램의 실제 코드

##### 스파크 클러스터를 생성하기 위해 Databricks의 무료 Community Edition을 사용할 것입니다. 사용된 코드는 여기에 있고, 필요한 리소스에 대한 링크는 장의 시작 부분에 있는 기술 요구 사항 섹션에서 찾을 수 있습니다.

***알림***

##### 여기에서는 Databricks Spark Clusters를 사용하고 있지만 Spark 클러스터에서 액세스할 수 있는 위치에서 데이터가 제공되는 한 스파크 3.0 이상을 실행하는 모든 Spark 클러스터에서 제공된 코드를 실행할 수 있습니다. 이제 RDD, 고차 함수, 람다 및 Spark 아키텍처와 같은 Spark의 핵심 개념을 이해했으므로 다음 코드를 사용하여 첫 번째 Spark 애플리케이션을 구현해 보겠습니다.

~~~
lines = sc.textFile("/databricks-datasets/README.md") 
words = lines.flatMap(lambda s: s.split(" ")) 
word_tuples = words.map(lambda s: (s, 1)) 
word_count = word_tuples.reduceByKey(lambda x, y:  x + y) 
word_count.take(10) 
word_count.saveAsTextFile("/tmp/wordcount.txt") 
~~~

##### 이전 코드 조각 모음에서는 다음과 같이 수행됩니다.
