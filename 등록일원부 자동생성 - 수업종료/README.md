# 등록일원부 자동생성 - 수업종료

> **Category:** Math4U  
> **Workflow ID:** `BrZ88oo3KRKccX0g`  
> **노션 메뉴얼:** https://www.notion.so/323c6a06e17e81b6b0a5d91342537f5c  
> **자동 생성:** Gemini AI  

---

n8n Workflow Expert.
Analyze a provided n8n workflow JSON and write a GitHub `README.md` in Korean.
"등록일원부 자동생성 - 수업종료" (Automatic Generation of Registration Ledger - Class End).
`BrZ88oo3KRKccX0g`.
`Math4U`.

        *   `Notion Trigger`: Watches for updates in the `Student_Study` database (polls every 10 mins).
        *   `Notion - Student_Study 최신 조회`: Gets the latest page data for the updated page.
        *   `Code - 종료 체크 및 데이터 추출`:
            *   Checks if `수업완료` (Class Completed) is checked.
            *   Checks if `등록일원부생성` (Ledger Generated) is *not* checked.
            *   Validates if the current session count matches the class count.
            *   Extracts `studentStudyPageId`, `studentPageId`, `classPageId`, `isoDate`, and `year`.
        *   `HTTP - 등록일원부생성 체크박스 업데이트`: Updates the `등록일원부 생성` checkbox to `true` to prevent duplicate runs.
        *   `Notion - Class 수업료 조회`: Gets the tuition fee from the `Class` database.
        *   `Code - 수업료 추출`: Merges the fee into the data object.
        *   `Notion - Students 이름 조회`: Gets the student's name from the `Students` database.
        *   `Code - 이름 병합`: Merges the student name into the data object.
        *   `HTTP - 납부회차 조회`: (JSON is truncated, but the name suggests it queries payment rounds/history).

    *   *Purpose:* Automatically generate a registration ledger (likely a record for payment or administrative tracking) when a student's class session ends.
    *   *Trigger:* A change in the Notion `Student_Study` database.
    *   *Condition:* Only runs if the class is marked as "Completed" and the ledger hasn't been created yet, and the session number matches the total class count.
    *   *Data Flow:* Notion (Study) $\rightarrow$ Logic Check $\rightarrow$ Update Status $\rightarrow$ Notion (Class/Fee) $\rightarrow$ Notion (Student/Name) $\rightarrow$ (Payment Query).

    *   *Title:* 등록일원부 자동생성 - 수업종료 (Automatic Registration Ledger Generation - Class End)
    *   *Overview:* Explain that this workflow automates the administrative process of creating a ledger when a student completes their course.
    *   *Workflow Steps:*
        1.  **Trigger:** Detect update in `Student_Study` database.
        2.  **Validation:** Check if "Class Completed" is true and "Ledger Generated" is false. Verify session count.
        3.  **Status Update:** Mark "Ledger Generated" as true.
        4.  **Data Gathering:** Fetch tuition fee from `Class` and student name from `Students`.
        5.  **Payment Check:** Query payment history (based on the final HTTP node).
    *   *Requirements:* Notion API Credentials.
    *   *Key Databases:* `Student_Study`, `Class`, `Students`.