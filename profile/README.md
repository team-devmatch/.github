# FESTIGO - 축제 정보 + AI 챗봇 플랫폼

> Cloud Native 기반 AI Agent 서비스를 개발하는 3기 3팀입니다.

---

## 팀원 소개

| 이름 | 역할 | 담당 |
|------|------|------|
| 김지환 | 팀장 / 프론트엔드 | 메인 페이지, 축제 상세 페이지, 라우팅, UI 설계, 캘린더 |
| 오충환 | 프론트엔드 | 로그인, 회원가입, 마이페이지, 게시판 |
| 이재욱 | 백엔드 | Spring Boot REST API, JWT 인증 |
| 오경준 | 인프라 / DB / AI | Docker, CI/CD, DB 설계, AI 챗봇, AWS 배포 |
---

## 프로젝트 소개
**FESTIVA**는 전국 축제 정보를 제공하고 AI 챗봇으로 축제를 추천해주는 플랫폼입니다.

### 주요 기능
- **축제 정보 조회** — 테마별 필터 (자연코스, 가족과함께, 연인과함께 등)
- **AI 챗봇** — 날짜/날씨 기반 맞춤 축제 추천
- **게시판** — 축제 후기 작성, 댓글, 좋아요
- **회원 시스템** — 회원가입/로그인 (JWT 인증)

---

## 기술 스택

| 분류 | 기술 |
|------|------|
| Frontend | React, Redux Toolkit, CSS Module |
| Backend | Spring Boot, JPA, JWT, Swagger |
| AI Service | FastAPI, LangChain, OpenAI gpt-4o-mini |
| Database | PostgreSQL, Redis |
| Infra | Docker, Docker Compose, GitHub Actions |

---

## 레포지토리
| 레포 | 설명 |
|------|------|
| frontend | React 기반 프론트엔드 |
| backend | Spring Boot 기반 REST API |
| ai-service | FastAPI 기반 AI 서비스 |
| database | ERD 설계 및 DDL |
| project-infra | Docker, AWS, CI/CD |

---

## 아키텍처
사용자 브라우저 → React(localhost:5173) → Spring Boot(localhost:8080) → FastAPI(localhost:8000)
→ PostgreSQL(localhost:5432),OpenAI API(외부 서비스)


## 로컬 실행 방법

### 사전 준비
- Docker Desktop 설치 및 실행
- Java 17 설치
- Node.js 설치
- Python 3.14 설치

### 1. DB 실행
```bash
cd project-infra
docker-compose up -d
```

### 2. 백엔드 실행
```bash
cd backend
./gradlew bootRun
```

### 3. AI 서비스 실행
```bash
cd ai-service
pip install -r requirements.txt
uvicorn main:app --reload
```

### 4. 프론트엔드 실행
```bash
cd frontend
npm install
npm run dev
```

### 5. 접속
http://localhost:5173

---

## 환경변수 설정

### ai-service/.env
OPENAI_API_KEY=your_openai_api_key
WEATHER_API_KEY=your_weather_api_key
DB_HOST=localhost
DB_PORT=5432
DB_NAME=festivaldb
DB_USER=admin
DB_PASSWORD=password

### backend
application.yml 참고

---

## DB 테이블 구조

| 테이블 | 설명 |
|--------|------|
| users | 회원 정보 |
| festival | 축제 기본 정보 |
| festival_detail | 축제 상세 정보 |
| review | 축제 리뷰 |
| post | 게시글 |
| comment | 댓글 |
| post_like | 게시글 좋아요 |

---

## CI/CD
코드 Push (ai-service) → GitHub Actions 실행 → Docker 이미지 빌드 → Docker Hub Push
