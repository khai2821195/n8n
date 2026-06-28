# Class_Study 월별 자동생성

> **Category:** Math4U  
> **Workflow ID:** `n7M2Z2BhVbGNWhqX`  
> **노션 메뉴얼:** https://www.notion.so/323c6a06e17e817daa0bc4f4b7c1bc98  
> **자동 생성:** Gemini AI  

---

n8n Workflow Expert.
Analyze a provided n8n workflow JSON and write a GitHub `README.md` in Korean.
"Class_Study 월별 자동생성" (Monthly Auto-generation of Class Study).
`n7M2Z2BhVbGNWhqX`.
Math4U.

        *   `Schedule - 매월 25일`: Triggered on the 25th of every month at 00:00.
        *   `Notion - Class DB 전체 조회`: Fetches all pages from a specific Notion database (`2d0c6a06-e17e-8104-9eae-c45a7a818f60`).
        *   `Aggregate - 전체 반 목록 합치기`: Aggregates all fetched items into a single list.
        *   `Code - 수업일정 계산`: A JavaScript node that:
            *   Calculates the dates for the *next* month.
            *   Parses class schedules (Regular classes 1-3 and Supplementary classes).
            *   Maps days of the week (Sun-Sat).
            *   Calculates specific dates and times for each class session.
            *   Groups them by week of the month.
            *   Generates a title like "[Class Name] [Month]월 [Week]-[Session Number]".
            *   Outputs a list of records containing `title`, `datetime`, `classId`, `studentIds`, and `반명`.

    *   *Purpose:* Automatically generate study session records for the next month based on class schedules stored in Notion.
    *   *Trigger:* Monthly (25th).
    *   *Logic:*
        1.  Get all classes from Notion.
        2.  For each class, look at "수업 1, 2, 3" and "정규보충" (days) and "시간 1, 2, 3, 4" (hours).
        3.  Find all matching dates in the next month.
        4.  Assign a sequence number (e.g., 1-1, 1-2) based on the week and order.
        5.  Prepare data for creation (likely to be inserted into another Notion DB, though the JSON cuts off before the final creation node, the logic clearly prepares records for it).

    *   *Title:* Class_Study 월별 자동생성 (Monthly Auto-generation of Class Study)
    *   *Description:* A workflow that automatically calculates and prepares the next month's class schedule based on Notion database settings.
    *   *Workflow Flow:*
        1.  **Schedule Trigger**: Every 25th of the month.
        2.  **Notion Get All**: Retrieve class info (Class name, students, schedule).
        3.  **Aggregate**: Combine data for processing.
        4.  **Code Node**: Complex date calculation logic (KST timezone, week-of-month calculation, session numbering).
    *   *Requirements:* Notion API Key (Integration Token), Database ID.
    *   *Key Logic Details:*
        *   Target: Next month.
        *   Format: `[Class Name] [Month]월 [Week]-[Session]`
        *   Timezone: KST (UTC+9).

    *   Ensure professional tone.
    *   Use clear headings.
    *   Use a table or list for node descriptions.