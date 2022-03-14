# 📚 Database

## 📘 데이터베이스

### 데이터베이스(DB)

- 데이터베이스는 **체계화된 데이터**의 모임
- 여러 사람이 공유하고 사용할 목적으로 통합 관리되는 정보의 집합

- 논리적으로 연관된 (하나 이상의) 자료의 모음으로 그 내용을 고도로 구조화 함으로써 검색과 갱신의 효율화를 꾀한 것
- 즉, **몇 개의 자료 파일을 조직적으로 통합**하여 **자료 항목의 중복을 없애고 자료를 구조화하여 기억시켜 놓은 자료의 집합체**



### 데이터베이스 얻는 장점들

- 데이터 중복 최소화
- 데이터 무결성(정확한 정보를 보장)
- 데이터 일관성
- 데이터 독립성(물리적/논리적)
- 데이터 표준화
- 데이터 보안 유지



## 📕 RDB

### 관계형 데이터베이스(RDB)

- Relational Database
- 키(key)와 값(value)들의 간단한 **관계**(relation)를 **표**(table) 형태로 정리한 데이터베이스
- 관계형 모델이 기반한다.



### 관계형 데이터베이스 용어정리

- 스미카(schema)
  - 데이터베이스에서 자료의 구조, 표현방법, 관계등 **전반적인 명세**를 **기술**한 것

- 테이블(table)
  - **열(컬럼/필드)**과 **행(레코드/값)**의 모델을 사용해 조직된 데이터 요소들의 집합
  - 명세를 기준으로 테이블이 형성된다.
- 열(column)
  - 각 열에는 고유한 데이터 형식이 지정된다.
- 행(row)
  - 실제 데이터가 저장되는 형태
- 기본 키(Primary Key)
  - 각 행(레코드)의 고유 값
  - 반드시 설정해야 하며 데이터베이스 관리 및 관계 설정 시 주요하게 활용된다.



## 📒 RDBMS

### 관계형 데이터베이스 관리 시스템 (RDBMS)

- Rleational Database Managament System
- 관계형 모델을 기반으로 하는 데이터베이스 관리시스템을 의미
- MySQL, SQLite, PostgreSQL, ORACLE, MS SQL



### SQLite

- 서버 형태가 아닌 파일 형식으로 응용 프로그램에 넣어서 사용하는 **비교적 가벼운 데이터베이스**
- 구글 안드로이드 운영체제에 기본적으로 탑재된 데이터베이스이며, 임베디드 소프트웨어에도 많이 활용된다.
- 로컬에서 간단한 DB구성을 할 수 있으며, 오픈소스 프로젝트이기 때문에 자유롭게 사용이 가능하다.



### Sqlite Data Type

1. NULL
2. INTEGER
   - 크기에 따라 0, 1, 2, 3 또는 8 바이트에 저장된 부호 있는 정수
3. REAL
   - 8바이트 부동 소수점 숫자로 저장된 부동 소수점 값
4. TEXT
5. BLOB
   - 입력된 그대로 정확히 저장된 데이터(별다른 타입없이 그대로 저장)



### Squlite Data Type

- sqlite에서는 동적인 데이터 타입을 가진다.
- 데이터타입을 지정하였어도, 혹은 지정하지 않았을 때 선호도 타입에 맞게 변경된다.

#### Squlite Type Affinity

- 선호도 타입





---

# 📚 SQL

## 📒 SQL

### SQL(Structured Query Language)

- 관계형 데이터베이스 관리시스템의 **데이터 관리**를 위해 설계된 **특수 목적의 프로그래밍 언어**

- 데이터베이스 스키마 생성 및 수정
- 자료의 검색 및 관리
- 데이터베이스 객체 접근 조정 관리



### SQL 분류

- DDL 데이터 정의 언어
  - 관계형 데이터베이스 구조(테이블, 스키마)를 정의하기 위한 명령어
- DML, 데이터 조작 언어
  - 데이터를 저장, 조회, 수정, 삭제 등을 하기 위한 명령어
  - INSERT, SELECT, UPDATE, DELETE
- DCL 데이터 제어 언어
  - 데이터베이스 사용자의 권한 제어를 위해 사용하는 명령어



### SQL Keywords - Data Manipulation Language

- INSERT : 새로운 데이터를 삽입(추가)
- SELECT : 저장되어있는 데이터 조회
- UPDATE : 저장되어있는 데이터 갱신
- DELETE : 저장되어있는 데이터 삭제



---

## 📚 테이블 생성 및 삭제

``` bash
$ sqlite3 tutorial.sqlite3
sqlite > .database
```

에서 '.'은 sqlite 프로그램의 기능을 실행하는 것이다.

### 데이터베이스 생성

``` bash
hyunbee@LAPTOP-VQFRJFAR MINGW64 ~/ssafy7/webex_student/db
$ sql3 example.sqlite3
SQLite version 3.38.1 2022-03-12 13:37:29
Enter ".help" for usage hints.
sqlite>.database
main: C:\Users\hyunbee\ssafy7\webex_student\db\example.sqlite3 r/w
```



### csv 파일을 table로 만들기

``` bash
sqlite> .mode csv
sqlite> .import hellodb.csv examples
sqlite> .tables
examples
sqlite>
```

- .mode는 ouput을 설정하는 명령어다.
- output을 csv파일로 설정한다. (csv파일을 불러올 때 모드설정을 필수로 해주어야 한다.)
- import 시킬 때 생성할 테이블 명으로 examples를 기재하였다.
- .table 해당 테이블이 생성된다.









---

# 📚 CREATE

## 📕 CTEATE

#### INSERT

- "insert a  single row into a table"
- 테이블에 단일 행 삽입

``` bash
INSERT INTO 테이블이름(컬럼1, 컬럼2, ...) VALUES (값1, 값2, ,,,);
```

- INSERT는 특정 레이블에 레코드(행)를 삽입(생성)한다.



## 📒 READ

### SELECT statement

- SELECT

  - "query data from a table"

  - 테이블에서 데이터를 조회

  - SELECT문은 SQLite에서 가장 복잡한 문이며 다양한 절(clause)과 함께 사용된다.

    - ORDERY BY, DISTINCT, WHERE, LIMIT, GROUP BY, ..

    

### SELECT와 함께 사용하는 clause

#### LIMIT

- "constrain the number of rows returned by a query"
- 쿼리에서 반환되는 행 수를 제한
- 특정 행부터 시작해서 조회하기 위해 OFFSET 키워드와 함께 사용하기도 한다.

#### WHERE

- "specify the search condition for rows returned by the query"
- 쿼리에서 반환된 행에 대한 특정 검색 조건을 지정

#### SELECT DISTINCT

- "remove duplicate rows in the result set"
- 조회 결과에서 중복 행을 제거
- DISTINCT 절은 SELECT 키워드 바로 뒤에 작성해야 한다.



## 📙 DELETE

### DELETE

- DELETE FROM 테이블명 WHERE 조건;

- 조건을 통해 특 레코드 삭제하기
- **중복 불가능한 값인 rowid를 기준**으로 **삭제**한다.

- 지워진 id의 값은 어떻게 되는가? 재활용된다.
  - 장고는 재활용하지 않고 다음 값부터 사용된다.
  - SQLite는 기본적으로 **id를 재사용**한다.



### AUTOINCREMENT

- Column attribute
- SQLite가 사용되지 않은 값이나 이전에 삭제된 행의 값을 재사용하는 것을 방지

- 테이블을 생성하는 단계에서 AUTOINCREMENT를 통해 설정이 가능하다.
  - 장고에서는 해당 속성을 기본 값으로 사용한다.



## 📗 UPDATE

### UPDATE statement

#### update

- update data of existing rows in the table
- 기존 행의 데이터를 수정한다
- SET clause에서 테이블의 각 열에 대해 새로운 값을 설정한다.

- 중복 불가능한 값인 rowid를 기준으로 수정하자



---



## 📗 SQLite Aggregate Functions

### Aggregate function

- 집계 함수
- 값 집합에 대한 계산을 수행하고 단일 값을 반환한다.
  - 여러 행으로부터 하나의 결과값을 반환한다. 
- SELECT 구문에서만 사용된다.
- 예시
  - 테이블 전체 행 수를 구하는 COUNT(*)
  - age 컬럼 전체 평균 값을 구하는 AVG(Age)



- AVG, SUM, MIN, MAX
  - 해당 컬럼이 숫자(정수)일 때만 사용가능하다.



---

## 📗 LIKE

### LIKE operator

- query data based on pattern matching
- 패턴 일치를 기반으로 데이터를 조회하는 방법
- SQLite는 패턴 구성을 위한 2개의 wildcards를 제공한다.
  - % (percent sign)
    - 0 개 이상의 문자
  - _ (underscore)
    - 임의의 단일 문자



---

## 📗 ORDER BY

### Order by clause

#### ORDER BY

- sort a result set of a query
- 조회 결과 집합을 정렬
- SELECT 문에 추가하여 사용한다.
- 정렬 순서를 위한 2개의 key word를 제공한다.
  - ASC - 오름차순(default)
  - DESC - 내림차순





---

## 📗 ORDER BY

### GROUP by clause

#### GROUP BY

- 행 집합에서 요약행 집합을 만든다.
- select문의 optional절
- 선택된 행 그룹을 하나 이상의 열 값으로 요약 행으로 만든다.
- 문장에 WHERE 절이 포함된 경우 반드시 WHERE 절 뒤에 작성해야 한다.



---