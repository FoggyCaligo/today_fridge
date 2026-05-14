<h1 align="center">오늘의 냉장고</h1>
<div align="center">

<h3>개인화 추천과 AI 기술을 결합한 스마트 레시피 플랫폼</h3>

<a href="http://todayfridge.com">todayfridge.com</a>
<a href="http://todayfridge.com">https://today-fridge-frontend-deploy.vercel.app/</a>


<img src="img/image.png" alt="Today Fridge Preview" height="250" width="auto" />


</div>

<p align="center">
  <img src="https://img.shields.io/badge/Next.js-v16.2-111111?style=for-the-badge&logo=nextdotjs&logoColor=white" />
  <img src="https://img.shields.io/badge/React-v18-20232A?style=for-the-badge&logo=react&logoColor=61DAFB" />
  <img src="https://img.shields.io/badge/Tailwind_CSS-v3-06B6D4?style=for-the-badge&logo=tailwindcss&logoColor=white" />
  <img src="https://img.shields.io/badge/Python-v3%2E10-3776AB?style=for-the-badge&logo=python&logoColor=white"/>
  <img src="https://img.shields.io/badge/JDK-v17-white?style=for-the-badge&logo=openjdk&labelColor=Grey&color=ED8B00&logoColor=red"/>
</p>

## 주요 기능

- **이커머스 연동:** 레시피에 필요한 부족한 식재료를 쿠팡 등 외부 쇼핑몰에서 즉시 검색하고 구매할 수 있습니다.
- **스마트 레시피 추천:** 냉장고 내 남은 식재료와 사용자의 영양 상태를 분석하여 맞춤형 레시피를 제안합니다.
- **영양 기반 식단 기록:** 매일의 식사를 기록하고 BMI, 키, 몸무게 등 신체 정보를 기반으로 한 영양 리포트를 생성합니다.
- **최신 UI/UX 구현:** TailwindCSS v3와 Ant Design을 활용하여 세련되고 반응성이 뛰어난 사용자 인터페이스를 제공합니다.
- **품질 보증:** Vitest와 React Testing Library를 활용한 단위 및 통합 테스트를 통해 코드의 안정성을 확보했습니다.

## 사용 방법

[스크린 샷 또는 영상]

## 로컬 설치 방법

1. Repository 을 git clone을 통하여 다운로드 받습니다.

```
    # Frontend
    git clone -b dev https://github.com/FoggyCaligo/project_final_frontend.git

    # Backend 1
    git clone -b dev https://github.com/FoggyCaligo/project_final_backend_1.git

    # Backend 2
    git clone -b dev https://github.com/FoggyCaligo/project_final_backend_2.git
```

2. .env 파일을 다음과 같이 작성합니다.

```
    # Front End
    NEXT_PUBLIC_API_URL=http://localhost:8080/api
    NEXT_PUBLIC_BACKEND_ORIGIN=http://localhost:8080
    
    # Back End 1
    SPRING_DATASOURCE_URL=
    SPRING_DATASOURCE_USERNAME= 
    SPRING_DATASOURCE_PASSWORD=
    
    SPRING_REDIS_HOST=
    SPRING_REDIS_PORT=
    MAIL_USERNAME=
    MAIL_PASSWORD=
    
    MAIL_HOST=smtp.gmail.com
    MAIL_PORT=587
    MAIL_SMTP_AUTH=true
    MAIL_SMTP_STARTTLS_ENABLE=true
    MAIL_SMTP_STARTTLS_REQUIRED=true
    MAIL_FROM=
    
    SERVER_TAILSCALE_IP=
    NEXT_PUBLIC_API_BASE_URL=
    
    KAKAO_REDIRECT_URI=
    FRONTEND_BASE_URL=

    # Back End 2
    DATABASE_URL=
    GEMINI_API_KEY=
    INTERNAL_API_TOKEN=change-me
```

3. 실행

```
    # Frontend
    준비:npm install
    실행:npm run dev

    # Backend 1
    실행: src\main\java\com\today\fridge\ TodayFridgeApplication.java 실행

    # Backend 2
    준비: pip install -r requirements.txt
    실행: uvicorn app.main:app --reload
```

4. “[Localhost:3000](http://Localhost:3000)”으로 접속

## 역할 분담

| 성함 | 담당 기능 |
| --- | --- |
| 신재용 [PM] | OCR 텍스트 인식, 레시피 크롤링 및 수집, & 1차 식재료 이미지 인식 |
| 한수정 | 추천 시스템 설계, 개인화 추천, 및 챗봇 |
| 김정호 | 레시피 상세 페이지, 영양 분석 리포트, 식단 관리 기능 |
| 정경안 | 커뮤니티  기능, 좋아요 및 신고 기능 |
| 장민재 | 식재료 CRUD, 2차 식재료 이미지 인식, 및 유통기한/카테고리 처리 |
| 임동주 | 마이페이지, 알림기능, 홈화면 대시보드 |
| 민예린 | 쇼핑 링크 연동, JWT 로그인 및 인증, 및 소셜 로그인 기능 |

## 사용한 AI 모델
<div align="center">
  <img src="img\image_02.png" alt="YOLO 식재료 분류 파이프라인" width="300" />
</div>

| 구분 | 모델 / 라이브러리 | 역할 |
|------|-------------------|------|
| 이미지 분류 (1차 라우팅) | YOLOv8 Classification (Ultralytics) | 업로드 이미지를 raw_ingredient/packaged_food/기타 등으로 1차 분기 |
| 이미지 분류 (2차 세부 분류) | YOLOv8 Classification (Ultralytics) | 원물(raw_ingredient) 경로에서 식재료 클래스 Top-K 후보 및 신뢰도 산출 |
| 라벨 → 서비스명 매핑 | DB 기반 메타데이터 | 모델 출력 ing_XXXXX를 한글 표시명·정규화명으로 변환해 UI에 표시 |
| 포장 식품 OCR | PaddleOCR + PaddlePaddle | 포장 식품 경로에서 라벨·상품명 텍스트 인식 후 후보 생성 |
| API 오케스트레이션 | FastAPI | Spring이 호출하는 내부 비전 API에서 위 모듈을 순서대로 호출·응답 정규화 |

## YOLO 데이터 분석 및 학습 결과
- YOLOv8 Classification 기반 식재료 이미지 분류 모델 학습 수행
- Flip, Mosaic, RandAugment 등 데이터 증강 기법을 적용하여 일반화 성능 향상
- Early Stopping(patience=8) 기반 학습 최적화 수행
- 최신 모델 기준:
 - Top-1 Accuracy: 71.65%
 - Top-5 Accuracy: 93.95%