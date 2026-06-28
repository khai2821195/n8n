# 🔧 WF Status Updater (공통 서브워크플로우)

> **Category:** 공통  
> **Workflow ID:** `eOopB5bbEEO9rjrg`  
> **자동 생성:** Gemini AI  

---

n8n Workflow Expert.
Analyze a provided JSON workflow and write a GitHub `README.md` in Korean.
`🔧 WF Status Updater (공통 서브워크플로우)` (Common Sub-workflow).
`eOopB5bbEEO9rjrg`.
Common.

        *   `Execute Workflow Trigger`: Receives calls from other workflows.
        *   `Code (validate)`: Validates input (`workflowId`, `notionPageId` are mandatory), sets defaults for `status`, `errorMessage`, `workflowName`, and generates a timestamp (`lastRun`).
        *   `HTTP Request (update-notion)`: Updates a Notion page via API (PATCH). Updates 'Status', 'Last Run', and 'Error Message'.
        *   `If (if-error)`: Checks if `status` is "❌ 에러".
        *   `If (filter-infra-error)`: If it's an error, checks if the error message matches infrastructure-related patterns (502, 503, 504, Bad Gateway, etc.) using regex.
        *   `Slack (slack-alert)`: Sends a notification to a specific Slack channel if it's a non-infra error.
        *   `Set (result)`: Returns a success response with status and timestamp.

    *   *Purpose:* A centralized sub-workflow to track the health/status of other n8n workflows. It updates a Notion dashboard and alerts Slack when critical errors occur.
    *   *Inputs:* `workflowId`, `notionPageId`, `status`, `errorMessage`, `workflowName`.
    *   *Logic:*
        1. Trigger $\rightarrow$ 2. Validate $\rightarrow$ 3. Update Notion $\rightarrow$ 4. Check if Error $\rightarrow$ 5. Filter Infra Errors $\rightarrow$ 6. Slack Alert (if applicable) $\rightarrow$ 7. Return Result.

    *   *Title:* 🔧 WF Status Updater (공통 서브워크플로우)
    *   *Description:* Centralized status management for n8n workflows.
    *   *Key Features:* Notion dashboard sync, Slack alerting (excluding transient infra errors).
    *   *Input Parameters Table:*
        *   `workflowId` (Required): ID of the calling workflow.
        *   `notionPageId` (Required): ID of the Notion page to update.
        *   `status` (Optional): `✅ 정상` or `❌ 에러`.
        *   `errorMessage` (Optional): Error details.
        *   `workflowName` (Optional): Name of the workflow.
    *   *Workflow Flow:*
        1. **Trigger**: Receives data from the parent workflow.
        2. **Validation**: Checks mandatory fields and sets timestamps.
        3. **Notion Update**: Updates the status, last run time, and error message in Notion.
        4. **Error Filtering**: If status is "Error", it checks if it's a temporary infrastructure error (502, 503, etc.).
        5. **Slack Notification**: Sends an alert for non-infra errors.
        6. **Result**: Returns the final execution status.
    *   *Requirements:* Notion API Credentials, Slack API Credentials.

    *   Ensure professional tone.
    *   Use clear headings and lists.
    *   Make sure the regex part (infra error filtering) is highlighted as a smart feature.