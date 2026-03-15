# DCT 트렌드 기반 블로그 자동작성 260314

> **Category:** DCT  
> **Workflow ID:** `ovShsLWKGcrOOgnE`  
> **노션 메뉴얼:** https://www.notion.so/323c6a06e17e818ba6d1f28ccacaeed0  

---

## 📋 개요

매주 일요일 오전 9시에 자동 실행되어 네이버 쇼핑 트렌드를 분석하고, Gemini AI가 판촉/홍보/답례품 추천 블로그 글을 작성해 노션에 저장하는 워크플로우.

블로그 컨셉: '26년 X월 X주 AI가 추천하는 판촉/홍보/답례품

---

## 🔄 전체 흐름

```javascript
매주 일요일 9시
  → 현재 시기 정보 (계절/이벤트 판단)
  → 네이버 데이터랩 트렌드 수집
  → 시기 + 트렌드 합치기
  → Gemini 블로그 작성 (TOP 5 품목 포함)
  → 블로그 추출 (JSON 파싱)
  → 노션 페이로드 준비
  → 노션 저장
  → 완료
```

---

## 🧩 노드별 설명

### 1. 매주 일요일 9시 (Schedule Trigger)

- 타입: Schedule Trigger
- 실행 주기: 매주 일요일 오전 9시
- 수동 테스트: n8n UI에서 워크플로우 Active 상태에서 "Test workflow" 버튼 클릭
---

### 2. 현재 시기 정보 (Code)

현재 날짜 기준으로 계절, 특수 이벤트, 네이버 API용 날짜 범위를 계산한다.

출력 데이터:

계절 판단 기준:

- 봄: 3~5월 (졸업/입학, 벚꽃, 신학기)
- 여름: 6~8월 (워터파크, 야외행사, 체육대회)
- 가을: 9~11월 (운동회, 추석, 기업행사)
- 겨울: 12~2월 (연말, 크리스마스, 설)
---

### 3. 네이버 트렌드 수집 (HTTP Request)

네이버 데이터랩 쇼핑인사이트 API로 판촉물/생활용품선물/답례품 카테고리의 최근 7일 검색 트렌드를 수집한다.

API 정보:

- URL: https://openapi.naver.com/v1/datalab/shopping/categories
- Method: POST
- 인증: X-Naver-Client-Id / X-Naver-Client-Secret 헤더
수집 카테고리:

> ⚠️ API 키 교체 필요 시: 노드 Headers에서 X-Naver-Client-Id, X-Naver-Client-Secret 값 직접 수정

---

### 4. 시기+트렌드 합치기 (Code)

현재 시기 정보와 네이버 트렌드 데이터를 하나로 합쳐 다음 노드로 전달한다.

트렌드 데이터에서 카테고리별 최고 검색비율을 추출해 trendSummary 문자열로 생성한다.

---

### 5. Gemini 블로그 작성 (HTTP Request)

Gemini API를 호출해 블로그 포스팅 초안을 작성한다.

API 정보:

- 모델: gemini-3.1-flash-lite-preview
- API 키: 환경변수 $env.GEMINI_API_KEY 사용
- 최대 토큰: 3000
- Temperature: 0.8
블로그 작성 규칙 (프롬프트):

1. 제목: 자동 생성된 blogTitle 그대로 사용
1. 본문: 1500자 이내
1. 구성: 도입부 → TOP 5 추천 품목(각 ## 소제목) → 마무리
1. SEO 키워드 자연스럽게 삽입
1. 각 품목마다 [이미지: 설명] 형식으로 이미지 설명 1개
1. 해시태그 20개
1. JSON 형식으로만 응답: {"title":"...","body":"...","hashtags":"..."}
> ⚠️ Gemini API 키 교체 시: Docker 환경변수 GEMINI_API_KEY 값 수정 (n8n 서버 재시작 필요)

---

### 6. 블로그 추출 (Code)

Gemini 응답에서 JSON을 파싱하고, 노션 API의 2000자 제한에 대비해 본문을 1900자씩 청크로 분할한다.

출력 데이터:

---

### 7. 노션 페이로드 준비 (Code)

노션 API 호출용 JSON 페이로드를 생성한다. bodyChunks 배열을 노션 paragraph 블록 배열로 변환한다.

저장되는 노션 DB 속성:

---

### 8. 노션 저장 (HTTP Request)

준비된 페이로드를 노션 API로 전송해 DB에 새 페이지를 생성한다.

API 정보:

- URL: https://api.notion.com/v1/pages
- Method: POST
- DB ID: 39b2fdcea0a345a48db21f22a6d6b0e0 (제품소개 블로그 초안 DB)
> ⚠️ 노션 인테그레이션 연결 확인: 노션 DB → ... → Connections → DCT 인테그레이션 활성화 필요

---

### 9. 완료 (Set)

워크플로우 완료 메시지를 생성한다.

---

## 🔑 필요한 API 키 및 설정

---

## 🛠️ 트러블슈팅

### 네이버 트렌드 수집 실패

- 증상: 401 인증 오류
- 원인: API 키 만료 또는 오입력
- 해결: 네이버 개발자센터에서 키 재확인 후 노드 헤더 값 수정
### Gemini 블로그 작성 실패

- 증상: 429 또는 빈 응답
- 원인: API 한도 초과 (하루 500회, 분당 15회)
- 해결: 잠시 후 재실행 또는 Google AI Studio에서 사용량 확인
### 노션 저장 실패 - 404

- 증상: "Could not find database"
- 원인: 노션 DB에 DCT 인테그레이션이 연결되지 않음
- 해결: 노션 DB → ... → Connections → DCT 활성화
### 노션 저장 실패 - 400

- 증상: "text.content.length should be ≤ 2000"
- 원인: 블로그 본문이 2000자 초과 (노션 블록 제한)
- 해결: 블로그 추출 노드에서 MAX 값을 더 줄이거나 Gemini 프롬프트에서 자수 제한 강화
---

## 📝 운영 가이드

### 수동 실행 방법

1. n8n UI 접속 (https://n8n.math4u.co.kr)
1. 워크플로우 Active 상태 확인
