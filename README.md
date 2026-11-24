# SAP Study

SAP ERP 업무와 ABAP, RAP 개발을 공부하며 이해한 내용을 정리합니다.

## 학습 목표

- SAP 조직 구조와 마스터·트랜잭션 데이터의 관계 이해
- FI, CO, HR, MM, PP, SD의 주요 업무와 모듈 간 연계 이해
- ABAP 데이터 모델링과 RAP 업무 애플리케이션 개발 학습
- 주요 개념과 동작 원리, 개념 간 차이를 설명할 수 있는 지식 축적

## 학습 항목

### Basic — SAP 공통 개념

목표: 조직, 데이터, 문서가 연결되는 이유를 설명한다.

- [x] [ERP의 목적과 SAP 모듈별 역할](basic/ERP의%20목적과%20SAP%20모듈별%20역할.md)
- [x] [Client와 회사코드, 관리회계영역의 역할과 관계](basic/Client와%20회사코드,%20관리회계영역의%20역할과%20관계.md)
- [x] [플랜트, 저장위치, 구매조직, 영업영역의 구분](basic/플랜트,저장위치,구매조직,영업영역의%20구분.md)
- [ ] 마스터 데이터와 트랜잭션 데이터
- [ ] Business Partner와 Customer, Supplier의 관계
- [ ] 회계연도, 회계연도 변형, 정상기간, 특별기간
- [ ] Header/Item 구조와 문서 간 참조
- [ ] 업무 이벤트와 회계 전표 발생 시점
- [ ] 구매부터 지급까지의 P2P 흐름
- [ ] 판매부터 수금까지의 O2C 흐름
- [ ] 전표부터 보고, 결산까지의 R2R 흐름
- [ ] S/4HANA Universal Journal의 목적
- [ ] DB Table, Compatibility View, CDS, API의 구분

### FI — Financial Accounting

목표: 업무 사건이 어떤 계정과 전표로 기록되는지 설명한다.

- [ ] G/L Account와 계정과목표, 계정 유형
- [ ] Journal Entry의 Header/Item과 차변, 대변
- [ ] 증빙일, 전기일, 회계연도, 회계기간의 차이
- [ ] Document Type과 Posting Key
- [ ] Tax Code와 매입·매출 부가세 전표
- [ ] AP: 공급업체 채무, 지급, 미결항목·반제
- [ ] AR: 고객 채권, 수금, 미결항목·반제
- [ ] 부분반제와 잔여항목 처리
- [ ] GR/IR 계정과 입고, 송장 간 차이
- [ ] 역분개와 원본 전표 추적
- [ ] 전기기간 개방, 잠금과 마감 후 전기 통제
- [ ] Trial Balance와 G/L Balance
- [ ] BKPF, BSEG, ACDOCA의 역할과 차이
- [ ] FI 관련 CDS/API와 표준 데이터 접근

결산 관리:
- [ ] 월말 마감과 Closing Cockpit 개념
- [ ] Closing Task, 담당자·기한·선후행 의존성
- [ ] 재고, GR/IR, AP, AR, G/L 대사
- [ ] Exception Log와 미해결 차이 관리
- [ ] 완료 증빙, 승인, 기간 잠금

### CO — Controlling

목표: 비용이 어디에서 발생하고 어디로 배부, 정산되는지 설명한다.

- [ ] FI와 CO의 목적 차이 및 Universal Journal 통합
- [ ] Controlling Area와 Company Code의 관계
- [ ] Cost Center와 비용 귀속
- [ ] Profit Center와 책임 단위별 손익
- [ ] Internal Order와 특정 목적의 비용 집계
- [ ] Cost Element와 G/L 계정의 통합
- [ ] 1차 원가와 2차 원가
- [ ] Activity Type, 활동단가, Statistical Key Figure
- [ ] Distribution과 Assessment의 차이
- [ ] Sender·Receiver, 배부 기준과 실행 결과
- [ ] 오더 정산과 수신자
- [ ] 계획 대비 실제원가 및 원가 보고
- [ ] 주요 테이블과 S/4HANA CDS/API 접근

### HR — Human Resources

목표: 인사 이력과 근태, 급여 결과가 인건비로 연결되는 과정을 이해한다.

- [ ] HR/HCM의 주요 영역과 적용 제품, 범위 구분
- [ ] Organizational Unit, Job·Position의 차이
- [ ] Personnel Area, Personnel Subarea
- [ ] 직원 기본정보와 조직배정 이력
- [ ] 유효기간 기반 데이터 관리
- [ ] Work Schedule, Time Entry·Absence
- [ ] Wage Type과 급여 구성요소
- [ ] Payroll 기간, 실행, 직원별 결과
- [ ] 급여비용, 미지급금과 FI 전기
- [ ] 직원 비용의 Cost Center 귀속과 배부
- [ ] 주요 테이블의 업무 의미와 접근 가능 범위

### MM — Materials Management

목표: 구매, 재고, 송장 처리에서 수량과 회계금액이 어떻게 연결되는지 설명한다.

- [ ] Plant와 Storage Location의 역할 및 복합키
- [ ] Purchasing Organization과 Purchasing Group
- [ ] Material Master의 일반, 플랜트, 저장위치, 평가 정보
- [ ] Supplier, Purchasing Info Record, 조달원
- [ ] Purchase Requisition과 Purchase Order
- [ ] 발주 Header/Item, 납품일정, 계정지정
- [ ] Goods Receipt와 Material Document
- [ ] Movement Type과 입고, 출고, 이동, 취소
- [ ] 재고 수불, 재고유형, 수량, 가액
- [ ] Valuation Class와 자동 계정결정
- [ ] Supplier Invoice와 3-way Match
- [ ] 수량, 가격 차이, 부분입고, 부분송장
- [ ] 입고, 송장, 지급의 FI 전표 연결
- [ ] 주요 테이블과 S/4HANA CDS/API 접근

### PP — Production Planning

목표: 생산계획이 자재 소비·생산실적·완제품·원가로 이어지는 과정을 설명한다.

- [ ] 생산관리의 주요 마스터와 문서
- [ ] BOM과 구성품 소요량
- [ ] Work Center와 생산능력, 원가 연결
- [ ] Routing과 공정, 표준시간
- [ ] Production Version의 BOM/Routing 연결
- [ ] 수요, 가용재고, MRP, 계획오더
- [ ] Production Order와 상태 전이
- [ ] 자재 예약, 구성품 출고, Backflush
- [ ] 공정실적, 작업시간, 양품, 폐기, 재작업
- [ ] 완제품 입고와 재고 증가
- [ ] 실제원가, WIP, 차이, 정산
- [ ] MM, FI, CO와의 연결 및 주요 테이블

### SD — Sales and Distribution

목표: 주문·출고·청구·수금의 차이와 회계 영향을 설명한다.

- [ ] Customer와 영업영역별 마스터
- [ ] Sales Organization·Distribution Channel·Division
- [ ] Sales Area와 출하 플랜트, Shipping Point
- [ ] Pricing Condition과 가격, 할인, 운송비·세금
- [ ] Sales Order의 Header/Item, 일정, Partner
- [ ] 가용수량 확인과 납기, 확정수량
- [ ] Delivery, Picking, Goods Issue
- [ ] 출고의 재고 감소, 매출원가 전표
- [ ] Billing의 매출, AR, 부가세 전표
- [ ] 수금과 AR Clearing
- [ ] Credit Memo, 반품, 취소의 구분
- [ ] 선행, 후속 문서와 누적수량 추적
- [ ] 주요 테이블과 S/4HANA CDS/API 접근

### ABAP

목표: 데이터 타입과 저장, 조회 구조를 이해하고 구현 이유를 설명한다.

- [x] [Classic ABAP, ABAP Objects, Modern ABAP의 흐름](ABAP/Classic%20ABAP,ABAP%20Objects,Modern%20ABAP의%20흐름.md)
- [x] [기본 데이터 타입과 Complete/Incomplete Type](ABAP/기본%20데이터%20타입과%20Complete,Incomplete%20Type.md)
- [x] [TYPE, LIKE, REF TO의 차이](ABAP/TYPE,%20LIKE,%20REF%20TO의%20차이.md)
- [ ] Domain, Data Element, Structure, Table Type
- [ ] Data Element의 의미와 재사용
- [ ] Database Table과 Internal Table의 차이
- [ ] MANDT와 Client, dependent 데이터

### RAP — RESTful ABAP Programming Model

목표: 업무 객체의 구조, 동작, 저장, 권한, 검증 흐름을 설명한다.

- [ ] RAP 전체 구성과 Managed/Unmanaged의 차이
- [ ] Root와 Child, Business Object의 경계
- [ ] Composition과 Association의 선택 기준
- [ ] Interface/Projection 계층과 서비스 노출
- [ ] Behavior Definition과 Behavior Implementation
- [ ] strict(2)와 UUID 기술키, 업무번호 분리
- [ ] Managed Numbering과 수동 채번
- [ ] key, %key, %tky의 구분
- [ ] Determination과 Validation의 역할, 실행 시점
- [ ] 파라미터가 있는 Action과 상태 전이
- [ ] Interaction Phase와 Save Sequence
- [ ] Draft의 목적과 활성 데이터의 관계
- [ ] Lock과 ETag를 통한 동시성 제어
- [ ] Global/Instance Authorization
- [ ] Feature Control과 상태별 기능 제어
- [ ] EML의 READ/MODIFY/COMMIT ENTITIES
- [ ] IN LOCAL MODE의 사용 범위와 우회 대상
- [ ] FAILED, REPORTED, MAPPED 결과 처리
- [ ] OData V4 Service Binding과 Fiori elements

테스트:
- [ ] setup, teardown, assert와 테스트 격리
- [ ] Action 성공, 실패 및 상태 전이 검증
- [ ] Validation, Determination 실행 결과 검증
- [ ] 테스트 더블과 테스트 데이터 정리
- [ ] 단위 테스트와 API, 화면, 통합 테스트의 구분
