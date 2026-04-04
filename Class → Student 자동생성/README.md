# Class → Student 자동생성

> **Category:** Math4U  
> **Workflow ID:** `PNn3uKuzuOyjgFbu`  
> **노션 메뉴얼:** https://www.notion.so/323c6a06e17e81649c02d5075f8b8945  
> **자동 생성:** Gemini AI  

---

# Class → Student 자동생성 워크플로우

## ⚙️ 워크플로우 개요
본 워크플로우는 **Math4U** 시스템의 핵심 자동화 프로세스로, 노션(Notion)의 'Class_Study' 데이터베이스에 수업이 생성될 때, 해당 수업에 배정된 학생들을 자동으로 추출하여 'Student_Study' 데이터베이스에 개별 학습 페이지를 생성하고 배정 상태를 업데이트하는 역할을 합니다.

## 🔄 전체 흐름
1. **Webhook**: 노션 또는 외부 시스템으로부터 수업 생성 이벤트(POST)를 수신합니다.
2. **Code - 입력 파싱**: 수신된 데이터에서 `classStudyId`와 `수업일정` 정보를 추출합니다.
3. **Class_Study Get**: 노션에서 해당 수업 페이지의 상세 정보를 조회합니다.
4. **Split Out - Student ID Split**: 수업에 연결된 학생 리스트(`property_students`)를 개별 항목으로 분리합니다.
5. **Student ID (Notion 조회)**: 각 학생의 상세 정보를 노션에서 조회합니다.
6. **Edit Fields**: 학생 이름과 수업 이름을 조합하여 새로운 페이지 제목을 생성합니다.
7. **Create Page Student_Study**: 'Student_Study' 데이터베이스에 수업일시, 학생, 수업 정보를 포함한 새 페이지를 생성합니다.
8. **Notion - 배정확인**: 모든 학생의 생성이 완료되면, 원본 'Class_Study' 페이지의 '배정확인' 체크박스를 활성화합니다.

## 🔧 주요 설정 및 수정 가이드
*   **입력 파라미터**: 데이터 구조 변경 시 `Code - 입력 파싱` 노드의 JavaScript 코드를 수정하십시오.
*   **Student_Study 생성 필드**: 생성되는 페이지의 속성값 변경이 필요할 경우 `Create Page Student_Study` 노드의 `propertiesUi`를 수정하십시오.
*   **배정확인 로직**: 배정 완료 후 상태 업데이트 방식 변경 시 `Notion - 배정확인` 노드를 수정하십시오.

## 📋 환경 설정 및 크레덴셜
*   **Notion Credentials**: 노션 API 접근을 위한 `Integration Token`이 필요합니다.
*   **Database ID**: 워크플로우 내 각 노드에서 참조하는 데이터베이스 ID가 실제 노션 페이지와 일치하는지 확인하십시오.
    *   `Create Page Student_Study` 노드의 `databaseId`
    *   각 조회 노드의 `pageId`

## ⚠️ 주의사항
*   **데이터 형식**: 노션 데이터베이스의 속성 이름(예: `수업일정`, `Students`, `Class` 등)이 변경되면 워크플로우 내 노드 설정도 함께 업데이트해야 합니다.
*   **관계형 속성**: 학생과 수업 간의 관계형(Relation) 속성이 올바르게 매핑되어 있는지 주기적으로 확인하십시오.
*   **Webhook 보안**: Webhook URL이 외부에 노출되지 않도록 관리하십시오.

## 📋 변경 이력
*   **2025-11-29**: 워크플로우 최초 생성
*   **2026-03-19**: 로직 최적화 및 성공 데이터 리턴 노드 추가