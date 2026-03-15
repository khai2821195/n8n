# Biz-mecca 납품사례 블로그 자동작성 260310

> **Category:** DCT  
> **Workflow ID:** `ruLfwzGZtsmLSD3k`  
> **노션 메뉴얼:** https://www.notion.so/323c6a06e17e8101b97ac00492a67ddd  

---

## ⚙️ 워크플로우 개요

## 🔄 전체 흐름

```javascript
납품사례 폼 입력 (Form Trigger)
  → 입력값 정리
  → [비활성] 제품 URL 크롤링
  → [비활성] 제품 정보 파싱
  → Gemini 프롬프트 조립
  → Gemini API 호출
  → 블로그 글 추출
  → 노션에 초안 저장
  → 심화 프롬프트 조립
  → Gemini 2차 호출
  → 심화 블로그 추출
  → 노션 심화본문 업데이트
  → 심화본문 블록 추가
  → 완료 메시지
```

## 🔧 수정이 필요할 때

- 폼 입력 항목 → 납품사례 폼 입력 노드
- Gemini 프롬프트 → Gemini 프롬프트 조립 / 심화 프롬프트 조립 노드
- 노션 저장 DB ID → 노션에 초안 저장 노드
- URL 크롤링 활성화 → 비활성 노드 2개 활성화
## 📋 변경 이력

