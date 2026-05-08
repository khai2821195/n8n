# AEGIS Pro 무료 체험 자동화

> **Category:** 공통  
> **Workflow ID:** `57LNfEjxyVpYIVvi`  
> **자동 생성:** Gemini AI  

---

# AEGIS Pro 무료 체험 자동화 워크플로우

본 워크플로우는 사용자가 노션(Notion) 데이터베이스를 통해 AEGIS Pro 무료 체험을 신청하면, 이를 자동으로 감지하여 Supabase를 통해 Pro 권한을 활성화하고 노션 상태를 업데이트하는 자동화 시스템입니다.

## 📋 워크플로우 개요
- **목적**: AEGIS Pro 체험 신청 프로세스 자동화
- **트리거**: 노션 데이터베이스 신규 항목 감지 (1분 주기)
- **주요 기능**: 
    - Supabase Edge Function 호출을 통한 Pro 권한 활성화
    - 처리 결과에 따른 노션 데이터베이스 상태 자동 업데이트 (성공/오류)
    - Pro 적용 시 시작일 및 만료일(30일 후) 자동 기록

## 🔄 워크플로우 흐름
1. **노션 신청 감지 (Notion Trigger)**: 지정된 노션 데이터베이스에서 새로운 신청 건을 1분마다 확인합니다.
2. **Supabase Pro 활성화 + 알림 (HTTP Request)**: 신청자의 정보(ID, 이메일, 이름)를 Supabase Edge Function으로 전송하여 Pro 권한을 활성화합니다.
3. **성공 여부 확인 (IF)**: Supabase로부터 받은 응답의 `success` 필드를 확인합니다.
4. **결과 처리**:
    - **성공 시**: 노션 페이지의 상태를 'Pro 적용됨'으로 변경하고, 시작일과 30일 후의 만료일을 기록합니다.
    - **오류 시**: 노션 페이지의 상태를 '오류'로 변경하고, 상세 오류 메시지를 메모란에 기록합니다.

## ⚙️ 설정 및 요구사항

### 1. 크레덴셜 (Credentials)
- **Notion API**: 데이터베이스 접근 권한이 있는 API 토큰이 필요합니다.
- **Supabase**: Edge Function 호출을 위한 권한 설정이 필요합니다.

### 2. 환경 변수 및 설정
- **Supabase Webhook Secret**: `x-webhook-secret` 헤더 값으로 `aegis-pro-trial-2026`이 설정되어 있습니다.
- **노션 데이터베이스 스키마**: 다음 필드가 데이터베이스에 존재해야 합니다.
    - `AEGIS ID` (Text)
    - `이메일` (Email)
    - `이름` (Text)
    - `상태` (Select: 'Pro 적용됨', '오류' 포함)
    - `Pro 시작일` (Date)
    - `Pro 만료일` (Date)
    - `메모` (Rich Text)

## ⚠️ 주의사항
- **폴링 주기**: 현재 1분 단위로 노션을 확인합니다. API 호출 횟수 제한을 고려하여 필요 시 조정하십시오.
- **데이터 형식**: 노션 데이터베이스의 필드명과 워크플로우 내 노드 설정이 일치하는지 확인하십시오.
- **보안**: `x-webhook-secret` 값은 Supabase Edge Function 측의 보안 설정과 일치해야 합니다. 외부로 노출되지 않도록 주의하십시오.