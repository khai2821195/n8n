# 🔧 WF Status Updater (공통 서브워크플로우)

> **Category:** 공통  
> **Workflow ID:** `eOopB5bbEEO9rjrg`  
> **자동 생성:** Gemini AI  

---

n8n Workflow Expert.
Analyze the provided JSON and write a GitHub `README.md` in Korean.
`🔧 WF Status Updater (공통 서브워크플로우)` (Common Sub-workflow).

        *   `executeWorkflowTrigger`: Receives calls from other workflows.
        *   `Code Node (validate)`: Validates input (`workflowId`, `notionPageId` are required) and prepares data (current time, status, etc.).
        *   `HTTP Request (update-notion)`: Updates a Notion page's status, last run date, and error message using the Notion API.
        *   `IF Node (if-error)`: Checks if the status is "❌ 에러".
        *   `IF Node (filter-infra-error)`: If it's an error, checks if it's an infrastructure error (502, 503, 504, etc.) using regex.
        *   `Slack Node (slack-alert)`: Sends a Slack notification if it's a non-infra error.
        *   `Set Node (result)`: Returns the final result (success, updatedAt, status).
        *   `Sticky Note`: Provides a summary of parameters and behavior.

    *   *Purpose:* A centralized sub-workflow to track the health/status of other n8n workflows by updating a Notion dashboard and sending Slack alerts for critical failures.
    *   *Input Parameters:* `workflowId`, `notionPageId` (Required), `status`, `errorMessage`, `workflowName`.
    *   *Logic Flow:* Trigger $\rightarrow$ Validate $\rightarrow$ Update Notion $\rightarrow$ Check Error $\rightarrow$ Filter Infra Error $\rightarrow$ Slack Alert (if applicable) $\rightarrow$ Return Result.

    *   *Title:* 🔧 WF Status Updater (공통 서브워크플로우)
    *   *Overview:* Explain that this is a shared utility workflow.
    *   *Key Features:* Notion status tracking, Smart Slack alerting (filtering infra errors).
    *   *Input Parameters Table:* List the required and optional fields.
    *   *Workflow Logic (Step-by-step):*
        1.  Call received.
        2.  Validation.
        3.  Notion API update.
        4.  Error handling (Slack).
        5.  Return result.
    *   *Requirements:* Notion API Credential, Slack API Credential.
    *   *Special Notes:* Mention the regex used to filter out temporary network/infra errors to prevent alert fatigue.