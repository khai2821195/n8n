# Supabase 클라우드 활성화 핑 (5일마다)

> **Category:** DCT  
> **Workflow ID:** `eiDJtQcixL9dancS`  
> **노션 메뉴얼:** https://www.notion.so/38ac6a06e17e81028050e5094f76c1e2  
> **자동 생성:** Gemini AI  

---

n8n Workflow Expert.
Analyze a provided JSON workflow and create a GitHub `README.md` in Korean.
"Supabase 클라우드 활성화 핑 (5일마다)" (Supabase Cloud Activation Ping - every 5 days).
`eiDJtQcixL9dancS`.
DCT.

        *   `Schedule Trigger`: Runs every 5 days.
        *   `Ping AttendanceApp` (HTTP Request): Calls a Supabase REST API (`/rest/v1/groups?select=id&limit=1`) with API keys.
        *   `Ping Aegis` (HTTP Request): Calls another Supabase REST API (`/rest/v1/profiles?select=id&limit=1`) with API keys.
        *   `Notion 상태 업데이트 (성공)` (Notion Node): Updates a specific page (`38ac6a06e17e81028050e5094f76c1e2`) to "✅ 정상" and updates the "Last Run" date.
        *   `에러 감지` (Error Trigger): Catches errors in the workflow.
        *   `Notion 상태 업데이트 (에러)` (Notion Node): Updates the same Notion page to "❌ 에러", updates the "Last Run" date, and logs the error message.

        *   Schedule Trigger $\rightarrow$ Ping AttendanceApp $\rightarrow$ Notion (Success).
        *   Schedule Trigger $\rightarrow$ Ping Aegis $\rightarrow$ Notion (Success).
        *   Error Trigger $\rightarrow$ Notion (Error).

    *   *Purpose:* Supabase free tier projects often pause after a period of inactivity. This workflow sends a "ping" (API request) every 5 days to keep the projects active and logs the status in Notion.
    *   *Flow:*
        1.  Trigger: Every 5 days.
        2.  Action: HTTP requests to two different Supabase projects.
        3.  Success: Update Notion page status to "Normal".
        4.  Failure: Update Notion page status to "Error" via Error Trigger.

    *   *Title:* Supabase 클라우드 활성화 핑 (5일마다)
    *   *Description:* Supabase 무료 티어 프로젝트의 휴면 상태 방지를 위해 주기적으로 API 요청을 보내고, 그 결과를 Notion에 기록하는 워크플로우입니다.
    *   *Workflow Structure:*
        *   Trigger $\rightarrow$ HTTP Request $\rightarrow$ Notion Update.
    *   *Required Credentials:*
        *   Supabase API Keys (included in the JSON, but should be mentioned as variables).
        *   Notion API Connection.
    *   *Key Nodes:*
        *   `Schedule Trigger`: 5일 주기 실행.
        *   `HTTP Request`: Supabase REST API 호출.
        *   `Notion`: 상태 업데이트.
        *   `Error Trigger`: 예외 처리.

    *   Ensure professional tone.
    *   Use clear headings.
    *   Make sure the logic matches the JSON exactly.