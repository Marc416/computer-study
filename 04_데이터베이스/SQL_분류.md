# SQL 분류 (DDL / DML / DCL)

## 핵심 요약
> SQL은 크게 **DDL**(정의), **DML**(조작), **DCL**(제어)로 나뉜다.
> DML은 **절차적 / 비절차적**으로 다시 나뉜다.

## 주요 개념

### 1. DDL (데이터 정의어, Data Definition Language)
- DB의 **구조(테이블, 스키마)를 만들고 바꾸고 삭제**하는 언어
- 비유: 건물의 설계도를 그리고, 수정하고, 철거하는 것

| 명령어 | 의미 | 설명 |
|--------|------|------|
| CREATE | 생성 | 테이블, 뷰, 인덱스 등 새로 만들기 |
| ALTER | 수정 | 기존 구조 변경 (컬럼 추가/삭제 등) |
| DROP | 삭제 | 테이블 자체를 완전히 제거 |
| RENAME | 이름변경 | 테이블 이름 변경 |
| TRUNCATE | 초기화 | 데이터만 전부 삭제 (구조는 유지) |

### 2. DML (데이터 조작어, Data Manipulation Language)
- DB의 **데이터를 조회, 삽입, 수정, 삭제**하는 언어
- 비유: 건물 안에서 물건을 넣고 빼고 정리하는 것

| 명령어 | 의미 |
|--------|------|
| SELECT | 조회 |
| INSERT | 삽입 |
| UPDATE | 수정 |
| DELETE | 삭제 |

#### 절차적 DML vs 비절차적 DML

| 구분 | 절차적 DML | 비절차적 DML |
|------|-----------|-------------|
| 특징 | **어떻게** 찾을지 순서대로 지시 | **뭘** 원하는지만 말함 |
| 방식 | 한 건씩 커서로 처리 | 한번에 결과 집합 반환 |
| 예시 | PL/SQL, 프로그래밍 언어 내 DB처리 | 일반 SQL (SELECT, INSERT 등) |
| 비유 | "냄비 꺼내고, 물 넣고, 끓여라" | "김치찌개 주세요" |

- ⚠️ **시험 포인트**: 일반 SQL = **비절차적**, PL/SQL 등 = **절차적**

### 3. DCL (데이터 제어어, Data Control Language)
- DB의 **권한, 보안, 무결성**을 관리하는 언어
- 비유: 회사 출입카드 관리 (누구한테 어떤 권한 줄지)

| 명령어 | 의미 |
|--------|------|
| GRANT | 권한 부여 |
| REVOKE | 권한 회수 |

### 4. TCL (트랜잭션 제어어) — DCL에 포함하기도 함

| 명령어 | 의미 |
|--------|------|
| COMMIT | 변경 내용 확정 저장 |
| ROLLBACK | 변경 내용 취소, 이전 상태로 되돌림 |
| SAVEPOINT | 롤백할 지점 지정 |

- ⚠️ 교재에 따라 COMMIT/ROLLBACK을 **DCL에 포함**하기도 하고 **TCL로 분리**하기도 함

### 🧠 TCL ⊂ DCL 암기법: "DCL = 컨트롤 타워"
- 컨트롤 타워에서 하는 일 두 가지:
  1. **출입 통제** → GRANT / REVOKE (권한 제어)
  2. **작업 확정/취소** → COMMIT / ROLLBACK (트랜잭션 제어)
- 공통점: 둘 다 **데이터 자체를 건드리지 않고 "제어"만 함** → 그래서 DCL로 묶임
- 시험 팁: 선택지에 COMMIT이 DCL에 있다고 바로 틀린 게 아님! 다른 항목도 비교해서 **가장 정확한 조합**을 골라야 함

### 5. DDL 제약조건 (CHECK 등) — CREATE / ALTER에서만 사용

- 제약조건은 **테이블의 "규칙"을 정하는 것** → DDL(CREATE, ALTER)에서만 등장
- 비유: 건물 설계할 때 "이 방은 5명까지만 입장 가능" 같은 규칙을 거는 것

| 제약조건 | 의미 | 예시 |
|---------|------|------|
| **PRIMARY KEY** | 기본키 (유일 + NOT NULL) | `id INT PRIMARY KEY` |
| **FOREIGN KEY** | 외래키 (다른 테이블 참조) | `REFERENCES 부서(부서코드)` |
| **UNIQUE** | 중복 불가 | `email VARCHAR(50) UNIQUE` |
| **NOT NULL** | NULL 불가 | `이름 VARCHAR(20) NOT NULL` |
| **CHECK** | 값의 범위/조건 지정 | `CHECK (나이 >= 18)` |
| **DEFAULT** | 기본값 설정 | `등급 VARCHAR(10) DEFAULT '일반'` |

- ⚠️ **시험 포인트**: CHECK 등 제약조건은 DML(SELECT, INSERT)이나 DCL(GRANT)에는 안 쓰임!

## 시험 빈출 포인트

### 단골 함정
| 함정 | 설명 |
|------|------|
| DROP vs DELETE vs TRUNCATE | DROP=테이블 자체 삭제, DELETE=데이터 행 삭제(롤백 가능), TRUNCATE=데이터 전체 삭제(롤백 불가) |
| 절차적 vs 비절차적 | 일반 SQL=비절차적, PL/SQL=절차적 |
| DCL vs TCL | GRANT/REVOKE=DCL 확정, COMMIT/ROLLBACK=DCL 또는 TCL |

## 기출 키워드
`DDL` `DML` `DCL` `TCL` `CREATE` `ALTER` `DROP` `TRUNCATE` `SELECT` `INSERT` `UPDATE` `DELETE` `GRANT` `REVOKE` `COMMIT` `ROLLBACK` `절차적 DML` `비절차적 DML` `PL/SQL`
