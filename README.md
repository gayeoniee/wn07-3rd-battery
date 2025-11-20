# 냉장고 재료 기반 맞춤 레시피 추천 서비스 CookUs



| 홍가연 | 박민상 | 김지영 | 신윤서 | 
|:------:|:------:|:------:|:------:|
| <img width="150" alt="hong" src="https://github.com/user-attachments/assets/9fa60bb2-6686-45f5-8b2f-d95d18834c74" /> | <img width="150" alt="park" src="https://github.com/user-attachments/assets/235c9ffe-99cb-4f7e-9187-3fc6bae16d77" /> | <img width="150" alt="kim" src="https://github.com/user-attachments/assets/cde8666b-9632-44a4-96c6-054f061d8e24" /> | <img width="150" alt="shin" src="https://github.com/user-attachments/assets/aedcdaa7-ef0d-46a4-a3ed-ac6b22aa711e" /> |
| PM · Frontend | 데이터 분석가 · DB | 기획 · Backend | 데이터 엔지니어 · DB |


# 프로젝트 계획서

<details>
  <summary>프로젝트 계획서</summary>

  - [프로젝트 계획서](./docs/CookUs_프로젝트계획서.pdf)

</details>

## 프로젝트 개요

- **서비스 목적**
  - 냉장고에 이미 있는 재료를 활용해 “오늘 뭐 먹지?” 고민을 줄여주는 맞춤 레시피 추천 서비스
- **핵심 컨셉**
  - 재료 기반 추천 + 요리 수행 기록 + 영양 루틴/뱃지로 이어지는 “요리 습관 형성” 지원
- **타깃 사용자**
  - 자취생, 직장인, 냉장고에 재료는 있지만 메뉴 결정이 어려운 1인 가구 사용자

## 주요 기능

1. **냉장고 재료 관리**
   - 보유 재료 등록/수정/삭제

2. **맞춤 레시피 추천**
   - 냉장고 재료를 기반으로 레시피 후보 추천
   - 난이도를 고려한 필터링

3. **식단 캘린더 & 요리 타이머**
   - 선택한 레시피를 캘린더에 기록
   - 요리할 때 사용할 수 있는 타이머 기능
   - 요리 완료 체크 → 기록 기반 통계에 반영

4. **영양제 루틴 관리**
   - 복용 중인 영양제 등록
   - 캘린더에서 영양제 복용 여부 체크
   - “오늘의 영양 루틴 완료” 피드백 제공

5. **대시보드 & 뱃지 (동기부여 기능)**
   - 기간별 요리 횟수, 카테고리별 조리 비율 등 시각화
   - 요리/기록 습관에 따라 뱃지 부여(예: 첫 요리, 연속 기록 등)


## 시스템 아키텍처
<img width="1537" height="1269" alt="CookUs_시스템아키텍처" src="https://github.com/user-attachments/assets/1d1712cb-8251-41d3-a1fc-6187bb357c6c" />


- EC2 분리
  - Backend 전용 EC2 1대, Front + Dashboard용 EC2 1대로 구성

- 컨테이너 기반 배포
  - 서비스별 도커 이미지 → 각자 ECR에 저장 후 EC2에 배포
 
- 깃 액션 사용으로 CI/CD

## 기술 스택
| 영역                         | 사용 기술                                       |
| -------------------------- | ------------------------------------------- |
| Frontend                   | React, TypeScript, Vite, Axios 등            |
| Backend                    | Python, FastAPI, Uvicorn                    |
| DB                         | MariaDB           |
| Infra & DevOps             | AWS EC2, ECR, GitHub Actions, Docker, Nginx |
| Data/Analytics (Dashboard) | Python, Streamlit          |

---------------------------------------

# 요구사항 정의서

<details>
  <summary>요구사항 정의서</summary>

  - [요구사항 정의서](./docs/CookUs_요구사항정의서.pdf)

</details>

----------------------------------------

# WBS

<details>
  <summary>WBS</summary>

  - [WBS](./docs/CookUs_WBS.pdf)

</details>

 
----------------------------------------

# 성능 평가 결과서

<details>
  <summary>성능 평가 결과서</summary>

  - [성능 평가 결과서](./docs/)

</details>

-----------------------------------------

# 최종 보고서

<details>
  <summary>최종발표자료</summary>

  - [최종발표자료](./docs/CookUs_최종발표자료.pdf)

</details>


-----------------------------------------

# 회고

## 1. 잘된 점

## 2. 개선할 점

## 3. 교훈

