# 🔧 Alimtalk 발송 (공통 서브워크플로우)

> **Category:** 공통  
> **Workflow ID:** `FKIIXxr7LFVwSUX0`  
> **자동 생성:** Gemini AI  

---

# 🔧 알림톡 발송 공통 서브워크플로우

본 워크플로우는 n8n에서 카카오 알림톡 발송 기능을 표준화하여 재사용하기 위한 **공통 서브워크플로우**입니다. `Execute Workflow` 노드를 통해 다른 워크플로우에서 호출하여 사용할 수 있습니다.

---

## 📋 워크플로우 개요
- **목적**: 카카오 알림톡 API를 호출하여 메시지를 발송하고, 결과를 표준화된 형식으로 반환합니다.
- **카테고리**: 공통 (Common)
- **ID**: `FKIIXxr7LFVwSUX0`

---

## ⚙️ 동작 방식 (Node Flow)

1. **Execute Workflow Trigger**: 상위 워크플로우로부터 데이터를 전달받습니다.
2. **Code - 입력값 검증**: 필수 파라미터(`senderKey`, `templateCode`, `recipientList`)가 누락되지 않았는지 검증합니다.
3. **HTTP - 알림톡 발송**: NHN Cloud 알림톡 API를 호출하여 메시지를 발송합니다.
4. **Code - 결과 정리**: API 응답을 파싱하여 성공 여부(`isSuccess`)와 결과 코드/메시지를 정리하여 반환합니다.

---

## 📥 입력 데이터 (Input)
상위 워크플로우에서 `Execute Workflow` 노드 설정 시 아래 데이터를 전달해야 합니다.

| 필드 | 타입 | 설명 |
| :--- | :--- | :--- |
| `senderKey` | string | 카카오 채널 발신 키 |
| `templateCode` | string | 알림톡 템플릿 코드 |
| `recipientList` | array | 수신자 목록 |

**recipientList 형식 예시:**
```json
[
  {
    "recipientNo": "010-1234-5678",
    "templateParameter": {
      "변수명": "값"
    }
  }
]
```

---

## 📤 출력 데이터 (Output)
워크플로우 실행 후 반환되는 결과값입니다.

- `isSuccess`: 발송 성공 여부 (boolean)
- `resultCode`: API 응답 코드
- `resultMessage`: API 응답 메시지
- `raw`: API 원본 응답 데이터

---

## ⚠️ 주의사항 및 설정
- **인증 정보**: `HTTP - 알림톡 발송` 노드에서 `X-Secret-Key` 및 `X-App-Key`가 설정되어 있습니다. 환경 변경 시 해당 헤더 값을 확인하십시오.
- **API 엔드포인트**: 현재 NHN Cloud 알림톡 API(`https://api-alimtalk.cloud.toast.com/...`)를 사용 중입니다.
- **사용 중인 워크플로우**:
    - Daily Report 260120
    - Alimtalk Sangdam 251201

---

## 🛠 수정 및 유지보수
- 입력값 검증 로직이나 API 응답 처리 방식 변경 시 `Code` 노드를 수정하십시오.
- 새로운 템플릿 추가 시 `recipientList`의 `templateParameter` 구조가 템플릿과 일치하는지 확인하십시오.