# Class → Student 자동생성

> **Category:** Math4U  
> **Workflow ID:** `PNn3uKuzuOyjgFbu`  
> **노션 메뉴얼:** https://www.notion.so/323c6a06e17e81649c02d5075f8b8945  
> **자동 생성:** Gemini AI  

---

# 📋 워크플로우: Class → Student 자동생성

## 1. 개요
이 워크플로우는 **Math4U** 시스템의 핵심 자동화 프로세스로, 노션(Notion)의 'Class_Study' 데이터베이스에 수업이 생성되면, 해당 수업에 배정된 학생별로 'Student_Study' 페이지를 자동으로 생성하고 배정 상태를 업데이트하는 역할을 합니다.

## 2. 🔄 전체 흐름
1. **Webhook**: 노션으로부터 수업 생성/수정 이벤트 데이터를 수신합니다.
2. **Code - 입력 파싱**: 수신된 JSON 데이터에서 `classStudyId`와 `수업일정` 정보를 추출합니다.
3. **Class_Study Get**: 추출된 ID를 바탕으로 노션에서 수업 상세 정보를 조회합니다.
4. **Split Out - Student ID Split**: 수업에 연결된 학생 리스트(Relation)를 개별 항목으로 분리합니다.
5. **Student ID (Notion 조회)**: 분리된 각 학생의 상세 정보를 노션에서 조회합니다.
6. **Edit Fields**: 학생 이름과 수업 이름을 조합하여 새로운 페이지 제목을 생성합니다.
7. **Create Page Student_Study**: 'Student_Study' 데이터베이스에 학생별 수업 페이지를 생성하고, 수업일시, 학생, 수업, 수업 상세 정보를 관계형으로 연결합니다.
8. **Notion - 배정확인**: 모든 생성이 완료되면 원본 'Class_Study' 페이지의 '배정확인' 체크박스를 활성화합니다.

## 3. ⚙️ 환경 설정 및 크레덴셜
이 워크플로우를 정상적으로 실행하기 위해 다음 설정이 필요합니다.

*   **Notion Credentials**: 
    *   워크플로우에서 사용하는 노션 데이터베이스에 접근 가능한 API 토큰이 필요합니다.
    *   해당 데이터베이스(Class_Study, Student_Study 등)에 대한 **연결(Connection)** 권한이 부여되어야 합니다.
*   **데이터베이스 ID**:
    *   `Create Page Student_Study` 노드의 `databaseId`가 실제 운영 중인 데이터베이스 ID와 일치하는지 확인하십시오.

## 4. 🔧 수정 및 유지보수
*   **입력 파라미터 변경**: 노션 데이터 구조가 변경될 경우 `Code - 입력 파싱` 노드의 로직을 수정하십시오.
*   **생성 필드 변경**: `Create Page Student_Study` 노드에서 매핑되는 노션 속성(Property)을 필요에 따라 추가하거나 수정할 수 있습니다.
*   **배정확인 로직**: 배정 완료 후 체크박스 외에 다른 상태값 변경이 필요하다면 `Notion - 배정확인` 노드를 수정하십시오.

## 5. ⚠️ 주의사항
*   **Webhook URL**: 노션의 자동화 설정(또는 n8n 연동)에서 Webhook URL이 올바르게 등록되어 있는지 확인하십시오.
*   **데이터 타입**: 노션의 관계형(Relation) 속성이나 날짜(Date) 속성 형식이 변경될 경우, 매핑 노드에서 데이터 형식을 재확인해야 합니다.
*   **에러 처리**: 대량의 학생이 배정된 경우, 노션 API 호출 제한(Rate Limit)이 발생할 수 있으므로 실행 속도를 고려하여 운영하십시오.

---
**작성일**: 2026-03-19
**워크플로우 ID**: `PNn3uKuzuOyjgFbu`