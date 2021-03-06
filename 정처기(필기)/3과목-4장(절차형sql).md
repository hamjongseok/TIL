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

데이터 전환

- 데이터 전환의 정의
  - 운영중인 기존 정보 시스템에 축적되어 있는 데이터를 추출(Extraction)하여 새로 개발할 정보 시스템에서 운영 가능하도록 변환(Transformation) 후, 적재(Loading)하는 일련의 과정
  - #ETL(Extraction, Transformation, Loading): 추출, 변환, 적재 과정
  - 데이터 이행(Data Migration), 데이터 이관이라고도 함

데이터 전환 계획서
![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/fe2777f0-20d6-4cae-8909-e2550a4672ce/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2022-02-26_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_2.42.24.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220226%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220226T062604Z&X-Amz-Expires=86400&X-Amz-Signature=01e276f3ba46bc9808c166bdb68da065d087ec74202720237f4b35e8769c26be&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA%25202022-02-26%2520%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE%25202.42.24.png%22&x-id=GetObject)
