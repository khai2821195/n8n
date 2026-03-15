# n8n Github Sync (노션 메뉴얼 → README)

> **Category:** 공통  
> **Workflow ID:** `gRhv6ri8Nq5sE1Ol`  
> **노션 메뉴얼:** https://www.notion.so/324c6a06e17e81728fb3ccec9d7bae3a  

---

## ⚙️ 워크플로우 개요

## 🔄 전체 흐름

```javascript
수동 실행
  → 노션 DB 조회 (Workflow ID + Notion Page ID)
  → 목록 준비 (삭제예정 항목 제외)
  → 루프 (1개씩 순차 처리)
      → n8n API → workflow.json 가져오기
      → workflow.json → Github 저장
      → 노션 메뉴얼 조회
      → 마크다운 변환 → README.md
      → README.md → Github 저장
  → 완료
```

## 📁 Github 폴더 구조

```javascript
workflows/
  워크플로우이름/
    workflow.json
    README.md
```

## 🔧 수정이 필요할 때

- Github repo 변경 → JSON SHA 조회, workflow.json 저장, README SHA 조회, README.md 저장 노드의 URL
- 노션 DB 변경 → 노션 DB 조회 노드의 database ID
- 새 워크플로우 추가 → 노션 DB에 항목 추가 후 Notion Page ID 컬럼 입력
## ⚠️ 필요한 환경변수

## 📋 변경 이력

