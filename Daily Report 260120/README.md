# Daily Report 260120

> **Category:** Math4U  
> **Workflow ID:** `zQOKALD9EOnl3qhd`  
> **노션 메뉴얼:** https://www.notion.so/323c6a06e17e811fa9f8f05949561409  
> **자동 생성:** Gemini AI  

---

n8n Workflow Expert.
Analyze provided JSON and write a GitHub `README.md` in Korean.
"Daily Report 260120", ID: `zQOKALD9EOnl3qhd`, Category: `Math4U`.

        *   `Webhook`: Trigger (POST request).
        *   `Notion - Student_Study 재조회`: Fetches a specific page from a Notion database using the ID from the webhook.
        *   `Notion - Students 조회`: Fetches student details (name, phone numbers) based on a relation in the `Student_Study` page.
        *   `Notion - Class_Study 조회`: Fetches class details based on a relation in the `Student_Study` page.
        *   `If - 지난수업 있는지 체크`: Checks if there is a "previous class" (지난수업) relation.
        *   `Notion - 지난수업 조회`: If yes, fetches the previous class page to get the "homework" (과제) info.
        *   `Code`: Processes all gathered data (dates, names, phone numbers, course info, content, homework) and prepares a list of recipients (parents) and parameters for a report.

    *   *Purpose:* Automate the generation and sending of daily study reports to parents.
    *   *Trigger:* An external webhook (likely from a Notion automation or a form).
    *   *Data Flow:* Webhook $\rightarrow$ Notion (Study Record) $\rightarrow$ Notion (Student Info) $\rightarrow$ Notion (Class Info) $\rightarrow$ (Optional) Notion (Previous Class Info) $\rightarrow$ JavaScript Data Processing.
    *   *Key Output:* A structured list of recipients (parents' phone numbers) and report parameters (student name, date, course, content, previous homework).

    *   *Title:* Daily Report 260120 (Math4U).
    *   *Overview:* Explain that this workflow automates sending reports to parents after a math class.
    *   *Workflow Steps:*
        1.  Webhook trigger.
        2.  Fetch study record from Notion.
        3.  Fetch student profile (contact info).
        4.  Fetch class info.
        5.  Check for previous class to extract homework.
        6.  Format data using JS.
    *   *Requirements:* Notion API credentials, Webhook URL.
    *   *Technical Details:* Mention the JS logic for date formatting and recipient list creation.