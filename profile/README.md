# 🍚 밥풀 BobFull

> **혼자여도 함께 먹을 수 있도록**  
> 개인 단위로 좌석을 예약하고, 다른 사용자와 함께 식사할 수 있도록 연결하는 **합석형 좌석 예약 플랫폼**입니다.

[📚 Technical Docs](https://github.com/bobfull-project/bobfull-docs) · [🔬 Flow Lab](https://bobfull-project.github.io/bobfull-docs/flow-lab/v3/operations-flow-lab/) · [⚙️ Backend](https://github.com/bobfull-project/bobfull-backend) · [🖥️ Frontend](https://github.com/bobfull-project/bobfull-frontend)

---

## 🍽️ 서비스 소개

혼자 여행하거나 식사할 때 겪는 `2인 이상 주문`, `1인 예약 제한`, 함께 식사할 사람을 직접 구해야 하는 불편을 해결합니다.

사용자는 원하는 식당과 회차를 선택해 **개인 단위로 좌석을 예약**하고, 최소 성사 인원이 모이면 합석이 성사되어 채팅 후 함께 식사할 수 있습니다.

**식당 탐색 → 회차·인원 선택 → 예약·결제 → 최소 인원 충족 → 합석 성사 → 채팅·식사**

---

## ✨ 핵심 기능

- 🍴 식당·합석 회차 탐색
- 👤 개인 단위 좌석 예약·잔여 좌석 관리
- 💳 PortOne 예약금 결제·취소·환불
- 🔒 동시 예약 상황의 좌석 정합성 보장
- 💬 다중 App 환경 실시간 채팅
- 🛡️ AI 채팅 위험 메시지 검수
- 🍽️ AI 식당 피드백 분석·익명 집계
- 📊 성능·장애·운영 검증 기반 시스템 고도화

---

## 🏗️ Engineering Highlights

**🔒 예약·결제 정합성**  
비관적 락과 상태 재검증으로 동시 예약 시 좌석 초과와 중복 상태 전이를 방지합니다.

**📨 비동기 신뢰성**  
ChatRoom·Email은 **Transactional Outbox**, AI 후속 처리는 **Outbox + Kafka**로 처리 경계를 분리했습니다.

**🤖 AI 채팅 검수 · 식당 피드백 분석**  
명확한 위험 메시지는 규칙으로 빠르게 걸러내고, 판단이 필요한 메시지만 LLM으로 분석해 결과를 저장합니다.  
또한 채팅 속 음식·서비스·가격·청결 관련 의견을 개인 식별정보 없이 구조화·집계해 사장님이 확인할 수 있는 피드백 인사이트로 만들었습니다.

**📊 측정 기반 의사결정**  
Redis Cache·Query/Index·Kafka·App 확장 여부를 k6, 통합 테스트, 실제 AWS 환경의 측정 결과로 판단했습니다.

---

## 🛠️ Tech Stack

| 영역 | 기술 |
|---|---|
| Backend | Java · Spring Boot · Spring Security · Spring Data JPA · Spring AI |
| Data | MySQL · Redis / ElastiCache |
| Messaging | Apache Kafka |
| Infra / CI·CD | AWS EC2 · ALB · RDS · S3 · Lambda · ECR · SSM · Docker · GitHub Actions |
| Monitoring | Prometheus · Grafana |
| Test | JUnit · Testcontainers · k6 |

---

## 🔎 더 알아보기

| 구분 | 내용 |
|---|---|
| [📚 Technical Docs](https://github.com/bobfull-project/bobfull-docs) | Architecture · API · ERD · ADR · Troubleshooting |
| [🔬 Flow Lab](https://bobfull-project.github.io/bobfull-docs/flow-lab/v3/operations-flow-lab/) | 주요 백엔드 시스템 흐름 인터랙티브 확인 |
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

**Project · 2026.07.21 ~ 2026.08.24**
