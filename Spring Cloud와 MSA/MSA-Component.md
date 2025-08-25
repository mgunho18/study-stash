## Service Discovery
micro service 간 통신을 위해 각 서비스 인스턴스의 정보를 관리하는 중앙관리 서버


>Q) service discovery는 SPOF가 될 수 있을까?

>A) 이중화 또는 클러스터링의 형태의 다중 노드 구성을 해 고가용성을 보장한다.<br>
> 이를 위해 노드 간 상태정보 공유가 필수적이며, 이때 gossip 프로토콜과 같은 heartbeat 기반 상태 모니터링 방식이 활용된다.<br>
> 서비스 디스커버리는 최종적 일관성(Eventual Consistency) 모델을 기반으로 하여 높은 가용성과 뛰어난 확장성을 보장한다.


## API Gateway



