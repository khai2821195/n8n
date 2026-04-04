# Alimtalk Sangdam 251201

> **Category:** Math4U  
> **Workflow ID:** `S1ObqqNJYt6Weh0b`  
> **노션 메뉴얼:** https://www.notion.so/323c6a06e17e815ca8a0eeba78761e16  
> **자동 생성:** Gemini AI  

---

# Alimtalk Sangdam 251201

본 워크플로우는 노션(Notion)에 접수된 신규 상담 신청 데이터를 자동으로 감지하여, 알림톡(Alimtalk) 발송 및 슬랙(Slack) 알림을 전송하고 노션 상태를 업데이트하는 자동화 프로세스입니다.

## 🔄 워크플로우 흐름

1.  **Schedule Trigger**: 매 시간마다 워크플로우를 실행하여 신규 상담 신청 건을 확인합니다.
2.  **Notion 신규상담신청 확인**: 'Potential' 데이터베이스에서 '알림톡 발송' 체크박스가 해제된(발송 대상) 데이터를 조회합니다.
3.  **Alimtalk Setting (HTTP Request)**: NHN Cloud 알림톡 API를 호출하여 신청자에게 상담 관련 메시지를 발송합니다.
4.  **Send a message (Slack)**: 슬랙 `#상담신청` 채널에 상담 신청자 정보(이름, 연락처, 상담 내용 등)를 요약하여 알림을 보냅니다.
5.  **Notion Update**: 알림톡 발송이 완료된 건에 대해 노션 데이터베이스의 '알림톡 발송' 체크박스를 체크(True)하여 중복 발송을 방지합니다.
6.  **상태 업데이트**: 워크플로우 실행 성공 여부를 기록합니다.

## ⚙️ 설정 및 환경 변수

워크플로우를 정상적으로 운영하기 위해 다음 항목이 설정되어 있어야 합니다.

*   **Notion**: 
    *   데이터베이스 ID: `229c6a06-e17e-8083-bf21-ec602b6a3033`
    *   필수 속성: `알림톡 발송`(Checkbox), `상담연락처S`(Formula), `생성일`, `상담 희망시간`, `학생이름`, `학교`, `학년`, `상담 내용`
*   **Alimtalk (NHN Cloud)**:
    *   API URL: `https://api-alimtalk.cloud.toast.com/...`
    *   인증 정보: `X-Secret-Key`, `X-App-Key` (HTTP Custom Auth 설정 필요)
    *   Sender Key: `7780249050d98477b04a1b589e4794c8ac1f7a78`
    *   Template Code: `Math4U-edu-2025001`
*   **Slack**:
    *   채널: `#상담신청`

## 🔧 수정 및 유지보수 가이드

*   **상담 신청 조회 조건 변경**: `Notion 신규상담신청 확인` 노드의 Filters 설정을 수정합니다.
*   **알림톡 메시지 수정**: `Alimtalk Setting` 노드의 `jsonBody` 내 `templateCode` 및 메시지 구조를 수정합니다.
*   **슬랙 채널 변경**: `Send a message` 노드의 `channelId`를 수정합니다.
*   **노션 업데이트 필드 추가**: `Notion Update` 노드에서 업데이트할 속성을 추가/변경할 수 있습니다.

## ⚠️ 주의사항

*   **API 호출 제한**: NHN Cloud 알림톡 API 호출 시 `X-Secret-Key`와 `X-App-Key`가 유효한지 주기적으로 확인하십시오.
*   **데이터 형식**: 노션의 `상담연락처S` 속성이 올바른 전화번호 형식(string)으로 반환되는지 확인해야 알림톡 발송 오류를 방지할 수 있습니다.
*   **중복 방지**: `Notion Update` 노드가 정상적으로 작동하지 않을 경우 동일한 고객에게 알림톡이 중복 발송될 수 있으므로, 실행 로그를 주기적으로 모니터링하십시오.