# My workflow

> **Category:** 공통  
> **Workflow ID:** `qWymLvS3naRN5DmD`  
> **자동 생성:** Gemini AI  

---

# Notion 연동형 AI 챗봇 워크플로우

이 워크플로우는 n8n의 LangChain 기능을 활용하여 사용자의 질문에 답변하고, Notion 데이터베이스(`Student_Study`)의 정보를 조회하여 답변에 활용하는 AI 에이전트 워크플로우입니다.

## 1. 워크플로우 목적
사용자와의 대화 맥락을 기억하고, 특정 Notion 데이터베이스에 저장된 학습 자료나 정보를 실시간으로 검색하여 정확한 답변을 제공하는 지능형 챗봇을 구축합니다.

## 2. 주요 구성 요소 (노드 흐름)

1.  **When chat message received (Trigger)**: 사용자가 보낸 채팅 메시지를 수신하여 워크플로우를 시작합니다.
2.  **AI Agent**: 전체 워크플로우의 두뇌 역할을 합니다. 수신된 메시지를 분석하고, 메모리와 도구를 사용하여 최적의 답변을 생성합니다.
3.  **Google Gemini Chat Model**: AI 에이전트가 답변을 생성하는 데 사용하는 언어 모델(LLM)입니다.
4.  **Simple Memory**: 대화의 맥락을 유지하기 위해 최근 10개의 메시지 기록을 저장합니다.
5.  **Get a database in Notion (Tool)**: AI 에이전트가 필요 시 Notion의 `Student_Study` 데이터베이스를 조회할 수 있도록 연결된 도구입니다.

## 3. 필수 설정 및 크레덴셜

이 워크플로우를 정상적으로 실행하기 위해서는 다음 항목이 설정되어야 합니다.

*   **Google Gemini API**: `Google Gemini Chat Model` 노드에서 유효한 Google Gemini API 키가 포함된 크레덴셜을 설정해야 합니다.
*   **Notion API**: `Get a database in Notion` 노드에서 Notion API 토큰이 설정되어야 하며, 해당 워크플로우가 연결된 Notion 페이지/데이터베이스에 대한 접근 권한이 부여되어야 합니다.
*   **데이터베이스 ID**: 현재 `2d0c6a06-e17e-8118-8ce1-dd2f76406aa1`로 설정된 Notion 데이터베이스 ID가 실제 사용자의 환경과 일치하는지 확인하십시오.

## 4. 주의사항

*   **메모리 제한**: `Simple Memory` 노드의 `contextWindowLength`가 10으로 설정되어 있습니다. 대화가 길어질 경우 이전 대화 내용은 삭제될 수 있습니다.
*   **Notion 권한**: Notion 노드가 데이터베이스를 읽지 못한다면, Notion 앱 설정에서 해당 데이터베이스에 대한 'Integration' 권한이 올바르게 추가되었는지 확인하십시오.
*   **비용**: Google Gemini API 사용량에 따라 비용이 발생할 수 있으니 API 사용량을 주기적으로 확인하시기 바랍니다.

## 5. 사용 방법
1. n8n에 위 JSON 코드를 Import 합니다.
2. 각 노드(Google Gemini, Notion)의 크레덴셜을 본인의 계정으로 업데이트합니다.
3. 워크플로우를 활성화(Active)합니다.
4. n8n 내장 채팅 인터페이스 또는 연동된 채널을 통해 질문을 입력하여 테스트합니다.