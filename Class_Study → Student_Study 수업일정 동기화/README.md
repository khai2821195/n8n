# Class_Study → Student_Study 수업일정 동기화

> **Category:** 공통  
> **Workflow ID:** `G5k8fgeviVCR8ixe`  
> **자동 생성:** Gemini AI  

---

# Class_Study → Student_Study 수업일정 동기화

본 워크플로우는 Notion의 `Class_Study` 데이터베이스에서 수업 일정이 변경될 때, 연결된 `Student_Study` 데이터베이스의 수업 일시를 자동으로 동기화하기 위해 설계되었습니다.

## 1. 워크플로우 목적
*   `Class_Study` 데이터베이스의 '수업일정' 속성 변경을 감지합니다.
*   해당 수업에 연결된 모든 학생(`Student_Study`)의 '수업일시' 속성을 최신 정보로 자동 업데이트합니다.
*   수동 작업 없이 데이터 일관성을 유지하여 운영 효율성을 높입니다.

## 2. 노드 흐름 설명
1.  **Class_Study 변경 감지 (Notion Trigger)**: `Class_Study` 데이터베이스의 페이지 업데이트를 1분 단위로 폴링하여 감지합니다.
2.  **수업일정 및 학생ID 추출 (Code)**: 변경된 페이지에서 '수업일정' 날짜와 연결된 'Student_Study' 관계형 ID들을 추출합니다. 데이터가 없거나 연결된 학생이 없는 경우 스킵 처리합니다.
3.  **업데이트 필요 여부 (If)**: 추출된 데이터가 유효한지 확인하여, 업데이트가 필요한 경우에만 다음 단계로 진행합니다.
4.  **Student_Study 수업일시 업데이트 (Notion)**: 추출된 각 학생 페이지의 '수업일시' 속성을 `Class_Study`의 날짜로 업데이트합니다.
5.  **상태 업데이트 (Execute Workflow)**: 작업 성공 시, 별도의 상태 관리 워크플로우를 호출하여 성공 로그를 기록합니다.
6.  **에러 감지 (Error Trigger)**: 워크플로우 실행 중 오류 발생 시, 에러 로그를 기록하는 별도 워크플로우를 호출합니다.

## 3. 필수 설정 및 크레덴셜
*   **Notion Credentials**: `Class_Study` 및 `Student_Study` 데이터베이스에 접근 가능한 API 토큰이 필요합니다.
*   **데이터베이스 연결**:
    *   `Class_Study` 데이터베이스 내에 '수업일정'(Date 타입)과 'Student_Study'(Relation 타입) 속성이 존재해야 합니다.
    *   `Student_Study` 데이터베이스 내에 '수업일시'(Date 타입) 속성이 존재해야 합니다.
*   **워크플로우 호출**: 성공/실패 상태 업데이트를 위해 연결된 하위 워크플로우(ID: `eOopB5bbEEO9rjrg` 등)가 활성화되어 있어야 합니다.

## 4. 주의사항
*   **폴링 간격**: 현재 1분 단위로 설정되어 있습니다. Notion API 사용량에 따라 폴링 간격을 조정하십시오.
*   **데이터 타입**: Notion 속성 이름이 변경될 경우, '수업일정 및 학생ID 추출' 노드의 코드 내 속성 키(`properties?.['수업일정']`)를 동일하게 수정해야 합니다.
*   **관계형 데이터**: `Student_Study` 관계가 설정되어 있지 않은 `Class_Study` 페이지는 자동으로 스킵됩니다.

## 5. 워크플로우 정보
*   **Workflow ID**: `G5k8fgeviVCR8ixe`
*   **카테고리**: 공통