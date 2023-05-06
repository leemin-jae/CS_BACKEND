# CS_BACKEND
cs 면접 정리

## CS 관련 지식

### DB

<details>
  <summary>데이터베이스에서 인덱스를 사용하는 이유 및 장단점에 대해 설명해주세요.</summary>
  </br>
  <p>데이터베이스에서 인덱스를 사용하는 이유는 검색성능을 향상시키기 위함입니다.</p>
  <p>하지만 검색성능을 실질적으로 향상시키기 위해서는 해당 쿼리가 index를 사용하는지, 카디널리티, Selectivity 같은 요소들이 고려된 인덱스가 생성되어야 합니다.</p>
  <p>일반적인 경우의 장점으로는 빠른 검색 성능을 들 수 있습니다.</p>
  <p>일반적인 경우의 단점으로는 인덱스를 구성하는 비용 즉, 추가, 수정, 삭제 연산시에 인덱스를 형성하기 위한 추가적인 연산이 수행됩니다.</p>
  <p>따라서, 인덱스를 생성할 때에는 트레이드 오프 관계에 놓여있는 요소들을 종합적으로 고려하여 생성해야합니다.</p>
</details>

<details>
  <summary>트랜잭션에 대해서 설명해주세요.</summary>
  </br>
  <p>트랜잭션이란 데이터베이스의 상태를 변화시키는 하나의 논리적인 작업 단위라고 할 수 있으며, 트랜잭션에는 여러개의 연산이 수행될 수 있습니다.</p>
  <p>트랜잭션은 수행중에 한 작업이라도 실패하면 전부 실패하고, 모두 성공해야 성공이라고 할 수 있습니다.</p>
</details>

<details>
  <summary>ACID에 대해서 설명해주세요.</summary>
  </br>
  <p>ACID는 트랜잭션이 안전하게 수행된다는 것을 보장하기 위한 성질입니다.</p>
  <p>
    <ul>
      <li>Atomicity(원자성): 트랜잭션의 연산은 모든 연산이 완벽히 수행되어야 하며, 한 연산이라도 실패하면 트랜잭션은 실패해야 합니다.</li>
      <li>Consistency(일관성): 트랜잭션은 유효한 상태로만 변경될 수 있습니다.</li>
      <li>Isolation(고립성): 트랜잭션은 동시에 실행될 경우 다른 트랜잭션에 의해 영향을 받지 않고 독립적으로 실행되어야 합니다.</li>
      <li>Durability(내구성): 트랜잭션이 커밋된 이후에는 시스템 오류가 발생하더라도 커밋된 상태로 유지되는 것을 보장해야 합니다. (일반적으로 비휘발성 메모리에 데이터가 저장되는 것을 의미)</li>
    </ul>
  </p>
</details>

<details>
  <summary>트랜잭션 격리 수준(Transaction Isolation Levels)에 대해서 설명해주세요.</summary>
  </br>
  <p>트랜잭션 격리수준은 고립도와 성능의 트레이드 오프를 조절합니다.</p>
  <p>
    <ul>
      <li>READ UNCOMMITTED: 다른 트랜잭션에서 커밋되지 않은 내용도 참조할 수 있다.</li>
      <li>READ COMMITTED: 다른 트랜잭션에서 커밋된 내용만 참조할 수 있다.</li>
      <li>REPEATABLE READ: 트랜잭션에 진입하기 이전에 커밋된 내용만 참조할 수 있다.</li>
      <li>SERIALIZABLE: 트랜잭션에 진입하면 락을 걸어 다른 트랜잭션이 접근하지 못하게 한다.(성능 매우 떨어짐)</li>
    </ul>
  </p>
</details>

<details>
  <summary>정규화에 대해서 설명해주세요.</summary>
  </br>
  <p>정규화는 데이터의 중복방지, 무결성을 충족시키기 위해 데이터베이스를 설계하는 것을 의미합니다.</p>
  <p>이 이상을 물어보는 경우가 있었는데, 학습이 좀 더 필요한 것 같습니다.</p>
</details>

<details>
  <summary>JOIN에 대해서 설명해주세요.</summary>
  </br>
  <p>단순히 SQL에서 JOIN 쿼리가 어떤식으로 동작하는지 알고 있어야 합니다.</p>
  <p>다이어그램으로 이해하는 편이 좋습니다.</p>
</details>

<details>
  <summary>RDBMS vs NOSQL에 대해서 설명해주세요.</summary>
  </br>
  <p>RDBMS는 데이터베이스를 이루는 객체들의 릴레이션을 통해서 데이터를 저장하는 데이터베이스입니다. SQL을 사용해 데이터의 저장, 질의, 수정, 삭제를 할 수 있으며 데이터를 효율적으로 보관하는 것을 목적으로 하고 구조화가 굉장히 중요합니다.</p>
  <p>장점으로는 명확한 데이터 구조를 보장하고, 중복을 피할 수 있습니다.</p>
  <p>NOSQL은 RDBMS에 비해 자유로운 형태로 데이터를 저장합니다. 또한 수평확장을 할 수 있고 분산처리를 지원합니다. 다양한 형태의 NOSQL 데이터베이스가 있고, 대표적으로 key-value store, bigtable, dynamo, document db, graph db 등이 있습니다.</p>
  <p>둘은 대체될 수 있는 것이 아니고, 각각 필요한 시점에 적절히 선택해서 사용해야 합니다. 둘 다 같이쓰는 상호보완적인 존재가 될 수도 있습니다.</p>
</details>

<details>
  <summary>Redis에 대해서 간단히 설명해주세요.</summary>
  </br>
  <p>Redis는 key-value store NOSQL DB입니다. 싱글스레드로 동작하며 자료구조를 지원합니다. 그리고 다양한 용도로 사용될 수 있도록 다양한 기능을 지원합니다. 데이터의 스냅샷 혹은 AOF 로그를 통해 복구가 가능해서 어느정도 영속성도 보장됩니다.</p>
  <p>스프링에서는 세션을 관리하거나, 캐싱을 하는데에 자주 사용되는 것으로 알고 있습니다.</p>
</details>

<details>
  <summary>Redis와 Memcached의 차이에 대해서 설명해주세요.</summary>
  </br>
  <p>Redis는 싱글 스레드 기반으로 동작하고, Memcached는 멀티스레드를 지원해서 멀티 프로세싱이 가능합니다.</p>
  <p>Redis는 다양한 자료구조를 지원하고, Memcached는 문자열 형태로만 저장합니다.</p>
  <p>Redis는 여러 용도로 사용할 수 있도록 다양한 기능을 지원합니다.</p>
  <p>Redis는 스냅샷, AOF 로그를 통해서 데이터 복구가 가능합니다.</p>
</details>

<details>
  <summary>Elastic Search에 대해서 간단히 설명해주세요.</summary>
  </br>
  <p>Elastic Search는 자바로 개발된 오픈소스 검색엔진 입니다. 보통 단독으로 사용하기보다는 ELK 스택이라고 부르는 Logstash, Kibana, Beats를 추가적으로 사용합니다.</p>
  <p>Inverted Index 구조로 데이터를 저장해서, 전문(Full-text) 검색시에 RDBMS에 비해 뛰어난 성능을 보장합니다.</p>
  <p>다양한 용도로 사용할 수 있습니다. (데이터 저장, 문서 검색, 위치 검색, 머신 러닝 기반 검색, 로그 분석, 보안 감사 분석 등)</p>
</details>

<details>
  <summary>Elastic Search의 인덱스구조와 RDBMS의 인덱스 구조의 차이에 대해 설명해주세요.</summary>
  </br>
  <p>Elastic Search는 Inverted-Index 구조로 데이터를 저장합니다. 이는 책의 색인을 생각해보면 쉬운데, 특정 단어가 출현하는 doc을 저장하는 것입니다. 반면 RDBMS는 B-Tree와 그와 유사한 인덱스를 사용합니다. 데이터가 어디에 존재하는지 어떤 순서로 저장하는 지의 차이라고 생각합니다. RDBMS에도 다양한 인덱스 구조가 있으나 여기서 예로 든 것은 B-Tree 인덱스입니다.</p>
</details>

<details>
  <summary>Elastic Search의 키워드 검색과 RDBMS의 LIKE 검색의 차이에 대해 설명해주세요.</summary>
  </br>
  <p>Elastic Search의 키워드 검색은 document를 저장할 때 수행하는 알고리즘과 동일한 알고리즘으로 키워드를 분리합니다. 그 중에서 랭킹알고리즘을 통해서 가장 유사한 순서대로 결과를 나타냅니다.</p>
  <p>RDBMS에서의 LIKE 검색은 와일드카드로 시작하지 않는 경우에만 인덱스를 사용하고 나머지 경우는 전체를 탐색하기 때문에 상대적으로 느립니다.</p>
</details>

<details>
  <summary>MongoDB에 대해서 간단히 설명해주세요.</summary>
  </br>
  <p></p>
</details>

<details>
  <summary>CAP 이론과, Eventual Consistency에 대해서 설명해주세요.</summary>
  </br>
  <p>CAP 이론은 분산 환경에서 모두를 만족하는 시스템은 없다는 이론입니다.</p>
  <p>
    <ul>
      <li>Consitenty(일관성): ACID의 일관성과는 약간 다릅니다. 모든 노드가 같은 시간에 같은 데이터를 보여줘야 한다는 것입니다.</li>
      <li>Availability(가용성): 모든 동작에 대한 응답이 리턴되어야 합니다.</li>
      <li>Partition Tolerance(분할 내성): 시스템 일부가 네트워크에서 연결이 끊기더라도 동작해야 합니다.</li>
    </ul>
  </p>
  <p>CAP는 해당 시스템이 이거다 하고 말하기 곤란한게 어떻게 클러스터링 하느냐에 따라 달라질 수 있습니다. 그렇기 때문에 어떤 전략을 취할 때 어떤 것을 선택했는가를 잘 알아야 합니다. (단순히 MySQL이 CA입니다. 보다는 어떤 이유로 CA인지 근거를 생각해보기) 그리고 어느정도 한계가 있는 이론이고 PACELC 이론이라고 또 있습니다.</p>
  <p>Eventual Consistency는 이 Consistency를 보장해주지 못하기 때문에 나온 개념으로, Consistency를 완전히 보장하지는 않지만, 결과적으로 언젠가는 Conssistency가 보장됨을 의미합니다.</p>
</details>

데이터베이스란 무엇인가요?
데이터베이스에서 테이블이란 무엇인가요?
관계형 데이터베이스와 NoSQL 데이터베이스의 차이는 무엇인가요?
인덱스(Index)란 무엇이며 어떤 경우에 사용하나요?
정규화(Normalization)란 무엇이며 왜 필요한가요?
ACID란 무엇이며 어떤 역할을 하나요?
트랜잭션이란 무엇이며 왜 필요한가요?
쿼리 튜닝(Query tuning)이란 무엇이며 어떤 방법이 있는가요?
데이터베이스 백업과 복구에 대해 설명해주세요.
데이터베이스 보안에 대해 설명해주세요.
SQL Injection이란 무엇이며 어떻게 방지할 수 있나요?

데이터베이스 트리거(Trigger)란 무엇이며 어떤 경우에 사용하나요?
데이터베이스 뷰(View)란 무엇이며 어떤 경우에 사용하나요?
데이터베이스 샤딩(Sharding)이란 무엇이며 어떤 장단점이 있나요?
데이터베이스 파티셔닝(Partitioning)이란 무엇이며 어떤 경우에 사용하나요?
데이터베이스 인덱스(Index)의 종류와 장단점은 무엇인가요?
트랜잭션 격리 수준(Transaction Isolation Level)이란 무엇이며 어떤 것이 있나요?
비정규화(De-normalization)란 무엇이며 어떤 경우에 사용하나요?
데이터베이스 트랜잭션(Transaction)의 성질에는 어떤 것이 있나요?
데이터베이스 락(Lock)의 종류와 장단점은 무엇인가요?
인덱스 클러스터링(Index Clustering)이란 무엇이며 어떤 장단점이 있나요?
NoSQL 데이터베이스의 특징과 장단점은 무엇인가요?
데이터베이스 쿼리(Query) 최적화에 대해 설명해주세요.
데이터베이스의 트랜잭션(Transaction)과 락(Lock)의 관계는 무엇인가요?
OLTP(Online Transaction Processing)와 OLAP(Online Analytical Processing)의 차이점은 무엇인가요?
데이터베이스 스키마(Schema)란 무엇이며 어떤 경우에 사용하나요?
데이터베이스 데드락(Deadlock)이란 무엇이며 어떻게 방지할 수 있나요?
데이터베이스 복제(Replication)란 무엇이며 어떤 경우에 사용하나요?
데이터베이스 인덱스(Index)의 작동 원리는 무엇인가요?
데이터베이스 성능 개선 방법에는 어떤 것이 있나요

DB정의, 장단점, 설계 시 고려해야할 점
데이터베이스에서 인덱스를 사용하는 이유 및 장단점
인덱스의 종류
트랜잭션에 대해서 
ACID
트랜잭션 격리 수준(Transaction Isolation Levels)에 대해서
정규화에 대해서 
.JOIN에 대해서 
샤딩이란?
RDBMS의 트리거란?
Table과 View의 차이
.RDBMS vs NOSQL
NoSQL의 CAP이론
Redis
Elastic Search
Elastic Search의 인덱스구조와 RDBMS의 인덱스 구조의 차이
Elastic Search의 키워드 검색과 RDBMS의 LIKE 검색의 차이
MongoDB에 대해서 
SQL Injection이란?
DB Key 종류 및 의미
