# NovaFund

## 프로젝트 소개
NovaFund는 사용자가 프로젝트를 등록하고 펀딩에 참여할 수 있는
참여형 펀딩 플랫폼입니다.
본 프로젝트는 팀 프로젝트로 진행되었으며,
저는 인증/회원/관리자 기능 및 캐시/정산 로직 설계를 담당했습니다.

## 기술 스택

### Backend
- Spring Framework(MVC)
- Spring Security

### Frontend
- JSP
- HTML/CSS/JavaScript

### Database
- Oracle DB

### Server/Tool
- Apache Tomcat
- Git / Github

## 프로젝트 구성
### 프로젝트 유형: 팀 프로젝트
### 담당 역할
- 로그인 / 회원가입
- 마이페이지
- 관리자 페이지
- 인증 및 권한 처리
- 캐시 사용내역 및 정산 로직 설계

## 담당 기능 상세
### 로그인/회원가입
- Spring Security 기반 인증 처리
- BCrypt 비밀번호 암호화 적용
- 사용자 / 관리자 권한 분리

### 마이페이지
- 회원 정보 조회 및 관리
- 후원 내역 / 캐시 사용 내역 조회

### 관리자 페이지
- 프로젝트 승인 / 반려 처리
- 프로젝트 상태 관리
- 펀딩 성공/실패에 따른 정산 및 환불 처리

### 후원 캐시 정산 관리
- 후원·충전·출금 내역을 캐시 기반으로 통합 관리
- 금액 변동에 따른 상태 및 색상 UI 처리
- 출금 요청 시 관리자 승인 -> 자동 상태 변경
- 캐시 잔액 실시간 반영

### 자동 상태 업데이트(Scheduler)
- Spring Scheduler를 이용해
  - 종료일이 지난 프로젝트 자동 조회
  - 목표 금액 달성 여부에 따라 성공/실패 상태 변경
- 상태 변경 후 관리자 승인 시
  - 성공 -> 프로젝트 생성자에게 캐시 지급
  - 실패 -> 후원자에게 캐시 자동 환불

### 인증 & 권한 설계
- USER, ADMIN 역할 기반 접근 제어
- 로그인 성공 후 이전 페이지 이동 처리

## DB 설정 구조(보안 분리)
DB 접속 정보는 보안 및 환경 분리를 위해 Git에 직접 포함하지 않았습니다.

### 설정 방식
- root-context.xml -> Git에 포함
- db.properties -> Git제외
- db.properties.example -> Git에 포함
### db.properties.example
- db.driver=oracle.jdbc.driver.OracleDriver
- db.url=jdbc:oracle:thin:@localhost:1521:xe
- db.username=YOUR_DB_USERNAME
- db.password=YOUR_DB_PASSWORD

## 실행 방법
### 환경
- JDK 8 이상
- Apache Tomcat 9
- Oracle DB

### DB설정
- src/main/resources/db.properties.example
-> db.properties로 복사 후 DB 계정 정보 입력

### 실행
- Tomcat 서버 실행
- 브라우저 접속 -> http://localhost:8080/novafund

## 프로젝트를 통해 얻은 점
- Spring Security 기반 인증/권한 흐름 이해
- 캐시·후원·정산을 포함한 상태 중심 도메인 설계 경험
- 스케줄러를 활용한 자동화 로직 구현
- 팀 프로젝트에서 핵심 기능 책임 구현 경험

## 참고
본 프로젝트는 학습 및 포트폴리오 목적의 팀 프로젝트이며, 실제 서비스 흐름을 고려한 구조로 구현되었습니다.


