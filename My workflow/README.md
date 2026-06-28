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
            *   `AI Agent` (LangChain Agent): The brain coordinating everything.
            *   `Google Gemini Chat Model` (LLM): The language model powering the agent.
            *   `Simple Memory` (Window Buffer Memory): Keeps track of the last 10 messages for context.
            *   `Get a database in Notion` (Notion Tool): Allows the agent to access a specific Notion database ("Student_Study").

        1.  Clear purpose and operation method.
        2.  Sequential node flow (Trigger $\rightarrow$ Process $\rightarrow$ Output).
        3.  Required environment variables/credentials.
        4.  Precautions/Special notes.
        5.  Markdown format.
        6.  Output *only* the README.md content.

    *   *Purpose:* This is a chatbot that uses Google Gemini and can interact with a Notion database (specifically "Student_Study"). It's an AI Agent capable of remembering past conversations.
    *   *Flow:*
        1.  User sends a message via the Chat Trigger.
        2.  The AI Agent receives the message.
        3.  The Agent uses Gemini for reasoning.
        4.  The Agent uses Window Buffer Memory to maintain context.
        5.  If the query requires data from Notion, the Agent uses the Notion Tool to fetch data from the "Student_Study" database.
        6.  The Agent generates a response and sends it back to the user.

    *   *Title:* Notion 연동 AI 챗봇 워크플로우 (Notion-Integrated AI Chatbot Workflow)
    *   *Description:* Google Gemini와 Notion을 결합하여 특정 데이터베이스의 정보를 조회하고 대화할 수 있는 AI 에이전트입니다.
    *   *Workflow Flow:*
        *   `When chat message received` $\rightarrow$ `AI Agent`
        *   `AI Agent` $\leftarrow$ `Google Gemini Chat Model` (LLM)
        *   `AI Agent` $\leftarrow$ `Simple Memory` (Memory)
        *   `AI Agent` $\leftarrow$ `Get a database in Notion` (Tool)
    *   *Credentials:*
        *   Google Gemini API Key.
        *   Notion API Integration Token (with access to the specific database).

    *   Check against the rules.
    *   Ensure Korean is natural and professional.
    *   Make sure the Notion database name "Student_Study" is mentioned.