# Alimtalk Sangdam 251201

> **Category:** Math4U  
> **Workflow ID:** `S1ObqqNJYt6Weh0b`  
> **노션 메뉴얼:** https://www.notion.so/323c6a06e17e815ca8a0eeba78761e16  
> **자동 생성:** Gemini AI  

---

# Alimtalk Sangdam 251201

본 워크플로우는 노션(Notion)에 접수된 신규 상담 신청 데이터를 자동으로 감지하여, 알림톡을 발송하고 슬랙(Slack)으로 알림을 전송한 뒤, 처리 상태를 노션에 업데이트하는 자동화 시스템입니다.

## 🔄 워크플로우 흐름

1.  **Schedule Trigger**: 매시간 정기적으로 워크플로우를 실행합니다.
2.  **Notion 신규상담신청 확인**: 노션 데이터베이스에서 '알림톡 발송' 체크박스가 선택되지 않은 신규 상담 신청 건을 조회합니다.
3.  **If - 신규 상담 있는지**: 조회된 데이터가 있는지 확인하여, 데이터가 있을 경우에만 다음 단계로 진행합니다.
4.  **Alimtalk Setting (HTTP Request)**: NHN Cloud 알림톡 API를 호출하여 신청자에게 상담 접수 알림톡을 발송합니다.
5.  **Send a message (Slack)**: 상담 신청 내용을 정리하여 지정된 슬랙 채널(#상담신청)에 알림 메시지를 전송합니다.
6.  **Notion Update**: 알림톡 발송이 완료된 건의 노션 '알림톡 발송' 체크박스를 체크하여 중복 발송을 방지합니다.

## ⚙️ 환경 설정 및 크레덴셜

워크플로우 정상 작동을 위해 다음 항목이 설정되어 있어야 합니다.

*   **Notion**: 
    *   데이터베이스 연결 권한 및 API 토큰
    *   필수 필드: `알림톡 발송`(Checkbox), `상담연락처S`(Formula), `생성일`(Formula), `학생이름`(Title), `학교`(Rich Text), `학년`(Select), `상담 내용`(Rich Text)
*   **Alimtalk (HTTP Request)**:
    *   `X-Secret-Key`: NHN Cloud API Secret Key
    *   `X-App-Key`: NHN Cloud App Key
*   **Slack**:
    *   워크스페이스 연동 및 채널 접근 권한

## 🔧 수정 및 유지보수 가이드

*   **상담 신청 조회 조건**: 'Notion 신규상담신청 확인' 노드의 필터 설정을 변경하여 조회 기준을 수정할 수 있습니다.
*   **알림톡 템플릿**: 'Alimtalk Setting' 노드의 `jsonBody` 내 `templateCode` 및 메시지 구조를 수정하십시오.
*   **슬랙 알림 채널**: 'Send a message' 노드의 `channelId`를 변경하여 알림을 받을 채널을 수정할 수 있습니다.
*   **노션 업데이트 필드**: 'Notion Update' 노드에서 상태값 변경 외에 추가적인 필드 업데이트가 필요한 경우 속성을 추가하십시오.

## ⚠️ 주의사항

*   **API 호출 제한**: 알림톡 발송 시 NHN Cloud API의 호출 제한(Rate Limit)을 확인하십시오.
*   **데이터 형식**: 노션의 Formula 필드(`상담연락처S`, `생성일`)가 올바른 형식으로 반환되는지 주기적으로 점검하십시오.
*   **에러 핸들링**: 알림톡 발송 실패 시 슬랙 알림이 가지 않거나 노션 업데이트가 누락될 수 있으므로, 필요시 Error Trigger를 추가하여 모니터링하는 것을 권장합니다.