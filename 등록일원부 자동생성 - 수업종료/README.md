# 등록일원부 자동생성 - 수업종료

> **Category:** Math4U  
> **Workflow ID:** `BrZ88oo3KRKccX0g`  
> **노션 메뉴얼:** https://www.notion.so/323c6a06e17e81b6b0a5d91342537f5c  
> **자동 생성:** Gemini AI  

---

n8n Workflow Expert.
Analyze the provided JSON and create a GitHub `README.md` in Korean.
"등록일원부 자동생성 - 수업종료" (Automatic Generation of Registration Ledger - Class End).
`BrZ88oo3KRKccX0g`.
`Math4U`.

        *   *Trigger:* `Notion Trigger` (Student_Study database, `pagedUpdatedInDatabase`, polls every 10 mins).
        *   *Node 1 (Notion):* Gets the latest page data for the updated page.
        *   *Node 2 (Code):* Logic check.
            *   Checks if '수업완료' (Class Completed) is checked.
            *   Checks if '등록일원부생성' (Ledger Created) is NOT checked (prevents duplicates).
            *   Compares '수업회차' (Session Count) with '수업구분' (Class Category/Count) to ensure it's the final session.
            *   Extracts IDs: `studentStudyPageId`, `studentPageId`, `classPageId`.
            *   Extracts/Calculates date (`isoDate`) and year.
        *   *Node 3 (HTTP Request):* Updates '등록일원부 생성' checkbox to `true` in Notion (marks as processed).
        *   *Node 4 (Notion):* Gets '수업료' (Tuition Fee) from the `Class` database.
        *   *Node 5 (Code):* Merges tuition fee into the data object.
        *   *Node 6 (Notion):* Gets '이름' (Student Name) from the `Students` database.
        *   *Node 7 (Code):* Merges student name into the data object.
        *   *Node 8 (HTTP Request - partial in JSON):* Looks like it's starting to query payment sessions (납부회차 조회). *Note: The JSON is truncated at the end, but the intent is clear.*

    *   *Purpose:* Automate the creation of a registration ledger (billing/record) when a student's class session is marked as completed, specifically for the final session of a course.
    *   *Flow:*
        1.  Detect change in `Student_Study` DB.
        2.  Verify if it's the final session and not yet processed.
        3.  Mark as processed immediately.
        4.  Fetch tuition fee from the `Class` DB.
        5.  Fetch student name from the `Students` DB.
        6.  (Implicitly) Prepare data for the ledger.

    *   *Title:* 등록일원부 자동생성 - 수업종료 (Automatic Registration Ledger Generation - Class End).
    *   *Description:* A workflow that monitors Notion for completed class sessions and automatically prepares data for the registration ledger when the final session is reached.
    *   *Workflow Steps:*
        1.  **Trigger**: Notion `Student_Study` database update.
        2.  **Validation**: Code node checks for "Class Completed" and "Final Session" match.
        3.  **Status Update**: Marks the record as "Ledger Created" to avoid loops.
        4.  **Data Enrichment**: Fetches Tuition Fee (from Class DB) and Student Name (from Students DB).
    *   *Requirements:* Notion API Credentials.
    *   *Key Logic:* The comparison between `sessionCount` and `classCount` is crucial.