# Class_Study → Student_Study 수업일정 동기화

> **Category:** Math4U  
> **Workflow ID:** `G5k8fgeviVCR8ixe`  
> **자동 생성:** Gemini AI  

---

n8n Workflow Expert.
Analyze a provided JSON workflow and write a GitHub `README.md` in Korean.
Class_Study → Student_Study 수업일정 동기화 (Class_Study to Student_Study Schedule Sync).
G5k8fgeviVCR8ixe.
Math4U.

        *   *Trigger:* `n8n-nodes-base.notionTrigger` (Polls every 5 minutes for updates in a specific Notion database `2d0c6a06e17e819c9347e50501c59069`).
        *   *Processing (Code):* `n8n-nodes-base.code` (Extracts '수업일정' date, '과정' course info, and 'Student_Study' relation IDs. It handles various property types for '과정' and checks if dates or student relations are missing).
        *   *Decision (IF):* `n8n-nodes-base.if` (Checks if `skip` is false).
        *   *Action (Notion Update):* `n8n-nodes-base.notion` (Updates the '수업일시' property of the related `Student_Study` page).
        *   *Logging (Set):* `n8n-nodes-base.set` (Logs skips or successes).

    *   *Purpose:* Automatically synchronize class schedules from a master class database (`Class_Study`) to individual student study records (`Student_Study`) in Notion.
    *   *Flow:*
        1.  **Trigger:** Detects changes in the `Class_Study` Notion database every 5 minutes.
        2.  **Extraction:** A JS code block parses the date and identifies which students are linked to that class.
        3.  **Filtering:** If no date is set or no students are linked, the process is skipped.
        4.  **Update:** For each linked student, the corresponding `Student_Study` record's date is updated.
        5.  **Logging:** Records the outcome (Success/Skip).

    *   *Title:* Class_Study → Student_Study 수업일정 동기화
    *   *Description:* Notion의 수업 관리 DB에서 일정이 변경되면, 연결된 학생들의 학습 기록 DB로 해당 일정을 자동으로 전파하는 워크플로우입니다.
    *   *Workflow Diagram/Flow:*
        *   `Class_Study 변경 감지` (Notion Trigger) $\rightarrow$ `수업일정 및 학생ID 추출` (Code) $\rightarrow$ `업데이트 필요 여부` (IF) $\rightarrow$ `Student_Study 수업일시 업데이트` (Notion Update) / `스킵 로그` (Set).
    *   *Requirements:* Notion API Credentials, Database IDs.
    *   *Key Logic:* Multi-select/Relation handling for courses, mapping one class to multiple students.