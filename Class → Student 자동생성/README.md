# Class → Student 자동생성

> **Category:** Math4U  
> **Workflow ID:** `PNn3uKuzuOyjgFbu`  
> **노션 메뉴얼:** https://www.notion.so/323c6a06e17e81649c02d5075f8b8945  
> **자동 생성:** Gemini AI  

---

n8n Workflow Expert.
Analyze provided JSON and write a GitHub `README.md` in Korean.
"Class → Student 자동생성" (Automatic generation of Student records from Class).
PNn3uKuzuOyjgFbu.
Math4U.

        *   `Webhook`: Trigger (POST).
        *   `Code - 입력 파싱`: Extracts `classStudyId` and `datetime` from the webhook body.
        *   `Class_Study Get` (Notion): Fetches details of the class study page using the ID.
        *   `Split Out - Student ID Split`: Splits the list of students (`property_students`) into individual items.
        *   `Student ID` (Notion): Fetches details for each student page.
        *   `Edit Fields` (Set): Creates a title for the new page: `Student Name | Class Name`.
        *   `Create Page Student_Study` (Notion): Creates a new page in the `Student_Study` database, linking it to the student, the class, and the class study record, and setting the date.
        *   `Notion - 배정확인` (Notion): Updates the original `Class_Study` page to check the "배정확인" (Assignment Confirmation) checkbox.
        *   `Set - 성공 데이터` (Set): Prepares a success response.

    *   *Purpose:* When a class study is scheduled/triggered, automatically create individual study records for every student enrolled in that class.
    *   *Flow:* Webhook $\rightarrow$ Parse $\rightarrow$ Get Class $\rightarrow$ Split Students $\rightarrow$ Get Student Info $\rightarrow$ Create Student Study Record $\rightarrow$ Mark Class as Processed.

    *   *Title:* # Class → Student 자동생성 (Math4U)
    *   *Description:* Notion 기반의 수업 관리 시스템에서 '수업(Class Study)' 정보가 생성되었을 때, 해당 수업에 배정된 '학생(Student)'별로 개별 학습 기록을 자동으로 생성하는 워크플로우입니다.
    *   *Workflow Diagram/Steps:*
        1.  **Webhook**: 외부 신호 수신.
        2.  **입력 파싱**: 필요한 ID와 날짜 추출.
        3.  **수업 정보 조회**: Notion에서 수업 상세 데이터 가져오기.
        4.  **학생 리스트 분리**: 다수의 학생을 개별 항목으로 분리.
        5.  **학생 정보 조회**: 각 학생의 이름 등 상세 정보 가져오기.
        6.  **데이터 가공**: 페이지 제목 생성 (`학생명 | 수업명`).
        7.  **학생 학습 기록 생성**: `Student_Study` 데이터베이스에 새 페이지 생성 및 관계 설정.
        8.  **처리 완료 표시**: 원본 수업 페이지의 '배정확인' 체크박스 업데이트.
    *   *Requirements:* Notion API Credentials, Database IDs.
    *   *Notes:* Relation fields must be correctly mapped.

    *   Ensure professional tone.
    *   Use clear headings.
    *   Check for technical accuracy based on the JSON.