# Class_Study 월별 자동생성

> **Category:** Math4U  
> **Workflow ID:** `n7M2Z2BhVbGNWhqX`  
> **노션 메뉴얼:** https://www.notion.so/323c6a06e17e817daa0bc4f4b7c1bc98  

---

## ⚙️ 워크플로우 개요

## 🔄 전체 흐름

```javascript
Schedule - 매월 1일
  → Notion - Class DB 전체 조회
  → Aggregate - 전체 반 목록
  → Code - 수업일정 계산
  → Notion - 기존 Class_Study 조회
  → Code - 중복 체크
  → If - 스킵 체크
    → Notion - Class_Study 생성
    → Code - Students 분리
    → Notion - Student_Study 생성
    → Notion - 배정확인
  → Wait - 5초 → 다음수업 연결
```

## 🔧 수정이 필요할 때

- 수업일정 계산 → Code - 수업일정 계산 노드
- 중복 체크 기준 → Code - 중복 체크 노드
- Student_Study 생성 필드 → Notion - Student_Study 생성 노드
## 📋 변경 이력

