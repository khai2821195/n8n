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
            2.  `Format & Path Encoding` (Code Node):
                *   Gets current date.
                *   Extracts `text` from the webhook body.
                *   Defines a folder path: `1. Projects (프로젝트)/AI Team Project/회의록`.
                *   Encodes the path and filename (`YYYY-MM-DD_AI팀_회의록.md`).
                *   Formats the content as a Markdown file with a header and participants (Kai, Cheryl, C-Levels).
                *   Outputs `apiUrl` (pointing to a local Obsidian REST API: `http://127.0.0.1:27123/vault/...`) and `markdown` content.
            3.  `Send to Obsidian` (HTTP Request Node):
                *   Method: PUT.
                *   URL: `{{$json.apiUrl}}`.
                *   Header: `Authorization: Bearer [token]`.
                *   Body: `{{$json.markdown}}` (text/markdown).

        1.  Clear purpose and behavior.
        2.  Step-by-step node flow (Trigger $\rightarrow$ Process $\rightarrow$ Output).
        3.  Environment variables/Credentials requirements.
        4.  Precautions/Special notes.
        5.  Markdown format.
        6.  Output *only* the README content.

    *   *Title:* AI Meeting Minutes Auto-Archiving Workflow (AI 팀 회의록 자동 저장 워크플로우).
    *   *Purpose:* Automatically receive meeting notes via Webhook and save them as Markdown files in a specific Obsidian vault folder.
    *   *Flow:*
        1.  **Webhook**: Receives the meeting text.
        2.  **Code Node**: Formats the date, creates the file path, and structures the Markdown content.
        3.  **HTTP Request**: Sends the data to the Obsidian Local REST API.
    *   *Requirements:*
        *   Obsidian Local REST API plugin installed and running.
        *   API Token for authentication.
        *   Local network access (since it uses `127.0.0.1`).

    *   *Header:* # AI 팀 회의록 자동 저장 워크플로우 (AI Meeting Archive)
    *   *Description:* 이 워크플로우는 외부에서 전달받은 회의록 텍스트를 정해진 형식의 마크다운 파일로 변환하여 Obsidian(옵시디언) 보관소에 자동으로 저장하는 자동화 프로세스입니다.
    *   *Workflow Steps:*
        1.  **Webhook (Trigger)**: `POST /ai-meeting-archive` 경로로 회의록 데이터 수신.
        2.  **Format & Path Encoding (Processing)**:
            *   현재 날짜 기반 파일명 생성 (`YYYY-MM-DD_AI팀_회의록.md`).
            *   Obsidian 저장 경로 인코딩 (`1. Projects (프로젝트)/AI Team Project/회의록`).
            *   마크다운 템플릿 적용 (참여자 정보 및 본문 구성).
        3.  **Send to Obsidian (Output)**: Obsidian Local REST API를 통해 `PUT` 요청을 보내 파일 생성 및 저장.
    *   *Setup/Requirements:*
        *   **Obsidian Local REST API**: 옵시디언 내에 해당 플러그인이 설치되어 있어야 하며, 서버가 활성화 상태여야 합니다.
        *   **API Token**: `Authorization` 헤더에 사용할 Bearer 토큰이 필요합니다.
        *   **Network**: n8n 서버가 옵시디언이 설치된 로컬 PC(`127.0.0.1`)에 접근 가능해야 합니다. (Docker 사용 시 `host.docker.internal` 등으로 수정 필요할 수 있음).
    *   *Notes:*
        *   파일 경로에 한글 및 특수문자가 포함되어 있어 `encodeURIComponent`를 통해 처리되었습니다.
        *   기본 저장 경로는 `1. Projects (프로젝트)/AI Team Project/회의록`으로 설정되어 있습니다.