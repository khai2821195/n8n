# My workflow 2

> **Category:** 공통  
> **Workflow ID:** `JNjq85FvYhUYjMZL`  
> **자동 생성:** Gemini AI  

---

n8n Workflow Expert.
Analyze the provided JSON and write a GitHub `README.md` in Korean.

        *   Name: My workflow 2
        *   ID: JNjq85FvYhUYjMZL
        *   Category: Common
        *   Nodes:
            1.  `Webhook` (POST, path: `ai-meeting-archive`): Trigger.
            2.  `Format & Path Encoding` (Code node):
                *   Gets current date.
                *   Extracts text from `body.text`.
                *   Defines folder path: `1. Projects (프로젝트)/AI Team Project/회의록`.
                *   Encodes path and filename (`YYYY-MM-DD_AI팀_회의록.md`).
                *   Formats content as Markdown (Title, Participants: Kai, Cheryl, C-Levels, Content).
                *   Outputs `apiUrl` (Obsidian Local REST API format) and `markdown` content.
            3.  `Send to Obsidian` (HTTP Request):
                *   Method: PUT.
                *   URL: `{{$json.apiUrl}}`.
                *   Header: `Authorization: Bearer [token]`.
                *   Body: `{{$json.markdown}}` (text/markdown).

        1.  Purpose and operation.
        2.  Node flow (Trigger $\rightarrow$ Process $\rightarrow$ Output).
        3.  Environment variables/Credentials.
        4.  Precautions/Special notes.
        5.  Markdown format.
        6.  Output *only* the README.md content.

    *   *Title:* AI Team Meeting Archive Workflow (AI 팀 회의록 자동 저장 워크플로우).
    *   *Purpose:* Automatically receive meeting notes via webhook and save them as Markdown files in a specific Obsidian vault folder.
    *   *Workflow Flow:*
        1.  **Webhook**: Receives a POST request containing meeting text.
        2.  **Code Node**: Formats the date, encodes the Obsidian folder path, and structures the Markdown content.
        3.  **HTTP Request**: Sends the formatted content to the Obsidian Local REST API using a PUT method.

    *   *Requirements:*
        *   Obsidian Local REST API plugin installed.
        *   API Token.
        *   Local server accessible by n8n (127.0.0.1:27123).

    *   *Precautions:*
        *   The local IP `127.0.0.1` suggests n8n and Obsidian are on the same machine or in a network where this is reachable.
        *   The folder path must exist or be supported by the API.

    *   Use clear headings.
    *   Use emojis for readability.
    *   Ensure technical terms are used correctly.