# 🍚 밥풀 BobFull

> **혼자여도 함께 먹을 수 있도록**  
> 개인 단위로 좌석을 예약하고, 다른 사용자와 함께 식사할 수 있도록 연결하는 **합석형 좌석 예약 플랫폼**입니다.

[📚 Technical Docs](https://github.com/bobfull-project/bobfull-docs) · [🔬 Flow Lab](https://bobfull-project.github.io/bobfull-docs/flow-lab/v3/operations-flow-lab/) · [⚙️ Backend](https://github.com/bobfull-project/bobfull-backend) · [🖥️ Frontend](https://github.com/bobfull-project/bobfull-frontend)

---

## 🍽️ 서비스 소개

혼자 여행하거나 식사하는 사용자는 `2인 이상 주문`, `1인 예약 제한`, `혼밥의 부담` 때문에 원하는 식당을 이용하기 어려울 수 있습니다.

**밥풀(BobFull)**은 사용자가 원하는 식당과 회차를 선택해 **개인 단위로 좌석을 예약**하고, 최소 성사 인원이 모이면 함께 식사할 수 있도록 연결합니다.

```text
식당 탐색
   ↓
회차 · 인원 선택
   ↓
예약 · 결제
   ↓
최소 인원 충족
   ↓
합석 성사
   ↓
채팅 · 함께 식사
```

---

## ✨ 핵심 기능

- 🍴 식당 및 합석 가능한 회차 탐색
- 👤 개인 단위 좌석 예약 및 잔여 좌석 관리
- 💳 PortOne 기반 예약금 결제 · 취소 · 환불
- 🔒 동시 예약 상황에서의 좌석 정합성 보장
- 💬 합석 성사 후 실시간 채팅
- 🤖 AI 기반 채팅 Moderation
- 🔔 핵심 거래 이후 후속 작업 비동기 처리
- 📊 성능 테스트 · 모니터링 · 장애 대응 구조

---

## 🏗️ 기술적 특징

### 안정적인 예약과 결제

동시 예약 환경에서 **좌석 초과 판매를 방지**하고, 결제 · 예약 · 취소 · 환불의 상태 전이를 명확하게 관리합니다.

### 신뢰성 있는 비동기 처리

핵심 거래 이후의 후속 작업은 **Transactional Outbox**로 작업 의도를 보존합니다.  
ChatRoom 생성과 이메일 발송은 Outbox 기반으로 처리하고, AI Moderation처럼 적체 · 재시도 · 실패 격리 · 독립 Consumer 경계가 필요한 작업에는 **Kafka**를 추가 적용했습니다.

### AI Moderation

단순 LLM 호출에 의존하지 않고 명확한 규칙과 AI 분석 경계를 분리해 **안전성 · 비용 · 응답 지연**을 함께 고려했습니다.

```text
명확한 위험 메시지
→ Rule Fast Path

판단이 필요한 메시지
→ LLM Moderation

→ 결과 검증 및 저장
```

### 측정 기반 성능·운영 판단

Redis Cache, Query/Index, Kafka Consumer, App 확장 여부 등을 단순 도입하지 않고 **k6 · 통합 테스트 · 실제 AWS 환경의 측정 결과를 기준으로 채택·유지·미도입을 판단**했습니다.

---

## 🛠️ Tech Stack

**Backend**  
Java · Spring Boot · Spring Security · Spring Data JPA · Spring AI

**Database / Cache**  
MySQL · Redis / ElastiCache

**Messaging**  
Apache Kafka

**Infrastructure / CI·CD**  
AWS EC2 · ALB · RDS · S3 · Lambda · ECR · SSM · Docker · GitHub Actions

**Monitoring**  
Prometheus · Grafana

**Test**  
JUnit · Testcontainers · k6

---

## 🔎 더 알아보기

| 구분 | 내용 |
|---|---|
| [📚 Technical Docs](https://github.com/bobfull-project/bobfull-docs) | System Architecture · API · ERD · ADR · Troubleshooting |
| [🔬 Flow Lab](https://bobfull-project.github.io/bobfull-docs/flow-lab/v3/operations-flow-lab/) | 주요 백엔드 시스템 흐름을 인터랙티브하게 확인 |
| [⚙️ Backend](https://github.com/bobfull-project/bobfull-backend) | Spring Boot 구현 · 정책 · Evidence · 상세 기술 문서 |
| [🖥️ Frontend](https://github.com/bobfull-project/bobfull-frontend) | React 클라이언트 구현 · 실행 · 배포 |

---

## 👥 Team 밥조

| 이름 | 주요 담당 |
|---|---|
| **김현승** | 결제 · 환불 · 정산 · AI · 시스템 신뢰성 |
| **배지현** | 예약 · 좌석 동시성 · Frontend |
| **정용태** | 회원 · 인증 · 식당 · 관리자 · 조회 성능 |
| **김홍기** | 합석 · 회차 · 검색 · 배포 · 모니터링 |

---

## 📅 Project

**2026.07.21 ~ 2026.08.24**
