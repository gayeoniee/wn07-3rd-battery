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


Frontend                   
![React](https://img.shields.io/badge/React-61DAFB?style=flat-square&logo=react&logoColor=000000)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=FFFFFF)
![Vite](https://img.shields.io/badge/Vite-646CFF?style=flat-square&logo=vite&logoColor=FFFFFF)

Backend                   
![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=FFFFFF)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=FFFFFF)
![Uvicorn](https://img.shields.io/badge/Uvicorn-4B8BBE?style=flat-squaree)

DB                         
![MariaDB](https://img.shields.io/badge/MariaDB-003545?style=flat-square&logo=mariadb&logoColor=FFFFFF)

Infra & DevOps             
![AWS EC2](https://img.shields.io/badge/EC2-FF9900?style=flat-square&logo=amazonec2&logoColor=FFFFFF)
![AWS ECR](https://img.shields.io/badge/ECR-FF9900?style=flat-square&logo=amazonaws&logoColor=FFFFFF)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=FFFFFF)
![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?style=flat-square&logo=githubactions&logoColor=FFFFFF)
![Nginx](https://img.shields.io/badge/Nginx-009639?style=flat-square&logo=nginx&logoColor=FFFFFF)

Data/Analytics (Dashboard)   

![Streamlit](https://img.shields.io/badge/Streamlit-FF4B4B?style=flat-square&logo=streamlit&logoColor=FFFFFF)


---------------------------------------

# 요구사항 정의서

<details>
  <summary>요구사항 정의서</summary>

  - [요구사항 정의서](./docs/CookUs_요구사항정의서.pdf)

</details>

### 기능적 요구사항

| 번호 | 기능 구분           | 상세 요구사항 |
|------|---------------------|---------------|
| 1    | 회원 관리 기능      | - 사용자 이메일/비밀번호와 성별을 입력해 가입한다.<br>- 사용자는 자신의 회원 정보를 수정할 수 있다.<br>- 사용자는 언제든 회원 탈퇴를 요청할 수 있다. |
| 2    | 재료 관리 기능      | - 사용자의 냉장고 재료 목록을 보여준다.<br>- 재료 목록 화면에서 추가 버튼으로 재료를 등록하는 흐름을 제공한다.<br>- 재료 목록에서 재료 삭제가 가능해야 한다.<br>- 재료 검색 기능을 제공하고, 검색 결과에서 선택하여 추가할 수 있다.<br>- 검색에 없을 경우 재료를 수동 입력하여 추가할 수 있다. |
| 3    | 레시피 추천 기능    | - 사용자의 보유 재료 + 난이도를 기반으로 레시피 후보군 매칭 자동 추천.<br>- LLM 기반 조리 가이드 정제(불필요한 설명 제거, 조리 단계 요약, 부족 재료 대체재 제안).<br>- 사용자 입력 외의 기본 재료(양념류 등)는 필요 시 자동 포함하여 레시피를 생성한다.<br>- 추천된 레시피 상세 3개씩 조회한다. |
| 4    | 난이도 선택 기능    | - 사용자 선택에 따라 “상/하” 레벨 레시피를 제공한다.<br>- 각 난이도별 예상 조리시간 및 필요한 재료를 표시한다. |
| 5    | 캘린더 연동 기능    | - 추천받은 레시피 중 진행 완료한 레시피를 캘린더에 등록한다.<br>- 요리 실천 여부를 캘린더에서 선택/체크할 수 있다. |
| 6    | 조리 편의 기능      | - 조리 타이머를 제공한다.<br>- 추천 레시피와 연동된 유튜브 Shorts(조리 영상)를 제공한다. |
| 7    | 사용자 대시보드 기능 | - 사용자가 실제 요리한 레시피 데이터를 기반으로 목표 달성률을 시각화한다.<br>- 사용 재료를 카테고리화하여 시각적으로 제공한다. |
| 8    | 대회 기능           | - 대회 목록 및 대회별 게시물 목록을 조회한다.<br>- 대회별 참가 게시물을 작성/수정/삭제할 수 있다.<br>- 게시물별 좋아요 선택 기능을 제공한다. |
| 9    | 영양제 추천 기능    | - 영양제 등록/수정/삭제 기능을 제공한다.<br>- 하루 섭취 여부를 기록할 수 있다.<br>- 사용자의 선호 및 섭취 이력을 기반으로 영양제를 추천한다. |


### 비기능적 요구사항

| 구분   | 항목       | 상세 요구사항 |
|--------|-----------|---------------|
| 성능   | 응답 시간 | - 추천 결과는 사용자의 요청 후 평균 3초 이내에 표시되어야 한다. |
| 보안   | 데이터 보안 | - 사용자 개인정보 및 레시피 데이터는 암호화하여 저장한다.<br>- API Key는 `.env` 파일로 안전하게 관리한다. |
| 확장성 | 외부 연동  | - 쇼핑 API, 영수증 OCR, 외부 레시피 데이터 연동이 가능하도록 확장성을 확보한다. |


----------------------------------------

# WBS

<details>
  <summary>WBS</summary>

  - [WBS](./docs/CookUs_WBS.pdf)

</details>

 
----------------------------------------

# 성능 평가 결과 보고서

<details>
  <summary>성능 평가 결과 보고서</summary>

  - [성능 평가 결과 보고서](./docs/CookUs_성능평가결과보고서.pdf)

</details>

-----------------------------------------

# 최종 보고서

<details>
  <summary>최종발표자료</summary>

  - [최종발표자료](./docs/CookUs_최종발표자료.pdf)

</details>



