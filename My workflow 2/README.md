# My workflow 2

> **Category:** 공통  
> **Workflow ID:** `JNjq85FvYhUYjMZL`  
> **자동 생성:** Gemini AI  

---

# AI 회의록 자동 아카이빙 워크플로우

이 워크플로우는 외부에서 전달받은 회의 내용을 자동으로 포맷팅하여 Obsidian(옵시디언) 로컬 볼트에 마크다운 파일로 저장하는 자동화 시스템입니다.

## 📋 워크플로우 목적
- 회의록 작성의 번거로움을 줄이고, 중앙화된 지식 관리 도구인 Obsidian에 즉시 기록을 동기화합니다.
- 날짜별로 정리된 회의록 파일을 자동으로 생성하여 체계적인 기록 관리를 지원합니다.

## ⚙️ 동작 방식 (Node Flow)

1. **Webhook (트리거)**
   - `POST` 방식으로 `ai-meeting-archive` 경로에 데이터를 수신합니다.
   - 외부 AI 서비스나 봇으로부터 회의 내용(`body.text`)을 전달받습니다.

2. **Format & Path Encoding (처리)**
   - 수신된 데이터를 바탕으로 현재 날짜를 추출합니다.
   - Obsidian 내 저장 경로(`1. Projects (프로젝트)/AI Team Project/회의록`)를 설정하고, 파일명을 `YYYY-MM-DD_AI팀_회의록.md` 형식으로 인코딩합니다.
   - 회의록 템플릿(참여자 정보 포함)을 적용하여 마크다운 본문을 생성합니다.

3. **Send to Obsidian (출력)**
   - Obsidian Local REST API를 호출하여 생성된 마크다운 파일을 지정된 경로에 저장합니다.

## 🔑 필수 설정 및 크레덴셜

- **Obsidian Local REST API**: 이 워크플로우는 로컬에서 실행 중인 Obsidian의 [Local REST API](https://github.com/coddingtonbear/obsidian-local-rest-api) 플러그인과 통신합니다.
- **Authorization**: `Send to Obsidian` 노드의 헤더에 설정된 `Bearer` 토큰은 Obsidian Local REST API 설정에서 발급받은 API 키와 일치해야 합니다.
- **포트**: 기본적으로 `http://127.0.0.1:27123`을 사용하므로, Obsidian 플러그인 설정에서 해당 포트가 활성화되어 있는지 확인하십시오.

## ⚠️ 주의사항

- **로컬 환경 실행**: 이 워크플로우는 로컬 네트워크의 Obsidian API를 호출하므로, n8n이 로컬 환경에서 실행 중이거나 Obsidian이 실행 중인 PC와 네트워크 통신이 가능해야 합니다.
- **경로 구조**: Obsidian 볼트 내에 `1. Projects (프로젝트)/AI Team Project/회의록` 폴더가 미리 생성되어 있어야 정상적으로 파일이 저장됩니다.
- **보안**: 코드 내에 하드코딩된 API 토큰은 민감한 정보이므로, 실제 운영 환경에서는 n8n의 **Credentials** 기능을 사용하여 관리하는 것을 권장합니다.