# My workflow

> **Category:** 공통  
> **Workflow ID:** `qWymLvS3naRN5DmD`  
> **자동 생성:** Gemini AI  

---

# Notion 연동형 AI 챗봇 워크플로우

이 워크플로우는 n8n의 LangChain 기능을 활용하여 사용자의 질문에 답변하고, Notion 데이터베이스(`Student_Study`)의 정보를 조회하여 답변에 활용하는 지능형 AI 에이전트입니다.

## 📋 워크플로우 개요
- **목적**: 사용자와의 대화 내용을 기억하고, 특정 Notion 데이터베이스의 데이터를 기반으로 답변을 제공하는 AI 챗봇 구축
- **핵심 기술**: n8n LangChain, Google Gemini, Notion API

## 🔄 워크플로우 동작 방식
1. **When chat message received**: 사용자의 채팅 메시지를 수신하는 트리거입니다.
2. **AI Agent**: 전체 워크플로우의 두뇌 역할을 하며, 사용자의 질문을 분석하고 필요한 도구(Notion)를 호출하거나 모델(Gemini)을 통해 답변을 생성합니다.
3. **Google Gemini Chat Model**: AI 에이전트가 답변을 생성하는 데 사용하는 언어 모델입니다.
4. **Simple Memory**: 대화의 맥락을 유지하기 위해 최근 10개의 메시지 기록(Context Window)을 저장합니다.
5. **Get a database in Notion**: AI 에이전트가 필요 시 Notion의 `Student_Study` 데이터베이스 정보를 조회할 수 있도록 연결된 도구입니다.

## ⚙️ 필수 설정 및 크레덴셜
이 워크플로우를 정상적으로 실행하려면 다음 항목이 설정되어야 합니다.

1. **Google Gemini API**: `Google Gemini Chat Model` 노드에서 유효한 Google Gemini API Key가 포함된 크레덴셜을 설정해야 합니다.
2. **Notion API**: `Get a database in Notion` 노드에서 Notion API 토큰을 설정하고, 해당 워크플로우가 접근할 수 있도록 Notion 페이지/데이터베이스에 통합(Integration) 권한을 부여해야 합니다.
3. **데이터베이스 ID**: 현재 `Student_Study` 데이터베이스가 연결되어 있습니다. 다른 데이터베이스를 사용하려면 노드 설정에서 `Database ID`를 변경하십시오.

## ⚠️ 주의사항
- **메모리 제한**: `Simple Memory` 노드의 `Context Window Length`가 10으로 설정되어 있습니다. 대화가 길어질 경우 이전 대화 내용을 잊을 수 있으니 필요에 따라 조정하십시오.
- **권한 관리**: Notion API 토큰은 보안을 위해 환경 변수나 n8n의 Credentials 기능을 통해 안전하게 관리하십시오.
- **API 비용**: Google Gemini API 사용량에 따라 비용이 발생할 수 있으므로 Google Cloud 콘솔에서 사용량을 모니터링하시기 바랍니다.