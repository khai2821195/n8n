# n8n Github Sync (노션 메뉴얼 → README)

> **Category:** 공통  
> **Workflow ID:** `gRhv6ri8Nq5sE1Ol`  
> **노션 메뉴얼:** https://www.notion.so/324c6a06e17e81728fb3ccec9d7bae3a  
> **자동 생성:** Gemini AI  

---

n8n Workflow Expert.
Analyze provided JSON and write a GitHub `README.md` in Korean.
n8n Github Sync (노션 메뉴얼 $\rightarrow$ README).
`gRhv6ri8Nq5sE1Ol`.
Common.

        *   *Sticky Note:* Summary of the flow (n8n list $\rightarrow$ Notion DB comparison $\rightarrow$ Delete archived $\rightarrow$ Add new $\rightarrow$ Backup loop $\rightarrow$ JSON backup + Notion storage + Gemini README generation).
        *   *Trigger:* Manual Trigger.
        *   *Node 1 (HTTP Request):* `get-n8n-list` - Fetches all workflows from n8n API using `N8N_API_KEY`.
        *   *Node 2 (HTTP Request):* `notion-db` - Queries Notion DB to get existing workflow records.
        *   *Node 3 (Code):* `sync-check` - Compares n8n list vs. Notion DB. Identifies workflows to delete (archived/missing in n8n) and workflows to add (new in n8n).
        *   *Node 4 (IF):* `check-action` - Splits flow based on `_action` (delete vs. add).
        *   *Node 5 (HTTP Request):* `notion-delete` - Archives the page in Notion if the workflow is deleted/archived.
        *   *Node 6 (HTTP Request):* `notion-add` (implied/partial in JSON) - Adds new workflows to Notion.
        *   *Implicit/Mentioned in Sticky Note:* The flow continues to back up JSON to GitHub, save JSON to Notion, and use Gemini to generate a README.

    *   *Purpose:* Automatically synchronize n8n workflows with a Notion database and back them up to GitHub, including AI-generated documentation.
    *   *Workflow Steps:*
        1.  Fetch n8n workflows.
        2.  Fetch Notion DB records.
        3.  Compare and sync (Add new/Delete archived).
        4.  Backup loop: Save JSON to GitHub and Notion.
        5.  AI Documentation: Use Gemini to create a README for each workflow.

    *   *Title:* # n8n Github Sync (노션 메뉴얼 → README)
    *   *Description:* A workflow that keeps n8n workflows, Notion documentation, and GitHub backups in sync.
    *   *Key Features:*
        *   Automatic sync between n8n and Notion.
        *   Workflow JSON backup to GitHub.
        *   AI-powered README generation via Gemini.
    *   *Workflow Process:*
        1.  **Trigger**: Manual execution.
        2.  **Data Collection**: Fetch n8n workflow list $\rightarrow$ Fetch Notion DB.
        3.  **Sync Logic**: Compare lists $\rightarrow$ Delete archived $\rightarrow$ Add new.
        4.  **Backup & Doc**: JSON backup $\rightarrow$ Notion update $\rightarrow$ Gemini README creation.
    *   *Environment Variables:* `N8N_API_KEY`, `GITHUB_TOKEN`, `GEMINI_API_KEY`.
    *   *Prerequisites:* Notion Database ID, API access.

    *   Ensure professional tone.
    *   Use clear headings and lists.
    *   Highlight the "AI" part as it's a key value-add.