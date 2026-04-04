# 🔧 Alimtalk 발송 (공통 서브워크플로우)

> **Category:** 공통  
> **Workflow ID:** `FKIIXxr7LFVwSUX0`  
> **자동 생성:** Gemini AI  

---

# 🔧 알림톡 발송 (공통 서브워크플로우)

본 워크플로우는 n8n 내에서 카카오 알림톡 발송 기능을 표준화하여 재사용하기 위한 **공통 서브워크플로우**입니다. `Execute Workflow` 노드를 통해 호출하여 다양한 메인 워크플로우에서 알림톡을 간편하게 발송할 수 있습니다.

---

## 📋 워크플로우 개요
- **ID**: `FKIIXxr7LFVwSUX0`
- **목적**: 카카오 알림톡 API 연동을 통한 메시지 발송 자동화
- **특징**: 입력값 검증, API 요청, 결과 정규화 과정을 포함한 표준화된 프로세스 제공

---

## ⚙️ 동작 방식 (Node Flow)

1. **Execute Workflow Trigger**: 메인 워크플로우로부터 발송에 필요한 데이터를 전달받습니다.
2. **Code - 입력값 검증**: 필수 파라미터(`senderKey`, `templateCode`, `recipientList`)가 누락되지 않았는지 확인합니다.
3. **HTTP - 알림톡 발송**: NHN Cloud 알림톡 API를 호출하여 실제 메시지를 발송합니다.
4. **Code - 결과 정리**: API 응답을 분석하여 성공 여부와 결과 메시지를 표준화된 포맷으로 반환합니다.

---

## 📥 입력 데이터 (Input)
호출 시 아래와 같은 JSON 객체를 전달해야 합니다.

```json
{
  "senderKey": "카카오 채널 발신 키",
  "templateCode": "알림톡 템플릿 코드",
  "recipientList": [
    {
      "recipientNo": "010-1234-5678",
      "templateParameter": {
        "변수명": "값"
      }
    }
  ]
}
```

---

## 📤 출력 데이터 (Output)
워크플로우 실행 후 반환되는 결과값입니다.

| 필드 | 타입 | 설명 |
| :--- | :--- | :--- |
| `isSuccess` | boolean | 발송 성공 여부 |
| `resultCode` | string | API 응답 코드 |
| `resultMessage` | string | API 응답 메시지 |

---

## ⚠️ 주의사항 및 환경 설정

- **인증 정보**: 본 워크플로우는 NHN Cloud 알림톡 API를 사용합니다.
    - `X-Secret-Key` 및 `X-App-Key`가 HTTP 노드 헤더에 설정되어 있습니다.
    - 보안을 위해 해당 키값이 변경될 경우 HTTP 노드의 헤더 설정을 업데이트해야 합니다.
- **데이터 형식**: `recipientList`는 반드시 배열 형태여야 하며, `templateParameter`는 템플릿에 정의된 변수명과 일치해야 합니다.
- **에러 처리**: 필수 입력값이 누락된 경우 워크플로우가 즉시 중단되고 에러를 발생시킵니다. 호출하는 메인 워크플로우에서 에러 핸들링(Error Trigger 등)을 고려하십시오.

---

## 🔗 사용 중인 워크플로우
- Daily Report 260120
- Alimtalk Sangdam 251201