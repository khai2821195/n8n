# 📚 Math4U - 수업 리포트 자동화 (Thinking Flow)

> **Category:** 공통  
> **Workflow ID:** `fLXAn8mq5xsr5GNE`  
> **자동 생성:** Gemini AI  

---

n8n Workflow Expert.
Analyze a provided n8n workflow JSON and write a GitHub `README.md` in Korean.
`📚 Math4U - 수업 리포트 자동화 (Thinking Flow)` (ID: `fLXAn8mq5xsr5GNE`).

        *   *Sticky Note:* Explains the purpose (Instructor submits form $\rightarrow$ n8n generates AI report $\rightarrow$ Kakao Notification sent to parents).
        *   *Webhook Trigger:* `math4u-lesson-report` (POST).
        *   *Set Node (Data Parsing):* Extracts `studentName`, `lessonDate`, `subjectUnit`, `discovery`, `generalization`, `concentration`, `eureka`, `weakness`, `presetMessage`.
        *   *Notion Node (Student Lookup):* Searches for student info/parent contact in a specific Notion DB.
        *   *HTTP Request (Gemini AI):* Uses Gemini 1.5 Flash Lite to generate a "VIP tone" report based on the parsed data.
        *   *Implicit/Missing Nodes (but mentioned in Sticky Note):* The JSON provided is truncated (it ends at the Gemini request), but the Sticky Note explicitly lists:
            *   Kakao Notification (알림톡 발송)
            *   Notion Record (발송 이력 저장)
            *   Slack Notification (강사 알림)
        *   *Note:* I must describe the *entire* flow as intended by the manual note, even if the JSON snippet is incomplete, while acknowledging the logic present in the JSON.

    *   *Title:* 📚 Math4U - 수업 리포트 자동화 (Thinking Flow)
    *   *Introduction:* Automated system for premium math academy reports.
    *   *Key Features:* Form $\rightarrow$ AI $\rightarrow$ Notification.
    *   *Workflow Steps:*
        1.  Webhook (Google Forms/Tally).
        2.  Data Parsing (Set node).
        3.  Student Search (Notion).
        4.  AI Report Generation (Gemini).
        5.  Notification (KakaoTalk - *based on manual*).
        6.  Logging (Notion - *based on manual*).
        7.  Alert (Slack - *based on manual*).
    *   *Requirements:* Gemini API Key, Notion API, KakaoTalk API (likely via a third-party gateway), Slack Webhook.
    *   *Configuration:* Webhook URL setup.

    *   *Tone:* Professional, clear, and structured.
    *   *Sections:*
        *   Project Name & Description.
        *   Workflow Diagram/Flow (Textual).
        *   Detailed Node Explanation.
        *   Prerequisites (Credentials/Env).
        *   Setup Guide.