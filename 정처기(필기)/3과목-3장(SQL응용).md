# **데이터베이스 구축**

## **SQL 응용** ⭐️⭐️

SQL 응용

- 1974년 IBM 연구소에서 개발한 SEQUEL에서 유래함
- 관계대수와 관계해석을 기초로 한 혼합 데이터 언어

SQL(Structured Query Language)의 분류

- DDL(Data Define Language, 데이터 정의어)

  - DOMAIN(도메인), SCHEMA(스키마), TABLE(테이블), VIEW(뷰),INDEX(인덱스)를 정의하거나 변경 또는 삭제 할때 사용하는 언어
  - #도스테뷰인

![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/6b57156c-d094-4bba-af96-e39b33cca899/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2022-02-25_%E1%84%8B%E1%85%A9%E1%84%8C%E1%85%A5%E1%86%AB_12.02.50.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220225%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220225T031545Z&X-Amz-Expires=86400&X-Amz-Signature=b2f07d27893f42dfc567b0d01690498c8a6e54a3a62a969a36787ea5b275bff0&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA%25202022-02-25%2520%25E1%2584%258B%25E1%2585%25A9%25E1%2584%258C%25E1%2585%25A5%25E1%2586%25AB%252012.02.50.png%22&x-id=GetObject)

DML(Data Manipulation Language, 데이터 조작어)

- 데이터베이스 사용자가 응용프로그램이나 질의어를 통해 저장된 데이터를 실질적으로 처리하는데 사용하는 언어

![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/c6f0fc6e-7529-4860-8b6e-d2fa6e2a06ec/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2022-02-25_%E1%84%8B%E1%85%A9%E1%84%8C%E1%85%A5%E1%86%AB_12.03.38.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220225%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220225T031642Z&X-Amz-Expires=86400&X-Amz-Signature=36d9dac955a9988f9b863ec019cc6adb902e7143c9675fb9b55d872027c38385&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA%25202022-02-25%2520%25E1%2584%258B%25E1%2585%25A9%25E1%2584%258C%25E1%2585%25A5%25E1%2586%25AB%252012.03.38.png%22&x-id=GetObject)

DCL(Data Control Language, 데이터 제어어)

- 데이터의 무결성, 보안, 회복, 병행수행 제어 등을 정의하는데 사용되는 언어
- 데이터 베이스 관리자(DBA)가 데이터 관리를 목적으로 사용

![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/cc67b1d5-705f-46f6-ba5f-b25c424583d7/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2022-02-25_%E1%84%8B%E1%85%A9%E1%84%8C%E1%85%A5%E1%86%AB_12.04.50.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220225%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220225T031713Z&X-Amz-Expires=86400&X-Amz-Signature=933b90f16787a8ebd327a93441a548d584808a8d2ea8126348bfa28e7af85fcf&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA%25202022-02-25%2520%25E1%2584%258B%25E1%2585%25A9%25E1%2584%258C%25E1%2585%25A5%25E1%2586%25AB%252012.04.50.png%22&x-id=GetObject)

ex) GRANT UPDATE IN ON 고객(테이블) TO 홍길동 WITH GRANT OPTION;

ex) REVOKE GRANT OPTION FOR UPDATE ON 고객(테이블) FROM 홍길동 CASCADE;

SELECT

- WHERE절 : 검색할 조건을 기술
- ORDER BY절 : 특정 속성을 기준으로 정렬해 검색할 때 사용
  - ASC(오름차순), DESC(내림차순)- 따로 설정이 없을 때는 기본적으로 ASC 사용
- GROUP BY절 : 특정 속성을 기준으로 그룹화해 검색할때 사용, 일반적으로 그룹 함수와 함께 사용
- HAVING절 : GROUPBY와 함께 사용되며, 그룹에 대한 조건 지정
  - DISTINCT: 중복 튜플 제거
- 집계/그룹함수 : GROUP BY절에 지정된 그룹별로 속성의 값을 집계할 함수를 기술함

![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/fa52f4db-540f-4ee8-adf8-ebcfcbc6308c/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2022-02-25_%E1%84%8B%E1%85%A9%E1%84%8C%E1%85%A5%E1%86%AB_12.09.12.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220225%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220225T031730Z&X-Amz-Expires=86400&X-Amz-Signature=56339b1bd79407842344e93c03a147b5da7e2932fb16cc7ecefbf972320d53bb&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA%25202022-02-25%2520%25E1%2584%258B%25E1%2585%25A9%25E1%2584%258C%25E1%2585%25A5%25E1%2586%25AB%252012.09.12.png%22&x-id=GetObject)

- 윈도우 함수: GROUP BY 절을 이용하지 않고 속성의 값을 집계할 함수를 기술함
  - 함수의 인수로 지정한 속성이 대상 레코드의 범위가 되는데, 이를 WINDOW라 함
  - PARTITION BY: 윈도우 함수가 적용될 범위로 사용할 속성 지정
  - → WINDOW 함수 OVER (PARTITION BY 속성 ORDER BY 속성)[AS 바꾸고 싶은 이름]

![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/cc2777e0-9a0e-4000-9259-63ac5e328645/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2022-02-25_%E1%84%8B%E1%85%A9%E1%84%8C%E1%85%A5%E1%86%AB_12.10.52.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220225%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220225T031800Z&X-Amz-Expires=86400&X-Amz-Signature=53885df0f2a71deb0e0af03d9ef179154b572bc4a289ce1172d01df1f7f1de05&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA%25202022-02-25%2520%25E1%2584%258B%25E1%2585%25A9%25E1%2584%258C%25E1%2585%25A5%25E1%2586%25AB%252012.10.52.png%22&x-id=GetObject)

- 조인(JOIN)
  - 결합을 의미하며, 관계형 데이터베이스에서의 조인은 교집합 결과를 가지는 결합 방법을 의미
  - 두 릴레이션으로부터 연관된 튜플들을 결합해, 하나의 새로운 릴레이션을 반환
- 논리적 조인
  ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/166d5320-a115-41bc-9e2d-0f0fe454c0d6/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2022-02-25_%E1%84%8B%E1%85%A9%E1%84%8C%E1%85%A5%E1%86%AB_12.12.10.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220225%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220225T031820Z&X-Amz-Expires=86400&X-Amz-Signature=a9c5999e581053ca47b2b10fb7e3fd34db5710c3019db295afa061f1dc4565e2&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA%25202022-02-25%2520%25E1%2584%258B%25E1%2585%25A9%25E1%2584%258C%25E1%2585%25A5%25E1%2586%25AB%252012.12.10.png%22&x-id=GetObject)

  물리적 조인
  ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/fd04e9bc-8b87-48d3-beb3-7ae6eb68d429/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2022-02-25_%E1%84%8B%E1%85%A9%E1%84%8C%E1%85%A5%E1%86%AB_12.12.25.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220225%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220225T031852Z&X-Amz-Expires=86400&X-Amz-Signature=098085aa5371a5638645965f0cc811e12a6fe814aa18a7ae0df4ae52d4365cc1&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA%25202022-02-25%2520%25E1%2584%258B%25E1%2585%25A9%25E1%2584%258C%25E1%2585%25A5%25E1%2586%25AB%252012.12.25.png%22&x-id=GetObject)

---

### `트랜잭션`

트랜잭션의 정의

- 데이터베이스의 상태를 변환시키는 하나의 논리적 기능을 수행하기 위한 작업의 단위
- 한꺼번에 모두 수행되어야 할 일련의 연산들
- COMMIT
  - 트랜잭션 처리가 정상으로 종료되어 수행한 변경내용을 DB 에 반영하는 명령어
- ROLLBACK
  - 트랜잭션 처리가 비정상으로 종료되어 DB의 일관성이 깨졌을때 트랜잭션이 행한 모든 변경 작업을 취소하고 이전상태로 되돌리는 연산
  - COMMIT과 ROLLBACK 명령어에 의해 보장받는 트랜잭션 특징 = 원자성(중요)
- SAVEPOINT(=CHECKPOINT)
  - 트랜잭션 내에서 ROLLBACK할 위치인 저장점을 지정하는 명령어, 여러개의 SAVEPOINT 지정 가능

트랜잭션의 특성(중요)
![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/f12ceaf6-035d-45f5-beae-ff4305f24075/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2022-02-23_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_1.42.32.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220223%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220223T044509Z&X-Amz-Expires=86400&X-Amz-Signature=dddb3a1c933169676a92136e943eead94ef0cc4a2b6fac0199ef7d3f8ce502aa&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA%25202022-02-23%2520%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE%25201.42.32.png%22&x-id=GetObject)

CRUD 매트릭스

- Create, Read, Update, Delete, ‘C > D > U > R’의 우선순위 적용
- 테이블, 프로세스에 C,R,U,D가 모두 없는 경우
- 테이블에 C 또는 R이 없는 경우 (프로세스는 하나만 있어도 돌아감)

---

## `인덱스`

인덱스의 개념 및 선정기준, 고려사항

- 데이터 레코드를 빠르게 접근하기 위해 <키 값, 포인터>쌍으로 구성된 데이터 구조

- 인덱스 컬럼의 분포도(Selectivity)가 10~15% 이내인 “컬럼”
- 가능한 한 수정이 빈번하지 않는 “컬럼”
- ORDER BY, GROP BY, UNION이 빈번한 “컬럼”
- 분포도가 좋은 컬럼은 단독 인덱스로 생성
- 인덱스 들이 자주 조합되어 사용하는 컬럼은 결합 인덱스로 생성

설계시 고려사항

- 새로 추가되는 인덱스는 기존 엑세스 경로에 영향을 미칠 수 있음
- 지나치게 많은 인덱스는 오버헤드(Overhead)발생
- 넓은 범위 인덱스 처리시 오히려 전체 처리보다 많은 오버헤드를 발생시킴
- 인덱스 만의 추가적인 저장공간이 필요
- 인덱스와 테이블 데이터의 저장 공간이 분리되도록 설계

인덱스 종류

- 클러스터드 인덱스/ 넌클러스터드 인덱스
- 트리 기반 인덱스 : 인덱스를 저장하는 블록들이 트리 구조를 이루고 있는것
- 비트맵 인덱스 : 인덱스 컬럼의 데이터를 Bit 값인 0,1로 변환해 인덱스 키 사용
- 함수 기반 인덱스 : 컬럼에 특정 함수나 수식을 적용해 산출된 값을 사용하는 것
- 비트맵 조인 인덱스 : 다수의 조인된 객체로 구성된 인덱스
- 도메인 인덱스 : 개발자가 필요한 인덱스를 직접 만들어 사용하는것 (확장형 인덱스)

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
