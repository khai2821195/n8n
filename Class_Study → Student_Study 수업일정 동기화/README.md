# Class_Study → Student_Study 수업일정 동기화

> **Category:** Math4U  
> **Workflow ID:** `G5k8fgeviVCR8ixe`  
> **자동 생성:** Gemini AI  

---

n8n Workflow Expert.
Analyze a provided n8n workflow JSON and write a GitHub `README.md` in Korean.
`Class_Study → Student_Study 수업일정 동기화` (Class_Study to Student_Study Class Schedule Synchronization).
`G5k8fgeviVCR8ixe`.
`Math4U`.

        *   *Trigger:* `notionTrigger` (Class_Study 변경 감지) - Polls every 5 minutes for updates in a specific Notion database.
        *   *Processing (Code):* `code` (수업일정 및 학생ID 추출) - Extracts `수업일정` (date), `과정` (course), and `Student_Study` (relation IDs). It handles various property types for 'course' and checks if dates or student relations are missing. If missing, it sets `skip: true`.
        *   *Condition (IF):* `if` (업데이트 필요 여부) - Checks if `skip` is false.
        *   *Action (Success):* `notion` (Student_Study 수업일시 업데이트) - Updates the `수업일시` property of the related student pages.
        *   *Action (Skip):* `set` (스킵 로그) - Logs the reason for skipping.
        *   *Logging (Partial):* There's a final `set` node for success logging (though the JSON is cut off, the intent is clear).

    *   *Purpose:* Automatically synchronize class dates from a master "Class_Study" database to individual "Student_Study" records in Notion.
    *   *Flow:*
        1.  **Trigger:** Detects changes in the `Class_Study` database every 5 minutes.
        2.  **Extraction:** A JS code node parses the date and identifies which students are linked to that class.
        3.  **Filtering:** If no date is set or no students are linked, the process is skipped.
        4.  **Update:** For each linked student, the `Student_Study` record's date is updated to match the class date.
        5.  **Logging:** Records whether the operation was successful or skipped.

    *   *Title:* Class_Study → Student_Study 수업일정 동기화
    *   *Description:* Notion-based synchronization for educational scheduling.
    *   *Workflow Diagram/Step-by-step:*
        *   Step 1: Notion Trigger (Polling)
        *   Step 2: Data Extraction (JS Code)
        *   Step 3: Condition Check (IF)
        *   Step 4: Notion Update (Student_Study) / Skip Log.
    *   *Requirements:* Notion API Credentials, Database IDs.
    *   *Notes:* Handling of multi-select/relation for courses, 5-minute polling interval.