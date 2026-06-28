# 🔧 슬랙 나에게 보내기 (공통 서브워크플로우)

> **Category:** 공통  
> **Workflow ID:** `L2oRzJDV57Rf8pcr`  
> **자동 생성:** Gemini AI  

---

n8n Workflow Expert.
Analyze the provided JSON and write a GitHub `README.md` in Korean.
"🔧 슬랙 나에게 보내기 (공통 서브워크플로우)" (Slack Send to Me - Common Sub-workflow).

        *   Trigger: `When Executed by Another Workflow` (Execute Workflow Trigger).
        *   Input: `text` (required), `channel` (optional).
        *   Node 1 (`Code - 채널 설정`): Handles input validation and sets a default Slack channel ID (`U07J6D9J5L6`).
        *   Node 2 (`Slack - 나에게 보내기`): Sends the message to the determined channel.
        *   Node 3 (`Code - 결과 정리`): Formats the output to `isSuccess`, `channel`, and `ts`.
        *   Settings: Timezone `Asia/Seoul`.

        1.  Purpose and operation.
        2.  Node flow (Trigger $\rightarrow$ Process $\rightarrow$ Output).
        3.  Environment variables/Credentials.
        4.  Precautions/Special notes.
        5.  Markdown format.
        6.  Output *only* the README.md content.

    *   *Title:* 🔧 슬랙 나에게 보내기 (공통 서브워크플로우)
    *   *Introduction:* This is a reusable sub-workflow designed to send notifications to a specific Slack user or channel. It's meant to be called by other workflows using the "Execute Workflow" node.
    *   *Workflow Flow:*
        1.  `When Executed by Another Workflow`: Receives `text` and `channel`.
        2.  `Code - 채널 설정`: Validates `text`. If `channel` is empty, uses the `DEFAULT_CHANNEL` constant.
        3.  `Slack - 나에게 보내기`: Uses Slack API to send the message.
        4.  `Code - 결과 정리`: Returns a clean success/fail status.
    *   *Input/Output Table:*
        *   Input: `text` (string), `channel` (string, optional).
        *   Output: `isSuccess` (boolean), `channel` (string), `ts` (string).
    *   *Setup/Configuration:*
        *   Slack Credentials needed.
        *   Need to change `DEFAULT_CHANNEL` in the code node to the user's own member ID.
    *   *How to get Member ID:* Profile $\rightarrow$ More $\rightarrow$ Copy member ID.

    *   Ensure professional and clear terminology.
    *   Use emojis for readability.
    *   Structure with clear headings.