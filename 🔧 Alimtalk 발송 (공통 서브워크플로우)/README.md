# 🔧 Alimtalk 발송 (공통 서브워크플로우)

> **Category:** 공통  
> **Workflow ID:** `FKIIXxr7LFVwSUX0`  
> **자동 생성:** Gemini AI  

---

n8n Workflow Expert.
Analyze the provided JSON and write a GitHub `README.md` in Korean.
"🔧 Alimtalk 발송 (공통 서브워크플로우)" (Alimtalk Sending - Common Sub-workflow).
`FKIIXxr7LFVwSUX0`.
Common.

        *   `Execute Workflow Trigger`: Entry point for other workflows.
        *   `Code - 입력값 검증`: Validates `senderKey`, `templateCode`, and `recipientList`.
        *   `HTTP - 알림톡 발송`: Sends a POST request to NHN Cloud Alimtalk API.
        *   `Code - 결과 정리`: Parses the API response into a standardized format (`isSuccess`, `resultCode`, `resultMessage`).
        *   `Sticky Note`: Contains manual/documentation for inputs and outputs.

        *   Input: `senderKey`, `templateCode`, `recipientList` (array of objects with `recipientNo` and `templateParameter`).
        *   Output: `isSuccess`, `resultCode`, `resultMessage`.
        *   API Endpoint: `https://api-alimtalk.cloud.toast.com/alimtalk/v2.0/appkeys/YuIB1lEDj8vuqME2/messages`.
        *   Headers: `Content-Type`, `X-Secret-Key`, `X-App-Key`.

    *   *Title:* 🔧 Alimtalk 발송 (공통 서브워크플로우)
    *   *Description:* A reusable sub-workflow to send Kakao Alimtalk messages via NHN Cloud API.
    *   *Workflow Flow:*
        1.  Trigger (Execute Workflow)
        2.  Input Validation (JS Code)
        3.  API Request (HTTP Request)
        4.  Response Formatting (JS Code)
    *   *Input Parameters:* Table format as seen in the sticky note.
    *   *Output Parameters:* Table format.
    *   *Configuration/Credentials:* Mention the API keys (X-App-Key, X-Secret-Key).
    *   *Usage Example:* JSON example for `recipientList`.

    *   Ensure professional and clear Korean.
    *   Use Markdown formatting (tables, code blocks, lists).
    *   Follow the user's specific rules (no intro/outro, just the README content).