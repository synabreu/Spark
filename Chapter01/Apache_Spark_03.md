### 1.2.2 RDD를 사용한 데이터 병렬 처리

##### RDD는 아파치 스파크 프레임워크의 핵심 추상화입니다. RDD는 일반적으로 프로그래밍 언어에서 발견되지만 단 하나가 아닌 여러 머신의 메모리에 상주하는 모든 종류의 불변 데이터 구조입니다. 또한, RDD는 RDD의 논리적 분할인 파티션으로 구성되며 그 중 몇 개는 각각 시스템으로 구성됩니다. 아래의 <그림 1-2>의 다이어그램은 RDD 및 해당 파티션의 개념을 설명하는 데 도움이 됩니다.

##### ![<그림 1-2> RDD 다이어그램](../images/DC-02.png)
##### <그림 1-2> RDD 다이어그램

##### 이전 다이어그램에는 3개의 머신 또는 노드로 구성된 클러스터가 있습니다. 클러스터에는 3개의 RDD가 있으며 각 RDD는 파티션으로 나뉩니다. 클러스터의 각 노드에는 개별 RDD의 몇 개의 파티션이 포함되며 각 RDD는 파티션을 통해 클러스터의 여러 노드에 분산됩니다.RDD 추상화에는 파티션 내에 저장된 데이터를 조작하기 위해 RRD에서 작동할 수 있는 고급 기능 세트가 수반됩니다. 이러한 함수를 고차 함수(Higher-Order Function)라고 합니다.
