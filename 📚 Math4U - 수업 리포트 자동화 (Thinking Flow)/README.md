# 📚 Math4U - 수업 리포트 자동화 (Thinking Flow)

> **Category:** 공통  
> **Workflow ID:** `fLXAn8mq5xsr5GNE`  
> **자동 생성:** Gemini AI  

---

n8n Workflow Expert.
Analyze a provided n8n workflow JSON and create a GitHub `README.md` in Korean.
"📚 Math4U - 수업 리포트 자동화 (Thinking Flow)" (Math4U - Lesson Report Automation).

        *   *Trigger:* Webhook (receives data from mobile forms like Google Forms/Tally).
        *   *Processing 1 (Set Node):* Parses input data (student name, date, subject, discovery, generalization, concentration, eureka moment, weakness, preset message).
        *   *Processing 2 (Notion Node):* Looks up student info (parent contact) in a Notion database.
        *   *Processing 3 (HTTP Request - Gemini AI):* Uses Google Gemini API to generate a high-end, professional report based on the parsed data.
        *   *Output 1 (Alimtalk - implied/missing in JSON but mentioned in Sticky Note):* Sends the report via Kakao Alimtalk.
        *   *Output 2 (Notion - implied/missing in JSON but mentioned in Sticky Note):* Records the history in Notion.
        *   *Output 3 (Slack - implied/missing in JSON but mentioned in Sticky Note):* Notifies the instructor.
        *   *Note:* The JSON provided is a partial snippet (it ends at the Gemini AI node), but the `stickyNote` provides the full intended flow. I must base the README on both the JSON structure and the manual note.

    *   *Title:* 📚 Math4U - 수업 리포트 자동화 (Thinking Flow)
    *   *Description:* Automating the process of creating and sending premium lesson reports to parents after a math class.
    *   *Key Features:*
        *   Mobile form input $\rightarrow$ AI generation $\rightarrow$ Parent notification.
        *   "The Thinking Flow" framework (Discovery, Generalization, Concentration).
        *   VIP tone and manner (Hermès-level elegance).
    *   *Workflow Steps:*
        1.  Webhook (Form submission).
        2.  Data Parsing (Standardizing inputs).
        3.  Notion Lookup (Fetching parent contact).
        4.  AI Generation (Gemini API).
        5.  Alimtalk Sending (Notification).
        6.  Notion Logging (History).
        7.  Slack Notification (Instructor alert).
    *   *Requirements:*
        *   n8n instance.
        *   Google Forms/Tally.
        *   Notion API Key & Database ID.
        *   Gemini API Key.
        *   Kakao Alimtalk API (via a provider).
        *   Slack Webhook/API.

    *   Use a clean, professional structure.
    *   Use emojis to make it visually appealing.
    *   Ensure the technical details (nodes) are accurately mapped.