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

        1.  `Notion Trigger` ("노션 신청 감지"): Polls a Notion database every minute.
        2.  `HTTP Request` ("Supabase Pro 활성화 + 알림"): Sends a POST request to a Supabase Edge Function (`activate-pro-trial`) with `username`, `email`, and `name`. Uses a secret header `x-webhook-secret`.
        3.  `IF Node` ("성공 여부 확인"): Checks if the response from Supabase has `success: true`.
        4.  `Notion Node (Success)` ("노션 상태 업데이트 (성공)"): Updates the Notion page status to "Pro 적용됨", sets the start date to today, and the expiry date to 30 days from now.
        5.  `Notion Node (Error)` ("노션 상태 업데이트 (오류)"): Updates the Notion page status to "오류" and adds the error message to the memo field.

    *   Purpose/Operation: Clear explanation.
    *   Node Flow: Sequence (Trigger $\rightarrow$ Process $\rightarrow$ Output).
    *   Environment/Credentials: Required items.
    *   Precautions/Special notes.
    *   Format: Markdown.
    *   Output: Only the `README.md` content.

    *   *Title:* AEGIS Pro 무료 체험 자동화 (AEGIS Pro Free Trial Automation).
    *   *Description:* This workflow automates the process of granting a 30-day free trial of "AEGIS Pro" when a user applies via a Notion database.

    *   *Step-by-step Flow:*
        1.  **Notion Trigger**: Monitors a specific database for new applications.
        2.  **Supabase API Call**: Sends user data to a Supabase function to activate the trial.
        3.  **Validation**: Checks if the activation was successful.
        4.  **Notion Update (Success)**: Marks as "Pro Applied" and calculates dates.
        5.  **Notion Update (Failure)**: Marks as "Error" and logs the reason.

    *   *Requirements:*
        *   Notion API Credentials (Integration Token).
        *   Notion Database ID.
        *   Supabase Edge Function URL.
        *   Webhook Secret (`aegis-pro-trial-2026`).

    *   *Special Logic:*
        *   Date calculation: `new Date()` for start, `+ 30 days` for expiry.

    *   Ensure professional tone.
    *   Use clear headings and lists.
    *   Check for accuracy against the JSON.