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
            *   `When chat message received` (Chat Trigger): Entry point.
            *   `AI Agent` (LangChain Agent): The brain.
            *   `Google Gemini Chat Model` (LLM): The language model powering the agent.
            *   `Simple Memory` (Window Buffer Memory): Remembers the last 10 messages.
            *   `Get a database in Notion` (Notion Tool): Allows the agent to access a specific Notion database ("Student_Study").

        *   Trigger $\rightarrow$ AI Agent.
        *   AI Agent $\leftarrow$ Google Gemini (Model).
        *   AI Agent $\leftarrow$ Simple Memory (Memory).
        *   AI Agent $\leftarrow$ Notion Tool (Tool).

        1.  Purpose and operation.
        2.  Node flow (Trigger $\rightarrow$ Process $\rightarrow$ Output).
        3.  Environment variables/Credentials.
        4.  Notes/Special considerations.
        5.  Markdown format.
        6.  Output *only* the README content.

    *   *Title:* Notion-connected AI Chatbot (based on "My workflow" and the Notion tool). Let's call it "Notion 기반 AI 학습 도우미" (Notion-based AI Study Assistant) since the database is named "Student_Study".
    *   *Purpose:* A chatbot that uses Google Gemini to answer questions and can retrieve/interact with a specific Notion database for student study data.
    *   *Flow:*
        1.  User sends a message via Chat Trigger.
        2.  AI Agent receives the input.
        3.  AI Agent uses Gemini for reasoning.
        4.  AI Agent uses Memory to maintain context.
        5.  AI Agent uses the Notion Tool to fetch data from the "Student_Study" database if needed.
        6.  AI Agent returns the final response to the user.
    *   *Credentials:*
        *   Google Gemini API Key.
        *   Notion API Key (Integration Token).

    *   *Header:* # Notion 기반 AI 학습 도우미 워크플로우
    *   *Description:* 이 워크플로우는 Google Gemini LLM과 Notion 데이터베이스를 결합하여, 사용자의 질문에 답변하고 Notion에 저장된 학습 데이터를 조회할 수 있는 AI 에이전트를 구현합니다.
    *   *Workflow Diagram/Flow:*
        1.  **Chat Trigger**: 채팅 메시지 수신.
        2.  **AI Agent**: 전체 프로세스 제어 및 판단.
        3.  **Google Gemini**: 자연어 처리 및 답변 생성.
        4.  **Simple Memory**: 이전 대화 내용(최근 10개) 기억.
        5.  **Notion Tool**: 'Student_Study' 데이터베이스 접근 및 정보 추출.
    *   *Setup:*
        *   Google Gemini API (Google Palm API).
        *   Notion API (Internal Integration Token).
        *   Notion Database ID (`2d0c6a06-e17e-8118-8ce1-dd2f76406aa1`).

    *   Check against rules: Korean? Yes. Markdown? Yes. Purpose clear? Yes. Flow explained? Yes. Credentials listed? Yes. Only README output? Yes.