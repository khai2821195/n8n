# My workflow 2

> **Category:** 공통  
> **Workflow ID:** `JNjq85FvYhUYjMZL`  
> **자동 생성:** Gemini AI  

---

# AI팀 회의록 자동화 워크플로우

이 워크플로우는 외부에서 전달받은 회의 내용을 자동으로 포맷팅하여 Obsidian(옵시디언)의 특정 폴더에 마크다운 파일로 저장하는 자동화 시스템입니다.

## 📋 워크플로우 개요
- **목적**: 회의록 작성의 번거로움을 줄이고, Obsidian을 활용한 지식 관리 효율화
- **동작 방식**: Webhook을 통해 데이터를 수신하고, 날짜별 파일명 생성 및 마크다운 템플릿을 적용하여 Obsidian Local REST API로 전송

## ⚙️ 노드 흐름
1. **Webhook (트리거)**
   - `POST` 요청을 통해 회의록 본문(`text`)을 수신합니다.
   - 엔드포인트: `/ai-meeting-archive`
2. **Format & Path Encoding (데이터 처리)**
   - 수신된 데이터를 바탕으로 현재 날짜(`YYYY-MM-DD`)를 추출합니다.
   - 지정된 경로(`1. Projects (프로젝트)/AI Team Project/회의록`)와 파일명(`날짜_AI팀_회의록.md`)을 인코딩합니다.
   - 회의록 마크다운 템플릿(참여자 정보 포함)을 구성합니다.
3. **Send to Obsidian (출력)**
   - Obsidian Local REST API를 호출하여 생성된 마크다운 파일을 저장합니다.

## 🔑 필수 설정 및 크레덴셜
- **Obsidian Local REST API**: Obsidian 내에 해당 플러그인이 설치되어 있어야 하며, 로컬 서버(기본값: `127.0.0.1:27123`)가 실행 중이어야 합니다.
- **Authorization**: `Send to Obsidian` 노드의 HTTP Header에 `Bearer [API_KEY]` 형식으로 인증 토큰이 설정되어 있습니다. (현재 설정된 토큰값 확인 필요)

## ⚠️ 주의사항
- **로컬 환경 의존성**: 본 워크플로우는 `127.0.0.1`을 대상으로 하므로, n8n이 Obsidian이 설치된 로컬 머신과 동일한 네트워크 환경(또는 로컬에서 실행 중)이어야 합니다.
- **경로 설정**: Obsidian Vault 내의 폴더 구조가 `1. Projects (프로젝트)/AI Team Project/회의록`과 일치해야 정상적으로 파일이 생성됩니다.
- **보안**: 코드 내에 하드코딩된 API Key는 보안상 위험할 수 있으므로, 실제 운영 환경에서는 n8n의 **Credentials** 기능을 사용하여 관리하는 것을 권장합니다.

## 💡 사용 방법
1. Webhook URL을 확인합니다.
2. 아래와 같은 JSON 형식으로 POST 요청을 보냅니다:
   ```json
   {
     "body": {
       "text": "회의 내용 입력"
     }
   }
   ```
3. Obsidian의 지정된 경로에 자동으로 생성된 회의록 파일을 확인합니다.