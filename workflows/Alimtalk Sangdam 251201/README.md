# Alimtalk Sangdam 251201

> **Category:** Math4U  
> **Workflow ID:** `S1ObqqNJYt6Weh0b`  
> **노션 메뉴얼:** https://www.notion.so/323c6a06e17e815ca8a0eeba78761e16  

---

## ⚙️ 워크플로우 개요

## 🔄 전체 흐름

```javascript
Schedule Trigger
  → Notion 신규상담신청 확인
  → Alimtalk Setting (HTTP Request)
  → Send a message (Slack)
  → Notion Update
```

## 🔧 수정이 필요할 때

- 상담신청 조회 조건 → Notion 신규상담신청 확인 노드
- 알림톡 메시지 템플릿 → Alimtalk Setting 노드 Body
- Slack 채널 → Send a message 노드
- 노션 업데이트 필드 → Notion Update 노드
## 📋 변경 이력

