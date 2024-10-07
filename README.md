### **SQL 개요 및 기본 개념**

**문제 1**

- SQL이란 무엇이며, 어떤 용도로 사용되나요?

SQL (Structured Query Language)은 데이터 베이스를 관리하고 조작하기 위한 표준언어이며 SQL을 사용하면 데이터 베이스에서 데이터를 저장하고 조회하며 수정 및 삭제할 수 있습니다.

SQL은 관계형 데이터베이스 관리 시스템(RDBMS)에서 데이터를 처리하는데 사용됩니다.

**문제 2**

- 관계형 데이터베이스(RDBMS)의 대표적인 예시 세 가지를 제시하세요.

MySQL, PostgreSQL, Oracle

**문제 3**

- SQL과 NoSQL 데이터베이스의 주요 차이점 두 가지를 설명하세요.

SQL 데이터베이스는 정해진 스키마를 사용하며, 데이터는 테이블 형태로 저장되고,
NoSQL 데이터베이스는 고정된 스키마가 없으며, 다양한 데이터 형식을 지원합니다.

SQL 데이터베이스는 수직적 확장이 가능한 반면 NoSQL 데이터베이스는 수평적 확장이 가능하며,
SQL 데이터베이스는 데이터 일관성 유지가 용이하지만 NoSQL 데이터베이스는 데이터 일관성 보장이 어렵습니다.

**문제 4**

- 다음 중 SQL의 기본 명령어에 해당하지 않는 것은 무엇인가요?
  A : d)DROP

a) SELECT
b) INSERT
c) UPDATE
d) DROP
e) DELETE

**문제 5**

- SELECT 문에서 모든 컬럼을 조회하기 위한 와일드카드는 무엇인가요?

* **문제 6**

- 특정 조건에 맞는 데이터를 조회할 때 사용하는 절은 무엇인가요?

WHERE

**문제 7**

- AND, OR, NOT 연산자의 기능을 간단히 설명하세요.

AND : 모든 조건이 참
OR : 하나 이상의 조건이 참
NOT : 조건의 부정

**문제 8**

- 다음 SQL 문에서 사용된 연산자는 무엇이며, 어떤 기능을 하나요?

SELECT \* FROM students WHERE name LIKE '김%';

LIKE (패턴 매칭 조회): 김으로 시작하는 문자열 조회

**문제 9**

- 범위를 지정하여 데이터를 조회할 때 사용하는 연산자는 무엇인가요? 예시와 함께 설명하세요.

BETWEEN
SELECT \* FROM student WHERE age BETWEEN 17 AND 19;

**문제 10**

- INSERT 문을 사용하여 여러 행을 한 번에 삽입하는 방법을 예시와 함께 설명하세요.

INSERT INTO students (name, age, grade) VALUES
('김철수', 17, 'B'),
('이영희', 20, 'A');

**문제 11**

- UPDATE 문을 사용하여 특정 조건의 데이터를 수정할 때 주의해야 할 점은 무엇인가요?

WHERE절 지정을 안하면 모두 업데이트 할 수 있어 주의해야 합니다. (WHERE절 명시)

**문제 12**

- DELETE 문과 TRUNCATE 문의 차이점을 설명하세요.

- DELETE문은 행을 한번에 하나씩 제거하고 삭제된 각 행에 대해 트랜잭션 로그에 항목을 기록합니다.
- TRUNCATE문은 테이블의 데이터를 저장하는데 사용되는 데이터 페이지의 할당을 취소하는 방식으로 데이터를 제거하며 페이지 할당 취소만을 트랜잭션 로그에 기록합니다.

**문제 13**

- GROUP BY 절의 기능과 함께 집계 함수를 사용하는 예시를 보여주세요.

SELECT grade, COUNT(\*) AS '학생 수' FROM students GROUP BY grade;

**문제 14**

- INNER JOIN과 LEFT JOIN의 차이점을 설명하세요.

INNER JOIN(교집합)은 양쪽테이블에서 조건체 맞는 데이터만 조회하고,
LEFT JOIN(한쪽원부분전체)은 왼쪽 테이블의 모든 데이터와 오른쪽 테이블의 일치하는 데이터를 조회합니다.

**문제 15**

- 서브쿼리(Subquery)란 무엇이며, 어떤 상황에서 사용되나요?

메인쿼리 안에 포함된 또 다른 쿼리 형태입니다.
주로 WHERE절이나 SELECT절에서 사용해서 복잡한 조건이나 계산된 값을 얻을 때 사용합니다.

**문제 16**

- 윈도우 함수(Window Function)의 목적과 예시를 설명하세요.

행 순서에 따라 계산을 수행합니다.
SELECT name, grade, RANK() OVER (ORDER BY grade DESC) AS '성적 순위' FROM students;

**문제 17**

- 테이블 생성 시 PRIMARY KEY와 FOREIGN KEY의 역할을 각각 설명하세요.

PRIMARY KEY : 고유한 식별자 / 테이블에서 각 행을 고유하게 식별할 수 있는 컬럼 혹은 컬럼들의 집합. 따라서 중복값을 허용하지 않으며 NULL값을 가질 수 없다.
FOREIGN KEY : 다른 테이블의 기본키를 참조 / 테이블 간 데이터의 무결성을 보장받을 수 있고, 테이블 간의 링크가 무너지는 것을 방지할 수 있다.

**문제 18**

- 트랜잭션(Transaction)이란 무엇이며, 어떤 특징을 가지나요?

트랜잭션은 데이터베이스의 일관성을 유지하기 위해 사용됩니다.

ACID
원자성 : 모두 성공하거나, 모두 실패해야합니다.
일관성 : 트랜잭션이 완료 되면, 데이터베이스는 일관된 상태여야 합니다.
격리성 : 동시에 실행되는 트랜잭션들은 서로 간섭하지 않아야 합니다.
내구성 : 트랜잭션이 완료되면 그 결과는 영구적으로 반영됩니다.

**문제 19**

- 사용자 계정을 생성하고 특정 권한을 부여하는 SQL 명령어를 작성하세요.

CREAT USER 'username'@'localhost' IDENTIFIED BY 'password';
GRANT SELECT, INSERT ON database.\* TO 'username'@'localhost';

**문제 20**

- SQL에서 데이터베이스의 성능을 향상시키기 위해 인덱스를 사용하는데, 인덱스의 장점과 단점을 각각 설명하세요.

장점은 데이터 조회 속도를 향상 시켜 성능이 향상됩니다.
단점은 추가 저장공간이 필요하며 관리하기 위한 추가 작업이 필요합니다.