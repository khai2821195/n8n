# Class → Student 자동생성

> **Category:** Math4U  
> **Workflow ID:** `PNn3uKuzuOyjgFbu`  
> **노션 메뉴얼:** https://www.notion.so/323c6a06e17e81649c02d5075f8b8945  

---

## ⚙️ 워크플로우 개요

## 🔄 전체 흐름

```javascript
Webhook
  → Code - 입력 파싱
  → Class_Study Get
  → Split Out - Student ID Split
  → Student ID (Notion 조회)
  → Edit Fields
  → Create Page Student_Study
  → Notion - 배정확인
```

## 🔧 수정이 필요할 때

- 입력 파라미터 → Code - 입력 파싱 노드
- Student_Study 생성 필드 → Create Page Student_Study 노드
- 배정확인 로직 → Notion - 배정확인 노드
## 📋 변경 이력

