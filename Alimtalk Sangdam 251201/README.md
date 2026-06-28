# Alimtalk Sangdam 251201

> **Category:** Math4U  
> **Workflow ID:** `S1ObqqNJYt6Weh0b`  
> **노션 메뉴얼:** https://www.notion.so/323c6a06e17e815ca8a0eeba78761e16  
> **자동 생성:** Gemini AI  

---

n8n Workflow Expert.
Analyze a provided n8n workflow JSON and create a GitHub `README.md` in Korean.
"Alimtalk Sangdam 251201" (ID: S1ObqqNJYt6Weh0b, Category: Math4U).

        *   `Schedule Trigger`: Runs every hour.
        *   `Notion 신규상담신청 확인` (Notion Node): Gets pages from a database ("Potential") where a checkbox "알림톡 발송" is unchecked (implied by the filter logic, though the JSON says `equals` without a value, usually this means looking for specific states).
        *   `If - 신규 상담 있는지` (If Node): Checks if the number of items returned is greater than 0.
        *   `Alimtalk Setting` (HTTP Request Node): Sends a POST request to NHN Cloud Alimtalk API using a specific template (`Math4U-edu-2025001`) and the recipient's phone number from Notion.
        *   `Send a message` (Slack Node): Sends a notification to a Slack channel (`#상담신청`) with detailed consultation info (date, contact, time, student name, school, grade, content).
        *   `Notion Update` (Notion Node): Updates the Notion page to check the "알림톡 발송" checkbox to `true` to prevent duplicate sends.
        *   `Set - 성공 데이터` (Set Node): Records success metadata (workflow ID, name, etc.).

    *   *Purpose:* Automate the process of notifying both the client (via Kakao Alimtalk) and the staff (via Slack) when a new consultation request is submitted via Notion.
    *   *Flow:* Schedule $\rightarrow$ Check Notion $\rightarrow$ Filter $\rightarrow$ Send Alimtalk $\rightarrow$ Notify Slack $\rightarrow$ Update Notion status.

    *   *Title:* Alimtalk Sangdam 251201 (Math4U)
    *   *Overview:* Automated consultation notification system.
    *   *Workflow Steps:*
        1.  **Trigger:** Hourly check.
        2.  **Notion Fetch:** Find new requests.
        3.  **Condition:** Proceed only if requests exist.
        4.  **Alimtalk:** Send automated Kakao message to the customer.
        5.  **Slack:** Notify the team with detailed request info.
        6.  **Notion Update:** Mark as "Sent" to avoid duplicates.
    *   *Requirements:*
        *   Notion API Key & Database ID.
        *   NHN Cloud Alimtalk API Key & Secret Key.
        *   Slack Bot Token & Channel ID.
    *   *Notes:* Template code must match the one registered in NHN Cloud.