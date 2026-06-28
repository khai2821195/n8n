# 대치Math4U - AI팀 회의실

> **Category:** 공통  
> **Workflow ID:** `MZK5Sv9zp1D0OMmx`  
> **자동 생성:** Gemini AI  

---

n8n Workflow Expert.
Analyze the provided JSON and write a GitHub `README.md` in Korean.
"대치Math4U - AI팀 회의실" (DaechiMath4U - AI Team Meeting Room).
A workflow that takes a meeting agenda via a form and generates opinions from four distinct AI personas (Neil, Jony, Bill, Tim) using Google Gemini, then compiles them into a meeting minutes format.

    *   *Trigger:* `n8n-nodes-base.formTrigger` ("회의 시작 폼") -> User inputs an `agenda`.
    *   *Parsing:* `n8n-nodes-base.set` ("입력 파싱") -> Sets `agenda` and `meetingDate`.
    *   *AI Personas (Sequential/Parallel-ish flow):*
        *   `@n8n/n8n-nodes-langchain.googleGemini` (Neil Patel - Marketer): SEO/SNS focus.
        *   `@n8n/n8n-nodes-langchain.googleGemini` (Jony Ive - Designer): Visual/Minimalism focus.
        *   `@n8n/n8n-nodes-langchain.googleGemini` (Bill Gates - Automation): System/Efficiency focus.
        *   `@n8n/n8n-nodes-langchain.googleGemini` (Tim Cook - Student Mgmt): Satisfaction/Trust focus.
    *   *Output Generation:* `n8n-nodes-base.set` ("회의록 생성" - implied by the last node's logic) -> Aggregates all AI responses into a Markdown meeting minutes format.
    *   *Final Step:* The form response mode is `lastNode`, meaning the final meeting minutes are displayed back to the user.

    *   *Title:* 대치Math4U - AI팀 회의실
    *   *Description:* A virtual brainstorming room where 4 AI experts provide multi-dimensional perspectives on a given agenda.
    *   *Workflow Flow:*
        1.  Form Input (Agenda)
        2.  Data Parsing (Date/Agenda)
        3.  AI Brainstorming (4 Personas)
        4.  Meeting Minutes Compilation
    *   *Personas Detail:*
        *   Neil: Marketing/SEO
        *   Jony: Design/UX
        *   Bill: Automation/Ops
        *   Tim: Customer/Student Care
    *   *Requirements:* Google Gemini API Key.
    *   *Usage:* Input agenda $\rightarrow$ Get structured minutes $\rightarrow$ Review with Claude (as suggested in the prompt's final node).