# AEGIS Pro 무료 체험 자동화

> **Category:** 공통  
> **Workflow ID:** `57LNfEjxyVpYIVvi`  
> **자동 생성:** Gemini AI  

---

n8n Workflow Expert.
Analyze a provided JSON workflow and write a GitHub `README.md` in Korean.
"AEGIS Pro 무료 체험 자동화" (AEGIS Pro Free Trial Automation).
`57LNfEjxyVpYIVvi`.
Common.

        1.  `노션 신청 감지` (Notion Trigger): Polls a Notion database every minute for new entries.
        2.  `Supabase Pro 활성화 + 알림` (HTTP Request): Sends a POST request to a Supabase Edge Function (`activate-pro-trial`) with `username` (AEGIS ID), `email`, and `name`. Uses a secret header `x-webhook-secret`.
        3.  `성공 여부 확인` (IF Node): Checks if the response from Supabase contains `success: true`.
        4.  `노션 상태 업데이트 (성공)` (Notion Node): Updates the Notion page status to "Pro 적용됨", sets the start date to today, and the expiry date to 30 days from now.
        5.  `노션 상태 업데이트 (오류)` (Notion Node): Updates the Notion page status to "오류" and logs the error message in the "메모" field.

    *   *Purpose:* Automate the process of granting a 30-day free trial of "AEGIS Pro" when a user applies via a Notion database.
    *   *Flow:* Notion Trigger $\rightarrow$ Supabase API $\rightarrow$ Success/Failure Check $\rightarrow$ Notion Update.
    *   *Credentials/Env:* Notion API, Supabase Webhook Secret.

    *   *Title:* AEGIS Pro 무료 체험 자동화 (AEGIS Pro Free Trial Automation).
    *   *Description:* A workflow that monitors Notion applications and activates Pro trials via Supabase.
    *   *Workflow Steps:*
        1.  **Trigger:** Notion database polling.
        2.  **Action:** HTTP POST to Supabase.
        3.  **Condition:** Check `success` boolean.
        4.  **Result (True):** Update Notion (Status: Pro 적용됨, Dates: Today & +30 days).
        5.  **Result (False):** Update Notion (Status: 오류, Memo: Error details).
    *   *Requirements:* Notion Database ID, Supabase Function URL, Webhook Secret.
    *   *Notes:* 30-day trial logic is handled within the n8n expression.