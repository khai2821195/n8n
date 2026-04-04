# My workflow

> **Category:** 공통  
> **Workflow ID:** `qWymLvS3naRN5DmD`  
> **자동 생성:** Gemini AI  

---

# Notion 연동형 AI 챗봇 워크플로우

이 워크플로우는 n8n의 LangChain 기능을 활용하여 사용자의 질문에 답변하고, Notion 데이터베이스 정보를 조회하여 학습 데이터를 기반으로 응답하는 AI 에이전트입니다.

## 📋 워크플로우 개요
- **목적**: Notion 데이터베이스(`Student_Study`)와 연동된 AI 챗봇을 통해 학습 관련 질문에 답변을 제공합니다.
- **핵심 기술**: n8n LangChain, Google Gemini, Notion API

## 🔄 워크플로우 흐름
1. **When chat message received (Trigger)**: 사용자의 채팅 메시지를 수신합니다.
2. **AI Agent**: 전체 워크플로우의 두뇌 역할을 하며, 메모리와 도구를 사용하여 답변을 생성합니다.
3. **Google Gemini Chat Model**: AI 에이전트가 사용할 언어 모델로, Google Gemini를 통해 자연스러운 대화를 생성합니다.
4. **Simple Memory**: 대화의 맥락을 유지하기 위해 최근 10개의 메시지 기록을 저장합니다.
5. **Get a database in Notion (Tool)**: AI 에이전트가 필요 시 Notion 데이터베이스(`Student_Study`)의 정보를 조회하여 답변에 활용합니다.

## ⚙️ 필수 설정 및 환경 변수
이 워크플로우를 정상적으로 실행하려면 다음 설정이 필요합니다.

1. **Google Gemini API**: `Google Gemini(PaLM) Api account` 크레덴셜을 생성하여 API 키를 등록해야 합니다.
2. **Notion API**:
   - Notion 통합(Integration) 토큰이 필요합니다.
   - 해당 워크플로우에서 사용하는 데이터베이스(`Student_Study`)에 연동된 앱(Integration)의 접근 권한을 허용해야 합니다.
3. **Notion Database ID**: 현재 설정된 `2d0c6a06-e17e-8118-8ce1-dd2f76406aa1` 데이터베이스 ID가 본인의 환경과 일치하는지 확인하십시오.

## ⚠️ 주의사항
- **메모리 제한**: `Simple Memory` 노드의 `Context Window Length`가 10으로 설정되어 있습니다. 대화가 길어질 경우 이전 대화 내용을 잊을 수 있으니 필요에 따라 조정하십시오.
- **API 비용**: Google Gemini API 사용량에 따른 비용이 발생할 수 있으므로, 사용량 제한을 확인하시기 바랍니다.
- **권한**: Notion 데이터베이스에 대한 읽기 권한이 올바르게 설정되어 있는지 확인하십시오. 권한이 없을 경우 AI가 데이터를 조회하지 못합니다.