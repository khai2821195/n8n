# n8n Github Sync (노션 메뉴얼 → README)

> **Category:** 공통  
> **Workflow ID:** `gRhv6ri8Nq5sE1Ol`  
> **노션 메뉴얼:** https://www.notion.so/324c6a06e17e81728fb3ccec9d7bae3a  
> **자동 생성:** Gemini AI  

---

n8n Workflow Expert.
Analyze n8n workflow JSON and write a GitHub `README.md` in Korean.
"n8n Github Sync (노션 메뉴얼 → README)" (ID: gRhv6ri8Nq5sE1Ol).

        *   *Sticky Note:* Summarizes the flow:
            1. Get all n8n WF list.
            2. Query Notion DB $\rightarrow$ Compare.
            3. Archive WF $\rightarrow$ Delete from Notion.
            4. New WF $\rightarrow$ Auto-add to Notion.
            5. Re-query Notion DB $\rightarrow$ Backup loop.
            6. For each WF: JSON backup + Save JSON to Notion page + Gemini README generation.
        *   *Environment Variables:* `N8N_API_KEY`, `GITHUB_TOKEN`, `GEMINI_API_KEY`.
        *   *Nodes:*
            *   `Manual Trigger`: Starts the process.
            *   `HTTP Request (n8n API)`: Fetches all workflows.
            *   `HTTP Request (Notion API)`: Queries the Notion database.
            *   `Code Node (sync-check)`: Logic to compare n8n list vs. Notion list. Determines if a workflow needs to be added or deleted (archived).
            *   `IF Node (check-action)`: Splits path based on `_action` (delete vs. add).
            *   `HTTP Request (Notion API - PATCH)`: Archives the page in Notion if the workflow is gone or archived in n8n.
            *   *(JSON cuts off, but the Sticky Note provides the full logic)*: The rest involves backing up JSON to GitHub, updating Notion, and using Gemini for README generation.

    *   *Purpose:* Automate the synchronization of n8n workflows with a Notion manual and GitHub repository. It ensures that the documentation (Notion) and the code (GitHub) stay up-to-date with the actual workflows running in n8n.
    *   *Key Features:*
        *   Auto-sync n8n $\leftrightarrow$ Notion.
        *   Automatic backup of workflow JSON to GitHub.
        *   AI-powered (Gemini) README generation for each workflow.
        *   Automatic cleanup of archived workflows.

    *   *Step-by-Step Flow:*
        1.  **Trigger:** Manual start.
        2.  **Data Collection:** Fetch current workflows from n8n API and existing entries from Notion DB.
        3.  **Comparison Logic:** Compare IDs.
            *   If in Notion but not in n8n (or archived) $\rightarrow$ Mark for deletion/archiving in Notion.
            *   If in n8n but not in Notion $\rightarrow$ Mark for addition to Notion.
        4.  **Notion Sync:** Execute the additions/deletions.
        5.  **Backup & Documentation Loop:**
            *   Export workflow JSON.
            *   Upload JSON to GitHub.
            *   Save JSON to the corresponding Notion page.
            *   Use Gemini AI to analyze the JSON and generate a README.md for GitHub.

    *   *Requirements:*
        *   `N8N_API_KEY`: To access n8n workflows.
        *   `GITHUB_TOKEN`: To push files to the repository.
        *   `GEMINI_API_KEY`: To generate AI documentation.
        *   Notion Integration: Internal Integration Token and Database ID.

    *   *Title:* # n8n Github Sync (노션 메뉴얼 → README)
    *   *Description:* n8n 워크플로우의 변경 사항을 자동으로 감지하여 노션(Notion) DB와 깃허브(GitHub) 저장소를 동기화하고, AI를 통해 문서화를 자동화하는 워크플로우입니다.
    *   *Workflow Flow:* (Use a list or diagram-like structure).
    *   *Environment Variables:* (Table or list).
    *   *Detailed Logic:* (Explain the sync and backup process).

    *   Ensure professional tone.
    *   Check if all requirements from the prompt are met.
    *   Make sure the "README.md only" constraint is followed.