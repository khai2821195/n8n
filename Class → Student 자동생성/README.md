# Class → Student 자동생성

> **Category:** Math4U  
> **Workflow ID:** `PNn3uKuzuOyjgFbu`  
> **노션 메뉴얼:** https://www.notion.so/323c6a06e17e81649c02d5075f8b8945  
> **자동 생성:** Gemini AI  

---

# Class → Student 자동생성 워크플로우

## ⚙️ 워크플로우 개요
본 워크플로우는 **Math4U** 시스템의 핵심 자동화 프로세스로, 노션(Notion)의 'Class_Study' 데이터베이스에 수업이 생성되면, 해당 수업에 배정된 학생들을 개별 'Student_Study' 페이지로 자동 생성하고 연결해주는 역할을 합니다.

## 🔄 전체 흐름
1. **Webhook**: 노션 또는 외부 시스템으로부터 수업 생성 이벤트(POST 요청)를 수신합니다.
2. **Code - 입력 파싱**: 수신된 데이터에서 `classStudyId`와 `수업일정` 정보를 추출합니다.
3. **Class_Study Get**: 추출된 ID를 바탕으로 노션에서 해당 수업의 상세 정보를 조회합니다.
4. **Split Out - Student ID Split**: 수업에 배정된 학생 목록(Relation)을 개별 항목으로 분리합니다.
5. **Student ID (Notion 조회)**: 각 학생의 상세 정보를 노션에서 조회합니다.
6. **Edit Fields**: 생성될 페이지의 제목(`학생이름 | 수업명`)을 구성합니다.
7. **Create Page Student_Study**: 'Student_Study' 데이터베이스에 새로운 페이지를 생성하고 수업일시, 학생, 수업 정보를 매핑합니다.
8. **Notion - 배정확인**: 모든 학생의 페이지 생성이 완료되면, 원본 'Class_Study' 페이지의 '배정확인' 체크박스를 활성화합니다.

## 🔧 주요 노드 설정 및 수정 가이드
*   **입력 파라미터**: 데이터 구조 변경 시 `Code - 입력 파싱` 노드의 자바스크립트 코드를 수정하십시오.
*   **Student_Study 생성**: 페이지 생성 필드나 매핑 규칙을 변경하려면 `Create Page Student_Study` 노드의 `propertiesUi`를 수정하십시오.
*   **배정확인 로직**: 배정 완료 후 상태 업데이트가 필요 없는 경우 `Notion - 배정확인` 노드를 비활성화하거나 수정하십시오.

## 📋 환경 설정 및 크레덴셜
*   **Notion Credentials**: 노션 API 접근을 위한 `Integration Token`이 필요합니다.
*   **데이터베이스 ID**: 
    *   `Create Page Student_Study` 노드에 타겟 데이터베이스 ID가 올바르게 설정되어 있는지 확인하십시오.
*   **권한**: 해당 노션 통합(Integration)이 사용 중인 데이터베이스에 '읽기/쓰기' 권한을 가지고 있어야 합니다.

## ⚠️ 주의사항
*   **Relation 데이터**: `Class_Study` 데이터베이스의 `property_students` 필드가 비어있을 경우 워크플로우가 정상적으로 작동하지 않을 수 있습니다.
*   **데이터 형식**: 노션의 날짜 속성(Date) 형식이 변경될 경우 `Code` 노드에서 파싱 로직을 업데이트해야 합니다.
*   **에러 처리**: 대량의 학생이 배정될 경우 API 호출 제한(Rate Limit)이 발생할 수 있으므로, 실행 속도를 고려하여 운영하십시오.

## 📋 변경 이력
*   **2026-03-19**: 워크플로우 최종 업데이트 (성공 데이터 반환 노드 추가)
*   **2025-11-29**: 워크플로우 초기 생성