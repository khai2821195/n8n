# Alimtalk Sangdam 251201

> **Category:** Math4U  
> **Workflow ID:** `S1ObqqNJYt6Weh0b`  
> **노션 메뉴얼:** https://www.notion.so/323c6a06e17e815ca8a0eeba78761e16  
> **자동 생성:** Gemini AI  

---

n8n Workflow Expert.
Analyze a provided n8n workflow JSON and write a GitHub `README.md` in Korean.
"Alimtalk Sangdam 251201" (ID: S1ObqqNJYt6Weh0b, Category: Math4U).

        1.  `Schedule Trigger`: Runs every hour.
        2.  `Notion 신규상담신청 확인` (Notion Node): Gets all pages from the "Potential" database where the "알림톡 발송" (Alimtalk Sent) checkbox is unchecked (implied by the filter, though the JSON says `equals` but usually, these workflows check for *false* to send). *Correction*: Looking at the filter `equals` for a checkbox, it's likely checking for those that *need* sending.
        3.  `If - 신규 상담 있는지` (If Node): Checks if the number of items returned from Notion is greater than 0.
        4.  `Alimtalk Setting` (HTTP Request Node): Sends a POST request to NHN Cloud Alimtalk API. It uses a specific template (`Math4U-edu-2025001`) and the recipient's phone number from Notion.
        5.  `Send a message` (Slack Node): Sends a notification to the `#상담신청` channel with detailed student and consultation info.
        6.  `Notion Update` (Notion Node): Updates the "알림톡 발송" checkbox to `true` to prevent duplicate sends.
        7.  `Set - 성공 데이터` (Set Node): Records success metadata (workflow ID, name, etc.).

    *   *Purpose:* Automate the process of notifying staff and customers when a new consultation request is submitted via Notion.
    *   *Flow:* Schedule $\rightarrow$ Notion Check $\rightarrow$ Condition $\rightarrow$ Alimtalk Send $\rightarrow$ Slack Notify $\rightarrow$ Notion Update.

    *   *Title:* Alimtalk Sangdam 251201 (Math4U)
    *   *Description:* A workflow that monitors Notion for new consultation requests, sends an Alimtalk message to the customer, notifies the team via Slack, and marks the request as processed.
    *   *Workflow Steps:*
        1.  **Trigger:** Hourly check.
        2.  **Notion Fetch:** Retrieve entries from the "Potential" database where Alimtalk hasn't been sent.
        3.  **Condition:** Proceed only if new requests exist.
        4.  **Alimtalk API:** Send a Kakao Alimtalk message using NHN Cloud API.
        5.  **Slack Notification:** Alert the team with detailed request info.
        6.  **Notion Update:** Mark the "Alimtalk Sent" checkbox as checked.
    *   *Requirements:*
        *   Notion API Key & Database ID.
        *   NHN Cloud Alimtalk API Keys (`X-Secret-Key`, `X-App-Key`, `senderKey`).
        *   Slack Bot Token & Channel ID.

    *   Ensure professional tone.
    *   Use clear headings and lists.
    *   Highlight the specific API endpoints and template codes used.