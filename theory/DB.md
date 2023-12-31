# DB
데이터베이스는 일정한 규칙 혹은 규약을 통해 구조화되 저장되는 데이터 모음입니다.


# 엔터티
Entity는 사람, 장소, 물건, 사건, 개념 등 여러 개의 속성을 지닌 실제, 객체를 뜻한다.


# 릴레이션
Relation은 데이터베이스에 정보를 구분하여 저장하는 기분 단위입니다.

 - 테이블과 컬렉션 : 데이터베이스의 종류는 크게 관계형 데이터베이스와 NoSQL 데이터베이스로 나눌 수 있다.
 대표적으로 관계형에는 MySQL, NoSQL에는 MongoDB가 있다.
 MySQL의 구조는 레코드-테이블-데이터베이스, MongoDB의 구조는 도큐먼트-컬렉션-데이터베이스로 이루어져 있다.


# 속성
Attribute는 릴레이션에서 관리하는 구체적이며 고유한 이름을 갖는 정보이다.


# 도메인
Domain이란 릴레이션에 포함된 각각의 속성들이 가질 수 있는 값의 집합을 말합니다.


# ERD
Entity Relationship Diagram은 DB를 구축할 때 가장 기초적인 뼈대 역할을 하며 릴레이션 간 관계들을 정의한 것이다.


# 정규화 과정
정규화 과정은 릴레이션 간 잘못된 종속 관계로 인해 DB 이상 현상이 일어나서 이를 해결하거나, 저장 공간을 효율적으로 사용하기 위해 릴레이션을 여러 개로 분리하는 과정입니다.

 - 정규형 원칙 : 좀 더 좋은 구조를 만들고, 자료의 중복성은 최소화하고, 독립적인 관계는 별개의 릴레이션으로 표현해야 하고, 각각의 릴레이션은 독립적인 표현이 가능해야 하는 것을 말합니다.

 - 제1정규형 : 릴레이션의 모든 도메인이 더 이상 분해될 수 없는 원자 값(Atomic Value)만으로 구성되어야 합니다. 릴레이션의 속성 값중에서 한 개의 기본키에 대해 두 개 이상의 값을 가지는 반복 집합이 있어서는 안 됩니다. 만약 반복 집합이 있다면 제거해야 합니다.

 - 제2정규형 : 릴레이션이 제1정규형이며 부분 함수의 종속성을 제거한 형태를 말합니다.

 - 제3정규형 : 제2정규형이고 기본키가 아닌 모든 속성이 이행적 함수 종속(Transitive FD)을 만족하지 않는 상태를 말합니다.

 - 보이스/코드 정규형 : 보이스/코드 정규형(BCNF)은 제3정규형이고, 결정자가 후보키가 아닌 함수 종속 관계를 제거하여 릴레이션의 함수 종속 관게에서 모든 결정자가 호보키인 상태를 말합니다.


# 트랜잭션
트랜잭션은 DB에서 하나의 논리적 기능을 수행하기 위한 작업의 단위를 말하며 DB에 접근하는 방법은 쿼리이므로, 즉 여러 개의 쿼리들을 하나로 묶는 단위를 말합니다. 이에 대한 특징으로 원자성, 일관성, 독립성, 지속성이 있으며 이를 한꺼번에 ACID 특징이라고 합니다.

 - 원자성 : Atomicity는 트랜잭션과 관련된 일이 모두 수행되었거나 되지 않았거나를 보장하는 특징입니다.
 - 일관성 : Consistrncy는 '허용된 방식'으로만 데이터를 변경해야 하는 것을 의미합니다.
 - 격리성 : Isolation은 트랜잭션 수행 시 서로 끼어들지 못하는 것을 말합니다.
 - 지속성 : Durability는 성공적으로 수행된 트랜잭션은 영원히 반영되어야 하는 것을 의미합니다.


# 무결성
무결성이란 데이터의 정확성, 일관성, 유효성을 유지하는 것을 말하며, 무결성이 유지되어야 데이터베이스에 저장된 값과 그 값에 해당하는 현실 세계의 실제 값이 일치하는지에 대한 신뢰가 생깁니다.


# 관계형 데이터베이스
관계형 데이터베이스(RDBMS)는 행과 열을 가지는 표 형식의 데이터를 저장하는 형태의 데이터베이스를 가리키며 SQL이라는 언어를 통해 조작합니다.


# NoSQL 데이터베이스
Not only SQL이라는 슬로건에서 생겨난 데이터베이스입니다. SQL을 사용하지 않는 데이터베이스를 말하며 대표적으로 MongoDB와 redis 등이 있다.


# 인덱스
인덱스는 데이터를 빠르게 찾을 수 있는 하나의 장치입니다.


# B-트리
인덱스는 보통 B-트리라는 자료 구조로 이루어져 있습니다.


# 조인
두 개 이상의 테이블을 묶어서 하나의 결과값을 만드는 것.

 - 내부 조인(Inner Join) : 왼쪽 테이블과 오른쪽 테이블의 두 행이 모두 일치하는 행이 있는 부분만 표기
 - 왼쪽 조인(Inner Join) : 왼쪽 테이블의 모든 행이 결과 테이블에 표기
 - 오른쪽 조인(Inner Join) : 오른쪽 테이블의 모든 행이 결과 테이블에 표기
 - 합집합 조인(Inner Join) : 두 개의 테이블을 기반으로 조인 조건에 만족하지 않는 행까지 모두 표기


# 내부 조인
내부 조인은 두 테이블 간에 교집합을 나타냅니다.

 - SELECT * FROM TabelA A
   INNER JOIN TabelB B ON A.key = B.key


# 왼쪽 조인
왼쪽 조인은 테이블 B의 일치하는 부분의 레코드와 함께 테이블 A를 기준으로 완전한 레코드 집합을 생성합니다.

 - SELECT * FROM TabelA A
   LEFT JOIN TabelB B ON A.key = B.key


# 오른쪽 조인
오른쪽 조인은 테이블 A에서 일치하는 부분의 레코드와 함께 테이블 B를 기준으로 완전한 레코드 집합을 생성합니다.

- SELECT * FROM TabelA A
  RIGHT JOIN TabelB B ON A.key = B.key


# 합집합 조인
합집합 조인(완전 외부 조인)은 양쪽 테이블에서 일치하는 레코드와 함께 테이블 A와 테이블 B의 모든 레코드 집합을 생성합니다.

- SELECT * FROM TabelA A
  FULL OUTER JOIN TabelB B ON A.key = B.key


# 중첩 루프 조인
NLJ, Nested Loop Join은 중첩 for 문과 같은 원리로 조건에 맞는 조인을 하는 방법이며, 랜덤 접근에 대한 비용이 많이 증가하므로 대용량의 테이블에서는 사용하지 않습니다.


# 정렬 병합 조인
정렬 병합 조인이란 각각의 테이블을 조인할 필드 기준으로 정렬하고 정렬이 끝난 이후에 조인 작업을 수행하는 조인입니다.


# 해시 조인
해시 조인은 해시 테이블을 기반으로 조인하는 방법입니다.
두 개의 테이블을 조인한다고 하였을 때, 하나의 테이블이 메모리에 온전히 들어가면 보통 중첩 루프 조인보다 더 효율적입니다.
