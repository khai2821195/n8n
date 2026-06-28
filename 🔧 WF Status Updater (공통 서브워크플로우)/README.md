# 🔧 WF Status Updater (공통 서브워크플로우)

> **Category:** 공통  
> **Workflow ID:** `eOopB5bbEEO9rjrg`  
> **자동 생성:** Gemini AI  

---

n8n Workflow Expert.
Analyze a provided n8n workflow JSON and create a GitHub `README.md` in Korean.
`🔧 WF Status Updater (공통 서브워크플로우)` (Common Sub-workflow).
`eOopB5bbEEO9rjrg`.

        *   *Trigger:* `executeWorkflowTrigger` (Called by other workflows).
        *   *Validation:* `Code` node (Checks for `workflowId` and `notionPageId`, sets defaults for `status`, `errorMessage`, `workflowName`, and generates `lastRun` timestamp).
        *   *Action 1:* `HTTP Request` (PATCH to Notion API to update a page's Status, Last Run date, and Error Message).
        *   *Decision 1:* `If` node (Checks if `status` == `❌ 에러`).
        *   *Decision 2:* `If` node (Regex check for infrastructure errors like 502, 503, 504, Bad Gateway, etc., to avoid spamming alerts for temporary server issues).
        *   *Action 2 (Error path):* `Slack` node (Sends a detailed alert message with workflow name, ID, time, and error message, including a direct link to the workflow).
        *   *Action 3 (Success/Infra error path):* `Set` node (Returns a success result).

    *   *Purpose:* A centralized sub-workflow to track the health of other n8n workflows. It updates a Notion dashboard and sends Slack alerts for critical failures.
    *   *Input Parameters:* `workflowId`, `notionPageId`, `status`, `errorMessage`, `workflowName`.
    *   *Logic Flow:*
        1. Receive call $\rightarrow$ 2. Validate input $\rightarrow$ 3. Update Notion $\rightarrow$ 4. Check if Error $\rightarrow$ 5. Filter out Infra errors $\rightarrow$ 6. Send Slack alert (if applicable) $\rightarrow$ 7. Return result.

    *   *Title:* 🔧 WF Status Updater (공통 서브워크플로우)
    *   *Description:* Centralized status management for n8n workflows.
    *   *Key Features:* Notion Dashboard sync, Smart Slack alerting (filtering infra errors).
    *   *Input Parameters Table:*
        *   `workflowId` (Required)
        *   `notionPageId` (Required)
        *   `status` (Optional, default: ✅ 정상)
        *   `errorMessage` (Optional)
        *   `workflowName` (Optional)
    *   *Workflow Step-by-Step:*
        1. Trigger $\rightarrow$ 2. Validation $\rightarrow$ 3. Notion Update $\rightarrow$ 4. Error Check $\rightarrow$ 5. Infra Filter $\rightarrow$ 6. Slack Alert/Result.
    *   *Credentials:* Notion API, Slack API.
    *   *Special Note:* Mention the regex filtering for 502/503 errors.