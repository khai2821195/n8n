# My workflow 2

> **Category:** 공통  
> **Workflow ID:** `JNjq85FvYhUYjMZL`  
> **자동 생성:** Gemini AI  

---

n8n Workflow Expert.
Analyze a provided n8n workflow JSON and write a GitHub `README.md` in Korean.

        *   Name: My workflow 2
        *   ID: JNjq85FvYhUYjMZL
        *   Category: Common
        *   Nodes:
            1.  `Webhook`: POST method, path `ai-meeting-archive`.
            2.  `Format & Path Encoding` (Code node):
                *   Gets current date.
                *   Gets text from `body.text`.
                *   Defines folder path: `1. Projects (프로젝트)/AI Team Project/회의록`.
                *   Encodes path and filename (`YYYY-MM-DD_AI팀_회의록.md`).
                *   Formats content as a Markdown header with participants (Kai, Cheryl, C-Levels).
                *   Outputs `apiUrl` (pointing to a local Obsidian REST API: `http://127.0.0.1:27123/vault/...`) and `markdown` content.
            3.  `Send to Obsidian` (HTTP Request node):
                *   Method: PUT.
                *   URL: `{{$json.apiUrl}}`.
                *   Header: `Authorization: Bearer [token]`.
                *   Body: `{{$json.markdown}}` (text/markdown).

        1.  Purpose and operation logic.
        2.  Node flow (Trigger $\rightarrow$ Process $\rightarrow$ Output).
        3.  Environment variables/Credentials.
        4.  Precautions/Special notes.
        5.  Markdown format.
        6.  Output *only* the README.md content.

    *   *Title:* AI Meeting Minutes Auto-Archiving Workflow (AI 팀 회의록 자동 저장 워크플로우).
    *   *Purpose:* Automatically receive meeting notes via webhook and save them as formatted Markdown files in an Obsidian vault.
    *   *Flow:*
        1.  Webhook (Entry point) $\rightarrow$ Receives meeting text.
        2.  Code Node (Formatting) $\rightarrow$ Generates date, encodes path, formats Markdown.
        3.  HTTP Request (Storage) $\rightarrow$ Sends data to Obsidian Local REST API.
    *   *Requirements:*
        *   Obsidian Local REST API plugin installed.
        *   API Token.
        *   Specific folder structure in Obsidian.

    *   *Header:* # AI 팀 회의록 자동 저장 워크플로우
    *   *Description:* 이 워크플로우는 외부에서 전달된 회의록 텍스트를 받아 정해진 형식의 마크다운 파일로 변환한 뒤, Obsidian(옵시디언) 노트에 자동으로 저장하는 자동화 프로세스입니다.
    *   *Workflow Steps:*
        1.  **Webhook**: `POST /ai-meeting-archive` 경로로 회의 내용(`text`)을 수신합니다.
        2.  **Format & Path Encoding**:
            *   현재 날짜를 기준으로 파일명을 생성합니다.
            *   Obsidian 내 저장 경로(`1. Projects (프로젝트)/AI Team Project/회의록`)를 URL 인코딩합니다.
            *   참여자 정보(카이, 셰릴, C-Levels)가 포함된 마크다운 템플릿을 적용합니다.
        3.  **Send to Obsidian**: Obsidian Local REST API를 통해 생성된 파일을 지정된 경로에 `PUT` 요청으로 저장합니다.
    *   *Setup/Credentials:*
        *   `Authorization`: Bearer Token (Obsidian Local REST API 설정에서 발급).
        *   `Obsidian API URL`: `http://127.0.0.1:27123` (로컬 환경 기준).
    *   *Notes:*
        *   Obsidian Local REST API 플러그인이 설치되어 있어야 합니다.
        *   지정된 폴더 경로가 Obsidian 보관소(Vault) 내에 미리 존재해야 합니다.