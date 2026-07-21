## 초기 Organization README

# 밥풀 BobFull

혼자 여행하는 사용자가 합석 가능한 좌석을 예약하고  
다른 사용자와 함께 식사할 수 있도록 연결하는 합석형 좌석 예약 플랫폼입니다.

## 프로젝트 정보

- 프로젝트명: 밥풀(BobFull)
- 팀명: 밥조
- 프로젝트 기간: 2026.07.21 ~ 2026.08.24
- 초기 타깃: 제주 평일 저녁, 혼자 여행하는 사용자

## 핵심 문제

- 혼자 방문하기 어려운 식당의 이용 제한
- 2인 이상 주문 조건으로 인한 1인 여행자의 불편
- 식당의 빈 좌석 및 노쇼 관리 문제
- 함께 식사할 사용자를 찾기 어려운 문제

## 핵심 흐름

```text
사장님
→ 식당·예약 시간·좌석 등록

사용자 A
→ 합석 예약 생성
→ 예약금 결제
→ 참여자 모집

사용자 B
→ 모집 중인 예약 참여
→ 예약금 결제

결제 완료 인원 2명 이상
→ 예약 확정
````

## Repositories

* `bobfull-backend` — Spring Boot 백엔드
* `bobfull-frontend` — 사용자 및 사장님 프론트엔드
* `.github` - profile 관리

## Team

| 이름  | 담당 영역                      |
| --- | -------------------------- |
| 김현승 | 예약금 결제·환불·정산, AI           |
| 김홍기 | 합석 예약·예약 시간·좌석·검색, 배포·모니터링 |
| 정용태 | 회원·인증·사장님·식당·관리자, 조회 성능    |
| 배지현 | 예약·좌석 재고·동시성, 프론트엔드        |

## Development Principles

* 이해하지 못한 코드는 병합하지 않습니다.
* 테스트하지 않은 기능은 완료로 판단하지 않습니다.
* 기술은 실제 문제와 검증 근거를 기준으로 도입합니다.
* 핵심 예약 흐름 완성을 부가 기술보다 우선합니다.

```

따라서 지금은 **`.github` 저장소를 추가로 만들고 `profile/README.md`를 넣는 게 맞다.** 백엔드와 프론트엔드 README는 그다음 각 저장소 소개용으로 별도로 작성하면 된다.
```

[1]: https://docs.github.com/en/organizations/collaborating-with-groups-in-organizations/customizing-your-organizations-profile?utm_source=chatgpt.com "Customizing your organization's profile - GitHub Docs"
