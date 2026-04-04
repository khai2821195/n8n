# 🔧 Alimtalk 발송 (공통 서브워크플로우)

> **Category:** 공통  
> **Workflow ID:** `FKIIXxr7LFVwSUX0`  
> **자동 생성:** Gemini AI  

---

# 🔧 알림톡 발송 (공통 서브워크플로우)

본 워크플로우는 n8n에서 카카오 알림톡 발송을 표준화하기 위해 설계된 **공통 서브워크플로우**입니다. 다른 메인 워크플로우에서 `Execute Workflow` 노드를 통해 호출하여 재사용할 수 있도록 제작되었습니다.

---

## 📋 워크플로우 개요
- **ID**: `FKIIXxr7LFVwSUX0`
- **목적**: 카카오 알림톡 API를 호출하여 메시지를 발송하고, 그 결과를 표준화된 형식으로 반환합니다.
- **카테고리**: 공통

## ⚙️ 동작 방식
1. **Execute Workflow Trigger**: 메인 워크플로우로부터 발송에 필요한 데이터를 전달받습니다.
2. **Code - 입력값 검증**: 전달받은 `senderKey`, `templateCode`, `recipientList`의 유효성을 검사합니다. 데이터가 누락된 경우 에러를 발생시켜 워크플로우를 중단합니다.
3. **HTTP - 알림톡 발송**: NHN Cloud 알림톡 API를 호출하여 메시지를 발송합니다.
4. **Code - 결과 정리**: API 응답을 파싱하여 성공 여부(`isSuccess`), 결과 코드(`resultCode`), 메시지(`resultMessage`)를 포함한 JSON 객체를 반환합니다.

## 📥 입력 데이터 형식
메인 워크플로우에서 호출 시 아래와 같은 JSON 구조를 전달해야 합니다.

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

## 📤 출력 데이터 형식
```json
{
  "isSuccess": true,
  "resultCode": "SUCCESS",
  "resultMessage": "성공",
  "raw": { ... }
}
```

## 🔑 환경 설정 및 크레덴셜
- **API URL**: `https://api-alimtalk.cloud.toast.com/alimtalk/v2.0/appkeys/{{AppKey}}/messages`
- **헤더 설정**:
    - `X-Secret-Key`: NHN Cloud Secret Key
    - `X-App-Key`: NHN Cloud App Key
    - `Content-Type`: `application/json;charset=UTF-8`

## ⚠️ 주의사항
- **데이터 검증**: `recipientList`는 반드시 배열 형태여야 하며, 비어있을 경우 워크플로우가 실패 처리됩니다.
- **재사용성**: 본 워크플로우는 독립적으로 실행되지 않으며, 반드시 `Execute Workflow` 노드를 통해 호출되어야 합니다.
- **API 제한**: NHN Cloud 알림톡 API 정책에 따라 발송 요청 횟수 및 템플릿 승인 여부를 사전에 확인하십시오.

## 🚀 사용 중인 워크플로우
- Daily Report 260120
- Alimtalk Sangdam 251201