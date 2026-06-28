# Supabase 클라우드 활성화 핑 (5일마다)

> **Category:** DCT  
> **Workflow ID:** `eiDJtQcixL9dancS`  
> **노션 메뉴얼:** https://www.notion.so/38ac6a06e17e81028050e5094f76c1e2  
> **자동 생성:** Gemini AI  

---

n8n Workflow Expert.
Analyze a provided JSON workflow and write a GitHub `README.md` in Korean.

        *   Name: Supabase 클라우드 활성화 핑 (5일마다)
        *   ID: eiDJtQcixL9dancS
        *   Category: DCT

        *   *Schedule Trigger*: Runs every 5 days.
        *   *HTTP Request (Ping AttendanceApp)*: Calls a Supabase REST API (`/rest/v1/groups?select=id&limit=1`) with specific API keys.
        *   *HTTP Request (Ping Aegis)*: Calls another Supabase REST API (`/rest/v1/profiles?select=id&limit=1`) with specific API keys.
        *   *Notion (Success Update)*: Updates a specific Notion page (ID: `38ac6a06e17e81028050e5094f76c1e2`) setting status to "✅ 정상" and updating "Last Run" date.
        *   *Error Trigger*: Catches errors in the workflow.
        *   *Notion (Error Update)*: Updates the same Notion page setting status to "❌ 에러", updating "Last Run" date, and recording the error message.

    *   *Purpose:* Supabase free tier projects often pause if there's no activity. This workflow "pings" the API every 5 days to keep the projects active and logs the status in Notion.
    *   *Flow:*
        1.  Trigger: Every 5 days.
        2.  Action: Send HTTP requests to two different Supabase projects.
        3.  Success: Update Notion page to "Normal".
        4.  Failure: Update Notion page to "Error" via Error Trigger.

    *   *Title:* Supabase 클라우드 활성화 핑 (5일마다)
    *   *Description:* Prevent Supabase project pausing by sending periodic requests.
    *   *Workflow Diagram/Logic:*
        *   `Schedule Trigger` $\rightarrow$ `HTTP Request (AttendanceApp & Aegis)` $\rightarrow$ `Notion (Success)`
        *   `Error Trigger` $\rightarrow$ `Notion (Error)`
    *   *Requirements:*
        *   n8n instance.
        *   Supabase API keys (provided in JSON, but should be mentioned as credentials).
        *   Notion API integration (Database Page ID).
    *   *Details:* Mention the specific intervals and the Notion properties being updated.

    *   Ensure professional tone.
    *   Use clear headings.
    *   Check for accuracy against the JSON.