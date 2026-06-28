# Supabase 클라우드 활성화 핑 (5일마다)

> **Category:** DCT  
> **Workflow ID:** `eiDJtQcixL9dancS`  
> **노션 메뉴얼:** https://www.notion.so/38ac6a06e17e81028050e5094f76c1e2  
> **자동 생성:** Gemini AI  

---

n8n Workflow Expert.
Analyze a provided n8n workflow JSON and write a GitHub `README.md` in Korean.
"Supabase 클라우드 활성화 핑 (5일마다)" (Supabase Cloud Activation Ping - every 5 days).
`eiDJtQcixL9dancS`.
DCT.

        *   `Schedule Trigger`: Runs every 5 days.
        *   `Ping AttendanceApp` (HTTP Request): Sends a request to a Supabase REST endpoint (`/rest/v1/groups?select=id&limit=1`) with API keys.
        *   `Ping Aegis` (HTTP Request): Sends a request to another Supabase REST endpoint (`/rest/v1/profiles?select=id&limit=1`) with API keys.
        *   `Notion 상태 업데이트 (성공)` (Notion Node): Updates a specific Notion page (`38ac6a06e17e81028050e5094f76c1e2`) setting status to "✅ 정상" and updating the "Last Run" date.
        *   `에러 감지` (Error Trigger): Catches errors in the workflow.
        *   `Notion 상태 업데이트 (에러)` (Notion Node): Updates the same Notion page setting status to "❌ 에러", updating the date, and recording the error message.

        *   Schedule Trigger $\rightarrow$ (Ping AttendanceApp AND Ping Aegis) $\rightarrow$ Notion Success Update.
        *   Error Trigger $\rightarrow$ Notion Error Update.

    *   *Purpose:* Supabase free tier projects often pause if there's no activity. This workflow prevents that by sending a request (ping) every 5 days to keep the projects active.
    *   *Flow:*
        1.  Trigger: Every 5 days.
        2.  Action: Request to two different Supabase projects.
        3.  Success: Update Notion status to "Normal".
        4.  Failure: Update Notion status to "Error" with the message.

    *   *Title:* Supabase 클라우드 활성화 핑 (Supabase Cloud Activation Ping)
    *   *Description:* Prevent Supabase project pausing by automating periodic API calls.
    *   *Workflow Diagram/Flow:*
        *   `Schedule Trigger` $\rightarrow$ `HTTP Request (Supabase)` $\rightarrow$ `Notion (Success)`
        *   `Error Trigger` $\rightarrow$ `Notion (Error)`
    *   *Requirements:*
        *   Supabase API Keys (already in JSON, but should be mentioned as credentials).
        *   Notion API Token & Database Page ID.
    *   *Configuration:*
        *   Interval: 5 days.
        *   Notion Page ID: `38ac6a06e17e81028050e5094f76c1e2`.

    *   Ensure professional tone.
    *   Use clear headings.
    *   Check against the "README 작성 규칙" (Purpose, Flow, Env/Credentials, Precautions, Markdown).