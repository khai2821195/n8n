# Class_Study 월별 자동생성

> **Category:** Math4U  
> **Workflow ID:** `n7M2Z2BhVbGNWhqX`  
> **노션 메뉴얼:** https://www.notion.so/323c6a06e17e817daa0bc4f4b7c1bc98  
> **자동 생성:** Gemini AI  

---

n8n Workflow Expert.
Analyze the provided JSON and write a GitHub `README.md` in Korean.
"Class_Study 월별 자동생성" (Monthly Auto-generation of Class Study).
`n7M2Z2BhVbGNWhqX`.
Math4U.

        *   `Schedule - 매월 25일`: Triggered on the 25th of every month at 00:00 (Cron: `0 0 25 * *`).
        *   `Notion - Class DB 전체 조회`: Fetches all pages from a specific Notion database (`2d0c6a06-e17e-8104-9eae-c45a7a818f60`).
        *   `Aggregate - 전체 반 목록 합치기`: Aggregates all fetched Notion items into a single array for processing.
        *   `Code - 수업일정 계산`: A JavaScript node that:
            *   Calculates the dates for the *next* month.
            *   Parses class names, student relations, and schedule slots (Regular classes 1-3 and Supplementary classes).
            *   Maps days of the week (Sun-Sat) to dates.
            *   Groups dates by week of the month.
            *   Generates a list of records with titles like "Class Name [Month]월 [Week]-[Session]".
            *   Formats dates to KST (ISO 8601).

    *   *Goal:* Automatically generate a study schedule for the next month based on class settings in Notion.
    *   *Logic:*
        1.  Trigger every 25th.
        2.  Get all classes from Notion.
        3.  For each class, look at "수업 1, 2, 3" and "정규보충" fields.
        4.  Match these with the calendar of the next month.
        5.  Create a sequence of sessions (e.g., 1-1, 1-2, 2-1...).
        6.  Output a list of objects ready to be inserted into another database (though the JSON cuts off before the final insertion node, the logic clearly prepares data for it).

    *   *Title:* Class_Study 월별 자동생성 (Monthly Auto-generation of Class Study)
    *   *Description:* A workflow that automatically calculates and generates the next month's class schedules based on Notion database settings.
    *   *Workflow Flow:*
        1.  **Schedule Trigger**: Runs on the 25th of each month.
        2.  **Notion Get All**: Retrieves all class information from the Class DB.
        3.  **Aggregate**: Combines all class data into one list.
        4.  **Code Node**: The core logic. Calculates dates, handles KST timezone, and assigns session numbers.
    *   *Requirements:* Notion API Credentials, Notion Database ID.
    *   *Key Logic Details:*
        *   Next month calculation.
        *   Multi-select parsing for days and times.
        *   Week-of-month numbering.

    *   Use professional, technical Korean.
    *   Ensure the structure follows the requested rules.