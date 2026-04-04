# My workflow 2

> **Category:** 공통  
> **Workflow ID:** `JNjq85FvYhUYjMZL`  
> **자동 생성:** Gemini AI  

---

# AI팀 회의록 자동화 워크플로우 (Obsidian 연동)

이 워크플로우는 외부에서 전달받은 회의 내용을 자동으로 포맷팅하여 Obsidian(옵시디언)의 특정 폴더에 마크다운 파일로 저장하는 자동화 시스템입니다.

## 📋 워크플로우 개요
- **목적**: 회의록을 수동으로 작성할 필요 없이, 웹훅을 통해 데이터를 전송하면 정해진 양식에 맞춰 Obsidian 볼트에 저장합니다.
- **동작 방식**: HTTP POST 요청으로 들어온 텍스트 데이터를 받아 날짜별 파일명으로 변환 후, Obsidian Local REST API를 통해 저장합니다.

## 🔄 노드 흐름
1. **Webhook (트리거)**: `POST /ai-meeting-archive` 엔드포인트로 들어오는 요청을 수신합니다.
2. **Format & Path Encoding (데이터 처리)**: 
   - 현재 날짜를 기반으로 파일명을 생성합니다.
   - 수신된 본문을 지정된 마크다운 템플릿(참여자 정보 포함)으로 변환합니다.
   - Obsidian 경로 및 파일명을 URL 인코딩하여 처리합니다.
3. **Send to Obsidian (출력)**: Obsidian Local REST API를 호출하여 변환된 마크다운 내용을 지정된 경로에 파일로 생성(PUT)합니다.

## ⚙️ 설정 및 요구사항

### 1. 환경 변수 및 크레덴셜
- **Obsidian Local REST API**: 이 워크플로우는 Obsidian 내에 `Obsidian Local REST API` 플러그인이 설치되어 있어야 하며, 해당 플러그인의 API 키가 필요합니다.
- **Authorization**: `Send to Obsidian` 노드의 헤더에 `Bearer <YOUR_API_KEY>` 형식으로 설정되어 있습니다.

### 2. 경로 설정
- 현재 회의록은 `1. Projects (프로젝트)/AI Team Project/회의록` 폴더에 저장되도록 설정되어 있습니다. 환경에 맞게 `Format & Path Encoding` 노드의 `folderPath` 변수를 수정하여 사용하세요.

## ⚠️ 주의사항
- **로컬 환경**: `127.0.0.1:27123` 주소를 사용하므로, n8n이 Obsidian이 실행 중인 로컬 머신과 동일한 네트워크(또는 로컬 환경)에서 구동되어야 합니다.
- **API 키 보안**: 워크플로우 내에 하드코딩된 API 키는 보안상 위험할 수 있으므로, n8n의 **Credentials** 기능을 사용하여 관리하는 것을 권장합니다.
- **데이터 형식**: 웹훅으로 데이터를 보낼 때 `body.text` 필드에 회의 내용을 담아 전송해야 정상적으로 처리됩니다.