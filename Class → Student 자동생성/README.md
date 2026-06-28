# Class → Student 자동생성

> **Category:** Math4U  
> **Workflow ID:** `PNn3uKuzuOyjgFbu`  
> **노션 메뉴얼:** https://www.notion.so/323c6a06e17e81649c02d5075f8b8945  
> **자동 생성:** Gemini AI  

---

n8n Workflow Expert.
Analyze a provided n8n workflow JSON and write a GitHub `README.md` in Korean.
"Class → Student 자동생성" (Automatic generation of Student records from Class).
PNn3uKuzuOyjgFbu.
Math4U.

        *   `Webhook`: Receives a POST request.
        *   `Code - 입력 파싱`: Extracts `classStudyId` and `datetime` from the webhook body.
        *   `Class_Study Get` (Notion): Fetches details of the specific class study page.
        *   `Split Out - Student ID Split`: Splits the `property_students` (likely a list of students in the class) into individual items.
        *   `Student ID` (Notion): Fetches details for each individual student.
        *   `Edit Fields` (Set): Creates a title for the new page: `[Student Name] | [Class Name]`.
        *   `Create Page Student_Study` (Notion): Creates a new page in the `Student_Study` database, linking it to the student, the class, and the class study record, and setting the date.
        *   `Notion - 배정확인` (Notion): Updates the original `Class_Study` page to check a "배정확인" (Assignment Confirmed) checkbox.
        *   `Set - 성공 데이터` (Set): Prepares a success response.

    *   *Purpose:* When a class is scheduled/created, this workflow automatically generates individual study records for every student enrolled in that class.
    *   *Flow:* Webhook $\rightarrow$ Parse $\rightarrow$ Get Class Info $\rightarrow$ Split Students $\rightarrow$ Get Student Info $\rightarrow$ Format Title $\rightarrow$ Create Student Study Record $\rightarrow$ Mark Class as Processed.

    *   *Title:* # Class → Student 자동생성 (Math4U)
    *   *Overview:* Explain that it automates the creation of individual student study logs based on a class schedule.
    *   *Workflow Steps:*
        1.  **Webhook**: Trigger.
        2.  **Parsing**: Extracting IDs and dates.
        3.  **Class Data Retrieval**: Getting the class details from Notion.
        4.  **Student Splitting**: Converting the list of students into separate items.
        5.  **Student Data Retrieval**: Getting individual student names.
        6.  **Page Creation**: Creating the `Student_Study` record.
        7.  **Completion**: Updating the class record status.
    *   *Requirements:* Notion API Credentials, Database IDs.
    *   *Notes:* Mention the specific database structure (Relations).