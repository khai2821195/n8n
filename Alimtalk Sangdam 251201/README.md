# Alimtalk Sangdam 251201

> **Category:** Math4U  
> **Workflow ID:** `S1ObqqNJYt6Weh0b`  
> **노션 메뉴얼:** https://www.notion.so/323c6a06e17e815ca8a0eeba78761e16  
> **자동 생성:** Gemini AI  

---

# Alimtalk Sangdam 251201

본 워크플로우는 노션(Notion)에 접수된 신규 상담 신청 데이터를 자동으로 감지하여, 알림톡(Alimtalk) 발송 및 슬랙(Slack) 알림을 전송하고 노션 상태를 업데이트하는 자동화 프로세스입니다.

## 🔄 워크플로우 흐름

1.  **Schedule Trigger**: 매 시간마다 워크플로우가 자동으로 실행됩니다.
2.  **Notion 신규상담신청 확인**: 노션 데이터베이스에서 '알림톡 발송' 체크박스가 선택되지 않은(또는 조건에 맞는) 신규 상담 신청 건을 조회합니다.
3.  **Alimtalk Setting (HTTP Request)**: NHN Cloud 알림톡 API를 호출하여 신청자에게 상담 접수 알림톡을 발송합니다.
4.  **Send a message (Slack)**: 상담 신청 내용을 슬랙 `#상담신청` 채널로 전송하여 담당자가 즉시 확인할 수 있도록 합니다.
5.  **Notion Update**: 알림톡 발송이 완료된 건에 대해 노션의 '알림톡 발송' 체크박스를 `true`로 업데이트하여 중복 발송을 방지합니다.
6.  **✅ 상태 업데이트 (성공)**: 워크플로우 실행 결과를 기록합니다.

## ⚙️ 주요 설정 및 환경변수

워크플로우 운영을 위해 다음 항목들이 설정되어 있어야 합니다.

*   **Notion**:
    *   데이터베이스 ID: `229c6a06-e17e-8083-bf21-ec602b6a3033`
    *   필수 속성: `알림톡 발송`(Checkbox), `상담연락처S`(Formula), `생성일`, `학생이름`, `학교`, `학년`, `상담 내용`
*   **Alimtalk (NHN Cloud)**:
    *   API URL: `https://api-alimtalk.cloud.toast.com/alimtalk/v2.0/appkeys/YuIB1lEDj8vuqME2/messages`
    *   Headers: `X-Secret-Key`, `X-App-Key`
    *   Template Code: `Math4U-edu-2025001`
*   **Slack**:
    *   채널: `#상담신청`

## 🔧 수정 및 유지보수 가이드

*   **상담 신청 조회 조건 변경**: `Notion 신규상담신청 확인` 노드의 `Filters` 설정을 수정하세요.
*   **알림톡 메시지 내용 변경**: `Alimtalk Setting` 노드의 `jsonBody` 내 `templateCode` 및 메시지 구조를 수정하세요.
*   **슬랙 알림 채널 변경**: `Send a message` 노드의 `channelId`를 수정하세요.
*   **노션 업데이트 필드 추가**: `Notion Update` 노드의 `propertiesUi`에서 업데이트할 속성을 추가/수정하세요.

## ⚠️ 주의사항

*   **API 크레덴셜**: NHN Cloud 및 Slack 연동을 위한 크레덴셜이 n8n에 올바르게 등록되어 있는지 확인하십시오.
*   **데이터 형식**: 노션의 속성 이름이 변경될 경우, 각 노드에서 참조하고 있는 `properties['이름']` 경로를 함께 업데이트해야 합니다.
*   **중복 방지**: 노션 업데이트 노드가 정상적으로 작동하지 않으면 동일한 고객에게 알림톡이 중복 발송될 수 있으므로, 실행 로그를 주기적으로 확인하십시오.