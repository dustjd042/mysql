# MySQL

## MySQL 구조
1. 파서: SQL 문법 검토
2. 전처리기: 실제 객체 존재 및 권한 확인
3. 옵티마이저: 실행 계획 생성
4. 엔진 실행기: 옵티마이저 생성한 실행 계획 수행
5. 스토리지 엔진: 실제 데이터 접근

## 스토리지 엔진 종류
* InnoDB (현재 표준)
  * 트랜잭션 지원 (ACID)
  * MVCC 지원
  * Row Lock 지원
  * Foreign Key 지원
  * 장애 복구 지원
* MyISAM
  * 트랜잭션 미지원
  * Foreign Key 미지원
  * Table Lock 사용
  * 읽기 성능 우수
* Memory
  * RAM 저장
  * 매우 빠름
  * 서버 재시작 시 데이터 소실
* Archive
  * 강한 압축
  * INSERT 가능
  * UPDATE, DELETE 제한적
* CSV
  * 엑셀 연동 쉬움

## 로그의 종류
* Redo Log
  * 변경 후 데이터를 기록하는 로그 
  * 장애 발생 시 Commit 데이터 복구 위해 사용
* Undo Log
  * 변경 전 데이터를 기록하는 로그
  * Rollback 및 MVCC 구현에 사용
* Binary Log
  * MySQL Server 레벨 로그
  * 모든 데이터 변경 이력을 기록

## 실행 계획
### id: 실행 순서
### select_type: SELECT 유형
### table: 테이블 명칭 혹은 별칭
### partitions: 파티션 접근 영역
### type: 테이블 데이터 접근 방식
### possible_keys: SQL 최적화 사용할 수 있는 인덱스 목록
### key: SQL 최적화 위해 사용한 인덱스
### key_len: 사용한 인덱스 바이트
### ref: 테이블 조인 수행 조건
### rows: SQL 수행 과정 접근한 데이터 행 갯수
### filtered: 필터 조건에 따라 제거된 데이터 비율
### extra: SQL 수행 과정 대한 부가 정보

