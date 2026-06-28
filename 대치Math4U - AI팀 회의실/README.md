# 대치Math4U - AI팀 회의실

> **Category:** 공통  
> **Workflow ID:** `MZK5Sv9zp1D0OMmx`  
> **자동 생성:** Gemini AI  

---

n8n Workflow Expert.
Analyze a provided n8n workflow JSON and write a GitHub `README.md` in Korean.
"대치Math4U - AI팀 회의실" (Daechi Math4U - AI Team Meeting Room).

        *   `form-trigger`: Form trigger for inputting a meeting agenda.
        *   `parse-input`: Set node to parse agenda and current date.
        *   `neil-gemini`: Google Gemini node acting as Neil Patel (Marketer/SEO).
        *   `john-gemini`: Google Gemini node acting as Jony Ive (Designer/Visual).
        *   `bill-gemini`: Google Gemini node acting as Bill Gates (Automation/Ops).
        *   `tim-gemini`: Google Gemini node acting as Tim Cook (Student Management/CRM).
        *   `minutes` (Set node): Aggregates all AI responses into a formatted Markdown meeting minute.

        1.  Clear purpose and operation method.
        2.  Sequential node flow (Trigger $\rightarrow$ Process $\rightarrow$ Output).
        3.  Required environment variables/credentials.
        4.  Precautions/Special notes.
        5.  Markdown format.
        6.  Output *only* the README content.

    *   *Title:* 대치Math4U - AI팀 회의실 (AI Team Meeting Room)
    *   *Purpose:* To simulate a multi-disciplinary brainstorming session. Instead of one AI, four specialized AI personas (Marketing, Design, Automation, Student Management) provide feedback on a specific agenda.
    *   *Flow:*
        1.  **Trigger:** User fills out a form with an "agenda".
        2.  **Preprocessing:** Extract agenda and set the current date.
        3.  **AI Brainstorming (Parallel/Sequential):**
            *   Neil (Marketing): Focuses on SEO, clicks, and trends.
            *   John (Design): Focuses on minimalism and brand consistency.
            *   Bill (Automation): Focuses on n8n, efficiency, and systems.
            *   Tim (Student Mgmt): Focuses on parent trust and student satisfaction.
        4.  **Aggregation:** Combine all responses into a structured Markdown meeting minute.
    *   *Credentials:* Google Gemini API Key.
    *   *Special Note:* The final output is designed to be pasted into Claude.ai (referred to as "Genie") for final synthesis and action item determination.

    *   *Header:* # 대치Math4U - AI팀 회의실
    *   *Introduction:* This workflow allows a user to input a meeting topic and receive diverse perspectives from four AI personas.
    *   *Workflow Steps:*
        1.  `회의 시작 폼` $\rightarrow$ Input agenda.
        2.  `입력 파싱` $\rightarrow$ Data cleaning.
        3.  `AI 페르소나 분석` $\rightarrow$ 4 Gemini nodes.
        4.  `회의록 생성` $\rightarrow$ Markdown formatting.
    *   *Personas Table:*
        *   Neil: Marketing/SEO.
        *   John: Design/Visual.
        *   Bill: Automation/Ops.
        *   Tim: Student/Parent Mgmt.
    *   *Requirements:* Google Gemini API.
    *   *Usage:* Form $\rightarrow$ Result $\rightarrow$ Claude.ai.