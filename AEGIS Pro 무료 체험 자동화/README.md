# AEGIS Pro 무료 체험 자동화

> **Category:** 공통  
> **Workflow ID:** `57LNfEjxyVpYIVvi`  
> **자동 생성:** Gemini AI  

---

n8n Workflow Expert.
Analyze the provided JSON and write a GitHub `README.md` in Korean.
"AEGIS Pro 무료 체험 자동화" (AEGIS Pro Free Trial Automation).
`57LNfEjxyVpYIVvi`.
Common.

        *   *Node 1: Notion Trigger ("노션 신청 감지")* -> Polls a Notion database every minute for new entries.
        *   *Node 2: HTTP Request ("Supabase Pro 활성화 + 알림")* -> Sends a POST request to a Supabase Edge Function (`activate-pro-trial`) with `username`, `email`, and `name`. Uses a secret header `x-webhook-secret`.
        *   *Node 3: IF Node ("성공 여부 확인")* -> Checks if the response from Supabase has `success: true`.
        *   *Node 4: Notion Update (Success) ("노션 상태 업데이트 (성공)")* -> Updates Notion page status to "Pro 적용됨", sets "Pro 시작일" to today, and "Pro 만료일" to 30 days from now.
        *   *Node 5: Notion Update (Error) ("노션 상태 업데이트 (오류)")* -> Updates Notion page status to "오류" and adds the error message to the "메모" field.

    *   Purpose/Mechanism.
    *   Node flow (Trigger $\rightarrow$ Process $\rightarrow$ Output).
    *   Required environment variables/credentials.
    *   Precautions/Special notes.
    *   Markdown format.
    *   *Constraint:* Output only the `README.md` content.

    *   *Title:* AEGIS Pro 무료 체험 자동화 (AEGIS Pro Free Trial Automation).
    *   *Description:* Automates the process of granting a 30-day Pro trial to users who apply via Notion.
    *   *Workflow Steps:*
        1.  **Notion Trigger:** Detects new applications in the Notion database.
        2.  **Supabase API:** Calls the activation function with user data.
        3.  **Conditional Logic:** Checks if the API call was successful.
        4.  **Notion Update:** Updates the database status based on the result (Success $\rightarrow$ Set dates; Failure $\rightarrow$ Log error).
    *   *Requirements:*
        *   Notion API Key (Internal Integration Token).
        *   Notion Database ID.
        *   Supabase Edge Function URL.
        *   Webhook Secret (`aegis-pro-trial-2026`).
    *   *Key Logic:* The date calculation for the 30-day trial is handled via JavaScript expressions in the Notion node.