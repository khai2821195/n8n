# n8n Github Sync (노션 메뉴얼 → README)

> **Category:** 공통  
> **Workflow ID:** `gRhv6ri8Nq5sE1Ol`  
> **노션 메뉴얼:** https://www.notion.so/324c6a06e17e81728fb3ccec9d7bae3a  
> **자동 생성:** Gemini AI  

---

n8n Workflow Expert.
Analyze the provided JSON and write a GitHub `README.md` in Korean.
`n8n Github Sync (노션 메뉴얼 → README)` (ID: `gRhv6ri8Nq5sE1Ol`).

        *   *Sticky Note:* Summary of flow (n8n list -> Notion DB comparison -> Delete archived -> Add new -> Backup loop -> JSON backup + Notion update + Gemini README generation).
        *   *Trigger:* Manual Trigger.
        *   *Node 1 (HTTP Request):* Fetches all n8n workflows via API (`/api/v1/workflows`).
        *   *Node 2 (HTTP Request):* Queries Notion DB for existing workflow records.
        *   *Node 3 (Code):* Compares n8n list with Notion DB. Identifies workflows to delete (archived or missing in n8n) and workflows to add (new active ones).
        *   *Node 4 (IF):* Branches based on action (`delete` vs `add`).
        *   *Node 5 (HTTP Request):* Archives the page in Notion if the action is `delete`.
        *   *Node 6 (HTTP Request - partial):* Queries Notion DB again (likely to start the backup loop).
        *   *Implicit Logic (from Sticky Note):* The workflow continues to backup JSONs to GitHub, update Notion pages, and use Gemini to generate READMEs.

    *   *Purpose:* Automate the synchronization of n8n workflow documentation. It keeps a Notion database in sync with actual n8n workflows and backs up the JSON definitions to GitHub while generating documentation using AI (Gemini).
    *   *Flow:*
        1.  **Trigger:** Manual start.
        2.  **Sync Phase:**
            *   Fetch n8n workflows.
            *   Fetch Notion DB records.
            *   Compare:
                *   If workflow is archived in n8n $\rightarrow$ Archive in Notion.
                *   If workflow is new in n8n $\rightarrow$ Add to Notion.
        3.  **Backup & Doc Phase:**
            *   For each workflow:
                *   Export JSON.
                *   Save JSON to Notion.
                *   Push JSON to GitHub.
                *   Use Gemini AI to analyze JSON and create a README.md.

    *   `N8N_API_KEY`: For n8n API access.
    *   `GITHUB_TOKEN`: For pushing files to GitHub.
    *   `GEMINI_API_KEY`: For generating README content.
    *   `Notion API Key/Integration Token`: For Notion DB access.

    *   *Title:* # n8n Github Sync (노션 메뉴얼 → README)
    *   *Description:* n8n 워크플로우의 상태를 노션 DB와 동기화하고, 자동으로 GitHub에 백업하며 AI(Gemini)를 통해 README 문서를 생성하는 자동화 워크플로우입니다.
    *   *Key Features:*
        *   n8n $\leftrightarrow$ Notion 실시간 동기화.
        *   워크플로우 JSON 자동 백업 (GitHub).
        *   Gemini AI 기반의 자동 문서화 (README.md).
    *   *Workflow Steps:*
        1.  **수동 실행**: 워크플로우 시작.
        2.  **목록 조회**: n8n API를 통해 전체 워크플로우 목록을 가져오고, 노션 DB의 기존 데이터를 조회합니다.
        3.  **동기화 비교**: n8n의 상태와 노션 DB를 비교하여 '삭제(아카이브)' 또는 '신규 추가' 대상을 분류합니다.
        4.  **노션 업데이트**: 분류된 결과에 따라 노션 페이지를 생성하거나 아카이브 처리합니다.
        5.  **백업 및 문서화**: 각 워크플로우의 JSON 데이터를 추출하여 노션에 저장하고, GitHub에 푸시하며, Gemini AI를 통해 README 파일을 생성합니다.
    *   *Requirements:* List the env vars.
    *   *Notes:* Mention the Notion DB ID and API versions.