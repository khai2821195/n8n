# Daily Report 260120

> **Category:** Math4U  
> **Workflow ID:** `zQOKALD9EOnl3qhd`  
> **노션 메뉴얼:** https://www.notion.so/323c6a06e17e811fa9f8f05949561409  
> **자동 생성:** Gemini AI  

---

n8n Workflow Expert.
Analyze the provided JSON and write a GitHub `README.md` in Korean.
"Daily Report 260120" (Category: Math4U).

        *   `Webhook`: Trigger (POST).
        *   `Notion - Student_Study 재조회`: Gets specific page data using the ID from the webhook.
        *   `Notion - Students 조회`: Gets student details (name, parent phone numbers) via relation.
        *   `Notion - Class_Study 조회`: Gets class study details via relation.
        *   `If - 지난수업 있는지 체크`: Checks if there's a "previous class" relation.
        *   `Notion - 지난수업 조회`: If yes, gets the previous class data (specifically for homework).
        *   `Code`: Processes all gathered data (dates, names, phone numbers, course info, content, homework) into a formatted object for reporting.

        *   Purpose/Operation.
        *   Node flow (Trigger $\rightarrow$ Process $\rightarrow$ Output).
        *   Environment variables/Credentials.
        *   Precautions/Special notes.
        *   Markdown format.
        *   *Output only the README.md content.*

    *   *Purpose:* This workflow automates the generation of a daily study report for students. When a webhook is triggered (likely from a Notion update or a specific action), it gathers data from multiple Notion databases (Student, Student_Study, Class_Study) and prepares a report to be sent to parents.
    *   *Flow:*
        1.  **Webhook**: Receives the Notion page ID.
        2.  **Notion (Student_Study)**: Fetches the specific study session record.
        3.  **Notion (Students)**: Fetches the student's profile (name, parent contact).
        4.  **Notion (Class_Study)**: Fetches the overall class context.
        5.  **Conditional Logic**: Checks if there was a previous session to retrieve the "previous homework" status.
        6.  **Code Node**: Formats the raw Notion data into a human-readable report format (dates, days of the week, etc.) and maps it to the parents' phone numbers.

    *   *Title:* Daily Report 260120 (Math4U)
    *   *Description:* 자동 일일 학습 보고서 생성 워크플로우. (Automated daily study report generation workflow).
    *   *Key Features:* Notion integration, relational data fetching, dynamic date formatting, parent notification preparation.
    *   *Detailed Flow:*
        *   Webhook $\rightarrow$ Student_Study $\rightarrow$ Students $\rightarrow$ Class_Study $\rightarrow$ (If) $\rightarrow$ Previous Class $\rightarrow$ Code.
    *   *Credentials:* Notion API Key.

    *   Ensure professional tone.
    *   Use clear headings.
    *   Highlight the logic in the `Code` node (date parsing, phone number mapping).