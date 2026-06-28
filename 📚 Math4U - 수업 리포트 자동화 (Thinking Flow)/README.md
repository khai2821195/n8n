# 📚 Math4U - 수업 리포트 자동화 (Thinking Flow)

> **Category:** 공통  
> **Workflow ID:** `fLXAn8mq5xsr5GNE`  
> **자동 생성:** Gemini AI  

---

n8n Workflow Expert.
Analyze a provided n8n workflow JSON and write a GitHub `README.md` in Korean.
"📚 Math4U - 수업 리포트 자동화 (Thinking Flow)".
A JSON object containing nodes (Webhook, Set, Notion, HTTP Request/Gemini, etc.).

        *   Clear purpose and operation method.
        *   Step-by-step node flow (Trigger $\rightarrow$ Process $\rightarrow$ Output).
        *   Required environment variables/credentials.
        *   Precautions/Special notes.
        *   Markdown format.
        *   *Output only the README.md content.*

    *   *Name:* Math4U - Lesson Report Automation (Thinking Flow).
    *   *Trigger:* Webhook (`/math4u-lesson-report`). Likely triggered by Google Forms or Tally.
    *   *Data Parsing (Set Node):* Extracts `studentName`, `lessonDate`, `subjectUnit`, `discovery`, `generalization`, `concentration`, `eureka`, `weakness`, `presetMessage`.
    *   *Notion Lookup:* Searches for student info in a Notion database (ID: `229c6a06...`) using the student's name.
    *   *AI Generation (HTTP Request):* Calls Gemini API (`gemini-3.1-flash-lite`).
        *   *Prompt:* Acts as a premium math academy expert. Creates a "The Thinking Flow" report. Focuses on "Generalization of basic concepts" and "Intellectual growth."
        *   *Structure:* Core principle $\rightarrow$ Flow of thought $\rightarrow$ Growth point $\rightarrow$ Next step.
    *   *Downstream (Implied by Sticky Note but partially cut off in JSON):*
        *   Kakao Alimtalk (Notification).
        *   Notion Log (Saving history).
        *   Slack Notification (Alerting the instructor).

    *   *Title:* 📚 Math4U - 수업 리포트 자동화 (Thinking Flow)
    *   *Overview:* Automating the process from instructor form submission to parent notification via AI-generated reports.
    *   *Workflow Steps:*
        1.  Webhook $\rightarrow$ 2. Data Parsing $\rightarrow$ 3. Notion Lookup $\rightarrow$ 4. Gemini AI Generation $\rightarrow$ 5. Notification/Logging.
    *   *Key Features:*
        *   AI-driven "VIP tone" reports.
        *   Integration with Notion for student management.
        *   Multi-channel output (Kakao, Notion, Slack).
    *   *Requirements:*
        *   n8n instance.
        *   Gemini API Key.
        *   Notion API Token & Database ID.
        *   (Implied) Kakao Alimtalk API / Slack Webhook.

    *   Ensure professional terminology (e.g., "사고의 궤적", "VIP 톤앤매너").
    *   Structure with clear headings and lists.