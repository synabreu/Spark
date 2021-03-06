### 1.1.2 맵리듀스 패러다임을 사용한 데이터 병렬 처리

##### 맵리듀스 패러다임은 데이터 병렬 처리 문제를 세 가지 주요 단계로 나눕니다.

- ##### 맵 스테이지(Map Stage)
- ##### 셔플 스테이지(Shuffle Stage)
- ##### 리듀스 스테이지(Reduce Stage) 

##### 첫째, 맵 스테이지는 입력 데이터 세트를 가져 와서 (key, value) 쌍으로 분할하고 쌍에 일부 처리를 적용하고 다른 (key, value) 쌍 세트로 변환합니다.
##### 둘째, 셔플 스테이지는 Map 스테이지에서 (키, 값) 쌍을 가져오고 동일한 키를 가진 쌍이 함께 끝나도록 섞기/정렬합니다.
##### 셋째, 리듀스 스테이지는 Shuffle 스테이지에서 결과(키, 값) 쌍을 가져오고 쌍을 축소하거나 집계하여 최종 결과를 생성합니다.

##### 여러 맵 스테이지와 여러 리듀스 스테이지가 있을 수 있습니다. 그러나 리듀스 스테이지 단계는 모든 맵 스테이지가 완료된 후에만 시작됩니다. 텍스트 문서에 있는 모든 다른 단어의 개수를 계산하고 여기에 맵리듀스 패러다임을 적용하려는 예를 살펴보겠습니다. 아래의 다이어그램은 맵리듀스 패러다임이 일반적으로 어떻게 작동하는지 보여줍니다.

##### ![맵리듀스 동작 방식](../images/DC-01.png)

##### <그림 1.1> 예제는 다음과 같은 방식으로 작동합니다.

  - ##### 1) <그림 1.1>에는 M1, M2, M3이라는 레이블이 붙은 3개의 노드 클러스터가 있습니다. 각 시스템에는 일반 텍스트로 된 여러 문장이 포함된 몇 개의 텍스트 파일이 있습니다. 여기에서 MapReduce를 사용하여 텍스트 파일의 모든 단어를 계산하는 것입니다.
  - ##### 2) 모든 텍스트 문서를 클러스터에 로드합니다. 각 머신은 해당 머신에 로컬인 문서를 로드합니다.
  - ##### 3) Map Stage는 텍스트 파일을 개별 라인으로 분할하고 각 라인을 개별 단어로 추가로 분할합니다. 그런 다음 각 단어에 1의 개수를 할당하여 (key, value) 쌍을 만듭니다.
  - ##### 4) Shuffle Stage는 Map Stage에서 (key, value) 쌍을 가져와서 같은 키워드를 가진 단어 쌍이 함께 끝나도록 섞기/정렬합니다.
  - ##### 5) Reduce Stage는 모든 키워드를 그룹화하고 해당 개수를 합산하여 각 개별 단어의 최종 개수를 생성합니다.

##### MapReduce 패러다임은 Hadoop 프레임워크에 의해 대중화되었으며 빅 데이터 워크로드를 처리하는 데 꽤 유명했습니다. 그러나 MapReduce 패러다임은 데이터 변환을 위한 매우 낮은 수준의 API를 제공하며 사용자는 Java와 같은 프로그래밍 언어에 대한 능숙한 지식이 있어야 합니다. Map 과 Reduce를 사용하여 데이터 분석 문제를 표현하는 것은 매우 직관적이거나 유연하지 않습니다.

##### MapReduce는 상용 하드웨어에서 실행되도록 설계되었으며 상용 하드웨어는 오류가 발생하기 쉽기 때문에 하드웨어 오류에 대한 복원력이 필요했습니다. MapReduce는 모든 단계의 결과를 디스크에 저장하여 하드웨어 장애에 대한 복원력을 달성합니다. 매 단계 이후에 디스크로의 이러한 왕복은 일반적으로 물리적 디스크의 느린 I/O 성능 때문에 MapReduce가 데이터 처리 속도를 상대적으로 느리게 만듭니다.

##### 이러한 한계를 극복하기 위해 차세대 MapReduce 패러다임이 만들어졌습니다. 이 패러다임은 디스크와 달리 훨씬 빠른 시스템 메모리를 사용하여 데이터를 처리하고 데이터 변환을 표현하기 위해 훨씬 더 유연한 API를 제공했습니다. 이 새로운 프레임워크를 Apache Spark라고 합니다. 

***중요 사항***

분산 컴퓨팅에서 클러스터라는 용어를 자주 접하게 됩니다. 클러스터는 컴퓨팅 문제를 해결하기 위해 단일 장치로 함께 작동하는 컴퓨터 그룹입니다. 클러스터의 기본 시스템은 일반적으로 클러스터의 오케스트레이션 및 관리를 담당하는 마스터 노드라고 하고 실제로 작업 실행을 수행하는 보조 시스템은 워커 노드라고 합니다. 클러스터는 모든 분산 컴퓨팅 시스템의 핵심 구성 요소입니다.

