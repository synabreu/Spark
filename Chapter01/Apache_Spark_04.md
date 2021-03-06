### 1.2.3 고차 함수

##### 고차 함수는 RDD를 조작하고 파티션 내에 저장된 데이터를 변환하는 비즈니스 논리를 작성하는 데 도움이 됩니다. 고차 함수(Higher-Order Function)는 다른 함수를 파라미터로 받아들이고 이러한 내부 함수는 데이터를 변환하고 RDD의 각 파티션에 병렬로 적용되는 실제 비즈니스 로직을 정의하는 데 도움이 됩니다. 고차 함수에 파라미터로 전달된 이러한 내부 함수를 람다 함수(Lambda Function) 또는 람다라고 합니다.

##### 아파치 스파크에는 다음과 같은 몇 가지 고차 함수가 있습니다.

##### 몇 가지 예를 들면 map, flatMap, reduce, fold, filter, reduceByKey, join 및 union이 있습니다. 이러한 함수는 고수준 함수이며 데이터 조작 논리를 매우 쉽게 표현하는 데 도움이 됩니다. 예를 들어, 앞에서 설명한 단어 개수 예제를 고려하자면, 텍스트 파일을 RDD로 읽고 공백과 같은 구분 기호를 기반으로 각 단어를 분할하려고 한다고 가정해 보겠습니다. RDD 및 고차 함수로 표현된 코드는 다음과 같습니다.

~~~
lines = sc.textFile("/databricks-datasets/README.md")
words = lines.flatMap(lambda s: s.split(" ")) 
word_tuples = words.map(lambda s: (s, 1)) 
~~~

##### 위의 소스 코드 조각의 동작원리는 다음과 같이 설명합니다. 

##### 1. 내장된 sc.textFile() 메서드를 사용하여 텍스트 파일을 로드하고 있습니다. 이 메서드는 지정된 위치의 모든 텍스트 파일을 클러스터 메모리로 로드하고, 개별 라인으로 분할하고, 라인 또는 문자열의 RDD를 반환합니다. 
##### 2. 그런 다음 flatMap() 고차 함수를 라인의 새 RDD에 적용하고 각 라인을 공백에 따라 분할하도록 지시하는 함수를 제공합니다. 우리가 flatMap()에 전달하는 람다 함수는 StringType의 개별 라인인 하나의 파라미터를 취하고 단어 목록을 반환하는 단순히 익명의 함수입니다. flatMap() 및 lambda() 함수를 통해 행의 RDD를 단어의 RDD로 변환할 수 있습니다.
##### 3. 마지막으로 map() 함수를 사용하여 모든 개별 단어에 1의 개수를 할당합니다. 이것은 Java 프로그래밍 언어를 사용하여 MapReduce 애플리케이션을 개발하는 것과 비교하여 매우 쉽고 확실히 더 직관적입니다.

##### 그러므로, 내용을 요약하자면 아파치 스파크 프레임워크의 기본 구성은 RDD입니다. RDD는 클러스터의 개별 노드에 분산된 파티션으로 구성됩니다. 고차 함수라고 하는 특수 함수를 사용하여 RDD에서 작동하고 비즈니스 논리에 따라 RDD를 변환합니다. 이 비즈니스 로직은 람다 또는 익명 함수의 형태로 고차 함수를 통해 워커 노드에 전달됩니다. 고차 함수와 람다 함수의 내부 작동을 더 깊이 파고들기 전에 아파치 스파크 프레임워크의 아키텍처와 일반적인 스파크 클러스터의 구성 요소를 이해해야 합니다. 

***알림***
##### RDD의 탄력적인 부분은 모든 RDD가 자신의 계보를 알고 있다는 사실에서 비롯됩니다. 특정 시점에서 RDD에는 수행된 모든 개별 작업에 대한 정보가 있으며 데이터 소스 자체까지 거슬러 올라갑니다. 따라서 오류로 인해 Executor가 손실되고 해당 파티션 중 하나 이상이 손실된 경우, 계보 정보를 사용하여 소스 데이터에서 해당 파티션을 쉽게 다시 생성할 수 있으므로 실패에 대한 복원력이 있습니다.

