# Alimtalk Sangdam 251201

> **Category:** Math4U  
> **Workflow ID:** `S1ObqqNJYt6Weh0b`  
> **노션 메뉴얼:** https://www.notion.so/323c6a06e17e815ca8a0eeba78761e16  
> **자동 생성:** Gemini AI  

---

n8n Workflow Expert.
Analyze the provided JSON and write a GitHub `README.md` in Korean.
"Alimtalk Sangdam 251201" (ID: S1ObqqNJYt6Weh0b, Category: Math4U).

        *   `Schedule Trigger`: Runs every hour.
        *   `Notion 신규상담신청 확인` (Notion Node): Gets pages from a database ("Potential") where a checkbox "알림톡 발송" is unchecked (or filtered for new entries).
        *   `If - 신규 상담 있는지` (If Node): Checks if the number of items returned is greater than 0.
        *   `Alimtalk Setting` (HTTP Request Node): Sends a POST request to NHN Cloud Alimtalk API using a specific template (`Math4U-edu-2025001`) and the recipient's phone number from Notion.
        *   `Send a message` (Slack Node): Sends a detailed notification to a Slack channel (`#상담신청`) including student name, school, grade, and consultation details.
        *   `Notion Update` (Notion Node): Updates the Notion page to check the "알림톡 발송" checkbox to prevent duplicate sends.
        *   `Set - 성공 데이터` (Set Node): Records success metadata (workflow ID, name, etc.).

    *   *Purpose:* Automate the process of notifying staff and clients when a new consultation request is submitted via Notion.
    *   *Flow:* Schedule $\rightarrow$ Check Notion $\rightarrow$ (If exists) $\rightarrow$ Send Alimtalk $\rightarrow$ Notify Slack $\rightarrow$ Update Notion.

    *   *Title:* Alimtalk Sangdam 251201 (Math4U)
    *   *Description:* A workflow that monitors Notion for new consultation requests, sends an Alimtalk message to the client, notifies the team via Slack, and marks the request as processed.
    *   *Workflow Steps:*
        1.  **Schedule Trigger**: Every hour.
        2.  **Notion Check**: Filter "Potential" database for items needing Alimtalk.
        3.  **Conditional Check**: Proceed only if new requests exist.
        4.  **Alimtalk Dispatch**: API call to NHN Cloud.
        5.  **Slack Notification**: Detailed alert to `#상담신청`.
        6.  **Notion Update**: Mark "알림톡 발송" as true.
    *   *Requirements:*
        *   Notion API Key & Database ID.
        *   NHN Cloud Alimtalk API Key & Secret Key.
        *   Slack Bot Token & Channel ID.
    *   *Notes:* Mention the specific template code and the importance of the checkbox for deduplication.