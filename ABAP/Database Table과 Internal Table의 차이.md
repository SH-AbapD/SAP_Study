# Database Table과 Internal Table의 차이

Database Table은 데이터를 DB에 저장하는 테이블이고, Internal Table은 ABAP 프로그램이 여러 행을 메모리에 담아 처리하는 데이터 객체
예를 들어 FI 전표 조회 프로그램은 DB에서 전표를 읽고, 조회 결과를 Internal Table에 담아 정렬한 뒤 화면에 표시 가능

| 구분 | Database Table | Internal Table |
|---|---|---|
| 목적 | 업무 데이터를 저장하고 이후에도 조회 | 프로그램에서 여러 행을 담아 가공 |
| 데이터 위치 | 데이터베이스 | ABAP 프로그램 메모리 |
| 데이터 수명 | 커밋된 데이터는 프로그램이 끝나도 남음 | 데이터 객체가 살아 있는 동안 유지 |
| 접근 방법 | ABAP SQL의 SELECT 등 | LOOP AT, READ TABLE, SORT 등 |
| 키 | 기본 키로 각 행을 고유하게 식별 | 테이블 종류와 키 정의에 따라 중복 허용 여부와 접근 방식이 달라짐 |

 ** 다만 최근 RAP에서는 Business Object를 통해 데이터를 조작하는 방식을 선호. 따라서 직접적인 DB 접근은 권장되지 않음.

## FI 전표 조회 예시

회사코드 1000의 전표를 읽어 전기일이 최근인 순서로 표시한다고 가정. zfi_doc는 예시를 위해 가정한 커스텀 DB 테이블

```
SELECT FROM zfi_doc
  FIELDS company_code, fiscal_year, doc_no, posting_date
  WHERE company_code = '1000'
  INTO TABLE @DATA(lt_docs).

SORT lt_docs BY posting_date DESCENDING.
```

1. SELECT FROM zfi_doc는 Database Table에서 조건에 맞는 전표를 읽음
2. INTO TABLE @DATA(lt_docs)는 조회 결과를 Internal Table에 담음
3. SORT lt_docs는 메모리에 담긴 조회 결과를 정렬. 이 목록에서 행을 삭제하거나 값을 바꿔도 DB에 저장된 전표에는 자동으로 반영되지 않음
