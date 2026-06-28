# 🔧 슬랙 나에게 보내기 (공통 서브워크플로우)

> **Category:** 공통  
> **Workflow ID:** `L2oRzJDV57Rf8pcr`  
> **자동 생성:** Gemini AI  

---

n8n Workflow Expert.
Analyze a provided JSON workflow and create a GitHub `README.md` in Korean.
"🔧 슬랙 나에게 보내기 (공통 서브워크플로우)" (Slack Send to Me - Common Sub-workflow).
`L2oRzJDV57Rf8pcr`.
Common.

        *   `When Executed by Another Workflow` (Trigger): Receives `text` and `channel`.
        *   `Code - 채널 설정` (Logic): Validates `text`, sets a default channel (`U07J6D9J5L6`) if `channel` is not provided.
        *   `Slack - 나에게 보내기` (Action): Sends the message to the determined channel.
        *   `Code - 결과 정리` (Logic): Formats the output (`isSuccess`, `channel`, `ts`).
        *   `Sticky Note`: Provides a manual for users.

        1.  Clear purpose and operation.
        2.  Sequential node flow (Trigger $\rightarrow$ Process $\rightarrow$ Output).
        3.  Environment variables/Credentials requirements.
        4.  Cautions/Special notes.
        5.  Markdown format.
        6.  Output *only* the README.md content.

    *   *Title:* 🔧 슬랙 나에게 보내기 (공통 서브워크플로우)
    *   *Description:* This is a reusable sub-workflow designed to send notifications to a specific Slack user or channel. It's meant to be called by other workflows using the "Execute Workflow" node.
    *   *Input Parameters:*
        *   `text` (Required): The message content.
        *   `channel` (Optional): Slack Channel/User ID.
    *   *Workflow Steps:*
        1.  **Trigger:** Receives data from a parent workflow.
        2.  **Channel Setup (Code):** Checks for `text`. If `channel` is missing, it uses a hardcoded default ID.
        3.  **Slack Send:** Uses the Slack API to post the message.
        4.  **Result Formatting (Code):** Returns a clean success/failure status.
    *   *Setup/Requirements:*
        *   Slack Credentials (OAuth2 or Bot Token).
        *   Update `DEFAULT_CHANNEL` in the Code node.
    *   *Output:* `isSuccess`, `channel`, `ts`.

    *   *Header:* # 🔧 슬랙 나에게 보내기 (공통 서브워크플로우)
    *   *Introduction:* 이 워크플로우는 다른 메인 워크플로우에서 호출하여 사용할 수 있는 **공통 서브워크플로우**입니다. 알림이나 로그를 슬랙의 특정 채널 또는 나에게 간편하게 보낼 때 사용합니다.
    *   *Input Table:* (As seen in the sticky note).
    *   *Flow Description:*
        1.  `When Executed by Another Workflow`: 부모 워크플로우로부터 메시지 내용과 채널 정보를 전달받습니다.
        2.  `Code - 채널 설정`: 입력값 검증 및 기본 채널 설정을 수행합니다.
        3.  `Slack - 나에게 보내기`: 설정된 채널로 메시지를 전송합니다.
        4.  `Code - 결과 정리`: 전송 결과(성공 여부, 채널 ID 등)를 정리하여 반환합니다.
    *   *Configuration:*
        *   Slack API Credentials 필요.
        *   `Code - 채널 설정` 노드의 `DEFAULT_CHANNEL` 변수를 본인의 슬랙 멤버 ID로 수정해야 합니다.
    *   *Output:* `isSuccess`, `channel`, `ts`.