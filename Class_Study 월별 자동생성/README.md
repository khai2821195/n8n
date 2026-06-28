# Class_Study 월별 자동생성

> **Category:** Math4U  
> **Workflow ID:** `n7M2Z2BhVbGNWhqX`  
> **노션 메뉴얼:** https://www.notion.so/323c6a06e17e817daa0bc4f4b7c1bc98  
> **자동 생성:** Gemini AI  

---

n8n Workflow Expert.
Analyze a provided n8n workflow JSON and write a GitHub `README.md` in Korean.
"Class_Study 월별 자동생성" (Monthly Automatic Generation of Class Study).
`n7M2Z2BhVbGNWhqX`.
`Math4U`.

        *   `Schedule - 매월 25일`: Triggered on the 25th of every month at 00:00.
        *   `Notion - Class DB 전체 조회`: Fetches all pages from a specific Notion database (Class DB).
        *   `Aggregate - 전체 반 목록 합치기`: Combines all fetched class items into a single array for processing.
        *   `Code - 수업일정 계산`: A JavaScript node that:
            *   Calculates the dates for the *next* month.
            *   Parses class names, student relations, and schedules (Regular classes 1-3 and Supplementary classes).
            *   Maps days of the week (Sun-Sat) to dates.
            *   Groups dates by week of the month.
            *   Generates a list of records with titles like "Class Name [Month]월 [Week]-[Session]".
            *   Formats dates to KST ISO string.

    *   *Purpose:* Automatically generate a study schedule for the following month based on a Notion Class database.
    *   *Trigger:* Monthly (25th).
    *   *Logic:*
        1.  Get all classes from Notion.
        2.  Extract schedule patterns (Day of week, Hour).
        3.  Calculate actual dates for the next month.
        4.  Assign session numbers (e.g., 1-1, 1-2) based on the week and order.
        5.  Prepare data for insertion (though the JSON ends at the Code node, the intent is clearly to create new records in another DB).

    *   *Title:* Class_Study 월별 자동생성 (Monthly Class Study Auto-Generator).
    *   *Overview:* Automates the creation of monthly study logs/schedules in Notion.
    *   *Workflow Steps:*
        1.  **Schedule Trigger**: Every 25th.
        2.  **Notion Get All**: Fetch Class DB.
        3.  **Aggregate**: Merge data.
        4.  **Code Node**: The "brain" that calculates dates and session IDs.
    *   *Requirements:* Notion API credentials, specific DB structure (Class DB with fields like '반명', '수업 1~3', '시간 1~4', '정규보충', 'Students').
    *   *Key Logic Details:* KST timezone handling, week-of-month calculation.