# Daily Report 260120

> **Category:** Math4U  
> **Workflow ID:** `zQOKALD9EOnl3qhd`  
> **노션 메뉴얼:** https://www.notion.so/323c6a06e17e811fa9f8f05949561409  

---

## ⚙️ 워크플로우 개요

## 🔄 전체 흐름

```javascript
Webhook
  → Notion - Student_Study 재조회
  → Notion - Students 조회
  → Notion - Class_Study 조회
  → Notion - 지난수업 조회
  → Code
  → HTTP Request - 수업 리포트
  → If - 납부 알림 조건 체크
    → HTTP Request - 수업료 납부 알림
       → Notion - 발송 완료 체크1
    → Notion - 발송 완료 체크
```

## 🔧 수정이 필요할 때

- 수업 리포튨 메시지 양식 → HTTP Request - 수업 리포트 Body
- 납부 알림 조건 → If - 납부 알림 조건 체크 노드
- 납부 알림 메시지 → HTTP Request - 수업료 납부 알림 Body
## 📋 변경 이력

