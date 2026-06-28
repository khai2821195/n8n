# 대치Math4U - AI팀 회의실

> **Category:** 공통  
> **Workflow ID:** `MZK5Sv9zp1D0OMmx`  
> **자동 생성:** Gemini AI  

---

n8n Workflow Expert.
Analyze a provided n8n workflow JSON and create a GitHub `README.md` in Korean.
"대치Math4U - AI팀 회의실" (Daechi Math4U - AI Team Meeting Room).
A JSON representation of an n8n workflow.

        1.  Clear purpose and operation method.
        2.  Step-by-step node flow (Trigger $\rightarrow$ Process $\rightarrow$ Output).
        3.  Required environment variables/credentials.
        4.  Precautions/Special notes.
        5.  Markdown format.
        6.  Output *only* the README.md content.

    *   *Trigger:* `n8n-nodes-base.formTrigger` ("회의 시작 폼"). It takes an `agenda` (textarea).
    *   *Processing 1:* `n8n-nodes-base.set` ("입력 파싱"). Sets `agenda` and `meetingDate` (current date).
    *   *AI Agents (Sequential/Parallel-ish flow):*
        *   `neil-gemini` (Neil Patel): Marketer/SEO/SNS perspective.
        *   `john-gemini` (Jony Ive): Designer/Visual/Brand perspective.
        *   `bill-gemini` (Bill Gates): Automation/System perspective.
        *   `tim-gemini` (Tim Cook): Student Management/Counseling perspective.
        *   *Model used:* `gemini-3.1-flash-lite`.
    *   *Output/Aggregation:* `n8n-nodes-base.set` ("회의록 생성" - though the JSON snippet ends abruptly, the logic is clear). It compiles the responses from all four AI agents into a formatted Markdown meeting minute.
    *   *Final Step:* The form response mode is `lastNode`, meaning the final formatted meeting minutes are shown back to the user who filled out the form.

    *   *Title:* # 대치Math4U - AI팀 회의실 (AI Team Meeting Room)
    *   *Introduction:* This workflow simulates a virtual meeting with four AI experts (Neil, Jony, Bill, Tim) to get multi-dimensional feedback on a specific agenda for a math academy.
    *   *Workflow Flow:*
        1.  **Form Trigger**: User enters the agenda.
        2.  **Data Parsing**: Sets the date and cleans the input.
        3.  **AI Brainstorming**:
            *   Neil (Marketing/SEO)
            *   Jony (Design/UX)
            *   Bill (Automation/Ops)
            *   Tim (Student/Parent Care)
        4.  **Minutes Generation**: Aggregates all AI responses into a structured Markdown report.
    *   *Credentials:* Google Gemini API Key.
    *   *Special Notes:* The final output is intended to be passed to another AI (Claude/Genie) for final action item refinement.