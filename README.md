# 📌 Fit Routine

## 👨‍👩‍👦 팀명/팀원

**BASIC 팀**

- 김일현(팀장)
- 안민영
- 유성재
- 정혜영

## 🗓️ 개발 기간

**2025.04.21 ~ 2025.06.17**

## 📝 프로젝트 개요

**Fit Routine**은 사용자의 운동 목표에 맞춰 식단과 운동을 추천받고, 이를 토대로 직접 계획을 설정하며, 인증 사진을 공유하고 소통할 수 있는 건강 관리 플랫폼입니다.

## 📄프로젝트 레포지토리

- [fit-routine-backend](https://github.com/basic-stack/fit-routine-backend)
- [fit-routine-frontend](https://github.com/basic-stack/fit-routine-frontend)

## 🎯 개발 배경 및 목적

### 배경

- 매일 내가 해야 할 운동과 식단을 찾는 것이 번거로움
- 건강 관리가 익숙하지 않은 사람은 무엇을 어떻게 시작해야 할지 모름
- 결심은 했지만 지속하는 것이 어려움 (3일의 벽)

### 목적

- 사용자 맞춤형 운동과 식단을 제공하여 **건강한 루틴 형성**을 돕고
- **커뮤니티 및 블로그** 기능으로 **동기 부여** 및 **지속적인 활동 유도**

## 👤 주요 사용자

- 건강 관리에 관심은 있지만 지속이 어려운 사람
- 운동 및 식단 관리가 막막한 일반 유저

## 🧩 핵심 기능

1. **맞춤 운동/식단 추천 및 설정**  
   사용자의 **신체 정보와 목표**를 기반으로 자동 추천 및 직접 설정

2. **운동/식단 인증 업로드**  
   사용자 본인의 식단, 운동 사진 등을 인증하여 기록

3. **커뮤니티 공유 기능**  
   다른 사용자들과 **게시물 소통** 및 **공감 활동**

4. **활동 히스토리 관리**  
   내 블로그에서 **나의 루틴과 게시물 이력**을 확인

## 팀 규칙

- [Backend 규칙](./docs/backend-rule.md)
- [Frontend 규칙](./docs/frontend-rule.md)
- [Git 규칙](./docs/git-rule.md)

## 🛠️ 사용 기술 스택

### Frontend

- React
- React Router
- Axios
- CSS Modules
- FullCalendar
- chartjs-2
- SweetAlert2
- Toastify

### Backend

- Spring
- Spring Boot
- Spring Security
- MyBatis
- Oracle JDBC
- Lombok
- JWT

### Database

- Oracle

### 개발 도구

- ERD Cloud (DB 테이블 설계)
- Figma (UI/UX 설계)
- Github (형상 관리)
- Notion (초안 아이디어 및 규칙 정리, 일정 및 역할 관리)
- Visual Studio Code (Frontend 개발)
- IntelliJ IDEA (Backend 개발)

### 외부 연계 서비스

- 공공데이터 포털 OPEN API (운동·식단 정보)

## 🗂️ 화면/기능 흐름

1. **회원가입 / 로그인**
2. **운동 · 식단 목표 설정 (TODO)**
3. **인증 게시물 작성 (운동 · 식단 기록)**
4. **게시판, 블로그를 통한 공유 및 소통**
