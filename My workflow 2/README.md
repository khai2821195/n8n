# My workflow 2

> **Category:** 공통  
> **Workflow ID:** `JNjq85FvYhUYjMZL`  
> **자동 생성:** Gemini AI  

---

# AI팀 회의록 자동화 워크플로우 (Obsidian 연동)

이 워크플로우는 외부에서 전달받은 회의 내용을 자동으로 포맷팅하여 Obsidian Vault에 마크다운 파일로 저장하는 자동화 시스템입니다.

## 📋 워크플로우 개요
- **목적**: 회의록을 수동으로 작성할 필요 없이, 웹훅을 통해 데이터를 전송하면 지정된 Obsidian 폴더에 날짜별로 자동 저장합니다.
- **동작 방식**: HTTP POST 요청으로 회의 내용을 수신 → 마크다운 형식으로 변환 → Obsidian Local REST API를 통해 파일 생성/업데이트.

## ⚙️ 노드 흐름
1. **Webhook**: `POST` 방식으로 `/ai-meeting-archive` 엔드포인트를 통해 데이터를 수신합니다.
2. **Format & Path Encoding**: 
   - 수신된 데이터를 바탕으로 현재 날짜(`YYYY-MM-DD`)를 생성합니다.
   - 회의록 템플릿을 적용하고, 파일명과 경로를 URL 인코딩하여 Obsidian API 규격에 맞게 변환합니다.
3. **Send to Obsidian**: 변환된 데이터를 Obsidian Local REST API로 전송하여 최종적으로 `.md` 파일을 생성합니다.

## 🔑 필수 설정 및 환경 변수
- **Obsidian Local REST API**: 이 워크플로우는 Obsidian 내에 [Local REST API](https://github.com/coddingtonbear/obsidian-local-rest-api) 플러그인이 설치되어 있어야 정상 작동합니다.
- **Authorization**: `Send to Obsidian` 노드의 헤더에 설정된 `Bearer` 토큰은 Obsidian Local REST API 설정에서 발급받은 API Key와 일치해야 합니다.
- **로컬 주소**: 현재 `http://127.0.0.1:27123`으로 설정되어 있으므로, n8n이 Obsidian이 실행 중인 로컬 환경과 통신 가능한 상태여야 합니다.

## ⚠️ 주의사항
- **경로 설정**: `Format & Path Encoding` 노드 내 `folderPath` 변수가 실제 Obsidian Vault 내의 경로와 일치하는지 확인하십시오.
- **데이터 구조**: Webhook으로 들어오는 JSON 데이터의 `body.text` 필드에 회의 내용이 포함되어 있어야 합니다.
- **보안**: API Key가 포함되어 있으므로 워크플로우 공유 시 해당 정보를 노출하지 않도록 주의하십시오.

## 📝 데이터 예시 (Webhook 요청)
```json
{
  "body": {
    "text": "오늘 회의 내용입니다..."
  }
}
```