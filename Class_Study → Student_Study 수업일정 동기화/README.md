# Class_Study → Student_Study 수업일정 동기화

> **Category:** Math4U  
> **Workflow ID:** `G5k8fgeviVCR8ixe`  
> **자동 생성:** Gemini AI  

---

n8n Workflow Expert.
Analyze provided JSON and write a GitHub `README.md` in Korean.
`Class_Study → Student_Study 수업일정 동기화` (Class_Study to Student_Study Lesson Schedule Synchronization).
`G5k8fgeviVCR8ixe`.
`Math4U`.

        *   *Trigger:* `n8n-nodes-base.notionTrigger` (Polls every 5 minutes for updates in a specific Notion database `2d0c6a06e17e819c9347e50501c59069`).
        *   *Processing (Code Node):* Extracts `수업일정` (date), `과정` (course - handles select, multi-select, relation, etc.), and `Student_Study` (relation IDs).
            *   If no date: skip.
            *   If no related students: skip.
            *   If valid: returns a list of student page IDs with the date and course.
        *   *Filtering (If Node):* Checks if `skip` is false.
        *   *Action (Notion Node):* Updates the `수업일시` (date) property of the `Student_Study` page.
        *   *Logging (Set Nodes):* Logs success or skip status (though the JSON is cut off at the end, the intent is clear).

    *   *Purpose:* Automatically synchronize lesson dates from a master "Class Study" database to individual "Student Study" records in Notion.
    *   *Flow:*
        1.  **Trigger:** Detects changes in the `Class_Study` database every 5 minutes.
        2.  **Extraction:** A JavaScript code node parses the date and identifies which students are linked to that class.
        3.  **Validation:** Checks if the necessary data (date and student links) exists.
        4.  **Update:** Updates the `수업일시` property for each linked student in the `Student_Study` database.
        5.  **Logging:** Records whether the process was successful or skipped.

    *   *Title:* Class_Study → Student_Study 수업일정 동기화
    *   *Description:* Notion의 `Class_Study` 데이터베이스에서 변경된 수업 일정을 연결된 `Student_Study` 레코드들에 자동으로 반영하는 워크플로우입니다.
    *   *Workflow Diagram/Flow:*
        *   `Class_Study 변경 감지` (Notion Trigger) $\rightarrow$ `수업일정 및 학생ID 추출` (Code) $\rightarrow$ `업데이트 필요 여부` (If) $\rightarrow$ `Student_Study 수업일시 업데이트` (Notion Update) / `스킵 로그` (Set).
    *   *Requirements:* Notion API Credentials, Database IDs.
    *   *Key Logic:* Multi-select/Relation handling for courses, 1:N mapping (one class to multiple students).