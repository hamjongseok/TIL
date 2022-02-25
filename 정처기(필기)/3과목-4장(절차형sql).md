# **데이터베이스 구축**

## **절차형 SQL** ⭐️⭐️

절차형 SQL

- C, JAVA 등의 프로그래밍 언어와 같이 연속적인 실행이나 분기, 반복등의 제어가 가능한 SQL
- 일반적인 프로그래밍 언어에 비해 효율이 떨어지지만, 연속적인 작업 처리 적합
- BEGIN ~ END 형식으로 작성되는 블록 구조로 기능별 모듈화 가능

## 프로시저 #디비컨SET

- 호출을 통해 실행되어 미리 저장해 놓은 SQL 작업 수행, 처리 결과는 한개 이상의 값 혹은 반환을 아예 하지 않음
- 시스템의 일일 마감 작업, 일괄(Batch)작업 등에 주로 사용됨

- DECLARE(필수)
  - 프로시저의 명칭, 변수, 인수, 데이터 타입을 정의하는 선언부
- BEGIN(필수)
  - 프로시저의 시작을 의미, 실행부
    - CONTROL
      - 조건문 또는 반복문이 삽입되어 순차적으로 처리됨
    - SQL
      - DML, DCL이 삽입되어 데이터 관리를 위한 작업 수행
    - EXCEPTION
      - BEGIN ~ END 안의 구문 실행시 예외가 발생하면 이를 처리
    - TRANSACTION
      - 수행된 데이터 작업들을 DB에 적용할지 말지 결정하는 처리부
- END(필수)
  - 프로시저의 종료를 의미, BEGIN/END는 함께 다님

![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/d560cff8-1e3d-40a0-a6f8-4165359e4702/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2022-02-26_%E1%84%8B%E1%85%A9%E1%84%8C%E1%85%A5%E1%86%AB_12.23.38.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220225%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220225T153846Z&X-Amz-Expires=86400&X-Amz-Signature=866a273050da26a103b9f01b151ca539b3deb6c2f505cbf82c08d687733c211d&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA%25202022-02-26%2520%25E1%2584%258B%25E1%2585%25A9%25E1%2584%258C%25E1%2585%25A5%25E1%2586%25AB%252012.23.38.png%22&x-id=GetObject)

- 동작 시기 옵션 : AFTER(테이블이 변경된 후 트리거 실행), BEFORE(변경 되기 전 실행)
- NEW | OLD
  - NEW(추가되거나 수정에 참여할 테이블), OLD(수정되거나 삭제 전 테이블)
- FOR EACH ROW : 각 튜플 마다 트리거 적용
- DROP TRIGGER 트리거명;

## 사용자 정의 함수

- 프로시저와 유사하게 SQL을 사용해 일련의 작업을 연속적으로 처리
- 종료시 예약어 RETURN을 사용해 처리 결과를 단일 값으로 반환
- DML문(SELECT, INSERT, DELETE, UPDATE)의 호출에 의해 실행됨
- RETURN을 통해 값을 반환해, 출력(OUT)파라미터가 없음
- INSERT, DELETE, UPDATE로 테이블을 조작은 할수 없고 SELECT으로 조회만 할수 있음
- 프로시저를 호출해 사용할수 없다

![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/0dce3a0c-58b3-4812-a3ac-321f6d776f29/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2022-02-26_%E1%84%8B%E1%85%A9%E1%84%8C%E1%85%A5%E1%86%AB_12.36.07.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220225%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220225T154017Z&X-Amz-Expires=86400&X-Amz-Signature=96fc01de63fd93dfdcd2d0fdf326303fbb15ce1a98263c808a1e49a7fe37c871&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA%25202022-02-26%2520%25E1%2584%258B%25E1%2585%25A9%25E1%2584%258C%25E1%2585%25A5%25E1%2586%25AB%252012.36.07.png%22&x-id=GetObject)
![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/f4d8cfd4-8cd6-47e7-91c1-a20903f7408e/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2022-02-26_%E1%84%8B%E1%85%A9%E1%84%8C%E1%85%A5%E1%86%AB_12.36.20.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220225%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220225T154041Z&X-Amz-Expires=86400&X-Amz-Signature=cab83ea4f2d0218e4132c7a6700d1d947f4d16444490241af1bb1c0043101f46&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA%25202022-02-26%2520%25E1%2584%258B%25E1%2585%25A9%25E1%2584%258C%25E1%2585%25A5%25E1%2586%25AB%252012.36.20.png%22&x-id=GetObject)

---

## DBMS 접속기술

웹 응용 시스템의 구조

- 사용자 ←→ 웹서버 ←→ WAS ←→ DBMS
- 사용자는 웹서버에 접속해 데이터를 주고받고 웹서버는 WAS에게 해당요청을 전달함 그다음 WAS는 수신한 요청을 트랜잭션 언어로 변환한후 DBMS에 전달해 데이터를 받으면, 이데이터를 다시 웹서버로 전달해 사용자에게 도달하게 함

DBMS 접속 기술

- JDBC(Java Database Connectivity)
  - 1997년 썬 마이크로 시스템에서 출시, JAVA 언어로 다양한 종류의 데이터 베이스에 접속하고 SQL 문을 수행 할때 사용되는 표준 API
  - 접속하려는 DBMS에 대한 드라이버가 필요
- ODBC(Open Database Connectivity)
  - 1992년 마이크로소프트에서 출시, 데이터베이스에 접근하기 위해 표준 개방형 API로 개발 언어에 관계없이 사용가능
  - OCBC도 접속하려는 DBMS에 대한 드라이버가 필요 하지만 접속하려는 DBMS의 인터페이스를 알지 못하더라도 ODBC문장을 사용해 SQL을 작성하면 ODBC에 포함된 드라이버 관리자가 해당 DBMS의 인터페이스에 맞게 연결해줌
  - → DBMS의 종류를 몰라도된다

정적 SQL vs 동적 SQL

![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/536355f7-adbd-49ce-95a9-62dad8d024ea/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2022-02-26_%E1%84%8B%E1%85%A9%E1%84%8C%E1%85%A5%E1%86%AB_1.08.53.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220225%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220225T161815Z&X-Amz-Expires=86400&X-Amz-Signature=a03b9023404600b8a1cb23023126ea8dfa1bf5cc323c512b3f04ac8fac3d0f2e&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA%25202022-02-26%2520%25E1%2584%258B%25E1%2585%25A9%25E1%2584%258C%25E1%2585%25A5%25E1%2586%25AB%25201.08.53.png%22&x-id=GetObject)

---

## `ORM(Object-Relational Mapping)`

ORM의 개요

- 객체와 관계형데이터 베이스(RDB)의 데이터를 연결(Mapping)하는 기술
- ORM으로 생성된 가상의 객체 지향 데이터 베이스는 프로그래밍 코드 또는 데이터베이스와 독립적이므로 재사용 및 유지보수 용이
- 직관적이고 간단하게 데이터 조작 가능

ORM 프레임 워크
![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/7c423fd6-a46c-43a2-9448-1692ba9c9838/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2022-02-26_%E1%84%8B%E1%85%A9%E1%84%8C%E1%85%A5%E1%86%AB_1.40.29.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220225%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220225T164859Z&X-Amz-Expires=86400&X-Amz-Signature=c1022fc06df3c91d24e9d6264be694e40dcb73e9b6e658cf60a218dd856dbf10&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA%25202022-02-26%2520%25E1%2584%258B%25E1%2585%25A9%25E1%2584%258C%25E1%2585%25A5%25E1%2586%25AB%25201.40.29.png%22&x-id=GetObject)

ORM의 한계

- 프레임 워크가 자동으로 SQL을 작성하기 때문에 의도대로 작성되었는지 확인해야함
- 객체 지향적인 사용 고려와 프로젝트가 크고 복잡해질 수록 적용하기 어려워짐
- 기존의 기업들은 ORM을 고려하지 않은 데이터베이스를 사용하고 있기 때문에, ORM에 적합하게 변환하려면 많은 시간과 노력 필요

---

### `뷰(view)`

뷰의 개요 및 특징

- 기본 테이블로부터 유도된, 이름을 가지는 가상 테이블로 기본 테이블과 같은 형태의 구조를 사용하며, 조작도 기본 테이블과 거의 같음
- 가상 테이블이기때문에 물리적으로 구현되어 있지 않지만 사용자에게 있는 것처럼 간주됨 → 저장 장치 내에 논리적으로 존재
- 정의된뷰로 다른 뷰를 정의할수 있음
- 뷰가 정의된 기본 테이블이나 뷰를 삭제하면 그 테이블이나 뷰를 기초로 정의된 다른뷰도 자동 삭제됨
  ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/d6fafb93-f392-4a3c-866c-c76a4b0fb14a/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2022-02-23_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_3.10.01.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220223%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220223T061224Z&X-Amz-Expires=86400&X-Amz-Signature=ef11b7f93031875d6476392816705426410b7cd122bd027cdb21cf4489c097fb&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA%25202022-02-23%2520%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE%25203.10.01.png%22&x-id=GetObject)

뷰의 장, 단점(중요)

- 장점
  - 논리적 데이터 독립성 제공
  - 접근 제어를 통한 자동 보안 제공
  - 사용자 데이터 관리 용이
- 단점
  - 독립적인 인덱스를 가질 수 없음
  - 뷰의 정의를 ALTER로 변경할수 없음 → DROP하고 새로 CREATE해야 함
  - 뷰로 구성된 내용에 대한 삽입, 삭제, 갱신, 연산에 제약이 따름

## `클러스터`

---

클러스터의 개요 및 특징

- 데이터 저장 시 데이터 액세스 효율을 향상 시키기 위해 동일한 성격의 데이터를 동일한 데이터 블록에 저장하는 물리적 저장 방법
- 인덱스의 단점을 해결한 기법 → 분포도가 넓을 수록 오히려 유리함
- 분포도가 넓은 테이블의 클러스터링은 저장 공간의 절약이 가능
- 대량의 범위를 자주 액세스(조회)하는 경우 적용
- 인덱스를 사용한 처리 부담이 되는 넓은 분포도에 활용

클러스터의 선정 기준 및 고려사항

- 클러스터 테이블 선정
  - 수정이 빈번하지 않는 테이블
  - ORDER BY, GROUP BY, UNION이 빈번한 테이블
  - 처리 범위가 넓어 문제가 발생하는 경우 단일 테이블 클러스터링 사용
  - 조인이 많아 문제가 발생되는 경우는 다중 테이블 클러스터링 사용
- 설계 시 고려사항
  - 클러스터링 된 테이블은 조회속도를 향상시켜주지만 입력, 수정, 삭제 시 성능이 저하됨(부하가 증가)
  - 대용량을 처리하는 트랜잭션은 전체 테이블을 스캔하는 일이 자주 발생하므로 클러스터링을 하지 않는것이 좋음
  - 클러스터링 된 테이블에 클러스터드 인덱스를 생성하면 접근 성능이 향상됨

---

## `분산 데이터 베이스 설계`

분산 데이터베이스 정의

- 논리적으로는 하나의 시스템에 속하지만 물리적으로는 네트워크를 통해 연결된 여러 개의 컴퓨터 사이트에 분산돼 있는 데이터 베이스

분산 데이터베이스의 구성요소
![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/c3dfab3c-e106-4dba-a6e3-aa7fd5fd06d0/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2022-02-23_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_3.38.59.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220223%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220223T064205Z&X-Amz-Expires=86400&X-Amz-Signature=6fbc69b4dcf7c598d9e29a810d24be3bbab99bc0e01cc01e41f6ce7d90e18fe0&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA%25202022-02-23%2520%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE%25203.38.59.png%22&x-id=GetObject)

분산 데이터 베이스의 목표(중요)
![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/bec7dd6e-ada9-4668-a10c-2286133dbcd5/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2022-02-23_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_3.39.25.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220223%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220223T064234Z&X-Amz-Expires=86400&X-Amz-Signature=69cb819ff9540448234d0b11bbf5e49197e721d189b9d13bfee41ab7ebc5bf08&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA%25202022-02-23%2520%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE%25203.39.25.png%22&x-id=GetObject)

분산 데이터베이스의 장,단점

![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/7e1b3f81-536c-4e88-b229-814107b22680/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2022-02-23_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_3.39.43.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220223%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220223T064300Z&X-Amz-Expires=86400&X-Amz-Signature=66e948415f9497c39e4c513b8e9a1c0b670a0503e221d1a66bb846a95a7ff363&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA%25202022-02-23%2520%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE%25203.39.43.png%22&x-id=GetObject)

분산 데이터베이스 설계

- 애플리케이션이나 사용자가 분산되어 저장된 데이터에 접근하게 하는것을 목적

분산 설계방법

- 테이블 위치 분산 : 테이블을 각기 다른 서버에 분산시켜 배치하는 방법
- 분할(Fragmentation):테이블의 데이터를 분할하여 분산시키는것
- 할당(Allocation): 동일한 분할을 여러 개의 서버에 생성하는 방법
- 중복이 없는 할당, 중복이 있는 할당

---

## `데이터 베이스 이중화(Database Replication)`

- 시스템 오류로 인한 데이터 베이스 서비스 중단이나 물리적 손상 발생시 이를 복구 하기 위해 동일한 데이터 베이스를 복제해 관리하는것

데이터베이스 이중화의 분류
![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/a7a440fc-0d39-42d3-8765-ffcd1e02005e/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2022-02-23_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_10.08.19.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220223%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220223T131153Z&X-Amz-Expires=86400&X-Amz-Signature=bf837d0fecd6de7efd53ffb001606366116142e1067fac21ff24b77d7baec858&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA%25202022-02-23%2520%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE%252010.08.19.png%22&x-id=GetObject)

데이터 베이스 이중화 구성방법
![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/b1d6f4e5-568d-47fa-a0cc-e904e43c703d/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2022-02-23_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_10.08.39.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220223%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220223T131228Z&X-Amz-Expires=86400&X-Amz-Signature=647e6ddb02514dbf33c6cc107605c63bbe708a75374072b2a18a1a26b3fa9825&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA%25202022-02-23%2520%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE%252010.08.39.png%22&x-id=GetObject)

서버 클러스터링

- 두대 이상의 서버를 하나의 서버처럼 운영하는 기술
- 고가용성 클러스터링: 하나의 서버에 장애 발생 → 다른 서버가 대신 처리
- 병렬 처리 클러스터링: 하나의 작업을 여러개의 서버에 분산해 처리

---

## `데이터 베이스 보안/스토리지`

데이터 베이스 보안의 개요

- 데이터 베이스 일부분 또는 전체에 대해서 권한이 없는 사용자가 액세스하는 것을 금지하기 위해 사용되는 기술
- 데이터베이스 사용자들은 일반적으로 서로 다른 객체에 대해 다른 접근 권리 또는 권한을 가짐

암호화(Encryption)

- 암호화(Encryption) 과정
  - 암호화되지않은 평문을 정보 보호를 위해 암호문으로 바꾸는 과정
  - 개인 암호 방식(대칭키), 공개키 암호 방식(비대칭키)
- 복호화(Decryption) 과정
  - 암호문을 원래의 평문으로 바꾸는 과정

암호화 방식
![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/b5f21025-fad8-455a-ac04-587dd504ee4d/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2022-02-23_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_10.20.43.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220224%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220224T045929Z&X-Amz-Expires=86400&X-Amz-Signature=ddde5e8205ea113ba57ca5f29bd6a87227c0fbe15fe3d4f4536388ccb20010dd&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA%25202022-02-23%2520%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE%252010.20.43.png%22&x-id=GetObject)

접근통제

- 데이터가 저장된 객체와 이를 사용하려는 주체 사이의 정보 흐름을 제한 하는것
- 접근 통제 3요소 : 접근통제 정책, 접근 통제 보안모델, 접근 통제 메커니즘
- #정보커

- 임의 접근통제(DAC; Discretionary Access Control)
  - 데이터에 접근하는 사용자의 신원에 따라 접근 권한 부여
  - 접근 통제 권한 = 주체
- 강제 접근통제(MAC; Mandatory Access Control)
  - 주체와 객체의 등급을 비교해 접근 권한 부여
  - 접근 통제 권한 = 제 3자

접근 통제 정책
![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/40d8197e-0531-4c2b-aac6-8db87faa72d9/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2022-02-23_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_10.23.14.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220224%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220224T050004Z&X-Amz-Expires=86400&X-Amz-Signature=4a0158d10fe27d5ee547ef25f703f2f9b8b52e3717379f0a0e9e2fef50983f55&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA%25202022-02-23%2520%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE%252010.23.14.png%22&x-id=GetObject)

접근통제 메커니즘

- 접근통제 목록(ACL; Access Control List)
  - 객체를 기준으로 특정 객체에 대해 어떤 주체가 어떤행위를 할 수 있는 지를 기록한 목록
- 능력리스트(CL; Capability List)
  - 주체를 기준으로 주체에게 허가된 자원 및 권한을 기록한 목록
- 보안 등급(Security Label), 패스워드, 암호화

접근통제 보안 모델

- 기밀성 모델
  - 군사적인 목적으로 개발된 최초의 수학적 모델, 기밀성 보장 최우선
  - 벨라파듈라 모델: No Read UP(기밀성), No Write Down
- 무결성 모델
  - 불법적인 정보 변경을 방지하기 위해 무결성을 기반으로 개발된 모델
  - 비바 모델 : No Read Down, No Write Up(무결성)
- 접근 통제 모델
  - 접근 통제 메커니즘을 보안 모델로 발전 시킨 것
  - 접근통제 행렬(Access Control Matrix): 행=주체, 열=객체

데이터 베이스 백업 종류
![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/8c32b441-6d3d-4c8f-9270-f855fdfbbb61/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2022-02-24_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_2.37.57.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220224%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220224T101703Z&X-Amz-Expires=86400&X-Amz-Signature=6f0de5f14a3be82bbd6b3fa39a8b229f48d90860fc7c91d481af37b8f37806e2&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA%25202022-02-24%2520%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE%25202.37.57.png%22&x-id=GetObject)
로그 파일 : 데이터베이스의 상태 변화를 시간의 흐름에 따라 모두 기록한 파일

스토리지
![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/1cd1561c-8c0c-4152-ae22-81438822ed1e/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2022-02-24_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_2.38.24.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220224%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220224T101737Z&X-Amz-Expires=86400&X-Amz-Signature=3166ac771aed0f35b51cfd752b15d231e17b53e7fba1abea58b205d9ba95aea6&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA%25202022-02-24%2520%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE%25202.38.24.png%22&x-id=GetObject)

---

## `논리 데이터 모델의 물리 데이터 모델 변환 및 품질 검토`

일반적인 변환 절차

- 단위 개체를 테이블로 변환 → 속성을 컬럼으로 변환 → UID(Unique Lentifier)를 기본 키(Primary Key)로 변환 → 관계를 외래 키(Foreign Key)로 변환 → 컬럼유형 (Type)과 길이(Length) 정의 → 반정규화(De-normalization) 수행

슈퍼타입/서브타입을 테이블로 변환

- 슈퍼타입 기준 테이블 변환: 서브타입을 슈퍼타입에 통합해 하나의 테이블로 만드는것
- 서브타입 기준 테이블 변환 : 슈퍼 타입 속성들을 각각의 서브타입에 추가해 서브타입들을 개별적인 테이블로 만드는 것
- 개별타입 기준 테이블 변환: 슈퍼타입과 서브타입들을 각각의 개별적인 테이블로 변환하는 것

물리데이터 모델 품질 기준 (=논리 데이터 모델 품질 기준)
![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/c4be1aa4-aaf5-4eca-8822-a7397c98b985/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2022-02-24_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_9.58.32.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220224%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220224T143239Z&X-Amz-Expires=86400&X-Amz-Signature=f72200d7c3669571a12bc45502df0fcdff13d6d15db9c988a7324f75e08b10ae&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA%25202022-02-24%2520%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE%25209.58.32.png%22&x-id=GetObject)

## 3장, 4장 내일 끝내기
