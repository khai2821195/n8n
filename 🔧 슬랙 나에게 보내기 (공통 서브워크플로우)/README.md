# 🔧 슬랙 나에게 보내기 (공통 서브워크플로우)

> **Category:** 공통  
> **Workflow ID:** `L2oRzJDV57Rf8pcr`  
> **자동 생성:** Gemini AI  

---

n8n Workflow Expert.
Analyze the provided JSON and write a GitHub `README.md` in Korean.
"🔧 슬랙 나에게 보내기 (공통 서브워크플로우)" (Slack Send to Me - Common Sub-workflow).
`L2oRzJDV57Rf8pcr`.
Common.

        *   `When Executed by Another Workflow` (Trigger): Receives `text` and `channel`.
        *   `Code - 채널 설정` (Code): Validates `text`, sets a default channel (`U07J6D9J5L6`) if `channel` is missing.
        *   `Slack - 나에게 보내기` (Slack): Sends the message to the specified channel.
        *   `Code - 결과 정리` (Code): Formats the response into `isSuccess`, `channel`, and `ts`.

        1.  Clear purpose and operation.
        2.  Step-by-step node flow.
        3.  Environment variables/Credentials.
        4.  Precautions/Special notes.
        5.  Markdown format.
        6.  Output *only* the README content.

    *   *Title:* 🔧 슬랙 나에게 보내기 (공통 서브워크플로우)
    *   *Description:* This is a reusable sub-workflow designed to send notifications to a specific Slack user or channel. It's meant to be called by other workflows using the "Execute Workflow" node.
    *   *Input Parameters:*
        *   `text` (Required): The message content.
        *   `channel` (Optional): Slack Channel/User ID.
    *   *Workflow Steps:*
        1.  **Trigger**: Starts when called by another workflow.
        2.  **Channel Setup**: Checks for input text. If no channel is provided, it uses a predefined default ID.
        3.  **Slack Send**: Uses the Slack API to post the message.
        4.  **Result Formatting**: Returns a clean success/fail status.
    *   *Setup/Requirements:*
        *   Slack Credentials (OAuth2).
        *   User ID configuration in the Code node.
    *   *Usage Example:* How to call it from a parent workflow.

    *   *Header:* # 🔧 슬랙 나에게 보내기 (공통 서브워크플로우)
    *   *Overview:* 이 워크플로우는 다른 워크플로우에서 알림을 보낼 때 공통적으로 사용할 수 있는 **서브워크플로우**입니다. 메시지 내용과 대상 채널을 입력받아 슬랙으로 전송합니다.
    *   *Input/Output Table:* Use the info from the `stickyNote` node.
    *   *Flow:*
        1. `When Executed by Another Workflow` $\rightarrow$ 2. `Code - 채널 설정` $\rightarrow$ 3. `Slack - 나에게 보내기` $\rightarrow$ 4. `Code - 결과 정리`.
    *   *Configuration:* Mention `DEFAULT_CHANNEL`.