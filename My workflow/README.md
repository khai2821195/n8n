# My workflow

> **Category:** 공통  
> **Workflow ID:** `qWymLvS3naRN5DmD`  
> **자동 생성:** Gemini AI  

---

n8n Workflow Expert.
Analyze a provided n8n workflow JSON and write a GitHub `README.md` in Korean.

        *   Name: My workflow
        *   ID: qWymLvS3naRN5DmD
        *   Category: Common
        *   Nodes:
            *   `When chat message received` (Chat Trigger): The entry point.
            *   `AI Agent` (LangChain Agent): The brain coordinating the process.
            *   `Google Gemini Chat Model` (LM): The LLM powering the agent.
            *   `Simple Memory` (Window Buffer Memory): Remembers the last 10 interactions.
            *   `Get a database in Notion` (Notion Tool): Allows the agent to access a specific Notion database ("Student_Study").

        1.  Clear purpose and operation logic.
        2.  Step-by-step node flow (Trigger $\rightarrow$ Process $\rightarrow$ Output).
        3.  Required environment variables/credentials.
        4.  Precautions/Special notes.
        5.  Markdown format.
        6.  Output *only* the README content.

    *   *Purpose:* This is a chatbot that uses Google Gemini and has access to a Notion database. It's designed to answer user queries by potentially retrieving information from a Notion database called "Student_Study".
    *   *Flow:*
        1.  User sends a message via the Chat Trigger.
        2.  The AI Agent receives the message.
        3.  The AI Agent uses the Gemini model for reasoning.
        4.  The AI Agent uses the Window Buffer Memory to maintain context.
        5.  If needed, the AI Agent uses the Notion Tool to fetch data from the "Student_Study" database.
        6.  The AI Agent generates a response and sends it back to the user.

    *   *Title:* Notion 데이터 기반 AI 챗봇 (My workflow)
    *   *Description:* Google Gemini와 Notion을 연동하여 특정 데이터베이스의 정보를 조회하고 답변하는 AI 에이전트 워크플로우입니다.
    *   *Workflow Flow:*
        1.  **트리거**: `When chat message received` - 사용자의 채팅 메시지 수신.
        2.  **핵심 처리**: `AI Agent` - LangChain 기반 에이전트가 요청 분석 및 도구 선택.
        3.  **지원 구성 요소**:
            *   `Google Gemini Chat Model`: 추론 및 텍스트 생성 담당.
            *   `Simple Memory`: 최근 10개의 대화 맥락 유지.
            *   `Get a database in Notion`: 'Student_Study' 데이터베이스에서 정보 조회.
    *   *Credentials:*
        *   Google Gemini API Key.
        *   Notion API Key (Integration Token) & Database Access.
    *   *Notes:* Notion 데이터베이스 ID 설정 필요, 메모리 윈도우 크기(10) 확인.

    *   Ensure professional tone.
    *   Use clear headings.
    *   Use lists for readability.