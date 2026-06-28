# 🔧 Alimtalk 발송 (공통 서브워크플로우)

> **Category:** 공통  
> **Workflow ID:** `FKIIXxr7LFVwSUX0`  
> **자동 생성:** Gemini AI  

---

n8n Workflow Expert.
Analyze a provided n8n workflow JSON and create a GitHub `README.md` in Korean.

        *   Name: 🔧 Alimtalk 발송 (공통 서브워크플로우)
        *   ID: FKIIXxr7LFVwSUX0
        *   Category: 공통 (Common/Shared)
        *   Nodes:
            *   `Execute Workflow Trigger`: Entry point for sub-workflows.
            *   `Code - 입력값 검증`: Validates `senderKey`, `templateCode`, and `recipientList`.
            *   `HTTP - 알림톡 발송`: Sends a POST request to NHN Cloud Alimtalk API.
            *   `Code - 결과 정리`: Parses the API response into a simplified success/fail format.
            *   `Sticky Note`: Contains manual/documentation.

        1.  Purpose and operation.
        2.  Node flow (Trigger $\rightarrow$ Process $\rightarrow$ Output).
        3.  Environment variables/Credentials.
        4.  Precautions/Special notes.
        5.  Markdown format.
        6.  Output *only* the README content.

    *   *Purpose:* A reusable sub-workflow to send Kakao Alimtalk messages via NHN Cloud API.
    *   *Input Parameters:*
        *   `senderKey` (String): Kakao channel sender key.
        *   `templateCode` (String): The specific template code for the message.
        *   `recipientList` (Array): List of recipients with their phone numbers and template variables.
    *   *Process:*
        1.  Triggered by another workflow.
        2.  Validates that required inputs are present.
        3.  Calls the NHN Cloud Alimtalk API (`https://api-alimtalk.cloud.toast.com/...`).
        4.  Processes the response to return `isSuccess`, `resultCode`, and `resultMessage`.
    *   *Output:*
        *   `isSuccess` (Boolean)
        *   `resultCode` (String)
        *   `resultMessage` (String)
        *   `raw` (Object): Original API response.

    *   *Title:* 🔧 Alimtalk 발송 (공통 서브워크플로우)
    *   *Description:* This workflow is a shared utility designed to be called by other workflows to send Kakao Alimtalk messages.
    *   *Workflow Flow:*
        1.  **Execute Workflow Trigger**: Receives input from the parent workflow.
        2.  **입력값 검증 (Code)**: Checks if `senderKey`, `templateCode`, and `recipientList` are provided.
        3.  **알림톡 발송 (HTTP Request)**: Sends the data to the Toast (NHN Cloud) Alimtalk API.
        4.  **결과 정리 (Code)**: Normalizes the API response for easy handling by the parent workflow.
    *   *Input/Output Tables:* (Based on the sticky note in the JSON).
    *   *Configuration:* Mention the API keys (X-App-Key, X-Secret-Key) used in the HTTP node.

    *   Ensure professional terminology (e.g., "서브워크플로우", "페이로드", "엔드포인트").
    *   Make sure the formatting is clean and readable.