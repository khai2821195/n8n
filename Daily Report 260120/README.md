# Daily Report 260120

> **Category:** Math4U  
> **Workflow ID:** `zQOKALD9EOnl3qhd`  
> **노션 메뉴얼:** https://www.notion.so/323c6a06e17e811fa9f8f05949561409  
> **자동 생성:** Gemini AI  

---

n8n Workflow Expert.
Analyze a provided JSON workflow and write a GitHub `README.md` in Korean.
"Daily Report 260120" (ID: zQOKALD9EOnl3qhd, Category: Math4U).

        *   `Webhook`: Trigger (POST method).
        *   `Notion - Student_Study 재조회`: Gets a specific page from Notion based on the ID from the webhook.
        *   `Notion - Students 조회`: Gets student details (name, parent phone numbers) via a relation from the `Student_Study` page.
        *   `Notion - Class_Study 조회`: Gets class study details via a relation from the `Student_Study` page.
        *   `If - 지난수업 있는지 체크`: Checks if there's a "previous lesson" (지난수업) relation.
        *   `Notion - 지난수업 조회`: If yes, fetches the previous lesson's details.
        *   `Code`: Processes all gathered data (dates, names, phone numbers, lesson content, homework) into a structured format for a report. It prepares a list of recipients (parents) and parameters for a report template.

    *   *Purpose:* Automatically generate and prepare a daily lesson report for parents when a lesson record is updated/created in Notion.
    *   *Flow:* Webhook $\rightarrow$ Fetch Student Study $\rightarrow$ Fetch Student Info $\rightarrow$ Fetch Class Study $\rightarrow$ (Optional) Fetch Previous Lesson $\rightarrow$ Data Processing (JS Code).
    *   *Key Data Points:* Student name, parent contact, lesson date, session number, course, lesson content, previous homework.

    *   *Title:* Daily Report 260120 (Math4U).
    *   *Description:* A workflow that triggers via webhook to collect lesson data from Notion and format it for sending reports to parents.
    *   *Workflow Steps:*
        1.  **Webhook Trigger**: Receives the Notion page ID.
        2.  **Data Retrieval (Notion)**:
            *   Fetches the specific `Student_Study` record.
            *   Fetches the linked `Student` profile (for contact info).
            *   Fetches the linked `Class_Study` record.
        3.  **Conditional Logic**: Checks if a previous lesson exists to retrieve the "Previous Homework" status.
        4.  **Data Transformation (Code Node)**:
            *   Parses dates and days of the week.
            *   Extracts text from Notion's complex property structures (rollups, relations, rich text).
            *   Maps the data to a recipient list (Mother/Father phone numbers).

    *   *Credentials:* Notion API.
    *   *Requirements:* Notion database structure (Students, Student_Study, Class_Study) with specific property names.

    *   Ensure professional tone.
    *   Use clear headings.
    *   Use lists for readability.