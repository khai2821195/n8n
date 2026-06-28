# Class → Student 자동생성

> **Category:** Math4U  
> **Workflow ID:** `PNn3uKuzuOyjgFbu`  
> **노션 메뉴얼:** https://www.notion.so/323c6a06e17e81649c02d5075f8b8945  
> **자동 생성:** Gemini AI  

---

n8n Workflow Expert.
Analyze a provided n8n workflow JSON and write a GitHub `README.md` in Korean.
"Class → Student 자동생성" (Class to Student Auto-generation).
PNn3uKuzuOyjgFbu.
Math4U.

        1.  `Webhook`: Trigger (POST).
        2.  `Code - 입력 파싱`: Extracts `classStudyId` and `datetime` from the webhook body.
        3.  `Class_Study Get` (Notion): Fetches details of the class study page using the ID.
        4.  `Split Out - Student ID Split`: Splits the `property_students` array (likely a list of student IDs linked to the class).
        5.  `Student ID` (Notion): Fetches individual student page details.
        6.  `Edit Fields` (Set): Creates a title for the new page: `[Student Name] | [Class Name]`.
        7.  `Create Page Student_Study` (Notion): Creates a new entry in the `Student_Study` database, linking the date, student, class, and class study.
        8.  `Notion - 배정확인` (Notion): Updates the original `Class_Study` page to check a "배정확인" (Assignment Confirmed) checkbox.
        9.  `Set - 성공 데이터` (Set): Prepares a success response.

    *   *Purpose:* Automatically create individual student study records when a class study is scheduled/triggered.
    *   *Logic:* Webhook $\rightarrow$ Parse $\rightarrow$ Get Class Info $\rightarrow$ Loop through Students $\rightarrow$ Create Student Study Record $\rightarrow$ Mark Class as Processed.

    *   *Title:* # Class → Student 자동생성 워크플로우
    *   *Description:* This workflow automates the process of generating individual student study records from a single class study entry in Notion.
    *   *Workflow Flow:*
        1.  **Webhook**: Receives the trigger.
        2.  **Parsing**: Extracts necessary IDs and dates.
        3.  **Class Data Retrieval**: Gets class details from Notion.
        4.  **Student Iteration**: Splits the student list and iterates.
        5.  **Student Data Retrieval**: Gets specific student names.
        6.  **Record Creation**: Creates a new page in the `Student_Study` database.
        7.  **Status Update**: Marks the class study as "Assignment Confirmed".
    *   *Requirements:* Notion API Credentials, Database IDs.
    *   *Notes:* Mention the specific Notion database structure (relations).