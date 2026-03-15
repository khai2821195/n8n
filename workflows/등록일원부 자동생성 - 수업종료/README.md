# 등록일원부 자동생성 - 수업종료

> **Category:** Math4U  
> **Workflow ID:** `BrZ88oo3KRKccX0g`  
> **노션 메뉴얼:** https://www.notion.so/323c6a06e17e81b6b0a5d91342537f5c  

---

## ⚙️ 워크플로우 개요

## 🔄 전체 흐름

```javascript
Notion Trigger (Student_Study 변경 감지)
  → Code - 종료 체크 및 데이터 추출
  → Notion - Class 수업료 조회
  → Code - 수업료 추출
  → Notion - Students 이름 조회
  → Code - 이름 병합
  → HTTP - 납부회차 조회
  → Code - 납부회차 계산
  → HTTP - 등록일원부 레코드 생성
```

## 🔧 수정이 필요할 때

- 수업료 조회 조건 → Notion - Class 수업료 조회 노드
- 납부회차 계산 로직 → Code - 납부회차 계산 노드
- 등록일원부 DB ID → HTTP - 등록일원부 레코드 생성 노드
## 📋 변경 이력

