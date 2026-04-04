# n8n Github Sync (노션 메뉴얼 → README)

> **Category:** 공통  
> **Workflow ID:** `gRhv6ri8Nq5sE1Ol`  
> **노션 메뉴얼:** https://www.notion.so/324c6a06e17e81728fb3ccec9d7bae3a  
> **자동 생성:** Gemini AI  

---

# n8n Github Sync (노션 메뉴얼 → README)

이 워크플로우는 n8n에서 관리되는 워크플로우의 상태를 노션(Notion) 데이터베이스와 동기화하고, 각 워크플로우의 정의(JSON)와 문서(README.md)를 GitHub 저장소에 자동으로 백업 및 생성하는 자동화 도구입니다.

## 🔄 워크플로우 개요

본 워크플로우는 n8n의 상태를 주기적으로 확인하여 노션 데이터베이스와 일치시키고, 최신 워크플로우 정보를 GitHub에 반영합니다.

### 전체 흐름
1. **n8n 전체 목록 조회**: 현재 n8n 인스턴스에 존재하는 모든 워크플로우를 가져옵니다.
2. **노션 DB 조회**: 관리 중인 노션 데이터베이스의 워크플로우 목록을 가져옵니다.
3. **동기화 비교**: 
   - n8n에서 삭제되었거나 아카이브된 워크플로우를 노션에서 업데이트합니다.
   - n8n에 새로 추가된 워크플로우를 노션 데이터베이스에 등록합니다.
4. **백업 및 문서화 루프**:
   - 각 워크플로우의 `workflow.json`을 추출하여 GitHub에 저장합니다.
   - 노션에 작성된 메뉴얼을 기반으로 `README.md`를 생성하여 GitHub에 저장합니다.

## 📁 GitHub 폴더 구조

GitHub 저장소는 다음과 같은 구조로 관리됩니다.

```text
workflows/
  워크플로우이름/
    workflow.json    # 워크플로우 설정 파일
    README.md        # 자동 생성된 문서
```

## ⚙️ 환경변수 및 크레덴셜

워크플로우 실행을 위해 다음 환경변수와 API 키 설정이 필요합니다.

*   **`N8N_API_KEY`**: n8n API 접근을 위한 키
*   **`GITHUB_TOKEN`**: GitHub 저장소에 파일을 쓰기 위한 Personal Access Token
*   **`GEMINI_API_KEY`**: README.md 내용 생성을 위한 Gemini API 키
*   **Notion API Key**: 노션 데이터베이스 접근을 위한 Bearer Token (노드 내 설정 확인 필요)

## 🔧 유지보수 가이드

*   **GitHub 저장소 변경**: GitHub API 호출 노드(JSON 저장, README 저장)의 URL 및 헤더 설정을 수정하십시오.
*   **노션 DB 변경**: 노션 조회 및 업데이트 노드 내의 `database_id`를 새로운 데이터베이스 ID로 변경하십시오.
*   **신규 워크플로우 추가**: 노션 데이터베이스에 새로운 항목을 추가하고, 해당 워크플로우의 `Workflow ID`를 정확히 입력하면 다음 실행 시 자동으로 동기화됩니다.

## ⚠️ 주의사항

*   **수동 실행**: 본 워크플로우는 수동 트리거로 설정되어 있습니다. 필요에 따라 `Schedule` 노드를 추가하여 자동화 주기를 설정할 수 있습니다.
*   **API 제한**: 노션 및 GitHub API 호출 시 속도 제한(Rate Limit)에 주의하십시오. 워크플로우 개수가 많을 경우 루프 처리 시 적절한 대기 시간을 고려해야 합니다.
*   **데이터 무결성**: 노션의 `Workflow ID` 컬럼은 n8n의 고유 ID와 일치해야 동기화가 정상적으로 작동합니다.