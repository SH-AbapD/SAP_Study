# Domain, Data Element, Structure, Table Type

ABAP Dictionary(DDIC)에서는 값의 형식, 필드의 업무 의미, 한 행의 구성, 여러 행을 담을 내부 테이블의 규칙을 각각 정의 가능하다.

FI 전표 목록을 예로 들면 다음과 같다.

| 객체 | 무엇을 정의하나? |
|---|---|---|
| Domain | 데이터 타입, 길이 등 기술적 속성 |
| Data Element | 한 필드의 타입과 업무 의미 |
| Structure | 한 행을 구성하는 필드와 각 필드의 타입 |
| Table Type | 내부 테이블의 행 타입, 테이블 종류, 키 |

## Domain과 Data Element

Domain은 여러 필드에서 공유할 기술적 속성을 정의

예를 들어 전표번호에 사용할 CHAR 10자리 형식을 정의 가능. 필요한 경우 고정값이나 값 범위도 지정 가능

Data Element는 한 필드에 사용할 타입과 업무 의미를 정의
Field Label을 지정할 수 있고, 문서를 작성해 두면 이를 사용하는 화면에서 F1 도움말로 표시 가능.
예를 들어 회계 전표번호와 원전표 번호는 둘 다 10자리 문자 형식을 쓸 수 있지만, 하나는 현재 전표를, 다른 하나는 참조하는 원전표를 가리킴.
두 Data Element가 같은 Domain을 참조하면서 각자의 Label을 가질 수 있음. Data Element는 Domain을 참조하거나 DDIC 기본 타입을 직접 지정 가능.

Label : 화면에서 사용자가 보는 필드 이름

## Structure와 Table Type

Structure는 여러 필드를 이름과 타입으로 묶음.
전표 조회 결과의 한 행에 회사코드, 회계연도, 전표번호, 원전표 번호를 담고 싶다면 이 필드들을 하나의 Structure로 정의 가능.

Table Type은 그 행을 담는 내부 테이블의 타입이다. 행 타입에 더해 STANDARD, SORTED, HASHED 중 어떤 종류의 테이블인지, 어떤 키를 사용할지 정의. 
행 타입에는 Structure 외에 Data Element도 사용 가능
예를 들어 전표번호만 담는 내부 테이블이라면 전표번호 Data Element를 행 타입 사용 가능

## ABAP에서 TYPE으로 사용하기

아래 Z 객체는 설명을 위해 가정한 DDIC 객체

zde_fi_doc_no는 전표번호 Data Element, zs_fi_doc는 전표 한 행의 Structure, ztt_fi_doc는 이 Structure를 행 타입으로 사용하는 Table Type

DATA lv_doc_no TYPE zde_fi_doc_no.
DATA ls_doc    TYPE zs_fi_doc.
DATA lt_docs   TYPE ztt_fi_doc.

- lv_doc_no에는 전표번호 하나
- ls_doc에는 여러 필드로 구성된 전표 한 행
- lt_docs는 전표 행을 여러 개 담을 수 있는 내부 테이블

TYPE에는 Data Element, Structure, Table Type을 직접 지정 가능
Domain은 Data Element에 기술적 속성을 제공하므로 DATA ... TYPE에 직접 지정 불가. 
DDIC의 Table Type은 내부 테이블의 타입을 정의하고, DATA 선언으로 프로그램에서 사용할 내부 테이블을 생성
