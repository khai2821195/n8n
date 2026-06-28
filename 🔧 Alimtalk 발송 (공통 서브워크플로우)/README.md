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
        *   `Code - 입력값 검증` (Input Validation): Checks for `senderKey`, `templateCode`, and `recipientList`. Throws errors if missing.
        *   `HTTP - 알림톡 발송` (HTTP Request): Sends a POST request to NHN Cloud Alimtalk API (`api-alimtalk.cloud.toast.com`). Uses custom headers (`X-Secret-Key`, `X-App-Key`).
        *   `Code - 결과 정리` (Result Formatting): Parses the API response to return `isSuccess`, `resultCode`, and `resultMessage`.
        *   `Sticky Note`: Provides a manual for input/output and lists dependent workflows.

    *   *Purpose:* A reusable sub-workflow to send Kakao Alimtalk messages via NHN Cloud API.
    *   *Input:* `senderKey`, `templateCode`, `recipientList` (array of objects with `recipientNo` and `templateParameter`).
    *   *Output:* `isSuccess`, `resultCode`, `resultMessage`.
    *   *Dependencies:* NHN Cloud Alimtalk API.

    *   *Title:* 🔧 Alimtalk 발송 (공통 서브워크플로우)
    *   *Description:* This workflow is designed as a common module to be called by other workflows to send Kakao Alimtalk messages.
    *   *Workflow Flow:*
        1.  `Execute Workflow Trigger`: Receives data from the parent workflow.
        2.  `Code - 입력값 검증`: Validates mandatory fields.
        3.  `HTTP - 알림톡 발송`: Calls the NHN Cloud API.
        4.  `Code - 결과 정리`: Simplifies the API response for the parent workflow.
    *   *Input/Output Tables:* (Based on the sticky note in the JSON).
    *   *Configuration:* Mention the API URL and Header keys.
    *   *Usage:* Mention the "Execute Workflow" node.