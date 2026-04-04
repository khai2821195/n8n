# 📚 Math4U - 수업 리포트 자동화 (Thinking Flow)

> **Category:** 공통  
> **Workflow ID:** `fLXAn8mq5xsr5GNE`  
> **자동 생성:** Gemini AI  

---

# 📚 Math4U - 수업 리포트 자동화 (The Thinking Flow)

본 워크플로우는 대치 Math4U 수학학원의 수업 리포트 작성 및 발송 과정을 자동화하여, 강사의 업무 효율을 높이고 학부모에게 고품질의 'The Thinking Flow(사고의 궤적)' 리포트를 제공하기 위해 설계되었습니다.

## 🎯 워크플로우 목적
강사가 모바일 폼을 통해 수업 내용을 입력하면, n8n이 이를 분석하여 AI(Gemini)를 통해 전문적인 리포트를 생성하고, 학부모에게 카카오알림톡으로 즉시 발송하며, 해당 이력을 Notion에 자동으로 기록합니다.

## 🔄 워크플로우 단계
1. **📱 폼 데이터 수신 (Webhook)**: Google Forms 또는 Tally 등에서 제출된 수업 데이터를 실시간으로 수신합니다.
2. **📊 데이터 파싱**: 수신된 데이터를 정제하여 학생 이름, 수업 날짜, 사고력 지표(Discovery, Generalization, Concentration), 유레카 모먼트 등을 추출합니다.
3. **🔍 Notion 학생 조회**: Notion 데이터베이스에서 학생 이름을 기준으로 학부모 연락처 및 학생 상세 정보를 조회합니다.
4. **🤖 AI 리포트 생성**: Gemini API를 호출하여 입력된 데이터를 바탕으로 '대치 Math4U 프리미엄' 톤앤매너에 맞춘 수업 리포트 문장을 생성합니다.
5. **💬 알림톡 발송**: 생성된 리포트를 학부모에게 카카오알림톡으로 발송합니다.
6. **📝 Notion 기록**: 발송된 리포트 내용을 Notion 데이터베이스에 저장하여 수업 이력을 관리합니다.
7. **🔔 Slack 알림**: 강사(카이)에게 발송 완료 알림을 전송하여 업무 처리를 확인합니다.

## ⚙️ 환경 설정 및 요구사항
워크플로우를 정상적으로 실행하기 위해 다음 환경변수와 크레덴셜 설정이 필요합니다.

### 환경변수 (Environment Variables)
- `GEMINI_API_KEY`: AI 리포트 생성을 위한 Google Gemini API 키

### 크레덴셜 (Credentials)
- **Notion API**: 학생 정보 조회 및 리포트 기록을 위한 Notion 연동 권한
- **Webhook**: 폼 데이터 수신을 위한 엔드포인트 설정
- **KakaoTalk API**: 알림톡 발송을 위한 서비스 연동 (별도 설정 필요)
- **Slack API**: 발송 완료 알림을 위한 Slack Webhook 또는 앱 연동

## ⚠️ 주의사항
- **데이터 매핑**: Notion 데이터베이스의 속성명(`학생이름|title` 등)이 워크플로우 내 노드 설정과 일치하는지 확인하십시오.
- **Webhook URL**: 모바일 폼(Google Forms/Tally)의 제출 완료 페이지 또는 연동 설정에서 본 워크플로우의 Webhook URL을 정확히 입력해야 합니다.
- **API 제한**: Gemini API 사용량 및 카카오알림톡 발송 건수에 따른 비용 발생 여부를 주기적으로 확인하시기 바랍니다.

---
*본 워크플로우는 Math4U의 수업 관리 효율화를 위해 최적화된 'Thinking Flow' 자동화 시스템입니다.*