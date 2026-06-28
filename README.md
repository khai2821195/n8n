# 🤖 n8n 워크플로우 자동화 시스템

> **운영자**: 김승현 (카이)  
> **서버**: https://n8n.math4u.co.kr (Rocky Linux 9 · Docker · n8n v2.8.3)  
> **최종 업데이트**: 2026-06-29

---

## 📁 워크플로우 목록

### ✅ 운영 중 (Active)

| ID | 워크플로우명 | 노드 수 | 설명 |
|----|------------|--------|------|
| `gRhv6ri8Nq5sE1Ol` | n8n Github Sync (노션 메뉴얼 → README) | 18 | Notion 워크플로우 메뉴얼을 GitHub에 JSON + README로 자동 백업 |
| `d0uNR6Mo92P94Wod` | 🔧 Github Sync - 백업 실행 (서브워크플로우) | 15 | GitHub Sync 메인에서 호출되는 실제 파일 업로드 서브워크플로우 |
| `eOopB5bbEEO9rjrg` | 🔧 WF Status Updater (공통 서브워크플로우) | 8 | 워크플로우 실행 상태를 Notion WF Management DB에 업데이트 |
| `G5k8fgeviVCR8ixe` | Class_Study → Student_Study 수업일정 동기화 | 13 | Class DB의 수업일정을 Student DB에 자동 동기화 |
| `n7M2Z2BhVbGNWhqX` | Class_Study 월별 자동생성 | 23 | 매월 수업 일정 페이지를 Class DB에 자동 생성 |
| `BrZ88oo3KRKccX0g` | 등록일원부 자동생성 - 수업종료 | 18 | 수업 종료 시 등록일원부 DB에 자동 기록 |
| `PNn3uKuzuOyjgFbu` | Class → Student 자동생성 | 14 | Class 페이지 생성 시 Student 페이지 자동 생성 |
| `L6uRu2oqasHrOIQR` | 📚 Math4U 학원 블로그 자동작성 | 27 | 4단계 AI 파이프라인으로 네이버 블로그 초안 자동 생성 후 Notion 저장 |
| `MZK5Sv9zp1D0OMmx` | 대치Math4U - AI팀 회의실 | 7 | AI 가상 임원진 회의 자동화 |
| `S1ObqqNJYt6Weh0b` | Alimtalk Sangdam 251201 | 12 | 상담 신청 시 카카오 알림톡 자동 발송 |
| `ovShsLWKGcrOOgnE` | DCT 트렌드 기반 블로그 자동작성 260314 | 18 | 트렌드 키워드 기반 DCT 블로그 자동 작성 |
| `ruLfwzGZtsmLSD3k` | Biz-mecca 납품사례 블로그 자동작성 260310 | 18 | 납품 사례를 Gemini로 블로그 포스팅으로 변환 |
| `zQOKALD9EOnl3qhd` | Daily Report 260120 | 28 | 매일 운영 현황 리포트 자동 생성 및 발송 |
| `VybPBg3dsRYm2K8l` | Slack → Obsidian Inbox | 2 | Slack 메시지를 Obsidian Inbox에 자동 저장 |
| `eiDJtQcixL9dancS` | Supabase 클라우드 활성화 핑 (5일마다) | 6 | Supabase 무료 플랜 슬립 방지 핑 (5일 주기) |
| `s4dOMX5JYm9rTkuH` | Gemini CLI connect trigger | 1 | Gemini CLI 연결 트리거 |
| `qWymLvS3naRN5DmD` | My workflow | 5 | - |

### 🔧 보류 / 비활성

| ID | 워크플로우명 | 상태 | 비고 |
|----|------------|------|------|
| `FKIIXxr7LFVwSUX0` | 🔧 Alimtalk 발송 (공통 서브워크플로우) | 비활성 | 공통 알림톡 발송 서브워크플로우 |
| `L2oRzJDV57Rf8pcr` | 🔧 슬랙 나에게 보내기 (공통 서브워크플로우) | 비활성 | 공통 Slack DM 발송 서브워크플로우 |
| `fLXAn8mq5xsr5GNE` | 📚 Math4U - 수업 리포트 자동화 (Thinking Flow) | 비활성 | 구버전 수업 리포트 자동화 |
| `57LNfEjxyVpYIVvi` | AEGIS Pro 무료 체험 자동화 | 비활성 | AEGIS 무료 체험 온보딩 자동화 |
| `JNjq85FvYhUYjMZL` | My workflow 2 | 비활성 | - |

---

## 🏗️ 시스템 구조

```
[트리거] Form / Webhook / Schedule / Notion Polling
    ↓
[처리] n8n 워크플로우 (self-hosted)
    ↓
[AI] Gemini API (gemma-4-31b-it / gemma-3-27b-it / gemma-4-26b-a4b-it)
    ↓
[저장] Notion Database
    ↓
[알림] Slack / 카카오 알림톡 (Solapi)
```

---

## 🔑 주요 연동 서비스

| 서비스 | 용도 |
|--------|------|
| **Notion** | 학원 관리 DB, 블로그 초안 저장, 워크플로우 메뉴얼 |
| **GitHub** | 워크플로우 JSON + README 자동 백업 |
| **Gemini API** | 블로그 초안 생성, 품질 평가 |
| **Slack** | 내부 운영 알림, 에러 감지 |
| **Solapi** | 학부모/학생 카카오 알림톡 발송 |
| **Supabase** | 외부 서비스 연동 데이터 저장 |

---

## 📚 Math4U 학원 블로그 자동작성 파이프라인

```
입력 (Form)
    ↓
1차 초안 → gemma-4-31b-it (1200~1500자)
    ↓
2차 보강 → gemma-3-27b-it (1800~2200자)
    ↓
품질 평가 → gemma-4-26b-a4b-it
    ├── 통과 → Notion 저장 (품질통과)
    └── 미달 → 3차 보강 → gemma-4-31b-it (2000~2500자) → Notion 저장
```

---

## ⚙️ 환경 변수

| 변수명 | 용도 |
|--------|------|
| `GEMINI_API_KEY` | Google Gemini / Gemma API 인증 키 |

> 환경변수는 `~/n8n-docker/docker-compose.yml`에서 관리

---

## 🗄️ 주요 Notion DB

| DB명 | ID |
|------|-----|
| n8n Workflow Management | `323c6a06-e17e-8032-82b4-db8024fdb18e` |
| Class DB (대치 Math4U 2026) | `47bc6a06-e17e-83b1-bed2-81851c889428` |
| 등록일원부 | `55aac51e-739c-4f8e-8709-03cb1eb252b6` |
| Math4U 블로그 자동작성 | `925413d91bd64c4abfd7904bf353f99d` |
| DCT 납품사례 블로그 | `5b2cee2d-2300-40c8-8dcc-2d0cf16e1e26` |
| DCT 제품소개 블로그 | `39b2fdce-a0a3-45a4-8db2-1f22a6d6b0e0` |

---

## ⚠️ 운영 시 주의사항

- **n8n Code 노드**: optional chaining(`?.`) 미지원 → 브래킷 표기법 사용
- **Notion relation 필드**: 네이티브 Notion 노드 불안정 → HTTP Request 직접 호출 권장
- **Execute Workflow 노드 (v1.1)**: `workflowId`는 반드시 `__rl` 포맷 사용
- **GitHub Secret Scanning**: Notion 토큰은 JSON 저장 전 regex 마스킹 처리
- **Gemini Rate Limit**: 병렬 호출 시 429 발생 → 노드 간 5초 지연 삽입
