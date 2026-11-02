# 🔐 닿음 (Dahum)

**AI 기반 가족 보안 서비스**

보안 위협을 탐지하는 것을 넘어, 사용자가 위험을 이해하고 올바르게 대응할 수 있도록 돕는 가족 보안 서비스입니다.

---

## 01. Project Overview

| 항목 | 내용 |
|---|---|
| 프로젝트명 | 닿음 (Dahum) |
| 개발 기간 | 2026.08.18 ~ 2026.08.19 (무박 2일) |
| 팀 구성 | 5명 |
| 프로젝트 주제 | AI 기반 가족 보안 서비스 |
| 참여 행사 | [EST AI Challengers 제주 해커톤](https://estsoft.ai/all/est-ai-challengers-jeju-day1) |

---

## 02. Background

기존 보안 서비스는 악성 앱 탐지에는 강점이 있지만, 보안 지식이 부족한 사용자는 위험 알림만으로 왜 위험한지, 어떻게 대응해야 하는지 이해하기 어렵습니다. 특히 디지털 보안에 익숙하지 않은 부모님 세대가 단순한 위험 알림만으로 적절한 대응을 판단하기 어렵다는 점에 주목했습니다.

2025년 1~3월 경찰청 통계에 따르면 보이스피싱 피해액은 **3,116억 원**으로 전년 동기 대비 **120% 증가**했으며, 기관사칭형 범죄가 전체 발생 건수의 **51%**를 차지했습니다.

또한 제공받은 악성 앱 탐지 로그 10,000건을 분석한 결과, 탐지 이후 사용자 조치 기록에서 Delete는 **4,424건**, Exclude는 **249건**으로 나타났습니다.

이에 닿음은 단순한 위험 탐지를 넘어, 사용자가 보안 위협을 이해하고 실질적인 대응으로 이어갈 수 있도록 돕는 **AI 기반 가족 보안 서비스**를 기획했습니다.

---

## 03. Key Features

### 1. 이미지 기반 앱 정보 추출

사용자가 스마트폰에 설치된 앱 목록 이미지를 업로드하면 CLOVA OCR API를 통해 이미지 속 텍스트를 추출합니다. 추출된 텍스트에서 정규식 기반으로 앱 패키지명을 식별하여 이후 악성 앱 탐지에 활용할 수 있는 데이터로 변환합니다.

### 2. 악성 앱 탐지 및 데이터 조회

OCR을 통해 추출한 패키지명을 악성 앱 탐지 데이터와 비교하여 위험 여부를 확인합니다. 사전에 구축한 악성 앱 데이터셋을 활용해 앱 정보를 조회하고, 사용자가 의심스러운 앱을 확인할 수 있도록 분석 결과를 제공합니다.

### 3. AI 기반 분석 및 쉬운 설명

검색된 악성 앱 관련 정보를 바탕으로 AI가 보안 지식이 부족한 사용자도 이해할 수 있는 설명을 제공하도록 설계했습니다. 전문적인 보안 용어를 그대로 전달하는 대신 위험 요소와 주의사항을 쉽게 이해할 수 있도록 안내하는 것이 핵심입니다.

### 4. 보호자 대응 가이드

분석 결과를 확인하는 데서 끝나지 않고, 보호자가 위험 상황을 이해하고 적절하게 대응할 수 있도록 안내하는 기능입니다. 특히 디지털 보안에 익숙하지 않은 부모님 세대도 결과를 이해하고 필요한 조치를 판단할 수 있도록 돕는 것을 목표로 합니다.

---

## 04. Tech Stack

| 분류 | 기술 |
|---|---|
| Language | Python, Java |
| Data & ML | Pandas, Scikit-learn |
| Backend | Spring Boot, REST API |
| Database | MariaDB |
| OCR & Tools | CLOVA OCR API, Postman |

---

## 05. My Contributions

### Data Analysis & Preprocessing

- Python·Pandas를 활용한 악성 앱 탐지 데이터 10,000건 분석
- 중복 및 결측 데이터 정제
- 2,522개 고유 패키지 기반 서비스용 데이터셋 구축

### Backend & OCR Integration

- CLOVA OCR API 연동 및 이미지 내 앱 정보 추출
- 정규식을 활용한 패키지명 추출·정제 로직 구현
- Spring Boot 기반 API 연동 및 데이터 전달
- Postman과 브라우저 개발자 도구를 활용한 통합 테스트
- CORS 및 요청·응답 데이터 구조 불일치 문제 해결

### Machine Learning

- 악성 앱 유형 분류 모델 관련 작업

---

## 06. System Architecture

![Dahum System Architecture](docs/images/system-architecture.svg)

> **My Contribution:** 데이터 분석 및 전처리, 패키지명 추출, 악성 앱 탐지 DB 구축, OCR·백엔드 API 연동

---

## 07. Troubleshooting

### 1. CORS 문제로 인한 API 통신 오류

- **문제 상황:** 프론트엔드에서 백엔드 API를 호출하는 과정에서 CORS 오류가 발생하여 브라우저 환경에서 정상적인 데이터 통신이 이루어지지 않는 문제 발생
- **원인 확인:** 브라우저 개발자 도구의 Console 및 Network 탭을 활용해 요청 실패 여부와 응답 상태를 확인하고, Postman으로 동일 API를 별도 호출하여 통신 환경에 따른 차이 분석
- **해결 과정:** 프론트엔드와 백엔드 간 요청 경로 및 통신 과정을 확인하고, CORS 관련 설정을 점검하여 API 연동 문제 해결
- **개선 결과:** 브라우저 환경에서 발생하는 API 통신 문제를 해결하고 프론트엔드와 백엔드 간 연동 안정성 개선

### 2. API 요청·응답 데이터 구조 불일치

- **문제 상황:** 프론트엔드와 백엔드에서 정의한 요청 및 응답 데이터 구조가 일치하지 않아 전달받은 데이터를 정상적으로 처리하지 못하는 문제 발생
- **원인 확인:** Postman을 활용해 API 요청값과 응답값을 확인하고, 브라우저 개발자 도구의 Network 탭에서 실제 전달되는 데이터와 서버 응답 구조 비교
- **해결 과정:** 프론트엔드에서 사용하는 데이터 필드와 백엔드 API의 요청·응답 구조를 대조하고, 서로 다른 데이터 형식을 확인하여 연동 규격 조정
- **개선 결과:** API 데이터 전달 과정의 불일치를 해소하고 프론트엔드에서 백엔드 응답 데이터를 정상적으로 처리할 수 있도록 개선

---

## 08. Project Retrospective

### 1. 데이터 품질의 중요성

악성 앱 탐지 로그를 분석하고 전처리하는 과정에서 데이터의 중복 및 결측 여부가 서비스의 분석 결과에 영향을 줄 수 있다는 점을 경험했습니다. 단순히 데이터를 수집하는 것보다 서비스 목적에 맞게 정제하고 활용 가능한 데이터셋으로 구축하는 과정이 중요하다는 것을 배웠습니다.

### 2. API 연동과 협업의 중요성

OCR 처리부터 백엔드 API 연동까지 진행하며 각 기능이 개별적으로 동작하는 것과 전체 시스템에서 정상적으로 연결되는 것은 다르다는 점을 경험했습니다. 특히 CORS 오류와 요청·응답 데이터 구조 불일치를 해결하며 프론트엔드와 백엔드 간 명확한 API 규격 공유와 지속적인 통합 테스트의 중요성을 체감했습니다.

### 3. End-to-End 서비스 구현 경험

데이터 분석과 전처리뿐 아니라 OCR 연동, 패키지명 추출, API 통신 테스트까지 경험하며 하나의 기능이 실제 서비스 흐름으로 연결되는 과정을 이해할 수 있었습니다. 이를 통해 개별 기술의 활용을 넘어 전체 시스템의 데이터 흐름을 고려하는 개발 역량의 필요성을 배웠습니다.

---

## 09. Project Structure

```text
Dahum/
│
├── frontend/                 # React 기반 사용자 인터페이스
│   └── src/
│       ├── imports/          # 화면별 디자인 리소스
│       └── pages/            # 주요 서비스 화면
│
├── backend/                  # Spring Boot 메인 서버
│   └── src/main/
│       ├── java/com/dahum/
│       │   ├── config/       # HTTP Client 설정
│       │   ├── controller/   # REST API 컨트롤러
│       │   ├── dto/          # 요청 및 응답 객체
│       │   └── service/      # OCR 및 데이터 처리 로직
│       └── resources/        # 서버 설정
│
├── ai/                       # FastAPI 기반 AI 서버
│   └── app/
│       ├── main.py           # AI API 및 분석 처리
│       └── llm.py            # LLM 안내 메시지 생성
│
├── clova_ocr_api/            # CLOVA OCR 테스트 코드
│
├── datas/                    # 악성 앱 데이터 분석 및 ML
│   ├── data/                 # 원본 및 가공 데이터
│   ├── models/               # 학습된 분류 모델
│   ├── results/              # 분석 및 모델 평가 결과
│   └── src/                  # 전처리, EDA, 모델 학습 코드
│
├── db/                       # MariaDB 스키마 및 마이그레이션
│   ├── init/                 # 초기 DB 생성 SQL
│   └── migration/            # DB 변경 이력
│
├── deploy/                   # Docker 및 배포 설정
│   ├── caddy/                # HTTPS 및 Reverse Proxy 설정
│   └── scripts/              # 자동 배포 및 운영 스크립트
│
├── docs/                     # 프로젝트 설계 및 기술 문서
│   └── images/
│       └── system-architecture.svg
│
├── .github/
│   └── workflows/            # GitHub Actions 자동화
│
├── README.md
└── FILE_STRUCTURE.md
```

---

## 10. Getting Started

### 1. Development Environment

| 구분 | 기술 및 환경 |
|---|---|
| Frontend | Node.js 20, React 19, Vite |
| Backend | Java 21, Spring Boot 3.4.1, Gradle |
| AI Server | Python, FastAPI |
| Database | MariaDB 11.4 |
| Deployment | Docker, Docker Compose, GitHub Actions, GHCR |

### 2. Frontend 실행

```bash
cd frontend

npm ci
npm run dev
```

Vite 개발 서버가 실행되면 터미널에 표시되는 로컬 주소로 접속합니다.

프로덕션 빌드는 다음 명령어로 진행합니다.

```bash
npm run build
```

### 3. Backend 실행

Java 21 환경과 MariaDB가 준비되어 있어야 합니다.

먼저 필요한 환경변수를 설정합니다.

```env
SPRING_DATASOURCE_URL=jdbc:mariadb://localhost:3306/dahum
SPRING_DATASOURCE_USERNAME=dahum_app
SPRING_DATASOURCE_PASSWORD=YOUR_DB_PASSWORD
AI_BASE_URL=http://localhost:8000
PUBLIC_BASE_URL=http://localhost:8080
CLOVA_OCR_URL=YOUR_CLOVA_OCR_ENDPOINT
CLOVA_OCR_SECRET=YOUR_CLOVA_OCR_SECRET
```

Windows 환경에서는 다음 명령어로 실행할 수 있습니다.

```bash
cd backend

gradlew.bat bootRun
```

### 4. Deployment

본 프로젝트는 GitHub Actions와 Docker 기반 자동 배포 구조를 사용합니다.

1. GitHub Repository에 서버 접속 정보를 Secrets로 등록합니다.
2. 운영 서버에 Docker 실행 환경을 준비합니다.
3. `deploy/.env.example`을 참고하여 운영 환경변수를 설정합니다.
4. 실제 환경변수는 서버의 `C:\home\dahum\runtime\.env`에서 관리합니다.
5. `main` 브랜치에 변경 사항을 Push하면 GitHub Actions가 Docker 이미지를 빌드하고 GHCR에 업로드합니다.
6. SSH를 통해 운영 서버에서 이미지를 가져와 Docker Compose로 서비스를 실행합니다.
7. 배포 후 시스템 상태 확인을 통해 서비스 실행 여부를 검증합니다.

### 5. Environment Variables

API Key, 데이터베이스 비밀번호 등 민감한 정보는 환경변수로 관리합니다.

- GitHub Actions: Repository Secrets
- 운영 서버: `runtime/.env`
- 환경변수 예시: `deploy/.env.example`

실제 인증 정보가 포함된 `.env` 파일은 GitHub에 업로드하지 않습니다.
