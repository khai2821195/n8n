# n8n Github Sync (노션 메뉴얼 → README)

> **Category:** 공통  
> **Workflow ID:** `gRhv6ri8Nq5sE1Ol`  
> **노션 메뉴얼:** https://www.notion.so/324c6a06e17e81728fb3ccec9d7bae3a  
> **자동 생성:** Gemini AI  

---

# n8n Github Sync (노션 메뉴얼 → README)

이 워크플로우는 n8n에서 관리되는 워크플로우의 상태를 노션(Notion) 데이터베이스와 동기화하고, 각 워크플로우의 설정 파일(`workflow.json`)과 문서(`README.md`)를 GitHub 저장소에 자동으로 백업 및 생성하는 자동화 도구입니다.

## 🔄 워크플로우 동작 방식

1.  **n8n 목록 조회**: n8n API를 통해 현재 서버에 존재하는 모든 워크플로우 목록을 가져옵니다.
2.  **노션 DB 비교**: 노션 데이터베이스에 기록된 워크플로우 ID와 비교하여 동기화 상태를 확인합니다.
    *   **삭제**: n8n에서 아카이브되었거나 삭제된 워크플로우를 노션에서 처리합니다.
    *   **추가**: 새로 생성된 활성 워크플로우를 노션 DB에 등록합니다.
3.  **백업 및 문서화 루프**:
    *   **JSON 백업**: 각 워크플로우의 `workflow.json` 파일을 추출하여 GitHub에 저장합니다.
    *   **README 생성**: 노션에 작성된 메뉴얼 내용을 바탕으로 Gemini AI를 활용하여 `README.md`를 생성하고 GitHub에 커밋합니다.

## 📁 GitHub 폴더 구조

워크플로우 데이터는 GitHub 저장소 내에 다음과 같은 구조로 저장됩니다.

```text
workflows/
  워크플로우이름/
    workflow.json    # 워크플로우 설정 파일
    README.md        # 자동 생성된 문서
```

## ⚙️ 필수 환경변수 및 크레덴셜

워크플로우 실행을 위해 다음 환경변수와 API 키 설정이 필요합니다.

*   `N8N_API_KEY`: n8n API 접근을 위한 인증 키
*   `GITHUB_TOKEN`: GitHub 저장소에 파일을 쓰기 위한 Personal Access Token
*   `GEMINI_API_KEY`: README.md 문서 자동 생성을 위한 Google Gemini API 키
*   **Notion API Key**: 노션 데이터베이스 읽기/쓰기를 위한 통합(Integration) 토큰

## 🔧 유지보수 가이드

*   **GitHub 저장소 변경**: 각 HTTP Request 노드의 URL 및 API 호출 경로를 수정하십시오.
*   **노션 DB 변경**: 노션 데이터베이스 ID가 변경될 경우, '노션 DB 조회' 및 '노션 아카이브 WF 삭제' 노드의 URL 내 데이터베이스 ID 값을 업데이트해야 합니다.
*   **새 워크플로우 추가**: 노션 DB에 수동으로 항목을 추가하고 `Workflow ID` 컬럼을 정확히 입력하면 다음 실행 시 자동으로 동기화됩니다.

## ⚠️ 주의사항

*   이 워크플로우는 수동 실행(Manual Trigger)을 기본으로 설계되었습니다.
*   노션 API 호출 시 사용하는 `Bearer Token`은 보안을 위해 환경변수로 관리하는 것을 권장합니다.
*   GitHub에 파일이 이미 존재하는 경우, `SHA` 값을 통한 업데이트 로직이 포함되어 있으므로 API 호출 시 해당 경로의 파일 존재 여부를 확인하십시오.