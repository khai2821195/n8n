# 등록일원부 자동생성 - 수업종료

> **Category:** Math4U  
> **Workflow ID:** `BrZ88oo3KRKccX0g`  
> **노션 메뉴얼:** https://www.notion.so/323c6a06e17e81b6b0a5d91342537f5c  
> **자동 생성:** Gemini AI  

---

n8n Workflow Expert.
Analyze a provided n8n workflow JSON and create a GitHub `README.md` in Korean.
"등록일원부 자동생성 - 수업종료" (Automatic Generation of Registration Ledger - Class End).
`BrZ88oo3KRKccX0g`.
`Math4U`.

        *   `Notion Trigger`: Detects updates in `Student_Study` database.
        *   `Notion (get)`: Fetches the latest page data for the updated record.
        *   `Code (JS)`:
            *   Checks if `수업완료` (Class Completed) is checked.
            *   Checks if `등록일원부생성` (Ledger Generated) is NOT checked (prevents duplicates).
            *   Validates `수업회차` (Session Count) matches `수업구분` (Class Category/Count).
            *   Extracts `studentStudyPageId`, `studentPageId`, `classPageId`, `isoDate`, and `year`.
        *   `HTTP Request (PATCH)`: Updates `등록일원부 생성` checkbox to `true` (marking it as processed).
        *   `Notion (get)`: Fetches `Class` page to get `수업료` (Tuition Fee).
        *   `Code (JS)`: Extracts the fee.
        *   `Notion (get)`: Fetches `Students` page to get `이름` (Student Name).
        *   `Code (JS)`: Merges the student name into the data object.
        *   `HTTP Request`: (JSON is cut off, but the name says "납부회차 조회" - Querying Payment Session).

    *   *Purpose:* When a class session is marked as "Completed" in Notion, this workflow automatically gathers student and class information (tuition, name, session count) to prepare for the creation of a registration ledger (payment record).
    *   *Trigger:* Notion database update.
    *   *Logic:*
        1.  Trigger $\rightarrow$ Get Page $\rightarrow$ Filter (Is it completed? Is it already processed? Do session counts match?).
        2.  Mark as processed (Checkbox update).
        3.  Fetch Class details (Tuition).
        4.  Fetch Student details (Name).
        5.  (Implicitly) Prepare data for payment session lookup.

    *   *Title:* # 등록일원부 자동생성 - 수업종료
    *   *Description:* Math4U 교육 관리 시스템의 일부로, 수업 종료 시 자동으로 등록일원부 생성을 위한 데이터를 수집하고 처리하는 워크플로우입니다.
    *   *Workflow Flow:*
        1.  **트리거**: Notion `Student_Study` 데이터베이스의 변경 사항 감지.
        2.  **검증**: 수업 완료 여부, 중복 생성 여부, 수업 회차 일치 여부 확인.
        3.  **상태 업데이트**: 중복 처리를 방지하기 위해 '등록일원부 생성' 체크박스를 활성화.
        4.  **데이터 수집**:
            *   `Class` 데이터베이스에서 수업료 정보 조회.
            *   `Students` 데이터베이스에서 학생 이름 조회.
        5.  **최종 처리**: 납부 회차 조회 및 데이터 병합 (이후 단계로 전달).
    *   *Requirements:* Notion API Credentials.
    *   *Key Variables/Fields:* `수업완료`, `등록일원부생성`, `수업회차`, `수업구분`, `수업료`, `이름`.