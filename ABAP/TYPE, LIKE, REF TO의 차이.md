# TYPE, LIKE, REF TO의 차이

TYPE, LIKE, REF TO는 단일 값뿐 아니라 Structure와 Internal Table을 선언할 때도 사용한다.

## TYPE이란?

타입 이름을 기준으로 새로운 데이터 객체를 선언하는 방식이다.

기본 타입, 직접 정의한 타입, ABAP Dictionary의 타입 등을 사용할 수 있다.

TYPES: BEGIN OF ty_user,
         name TYPE string,
         age  TYPE i,
       END OF ty_user.

TYPES tt_users TYPE STANDARD TABLE OF ty_user WITH EMPTY KEY.

DATA lv_count TYPE i.
DATA ls_user  TYPE ty_user.
DATA lt_users TYPE tt_users.

- lv_count: 정수 변수
- ls_user: 이름과 나이를 담는 Structure
- lt_users: 여러 사용자 행을 담는 Internal Table

## LIKE란?

기존 데이터 객체와 같은 타입으로 새로운 데이터 객체를 선언하는 방식이다.

DATA lv_other_count LIKE lv_count.
DATA ls_other_user  LIKE ls_user.
DATA lt_other_users LIKE lt_users.

- 단일 값은 같은 타입과 길이로 선언
- Structure는 같은 구성요소와 타입으로 선언
- Internal Table은 같은 행 타입·테이블 종류·키로 선언
- 기존 값이나 행은 복사하지 않으며, 별개의 데이터를 저장

Internal Table의 한 행과 같은 타입으로 선언하려면 LINE OF를 사용

DATA ls_row LIKE LINE OF lt_users.

ls_row는 Internal Table이 아니라, 한 명의 사용자 정보를 담는 Structure

## REF TO란?

데이터나 객체를 가리키는 참조 타입을 지정할 때 사용한다. 주로 TYPE REF TO 형태로 작성한다.

DATA lr_count TYPE REF TO i.
DATA lr_user  TYPE REF TO ty_user.
DATA lr_users TYPE REF TO tt_users.

참조 변수를 선언한 것만으로는 어떤 대상도 가리키지 않음. 다음처럼 기존 데이터에 연결할 수 있음

lr_count = REF #( lv_count ).
lr_user  = REF #( ls_user ).
lr_users = REF #( lt_users ).

lr_count → lv_count: 정수 변수
lr_user  → ls_user:  Structure
lr_users → lt_users: Internal Table

참조를 통해 대상의 데이터를 변경하면 원래 데이터가 변경됨

lr_count->* = 10.
lr_user->name = 'Kim'.

- lv_count의 값이 10으로 변경됨
- ls_user의 이름이 'Kim'으로 변경됨

클래스나 인터페이스를 대상으로 하면 객체 참조 타입을 선언할 수도 있음

## 요약

| 구분 | 의미 |
|---|---|
| TYPE | 타입을 기준으로 새로운 데이터 객체 선언 |
| LIKE | 기존 데이터 객체와 같은 타입으로 별도의 데이터 객체 선언 |
| REF TO | 데이터나 객체를 가리키는 참조 타입 지정 |

LIKE는 같은 형식의 별도 데이터를 만들고, 참조는 연결된 대상을 가리킨다.

TYPE과 LIKE는 타입을 지정하는 기준의 차이이고, REF TO는 참조 타입을 만드는 구문이다.
