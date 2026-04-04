# 🔧 Alimtalk 발송 (공통 서브워크플로우)

> **Category:** 공통  
> **Workflow ID:** `FKIIXxr7LFVwSUX0`  
> **자동 생성:** Gemini AI  

---

# 🔧 알림톡 발송 공통 서브워크플로우

본 워크플로우는 n8n 내에서 카카오 알림톡 발송 기능을 표준화하여 재사용하기 위한 **공통 서브워크플로우**입니다. `Execute Workflow` 노드를 통해 호출하여 다양한 메인 워크플로우에서 알림톡을 간편하게 발송할 수 있습니다.

---

## 📋 워크플로우 개요
- **ID**: `FKIIXxr7LFVwSUX0`
- **목적**: 카카오 알림톡 API 연동을 통한 메시지 발송 자동화
- **방식**: 외부 호출(Execute Workflow)을 통한 파라미터 전달 및 결과 반환

## ⚙️ 동작 흐름
1. **Execute Workflow Trigger**: 메인 워크플로우로부터 발송에 필요한 데이터를 수신합니다.
2. **Code - 입력값 검증**: 전달받은 `senderKey`, `templateCode`, `recipientList`의 유효성을 검사합니다. 데이터가 누락되었을 경우 에러를 발생시켜 프로세스를 중단합니다.
3. **HTTP - 알림톡 발송**: 검증된 데이터를 바탕으로 NHN Cloud 알림톡 API를 호출합니다.
4. **Code - 결과 정리**: API 응답을 파싱하여 성공 여부(`isSuccess`), 결과 코드(`resultCode`), 메시지(`resultMessage`)를 표준화된 형태로 반환합니다.

## 📥 입력 파라미터 (Input)
메인 워크플로우에서 호출 시 아래 JSON 구조를 전달해야 합니다.

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

## 📤 출력 결과 (Output)
호출한 워크플로우는 다음과 같은 결과를 반환받습니다.
- `isSuccess` (boolean): 발송 성공 여부
- `resultCode` (string): API 응답 코드
- `resultMessage` (string): API 응답 메시지

## 🔑 환경 설정 및 크레덴셜
- **API URL**: NHN Cloud 알림톡 API (v2.0)
- **헤더 정보**:
    - `X-Secret-Key`: 발송 인증을 위한 시크릿 키
    - `X-App-Key`: 앱 키
- **인증 방식**: HTTP Custom Auth 설정이 필요합니다.

## ⚠️ 주의사항
- `recipientList`는 반드시 배열 형태여야 하며, 최소 1개 이상의 수신자 정보가 포함되어야 합니다.
- API 호출 시 `Content-Type`은 `application/json;charset=UTF-8`로 고정되어 있습니다.
- 본 워크플로우는 공통 모듈이므로 수정 시 이를 사용하는 모든 메인 워크플로우에 영향을 줄 수 있습니다. 변경 전 의존성을 확인하시기 바랍니다.

## 🚀 사용 중인 워크플로우
- Daily Report 260120
- Alimtalk Sangdam 251201