# My workflow

> **Category:** 공통  
> **Workflow ID:** `qWymLvS3naRN5DmD`  
> **자동 생성:** Gemini AI  

---

# Notion 연동형 AI 챗봇 워크플로우

이 워크플로우는 Google Gemini AI 모델을 기반으로 하며, Notion 데이터베이스와 연동하여 사용자의 질문에 답변하는 지능형 챗봇 시스템입니다.

## 📋 워크플로우 개요
- **목적**: 사용자의 채팅 메시지를 입력받아 AI가 문맥을 기억하고, Notion 데이터베이스(`Student_Study`)의 정보를 조회하여 답변을 제공합니다.
- **주요 기술**: n8n LangChain, Google Gemini, Notion API

## ⚙️ 워크플로우 구성 (노드 흐름)

1. **When chat message received (트리거)**: 사용자의 채팅 메시지를 수신하는 웹훅 엔드포인트입니다.
2. **AI Agent**: 전체 워크플로우의 두뇌 역할을 합니다. 언어 모델, 메모리, 도구(Notion)를 통합하여 답변을 생성합니다.
3. **Google Gemini Chat Model**: AI Agent가 사용할 언어 모델입니다.
4. **Simple Memory**: 대화의 문맥을 유지하기 위한 메모리 노드입니다. 최근 10개의 대화 메시지(Context Window)를 기억하여 자연스러운 대화를 가능하게 합니다.
5. **Get a database in Notion (도구)**: AI Agent가 필요 시 Notion의 `Student_Study` 데이터베이스 정보를 조회할 수 있도록 연결된 도구 노드입니다.

## 🔑 필수 설정 및 크레덴셜

이 워크플로우를 정상적으로 실행하려면 다음 설정이 필요합니다:

- **Google Gemini API**: `Google Gemini(PaLM) Api account` 크레덴셜이 설정되어 있어야 합니다.
- **Notion API**: Notion 데이터베이스에 접근하기 위한 API 토큰이 필요하며, 해당 데이터베이스(`2d0c6a06-e17e-8118-8ce1-dd2f76406aa1`)에 대한 접근 권한이 부여되어야 합니다.

## ⚠️ 주의사항 및 참고사항

- **메모리 설정**: `Simple Memory` 노드의 `Context Window Length`가 10으로 설정되어 있습니다. 대화가 길어질 경우 이전 대화 내용은 삭제될 수 있습니다.
- **데이터베이스 권한**: Notion 노드에서 데이터베이스를 찾을 수 없는 경우, n8n 연동 앱이 해당 Notion 페이지에 공유(Share)되어 있는지 확인하십시오.
- **환경 변수**: n8n 인스턴스에서 외부 통신이 가능한 환경인지 확인하시기 바랍니다.

---
*본 워크플로우는 n8n의 LangChain 기능을 활용하여 구축되었습니다.*