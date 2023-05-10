# CS_BACKEND
cs 면접 정리

## CS 관련 지식

### DB

<details>
  <summary>데이터베이스, DBMS란 무엇인가, 사용하는 이유는 무엇인가</summary>
  </br>
  <p>DB (데이터베이스)는 체계적으로 구성된 데이터의 모임을 말합니다. 데이터는 컴퓨터에서 처리할 수 있는 숫자, 문자, 이미지, 음성 등의 형태가 있으며, 데이터베이스는 이러한 데이터들이 저장, 관리, 처리되는 공간입니다.</p>
  <p>DBMS는 데이터베이스 관리 시스템으로, 여러 사용자가 DB에 접근, 사용할 수 있도록 해주는 소프트웨어</p>
  <p>파일 시스템의 단점을 보완하여 데이터의 중복, 검색 등의 문제를 해결하기 위해서 사용</p>
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
  <summary>데이터베이스에서 인덱스를 사용하는 이유 및 장단점에 대해 설명해주세요.</summary>
  </br>
  <p>데이터베이스에서 인덱스를 사용하는 이유는 검색성능을 향상시키기 위함입니다.</p>
  <p>하지만 검색성능을 실질적으로 향상시키기 위해서는 해당 쿼리가 index를 사용하는지, 카디널리티, Selectivity 같은 요소들이 고려된 인덱스가 생성되어야 합니다.</p>
  <p>인덱스는 보통 B-트리(B-Tree)나 해시(Hash) 등의 자료구조를 사용하여 구현됩니다. B-트리 인덱스는 범위 검색에 뛰어나고, 해시 인덱스는 등값 검색에 효과적입니다.</p>
  <p>일반적인 경우의 장점으로는 빠른 검색 성능을 들 수 있습니다.</p>
  <p>일반적인 경우의 단점으로는 인덱스를 구성하는 비용 즉, 추가, 수정, 삭제 연산시에 인덱스를 형성하기 위한 추가적인 연산이 수행됩니다.인덱스를 생성하면 디스크 공간과 추가적인 쓰기 연산이 필요하므로, 인덱스를 너무 많이 사용하면 오히려 성능이 저하될 수 있습니다. 또한 인덱스가 자주 업데이트되는 경우에는 오버헤드가 발생할 수 있습니다. </p>
  <p>따라서, 인덱스를 생성할 때에는 트레이드 오프 관계에 놓여있는 요소들을 종합적으로 고려하여 생성해야합니다.</p>
</details>

<details>
  <summary>인덱스 클러스터링(Index Clustering)이란 무엇이며 어떤 장단점이 있나요?</summary>
  </br>
  <p>인덱스 클러스터링(Index Clustering)은 데이터베이스에서 인덱스와 데이터가 물리적으로 동일한 영역에 저장되는 것을 의미합니다. 즉, 클러스터형 인덱스(Clustered Index)를 생성하면 인덱스 키의 값을 기준으로 데이터가 정렬되어 저장됩니다.</p>
  <p> 장점
    <ul>
      <li>테이블에 대한 클러스터형 인덱스는 하나만 생성할 수 있습니다. 따라서 테이블에 대해 자주 사용되는 여러 개의 쿼리가 있다면, 하나의 클러스터형 인덱스로 모두 처리할 수 없을 수 있습니다.</li>
      <li>클러스터형 인덱스의 키 값이 변경되는 경우, 해당 레코드를 다시 정렬해야 하기 때문에 비용이 많이 듭니다. 따라서 키 값이 자주 변경되는 테이블에서는 클러스터형 인덱스를 사용하는 것이 적합하지 않을 수 있습니다.</li>
      <li>클러스터형 인덱스를 사용하면 인덱스 키의 값에 따라 데이터가 정렬되어 저장되기 때문에, 키 값의 분포가 균등하지 않은 경우 인덱스의 효율성이 떨어질 수 있습니다.</li>
    </ul>
  </p>
  <p> 단점
    <ul>
      <li>데이터베이스에서 인덱스를 검색할 때 물리적인 I/O 비용이 감소합니다. 클러스터형 인덱스는 인덱스 키의 값을 기준으로 데이터가 정렬되어 저장되기 때문에 검색 시 빠르게 찾을 수 있습니다.</li>
      <li>범위 검색(Range Scan)의 성능이 향상됩니다. 클러스터형 인덱스는 인덱스 키의 값에 따라 데이터가 정렬되어 저장되기 때문에 범위 검색 시 효율적으로 처리할 수 있습니다.</li>
    </ul>
  </p>
  <p>어떤 인덱스를 사용할지 선택하는 것은 해당 테이블에 대한 데이터의 사용 패턴에 따라 달라질 수 있습니다. 검색 작업이 빈번하고 대량의 데이터가 저장된 경우 클러스터형 인덱스를 사용하는 것이 적합하며, 검색 작업보다는 데이터 수정, 삭제, 추가 등의 작업이 빈번하게 발생하는 경우에는 비클러스터형 인덱스를 사용하는 것이 적합합니다.</p>
</details>

<details>
  <summary>클러스터형 인덱스(Clustered Index)와 비클러스터형 인덱스(Non-clustered Index)의 차이는 무엇인가요?</summary>
  </br>
  <p>데이터베이스에서 인덱스를 사용하는 이유는 검색성능을 향상시키기 위함입니다.</p>
  <p>
    <ul>
      <li>클러스터형 인덱스: 테이블의 모든 데이터를 지정된 칼럼 기준으로 정렬하여 저장하는 인덱스입니다. 이 때 지정된 칼럼은 유일한 값을 가져야 합니다. 클러스터형 인덱스는 테이블 당 하나만 생성할 수 있으며, 테이블 자체가 인덱스를 형성하므로 데이터베이스에서 매우 빠른 검색 속도를 제공합니다.</li>
      <li>비클러스터형 인덱스: 인덱스가 지정된 칼럼을 기준으로 데이터를 정렬하지만, 데이터 자체는 인덱스와 별도의 영역에 저장됩니다. 이 때 지정된 칼럼은 유일한 값을 가질 필요가 없습니다. 하나의 테이블에 여러 개의 비클러스터형 인덱스를 생성할 수 있으며, 인덱스를 사용하여 데이터를 찾는 데 시간이 더 걸릴 수 있지만, 데이터의 추가, 수정, 삭제 등의 작업이 발생했을 때 클러스터형 인덱스보다 더 빠르게 처리됩니다.</li>
    </ul>
  </p>
  <p>어떤 인덱스를 사용할지 선택하는 것은 해당 테이블에 대한 데이터의 사용 패턴에 따라 달라질 수 있습니다. 검색 작업이 빈번하고 대량의 데이터가 저장된 경우 클러스터형 인덱스를 사용하는 것이 적합하며, 검색 작업보다는 데이터 수정, 삭제, 추가 등의 작업이 빈번하게 발생하는 경우에는 비클러스터형 인덱스를 사용하는 것이 적합합니다.</p>
</details>

<details>
  <summary>트랜잭션에 대해서 설명해주세요.</summary>
  </br>
  <p>트랜잭션이란 데이터베이스의 상태를 변화시키는 하나의 논리적인 작업 단위라고 할 수 있으며, 트랜잭션에는 여러개의 연산이 수행될 수 있습니다.</p>
  <p>트랜잭션은 수행중에 한 작업이라도 실패하면 전부 실패하고, 모두 성공해야 성공이라고 할 수 있습니다.</p>
  <p> 트랜잭션은 데이터베이스에서 데이터의 일관성과 무결성을 보장하는 데 필수적인 개념이며, 데이터베이스에서 데이터를 안전하게 처리하기 위해서 반드시 사용되어야 합니다.</p>
</details>

<details>
  <summary>ACID에 대해서 설명해주세요.</summary>
  </br>
  <p>ACID는 트랜잭션이 안전하게 수행된다는 것을 보장하기 위한 성질입니다.</p>
  <p>
    <ul>
      <li>Atomicity(원자성): 트랜잭션의 연산은 모든 연산이 완벽히 수행되어야 하며, 한 연산이라도 실패하면 트랜잭션은 실패해야 합니다.</li>
      <li>Consistency(일관성): 트랜잭션은 유효한 상태로만 변경될 수 있습니다. DB 규칙, 조건 등을 지켜야한다.</li>
      <li>Isolation(고립성): 트랜잭션은 동시에 실행될 경우 다른 트랜잭션에 의해 영향을 받지 않고 독립적으로 실행되어야 합니다.</li>
      <li>Durability(내구성): 트랜잭션이 커밋된 이후에는 시스템 오류가 발생하더라도 커밋된 상태로 유지되는 것을 보장해야 합니다. (일반적으로 비휘발성 메모리에 데이터가 저장되는 것을 의미)</li>
    </ul>
  </p>
</details>

<details>
  <summary>트랜잭션 격리 수준(Transaction Isolation Levels)에 대해서 설명해주세요.</summary>
  </br>
  <p>트랜잭션 격리 수준(Transaction Isolation Level)은 여러 개의 트랜잭션이 동시에 실행될 때, 각 트랜잭션이 다른 트랜잭션의 영향을 받는 정도를 나타내는 개념입니다. 데이터베이스 시스템은 트랜잭션 격리 수준을 설정하여 데이터의 일관성과 무결성을 유지하면서 동시성을 향상시킵니다.</p>
  <p>
    <ul>
      <li>READ UNCOMMITTED: 다른 트랜잭션에서 커밋되지 않은 내용도 참조할 수 있다.</li>
      <li>READ COMMITTED: 다른 트랜잭션에서 커밋된 내용만 참조할 수 있다.</li>
      <li>REPEATABLE READ: 트랜잭션에 진입하기 이전에 커밋된 내용만 참조할 수 있다.</li>
      <li>SERIALIZABLE: 트랜잭션에 진입하면 락을 걸어 다른 트랜잭션이 접근하지 못하게 한다. 모든 트랜잭션을 순차적으로 실행하는 것처럼 동작합니다.(성능 매우 떨어짐)</li>
    </ul>
  </p>
</details>

<details>
  <summary>트랜잭션의 락(Lock)이란 무엇인가요? 공유 락(Shared Lock)과 배타적 락(Exclusive Lock)의 차이는 무엇인가요?</summary>
  </br>
  <p>트랜잭션에서 락(Lock)은 동시에 여러 트랜잭션이 같은 데이터에 접근할 때, 데이터의 일관성과 무결성을 유지하기 위해 사용되는 기술입니다. 트랜잭션이 데이터에 락을 걸면, 다른 트랜잭션은 그 데이터를 변경하거나 접근할 수 없게 됩니다.</p>
  <p>공유 락(Shared Lock)은 여러 트랜잭션이 동시에 데이터를 읽을 수 있는 락입니다. 여러 트랜잭션이 동시에 같은 데이터에 접근할 수 있지만, 그 데이터를 변경할 수 없습니다. 공유 락을 사용하는 경우 데이터베이스는 데이터의 일관성을 유지하면서 여러 트랜잭션이 동시에 데이터를 읽을 수 있도록 합니다.</p>
  <p>배타적 락(Exclusive Lock)은 특정 트랜잭션이 데이터를 읽고 쓸 수 있는 락입니다. 배타적 락을 건 트랜잭션이 해당 데이터를 사용 중일 때, 다른 트랜잭션은 그 데이터를 읽거나 쓸 수 없습니다. 배타적 락을 사용하는 경우 데이터베이스는 데이터의 무결성을 보장하기 위해 여러 트랜잭션들이 동시에 데이터를 변경하는 것을 방지합니다.</p>
</details>

<details>
  <summary>트랜잭션의 데드락(Deadlock)이란 무엇인가요? 이를 방지하기 위한 방법은 무엇인가요?</summary>
  </br>
  <p>데드락(Deadlock)은 두 개 이상의 트랜잭션이 서로 상대방이 가지고 있는 락을 기다리며 무한히 대기하는 상황을 말합니다. 이러한 상황에서는 어떤 트랜잭션도 진행되지 못하며, 시스템의 성능 저하나 데이터 불일치 문제를 일으킬 수 있습니다.</p>
  <p>데드락을 방지하기 위한 방법은 크게 두 가지가 있습니다. 첫 번째 방법은 트랜잭션들이 데이터베이스 객체에 접근하는 순서를 일관성 있게 유지하는 것입니다. 이를 위해서는 트랜잭션들이 데이터베이스 객체에 접근할 때 일정한 순서로 접근하도록 강제하는 방법이 있습니다. 두 번째 방법은 트랜잭션들이 필요한 데이터베이스 객체를 사용할 때 락을 설정하는 순서를 일관성 있게 유지하는 것입니다. 이를 위해서는 모든 트랜잭션에서 데이터베이스 객체에 접근할 때 일정한 순서로 락을 설정하도록 강제하는 방법이 있습니다.</p>
</details>


<details>
  <summary>정규화에 대해서 설명해주세요.</summary>
  </br>
  <p>정규화는 데이터의 중복방지, 무결성을 충족시키기 위해 데이터베이스를 설계하는 것을 의미합니다.</p>
  <p>데이터베이스 설계 시에는 데이터 중복성을 최소화하고 일관성을 유지하는 것이 중요한데, 이를 위해서는 각 데이터 요소가 중복되지 않도록 테이블을 분리하고, 각각의 테이블 간에 관계를 설정해야 합니다. 이러한 과정에서 정규화를 수행합니다.</p>
   <p>
    <ul>
      <li>제1정규화(1NF) : 테이블의 각 필드는 원자값(Atomic value)만을 포함하도록 분해합니다.</li>
      <li>제2정규화(2NF) : 테이블의 모든 필드가 기본 키에 대해 완전 함수 종속( Fully functional dependency)을 갖도록 테이블을 분해합니다.</li>
      <li>제3정규화(3NF) : 테이블에서 이행적 함수 종속(Transitive dependency)이 존재하지 않도록 테이블을 분해합니다.</li>
    </ul>
  </p>
</details>

<details>
  <summary>JOIN에 대해서 설명해주세요.</summary>
  </br>
  <p>JOIN은 두 개 이상의 테이블에서 데이터를 검색하거나 결합하는 방법입니다. JOIN은 데이터베이스에서 가장 많이 사용되는 연산 중 하나이며, 테이블 간 관계를 사용해 데이터를 가져오는 데 사용됩니다.</p>
  <p>JOIN은 일반적으로 두 가지 방법으로 수행됩니다. 첫 번째 방법은 Nested Loop Join입니다. 이 방법은 두 테이블을 루프로 반복하고 조건을 충족하는 행을 찾아 조인합니다. 두 번째 방법은 Hash Join입니다. 이 방법은 두 테이블을 해시 함수를 사용해 조인합니다. 해시 함수는 데이터의 일부를 사용해 키를 만들고 이를 사용해 테이블을 연결합니다.</p>
</details>


<details>
  <summary>Redis에 대해서 간단히 설명해주세요.</summary>
  </br>
  <p>Redis는 메모리 기반의 Key-Value 형태의 오픈소스 데이터베이스이며, NoSQL 데이터베이스의 일종입니다. 데이터를 디스크가 아닌 메모리에 저장하기 때문에 속도가 빠르며, 데이터 처리 속도가 빠르다는 장점이 있습니다.</p>
    <p>특징
    <ul>
      <li>In-Memory 데이터베이스: 데이터를 메모리에 저장하기 때문에 처리 속도가 매우 빠르며, 캐시로 많이 사용됩니다.</li>
      <li>다양한 데이터 타입 지원: 문자열(String), 리스트(List), 셋(Set), 정렬된 셋(Sorted Set), 해시(Hash) 등 다양한 데이터 타입을 지원합니다.</li>
      <li>높은 가용성(High Availability): 마스터-슬레이브 복제 기능을 지원하여, 마스터 노드가 다운되었을 때 자동으로 슬레이브 노드가 마스터 역할을 대신 수행할 수 있습니다.
      </li>
      <li>데이터 영속화(Persistence): RDB와 AOF 방식을 지원하여, 데이터의 영속성을 보장합니다.</li>
    </ul>
  </p>
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


<details>
  <summary>추가 정리</summary>
쿼리 튜닝(Query tuning)이란 무엇이며 어떤 방법이 있는가요?
데이터베이스 백업과 복구에 대해 설명해주세요.
데이터베이스 보안에 대해 설명해주세요.
SQL Injection이란 무엇이며 어떻게 방지할 수 있나요?
데이터베이스 트리거(Trigger)란 무엇이며 어떤 경우에 사용하나요?
데이터베이스 뷰(View)란 무엇이며 어떤 경우에 사용하나요?
데이터베이스 샤딩(Sharding)이란 무엇이며 어떤 장단점이 있나요?
데이터베이스 파티셔닝(Partitioning)이란 무엇이며 어떤 경우에 사용하나요?
데이터베이스 쿼리(Query) 최적화에 대해 설명해주세요.
OLTP(Online Transaction Processing)와 OLAP(Online Analytical Processing)의 차이점은 무엇인가요?
데이터베이스 스키마(Schema)란 무엇이며 어떤 경우에 사용하나요?
데이터베이스 복제(Replication)란 무엇이며 어떤 경우에 사용하나요?
Table과 View의 차이
DB Key 종류 및 의미
</details>


### Java

<details>
  <summary>JVM의 구조와 Java의 실행방식을 설명해주세요.</summary>
  </br>
  <p>자바 가상 머신의 약자를 따서 줄여 부르는 용어로 JVM의 역할은 자바 애플리케이션을 클래스 로더를 통해 읽어 자바 API와 함께 실행하는 것입니다. 메모리 관리(GC)을 수행하며 스택기반의 가상머신입니다.</p>
  <p>JVM의 구조는 Class Loader, Execution engine, Runtime Data Area, JNI, Native Method Library로 이루어져 있습니다.</p>
  <ul>
    <li>클래스 로더: JVM내로 클래스를 로드하고, 링크를 통해 배치하는 작업을 수행하는 모듈</li>
    <li>실행 엔진: 바이트 코드를 실행시키는 역할</li>
    <ul>
      <li>인터프리터: 바이트 코드를 한줄 씩 실행합니다.</li>
      <li>JIT 컴파일러: 인터피르터 효율을 높이기 위한 컴파일러로 인터프리터가 반복되는 코드를 발견하면 JIT 컴파일러가 반복되는 코드를 네이티브 코드로 바꿔줍니다. 그 다음부터 인터프리터는 네이티브 코드로 컴파일된 코드를 바로 사용합니다.</li>
      <li>GC(Garbage Collector): 가비지 컬렉터로 힙 영역에서 사용되지 않는 객체들을 제거하는 작업을 의미합니다.</li>
    </ul>
    <li>Runtime Data Areas: 프로그램 실행 중에 사용되는 다양한 영역입니다.</li>
    <ul>
      <li>PC Register: Thread가 시작될 때 생성되며 현재 수행 중인 JVM 명령의 주소를 갖고 있습니다.</li>
      <li>Stack Area: 지역 변수, 파라미터 등이 생성되는 영역. 실제 객체는 Heap에 할당되고 해당 레퍼런스만 Stack에 저장됩니다.</li>
      <li>Heap Area: 동적으로 생성된 오브젝트와 배열이 저장되는 곳으로 GC의 대상 영역입니다.</li>
      <li>Method Area: 클래스 멤버 변수, 메소드 정보, Type 정보, Constant Pool, static, final 변수 등이 생성됩니다. 상수 풀(Constant Pool)은 모든 Symbolic Reference를 포함하고 있습니다.</li>
    </ul>
    <li>JNI(Java Native Interface): 자바 애플리케이션에서 C, C++, 어셈블리어로 작성된 함수를 사용할 수 있는 방법을 제공해줍니다. Native 키워드를 사용하여 메서드를 호출합니다. 대표적인 메서드는 Thread의 currentThread()입니다.</li>
    <li>Native Method Library: C, C++로 작성된 라이브러리 입니다.</li>
  </ul>
  <p>Java의 실행방식
    <ul>
    <li>자바 컴파일러(javac)가 자바 소스코드(.java)를 읽어 자바 바이트코드(.class)로 변환시킵니다.</li>
    <li>Class Loader를 통해 class 파일들을 JVM으로 로딩합니다.</li>
    <li>로딩된 class파일들은 Execution engine을 통해 해석됩니다.</li>
    <li>해석된 바이트코드는 Runtime Data Areas 에 배치되어 실질적인 수행이 이루어집니다.</li>
    </ul>
  </p>
</details>

<details>
  <summary>GC가 무엇인지, 필요한 이유는 무엇인지, 동작방식에 대해 설명해주세요.</summary>
  </br>
  <p>GC는 힙 영역에서 사용하지 않는 객체들을 제거하는 작업을 총칭합니다. 이 객체를 제거하는 작업이 필요한 이유는 자바는 개발자가 메모리를 직접 해제해줄 수 없는 언어이기 때문입니다. 따라서 객체를 사용하고 제거하는 기능이 필요하게 됩니다.</p>
  <p>GC의 동작방식은 가장 간단한 Serial GC 방식으로 설명합니다. 좀 더 진보된 GC는 G1 GC, ZGC가 있으며 여기선 다루지 않습니다.</p>
  <p>GC는 Minor GC, Major GC로 구분할 수 있습니다. Minor GC는 young 영역에서, Major GC는 old 영역에서 일어난다고 정의합니다. (Major GC, Full GC는 명확히 정의된 문서가 없습니다.) GC를 수행할 때는 GC를 수행하는 스레드 이외의 스레드는 모두 정지합니다. 이를 Stop-the-world라고 합니다.</p>
  <p>Minor GC는 Eden 영역이 가득 참에서 부터 시작됩니다. Eden 영역에서 참조가 남아있는 객체를 mark하고 survivor 영역으로 복사합니다. 그리고 Eden 영역을 비웁니다. Survivor 영역도 가득차면 같은 방식으로 다른 Survivor 영역에 복사하고 비웁니다. 이를 반복하다 보면 계속 해서 살아남는 객체는 old 영역으로 이동하게 됩니다.</p>
  <p>Major GC는 old 영역에서 일어납니다. 위와 반대로 삭제되어야 하는 객체를 mark합니다. 그리고 지웁(sweep)니다. 메모리는 단편화 된 상태이므로 이를 한 군데에 모아주는 것을 Compaction이라 하며 compact라고 합니다. 그래서 Mark-Sweep-Compact 알고리즘이라고 합니다.</p>
  <p>이것이 중요한 이유는 GC 수행시 시스템이 멈추기 때문에 의도치 않은 장애의 원인이 될 수 있습니다. 따라서 이를 위해 힙 영역을 조정하는 것을 GC 튜닝이라고 하고 JVM 메모리는 절대 마음대로 조정해선 안됩니다.</p>
</details>

<details>
  <summary>컬렉션 프레임워크에 대해서 설명해주세요.</summary>
  </br>
  <p>Java Collection은 널리 알려져 있는 자료구조를 바탕으로 객체, 데이터들을 효율적으로 관리 할 수 있는 자료구조들이 있는 라이브러리를 컬렉션 프레임워크라고 합니다.</p>
  <p>List, Set은 Collection 인터페이스을 상속받지만, Map 인터페이스는 구조상의 차이라 별도로 정의합니다.</p>
</details>

<details>
  <summary>제네릭에 대해서 설명해주세요.</summary>
  </br>
  <p>제네릭은 자바의 타입 안정성을 맡고 있습니다. 컴파일 과정에서 타입체크를 해주는 기능으로 객체의 타입을 컴파일 시에 체크하기 때문에 객체의 타입 안정성을 높이고 형변환의 번거로움을 줄여줍니다.</p>
</details>

<details>
  <summary>애노테이션에 대해서 설명해주세요.</summary>
  </br>
  <p>애노테이션은 인터페이스를 기반으로 한 문법으로 주석처럼 코드에 달아 클래스에 특별한 의미를 부여하거나 기능을 주입할 수 있습니다. built-in annotation은 상속받아서 메소드를 오버라이드 할 때 나타나는 @Override 애노테이션이 그 대표적인 예입니다.</p>
  <p>메타 애너테이션은 애노테이션을 선언할 때 사용하는 애노테이션입니다.</p>
  <ul>
    <li>@Retention: 애노테이션 유지 범위를 지정합니다. (소스, 클래스, 런타임)</li>
    <li>@Inherit: 애노테이션을 하위 클래스까지 전달여부를 지정합니다. 이 애노테이션이 있으면 하위 클래스까지 상속이 가능합니다.</li>
    <li>@Target: 해당 애노테이션을 어디에 사용할 지 결정합니다. (타입, 필드, 메서드, 파라미터, 생성자, 로컬변수, 애노테이션 타입)</li>
  </ul>
</details>

<details>
  <summary>오버라이딩과 오버로딩이 무엇이며 어떤 차이가 있을까요?</summary>
  </br>
  <p>의외로 굉장히 많은 답을 들을 수 있는 질문입니다.</p>
  <p>오버라이딩은 상위 클래스의 메소드를 재정의 하는 것을 의미합니다. 또, 런타임 다형성이기도 합니다.</p>
  <p>오버로딩은 같은 클래스 내에서 동일한 메소드 이름을 가지지만, 매개변수의 타입, 개수가 다르게 구현할 수 있는 것을 의미하며 컴파일 타임 다형성이기도 합니다. 따라서 오버라이딩 될 수 있습니다.</p>
  <p>추가로 `@Override`를 써야하는 이유를 꼭 생각해보세요. 이 애노테이션은 컴파일 타임에 오버라이딩에 대한 안정성을 부여해주기 때문에 반드시 써주는 것이 좋습니다.</p>
</details>

<details>
  <summary>인터페이스와 추상클래스의 차이점에 대해 설명해주세요.</summary>
  </br>
  <p>추상클래스는 객체의 추상적인 상위 개념으로 공통된 개념을 표현할 때 사용합니다. 단일 상속만 가능합니다. 추상클래스를 상속하는 집합간에는 연관관계가 있습니다.</p>
  <p>인터페이스는 구현 객체가 같은 동작을 한다는 것을 보장하기 위해 사용합니다. 다중 상속이 가능합니다. 인터페이스를 구현하는 집합간에는 관계가 없을 수 있습니다.</p>
</details>

<details>
  <summary>클래스는 무엇이고 객체는 무엇인가요?</summary>
  </br>
  <p>클래스는 객체를 정의하는 틀 또는 설계도와 같은 의미로 사용됩니다.</p>
  <p>객체는 식별 가능한 개체 또는 사물입니다. 객체는 구별 가능한 식별자, 특징적인 행동, 변경 가능한 상태를 가집니다. 인스턴스들을 통칭하는 용도로 사용합니다.</p>
</details>

<details>
  <summary>정적(static)이란 무엇인가요?</summary>
  </br>
  <p>static은 클래스 멤버라고 하며, 클래스 로더가 클래스를 로딩해서 메소드 메모리 영역에 적재할 때 클래스별로 관리됩니다.</p>
  <p>static 키워드를 통해 생성된 정적멤버들은 PermGen 또는 Metaspace에 저장되며 저장된 메모리는 모든 객체가 공유하며 하나의 멤버를 어디서든지 참조할 수 있는 장점이 있습니다.</p>
  <p>그러나, GC의 관리 영역 밖에 존재하기 때문에 프로그램 종료시까지 메모리가 할당된 채로 존재합니다. 너무 남발하게 되면 시스템 성능에 악영향을 줄 수 있습니다.</p>
</details>

<details>
  <summary>자바의 원시타입들은 무엇이 있으며 각각 몇 바이트를 차지하나요?</summary>
  </br>
  <p>실제 면접에서 들었던 질문입니다. 들었을 때 굉장히 당황했던 기억이 나네요.</p>
  <p>boolean(1), char(unsigned 2), byte(1), short(2), int(4), long(8), float(4), double(8)</p>
  <p>사실 JVM에 의존적이기 때문에 정확한 크기라기 보다는 대략적인 크기입니다.</p>
</details>

<details>
  <summary>접근 제어자의 종류와 이에 대해 설명해주세요.</summary>
  </br>
  <p>private, default, protected, public이 있습니다. private은 해당 클래스 내에서만 접근 가능하고, default는 해당 패키지, protected는 상속한 클래스, public은 전체 영역에서 접근 가능합니다.</p>
  <p>접근 제어자를 사용하는 이유는 외부에 보여주고 싶은 정보들을 선택적으로 제공하기 위함이고, 캡슐화와 통하는 면이 있습니다.</p>
</details>

<details>
  <summary>객체지향에 대해서 설명해주세요.</summary>
  </br>
  <p>객체지향을 정의하면, 의존성 관리입니다.</p>
  <p>객체지향으로 의존성을 관리함으로써 변경 영향을 최소화하고 독립적인 배포가 가능해지며 독립적인 개발이 가능해집니다. 따라서 객체지향에서 가장 중요한 것은 DIP(Dependency Inversion Principle)를 통한 고수준 정책(High Level Policy)와 저수준 구현 세부사항(Low Level Details)의 분리라고 할 수 있습니다.</p>
</details>

<details>
  <summary>SOLID(객체지향 5대원칙)에 대해서 설명해주세요.</summary>
  </br>
  <p>SRP(단일책임원칙)은 한 클래스의 하나의 책임만 가져야 합니다.</p>
  <p>OCP(개방-폐쇄 원칙)은 확장에는 열려 있으나 변경에는 닫혀 있어야 하며, 다형성을 활용해야 합니다.</p>
  <p>LSP(리스코프 치환 원칙)은 프로그램의 객체는 프로그램의 정확성을 깨뜨리지 않으면서 하위 타입의 인스턴스로 바꿀 수 있어야하는 원칙으로 상위 타입을 상속해서 재정의 했을 때 프로그램이 깨지지 않아야 합니다.</p>
  <p>ISP(인터페이스 분리 원칙)은 클라이언트는 자신이 사용하지 않는 메서드에 의존 관계를 맺으면 안되는 원칙입니다. 특정 클라이언트를 위한 인터페이스 여러 개가 범용 인터페이스 하나보다 더 낫습니다. 즉, 비대한 인터페이스보단 더 작고 구체적인 인터페이스로 분리해야합니다.</p>
  <p>DIP(의존관계 역전 원칙)은 추상적인 것은 자신보다 구체적인 것에 의존하지 않고, 변화하기 쉬운 것에 의존해서는 안된다는 원칙입니다. 구체적으론 구현 클래스에 의존하지 말고, 인터페이스에 의존해야 하는 원칙입니다.</p>
</details>

<details>
  <summary>동일성(identity)와 동등성(equality)에 대해 설명해주세요. (equals(), ==)</summary>
  </br>
  <p>동일성은 객체의 주소를 비교하는 것이고, 동등성은 객체의 같음을 비교하는 것입니다.</p>
  <p>기본적으로 자바에서는 Object 클래스에 정의된 equals() 메소드가 동일성 비교를 합니다. 따라서, 개발자는 원한다면 equals() 메소드를 오버라이딩해서 동등성의 판단 기준을 정의해주면 됩니다.</p>
</details>

<details>
  <summary>원시타입과 참조타입의 차이에 대해 설명해주세요.</summary>
  </br>
  <p>원시타입은 Java에서 단 8개 밖에 존재하지 않는 타입입니다. 나머지는 모두 참조타입이라고 볼 수 있고, Object 클래스이거나 이를 상속하는 클래스들로 이루어져 있습니다.</p>
  <p>원시타입은 항상 값이 존재해야 합니다. 반면, Object 타입은 null 포인터를 가질 수 있습니다. 그리고 멤버변수가 초기화될 때, 원시타입은 기본값을 가지지만, 참조타입은 null 포인터를 가지는 차이도 있습니다.</p>
</details>

<details>
  <summary>String, StringBuilder, StringBuffer 각각의 차이에 대해 설명해주세요.</summary>
  </br>
  <p>String은 불변입니다. StringBuilder와 StringBuffer는 이런 String의 특징때문에 사용하는 가변타입이라고 볼 수 있습니다.</p>
  <p>StringBuilder와 StringBuffer는 Thread-safe 여부의 차이가 있습니다. StringBuilder는 Thread-safe하지 않습니다. 따라서 Multi-Thread 환경에서 사용할 때는 StringBuffer를 사용합니다.</p>
</details>

<details>
  <summary>Checked Exception과 Unchecked Exception에 대해 설명해주세요. 스프링 트랜잭션 추상화에서 rollback 대상은 무엇일까요?</summary>
  </br>
  <p>둘의 차이는 RuntimeException을 상속하는가의 여부에 따라 다릅니다. RuntimeException을 상속하면 UncheckedException이 됩니다. 스프링 트랜잭션 추상화에서 rollback 대상은 바로 UncheckedException입니다.</p>
  <p>이 둘을 잘 알기 위해서는 토비의 스프링을 보시는 것을 추천합니다.</p>
</details>

<details>
  <summary>Java8에서 추가된 기능에 대해서 설명해주세요.</summary>
  </br>
  <p>자신이 사용한 경험을 말해주면 더 효과적일 것 같습니다.</p>
  <p>Java8에서는 Lambda식, Stream API, Optional, 날짜 시간 API, StringJoiner 등이 추가되었습니다.</p>
  <p>lambda는 함수형 프로그래밍을 지원하기 위한 기능이고, Stream API는 고차함수를 지원합니다. Optional은 Null-safety를 제공하며, Stream과 사용법이 유사합니다. 날짜 시간 API는 Joda-time등의 라이브러리에서 영향을 받아 괜찮은 API가 되었으며, StringJoiner는 문자열을 간단하게 구분자로 합칠 수 있는 기능을 제공합니다.</p>
</details>

<details>
  <summary>try-with-resource에 대해서 설명해주세요.</summary>
  </br>
  <p>try-with-resources는 자바 버전7에 도입된 문법입니다.</p>
  <p>자바 7 버전 이전에서 하나 이상의 리소스(java.lang.AutoCloseable을 구현한 객체 혹은 java.io.Closeable를 구현한 객체)를 사용할 경우 개발자가 임의로 finally 문에서 ~~.close()를 사용하여 자원 해제를 시켜줘야 했습니다.</p>
  <p>만약 개발자가 사용한 자원을 finally 문에서 해제시켜주지 않고 누락시켰다면 자원이 해제되지 않은 채로 프로그램이 오작동하게 되고, finally 문에서 자원을 해제 시켜주더라도 자원 해제를 위한 중복 코드가 발생하기 때문에 소스 코드의 가독성을 해치는 단점이 있었습니다.</p>
  <p>이를 해결하기 위해 try() 안에 사용할 리소스 객체를 명시적으로 선언하여 사용하면, try 블록 안에서 로직이 정상적으로 완료되었는지, 갑작스럽게 완료되었는지 여부와 관계 없이 JVM에서 자동으로 자원을 반납해주는 기능을 하도록 도입하였습니다.</p>
  <p>추가로, 자바 9 버전에서는 try() 문 안에 명시적으로 객체 선언을 하기 보다는 try 문 바깥에서 객체 선언을 하고 생성된 인스턴스의 변수를 넣어줄 수 있도록 바뀌었습니다.</p>
  <p>
  Java 7 : try(BufferedReader br = new BufferedReader()) <br>
  Java 9 : try(br)
  </p>
</details>

<details>
  <summary>강한 결합과 느슨한 결합이 무엇인지 설명해주세요.</summary>
  </br>
  <p>결합도는 의존성의 정도를 나타내며 다른 모듈에 대해 얼마나 많은 정보를 알고 있는지에 대한 척도입니다.</p>
  <p>어떤 모듈이 다른 모듈에 너무 자세한 부분(구현 세부사항)까지 알고 있을 경우에 강한 결합도를 가진다고 합니다.</p>
  <p>어떤 모듈이 다른 모듈에 대해 필요한 정보(인터페이스로 추상화된 고수준 정책)만 알고 있다면 두 모듈은 낮은 결합도를 가진다고 합니다.</p>
  <p>객체지향 관점에서 결합도는 객체 또는 클래스가 협력에 필요한 적절한 수준의 관계만을 유지하고 있는지를 나타냅니다. 이러한 관점에서 강한 결합도는 반드시 지양해야 하며, 개발자는 적절한 결합도를 유지할 수 있도록 고민하고 설계해야 합니다.</p>
</details>

<details>
  <summary>직렬화와 역직렬화에 대해서 설명해주세요.</summary>
  </br>
  <p>직렬화란 자바 시스템 내부에서 사용되는 객체 또는 데이터를 외부의 자바 시스템에서도 사용할 수 있도록 바이트 형태로 데이터 변환하는 기술과 바이트로 변환된 데이터를 다시 변환하는 기술(역직렬화)을 아울러서 이야기 합니다.</p>
  <p>자바 직렬화는 JVM의 메모리에서만 상주되어있는 객체 데이터를 영속화(Persistence)가 필요할 때 사용됩니다. 시스템이 종료되더라도 없어지지 않는 장점을 가지며 영속화된 데이터이기 때문에 네트워크로 전송이 가능합니다.</p>
</details>

<details>
  <summary>자바의 동시성 이슈(공유자원 접근)에 대해 설명해주세요.</summary>
  </br>
  <p></p>
</details>

<details>
  <summary>Mutable 객체와 Immutable 객체의 차이점에 대해 설명해주세요.</summary>
  </br>
  <p>Mutable 객체는 변경 가능 객체이고, Immutable 객체는 불변 객체라고 흔히들 말합니다.</p>
  <p>Mutable 객체는 도메인 개체(도메인 클래스 혹은 엔터티)로 사용됩니다. Mutable 객체의 변경 메서드는 Command method라고도 부르며, 리턴 타입을 void 로 정의합니다. 또한 void 리턴 타입의 어떠한 상태를 변경하는 메서드는 모두 Command method의 상징입니다.</p>
  <p>
  Immutable 객체는 불변객체이며 값 객체, 서비스 객체 등에 사용됩니다. Immutable 객체의 변경 메서드는 변경한 객체의 복사본을 반환해야 합니다.
  </p>
</details>

<details>
  <summary>자바에서 null을 안전하게 다루는 방법에 대해 설명해주세요.</summary>
  </br>
  <p>공개 메서드가 아닌 곳에는 assert를 사용하여 null을 방어할 수 있습니다. 또한 메서드의 인자를 받을 때 Objects.requireNonNull()을 사용하여 방어할 수 있습니다. 그리고 Optional을 사용해 리턴 타입에서 null을 반환하지 않도록 방어할 수 있습니다. 마지막으로 사전 조건과 사후 조건을 명확히 하여 계약에 의한 설계를 실천해야 합니다.</p>
</details>

### Spring

<details>
  <summary>Spring DI/IoC는 어떻게 동작하나요?</summary>
  </br>
  <p>IoC(제어의 역전)은 프로그램의 제어 흐름을 직접 제어하는 것이 아니라 외부에서 관리하는 것으로 코드의 최종호출은 개발자가 제어하는 것이 아닌 프레임워크의 내부에서 결정된 대로 이루어집니다.</p>
  <p>DI(의존관계 주입)은 Spring 프레임워크에서 지원하는 IoC의 형태로 클래스 사이의 의존관계를 빈 설정 정보를 바탕으로 컨테이너가 자동으로 연결해줍니다.</p>
  <p>스프링에서는 스프링 컨테이너 ApplicationContext를 이용하여 설정 정보를 생성, 등록하고 필요한 객체를 생성자 혹은 setter를 통해 주입합니다.</p>
</details>

<details>
  <summary>Spring Bean이란 무엇인가요?</summary>
  </br>
  <p>IoC 컨테이너 안에 들어있는 객체로 필요할 때 IoC컨테이너에서 가져와서 사용합니다. @Bean 을 사용하거나 xml설정을 통해 일반 객체를 Bean으로 등록할 수 있습니다.</p>
</details>

<details>
  <summary>스프링 Bean의 생성 과정을 설명해주세요.</summary>
  </br>
  <p>객체 생성 → 의존 설정 → 초기화 → 사용 → 소멸 과정의 생명주기를 가지고 있습니다. Bean은 스프링 컨테이너에 의해 생명주기를 관리하며 빈 초기화방법은 @PostConstruct 를 빈 소멸에서는 @PreDestroy 를 사용합니다.</p>
  <p>생성한 스프링 빈을 등록할 때는 ComponentScan을 이용하거나 @Configuration 의 @Bean 을 사용하여 빈 설정파일에 직접 빈을 등록할 수 있습니다.</p>
</details>

<details>
  <summary>스프링 Bean의 Scope에 대해서 설명해주세요.</summary>
  </br>
  <p>빈 스코프는 빈이 존재할 수 있는 범위를 뜻하며 싱글톤, 프로토타입, request, session, application 등이 있습니다.</p>
  <p>싱글톤은 기본 스코프로 스프링 컨테이너의 시작과 종료까지 유지되는 가장 넓은 범위의 스코프입니다.</p>
  <p>프로토타입은 빈의 생성과 의존관계 주입까지만 관여하고 더는 관리하지 않는 매우 짧은 범위의 스코프입니다.</p>
  <p>request는 웹 요청이 들어오고 나갈때까지 유지하는 스코프, session은 웹 세션이 생성, 종료할때까지, application은 웹 서블릿 컨텍스트와 같은 범위로 유지하는 스코프입니다.</p>
</details>

<details>
  <summary>IoC 컨테이너의 역할은 무엇이 있을까요?</summary>
  </br>
  <p>애플리케이션 실행시점에 빈 오브젝트를 인스턴스화하고 DI 한 후에 최초로 애플리케이션을 기동할 빈 하나를 제공해준다</p>
</details>

<details>
  <summary>DI 종류는 어떤것이 있고, 이들의 차이는 무엇인가요?</summary>
  </br>
  <p>DI는 세가지 방법이 있습니다. 생성자 삽입, Setter를 이용한 메소드 매개 변수 삽입, 필드 주입이 있습니다.</p>
  <p>생성자 주입은 생성자 호출시점에 딱 1번만 호출되는 것을 보장하며 불변, 필수 의존관계에 사용합니다.</p>
  <p>Setter주입은 선택, 변경 가능성이 있는 의존관계에 사용되며 스프링빈을 선택적으로 등록이 가능합니다.</p>
  <p>필드 주입은 `@Autowired` 를 사용하는데 외부에서 변경이 불가능하여 테스트 하기 힘듭니다. DI 프레임워크 없이는 작동하기 힘들며, 주로 애플리케이션과 관계없는 테스트코드나 `@Configuration` 같은 스프링 설정 목적으로 사용합니다. </p>
</details>

<details>
  <summary>Autowiring 과정에 대해서 설명해주세요.</summary>
  </br>
  <p>컨테이너에서 타입(인터페이스 또는 오브젝트)을 이용해 의존 대상 객체를 검색하고 할당할 수 있는 빈 객체를 찾아 주입한다</p>
</details>

<details>
  <summary>Spring Web MVC의 Dispatcher Servlet의 동작 원리에 대해서 간단히 설명해주세요.</summary>
  </br>
  <p></p>
</details>

<details>
  <summary>프론트 컨트롤러 패턴이란 무엇인가요?</summary>
  </br>
  <p>클라이언트의 다양한 요청마다 서블릿을 만들어서 사용한다고 하면 개발과 유지보수의 효율이 떨어질 수 밖에 없습니다. 프론트 컨트롤러 패턴을 사용함으로써 각 요청을 적절한 곳으로 위임해줌으로써 개발과 유지보수의 효율성이 증가하고 모든 요청에 대해 보안, 국제화, 라우팅 및 로그와 같은 일반적인 기능을 한 곳에서 캡슐화할 수 있습니다. Spring에서는 DispatcherServlet이 프론트 컨트롤러 패턴을 사용한 예이며, DispatcherServlet이 Bean으로 등록되어 package를 scan하고 @Controller, @RestController 애노테이션을 확인하여 어떠한 요청이 들어왔을 때 적절한 Handler Method에 위임해줍니다.</p>
</details>

<details>
  <summary>Servlet Filter와 Spring Interceptor의 차이는 무엇인가요?</summary>
  </br>
  <p>Filter는 Servlet Filter로써 javax.servlet 스펙에 포함되는 클래스입니다.</p>
  <p>Interceptor는 Spring MVC 스펙에 포함되어 있는 클래스입니다.</p>
  <p>Filter는 Servlet에서 전후처리를 담당하며, Interceptor는 Spring에서 Handler를 실행하기 전후나, ViewResolver를 통해 컨트롤러에서 리턴한 View Name으로부터 렌더링을 담당할 View 오브젝트를 준비해 돌려준 후 실제 View를 렌더링한 후에 어떠한 처리를 담당합니다.</p>
  <p>Filter는 Web Application(Tomcat을 사용할 경우 web.xml)에 등록하며, Interceptor는 Spring의 Application Context에 등록합니다.</p>
  <p>Filter는 Method Signature에 있는 Argument인 HttpServletRequest 혹은 HttpServeltResponse를 ServletRequest, ServletResponse 등으로 교체할 때 사용하거나, 데이터 변환(다운로드 파일의 압축 및 데이터 암호화 등), XSL/T를 이용한 XML 문서 변경, 사용자 인증, 자원 접근에 대한 로깅 등에 사용합니다.</p>
  <p>Interceptor의 경우 AOP를 흉내내거나, Spring 애플리케이션에서 전역적으로 전후처리 로직에서 예외를 사용하도록 하거나, Handler Method에서 사용자의 권한을 체크해서 다른 동작을 시켜준다거나 할 때 사용합니다.</p>
  <p></p>
</details>

<details>
  <summary>Spring에서 CORS 에러를 해결하기 위한 방법을 설명해주세요.</summary>
  </br>
  <p>Servlet Filter를 사용하여 커스텀한 Cors 설정하거나, WebMvcConfiguer를 구현한 Configuration 클래스를 만들어서 addCorsMappings()를 재정의할 수도 있고, 마지막으로 Spring Security에서 CorsConfigurationSource를 Bean으로 등록하고 config에 추가해줌으로써 해결할 수 있습니다.</p>
  <p>Controller 클래스에 @Crossorigin 어노테이션을 통해 해결할 수 있습니다.</p>
</details>

<details>
  <summary>Bean/Component 어노테이션에 대해서 설명해주시고, 둘의 차이점에 대해 설명해주세요.</summary>
  </br>
  <p>두 어노테이션 모두 IoC 컨테이너에 Bean을 등록하기 위해 사용합니다</p>
  <p>@Component : 개발자가 작성한 class를 기반으로 실행시점에 인스턴스 객체를 1회(싱글톤) 생성합니다</p>
  <p>@Controller, @Service, @Repository 는 모두 @Component 이며 실행시점에 자동으로 의존성을 주입합니다</p>
  <p>@Bean : 개발자가 작성한 method를 기반으로 메서드에서 반환하는 객체를 인스턴스 객체로 1회(싱글톤) 생성합니다</p>
</details>

<details>
  <summary>POJO란 무엇인가요? Spring Framework에서 POJO는 무엇이 될 수 있을까요?</summary>
  </br>
  <p>POJO는 프레임워크 인터페이스, 클래스를 구현하거나 확장하지 않은 단순한 클래스로 Java에서 제공하는 API 외에 종속되지 않습니다. 특정 환경에 종속되지 않아 코드가 간결하고 테스트 자동화에 유리합니다. 스프링에서는 도메인과 비즈니스 로직을 수행하는 대상이 POJO대상이 될 수 있습니다.</p>
</details>

<details>
  <summary>Spring Web MVC에서 요청 마다 Thread가 생성되어 Controller를 통해 요청을 수행할텐데, 어떻게 1개의 Controller만 생성될 수 있을까요?</summary>
  </br>
  <p></p>
</details>

<details>
  <summary>Filter는 Servlet의 스펙이고, Interceptor는 Spring MVC의 스펙입니다. Spring Application에서 Filter와 Interceptor를 통해 예외를 처리할 경우 어떻게 해야 할까요?</summary>
  </br>
  <p>Filter는 DispatcherServlet 외부에 존재하기 때문에 예외가 발생했을 때 ErrorController에서 처리해야 합니다. 하지만 Interceptor는 DispatcherServlet 내부에 존재하기 때문에 @ControllerAdvice를 적용해서 처리할 수 있습니다.</p>
</details>

<details>
  <summary>Spring Application을 구동할 때 메서드를 실행시키는 방법에 대해 설명해주세요.</summary>
  </br>
  <p>CommandLineRunner, ApplicationRunner를 구현한 클래스를 만들어서 실행시키는 2가지 방법이 있습니다. 또한 Spring의 ApplicationEvent를 사용한 방법, @Postconstruct를 사용한 방법, InitializingBean 인터페이스를 구현하는 방법, @Bean의 initMethod를 사용한 방법이 있습니다.</p>
</details>

<details>
  <summary>의존성과 설정값을 생성자 인자로 주입해야 하는 이유에 대해 설명해주세요.</summary>
  </br>
  <p>모든 의존성을 생성자를 통해 주입하면, 인스턴스 생성 시 즉시 어떠한 동작을 실행할 수 있습니다. 또한 추가적인 설정은 필요하지 않으며, 뜻하지 않게 의존성과 설정값을 빠뜨리는 일이 발생하지 않고 테스트에도 용이합니다.</p>
</details>

### JPA

<details>
  <summary>JPA 영속성 컨텍스트의 이점(5가지)을 설명해주세요.</summary>
  </br>
  <p>영속성 컨텍스트는 엔티티를 영구 저장하는 환경을 의미합니다.</p>
  <p>영속성 컨텍스트를 쓰는 이유는 1차 캐시, 동일성 보장, 쓰기 지연, 변경감지(Dirty checking), 지연로딩이 있습니다.</p>
  <ul>
    <li>1차 캐시: 조회가 가능하며 1차 캐시에 없으면 DB에서 조회하여 1차 캐시에 올려 놓습니다.</li>
    <li>동일성 보장: 동일성 비교가 가능합니다.(==)</li>
    <li>쓰기 지연: 트랜잭션을 지원하는 쓰기 지연이 가능하며 트랜잭션 커밋하기 전까지 SQL을 바로 보내지 않고 모아서 보낼 수 있습니다.</li>
    <li>변경 감지(Dirty checking): 스냅샷을 1차 캐시에 들어온 데이터를 찍습니다. commit 되는 시점에 Entity와 스냅샷과 비교하여 update SQL을 생성합니다.</li>
    <li>지연 로딩: 엔티티에서 해당 엔티티를 불러올 때 그 때 SQL을 날려 해당 데이터를 가져옵니다.</li>
  </ul>
</details>

<details>
  <summary>JPA Propagation 전파단계를 설명해주세요.</summary>
  </br>
  <p>대기업면접에서 나왔던 질문으로 트랜잭션 고립단계와 같이 질문할 가능성이 있습니다.</p>
  <p>JPA Propagation은 트랜잭션 동작 도중 다른 트랜잭션을 호출(실행)하는 상황에 선택할 수 있는 옵션입니다.</p>
  <p>@Transactional의 propagation 속성을 통해 피호출 트랜잭션의 입장에서는 호출한 쪽의 트랜잭션을 그대로 사용할 수도 있고, 새롭게 트랜잭션을 생성할 수도 있습니다.</p>
  <p>REQUIRED(디폴트): 부모 트랜잭션 내에서 실행하며 부모 트랜잭션이 없을 경우 새로운 트랜잭션을 생성합니다.</p>
  <p>이 외에도 종류가 REQUIRES_NEW, SUPPORTS, MANDATORY, NOT_SUPPORT, NEVER, NESTED 가 있지만 신입이 실제로 다뤄본 경험이 적기 때문에 REQUIRED(디폴트)값만 답변했습니다.</p>
</details>

<details>
  <summary>JPA를 쓴다면 그 이유에 대해서 설명해주세요.</summary>
  </br>
  <p>사실 면접관이 의도한 바를 파악하는게 중요합니다. 각기 다른 조건에서 같은 질문을 들었을 때 대답을 다르게 했던 기억이 납니다.</p>
  <p>제가 JPA를 사용하는 이유는 객체지향 프레임워크이기 때문입니다. JPA를 사용하면 비즈니스 로직이 RDBMS에 의존하는 것이 아니라, 자바 코드로 표현될 수 있기 때문입니다. 그로 인해서 생산성이 높아진다고 볼 수 있습니다.(이는 JPA에 익숙하다는 것을 전제로 합니다.)</p>
  <p>또, JPA는 JPQL로 SQL을 추상화하기 때문에 RDBMS Vendor에 관계없이 동일한 쿼리를 작성해서 같은 동작을 기대할 수 있다는 장점도 가지고 있습니다. 이는 database dialect를 지원하기 때문에 가지는 장점입니다.</p>
</details>

<details>
  <summary>N + 1 문제는 무엇이고 이것이 발생하는 이유와 이를 해결하는 방법을 설명해주세요.</summary>
  </br>
  <p>JPA와 관련된 단골문제입니다. 꼭 학습해둡시다.</p>
  <p>N + 1 쿼리 문제는 즉시 로딩과 지연 로딩 전략 각각의 상황에서 발생할 수 있습니다. 하위 엔티티들이 존재하는 경우 한 쿼리에서 모두 가져오는 것이 아닌, 필요한 곳에서 각각 쿼리가 발생하는 경우를 이릅니다.</p>
  <p>즉시 로딩에서 발생하는 이유는 JPQL을 사용하는 경우 전체 조회를 했을 때, 영속성 컨텍스트가 아닌 데이터베이스에서 직접 데이터를 조회한 다음 즉시로딩 전략이 동작하기 때문입니다.<br>
  지연 로딩에서 발생하는 이유는 지연로딩 전략을 사용한 하위 엔티티를 로드할 때, JPA에서 프록시 엔티티를 unproxy 할 때 해당 엔티티를 조회하기 위한 추가적인 쿼리가 실행되어 발생합니다.</p>
  <p>해결 방법으로는 Fetch Join이라고 불리는 JPQL의 join fetch를 사용하는 방법이 있으며, 또 다른 방법으로는 <code>@EntityGraph</code>를 사용하는 방법, <code>@Fetch(FetchMode.SUBSELECT)</code>를 사용하는 방법, <code>@BatchSize</code>를 사용해 조절하거나 전역적인 batch-size를 설정하는 방법이 있습니다.</p>
  <p>각 해결방안에 대한 유의점은 작성하지 않습니다.</p>
</details>
