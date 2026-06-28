# 📚 Math4U 학원 블로그 자동작성

> **Category:** Math4U  
> **Workflow ID:** `L6uRu2oqasHrOIQR`  
> **자동 생성:** Gemini AI  

---

n8n Workflow Expert.
Analyze the provided JSON and write a GitHub `README.md` in Korean.
"📚 Math4U 학원 블로그 자동작성" (Math4U Academy Blog Auto-Writer).

        *   `node-form` (Form Trigger): Collects topic, target reader, tone, reference URLs, and additional memos.
        *   `node-parse` (Set): Parses form inputs into variables.
        *   `node-url-prep` (Code): Splits reference URLs and prepares them for Jina AI (`https://r.jina.ai/`).
        *   `node-jina` (HTTP Request): Fetches content from the URLs via Jina AI.
        *   `node-url-merge` (Code): Merges fetched content into a single string.
        *   `node-ai-prompt` (Code/AI - partial JSON provided): Constructs a prompt for an AI to write a Naver Blog post for "대치Math4U 동탄캠".

        1.  Purpose and operation.
        2.  Node flow (Trigger $\rightarrow$ Process $\rightarrow$ Output).
        3.  Environment variables/Credentials.
        4.  Precautions/Special notes.
        5.  Markdown format.
        6.  Output *only* the README.md content.

    *   *Title:* 📚 Math4U 학원 블로그 자동작성 (Math4U Academy Blog Auto-Writer).
    *   *Purpose:* Automate the creation of Naver Blog drafts for a math academy based on user input and reference URLs.
    *   *Workflow Steps:*
        1.  **Input:** User fills out a form (Topic, Target, Tone, URLs, Memo).
        2.  **Parsing:** Data is structured.
        3.  **Web Scraping:** Reference URLs are converted to Jina AI links and fetched to get clean text.
        4.  **Aggregation:** All scraped content is merged.
        5.  **AI Generation:** A detailed prompt is sent to an AI (LLM) to generate a professional blog post tailored to the academy's branding.

    *   *Header:* Title and a brief description.
    *   *Key Features:* Form-based input, AI-powered writing, Web scraping (Jina AI).
    *   *Workflow Architecture:*
        *   `📝 블로그 작성 폼` $\rightarrow$ `입력값 파싱` $\rightarrow$ `URL 콘텐츠 수집` $\rightarrow$ `Jina URL 읽기` $\rightarrow$ `URL 자료 통합` $\rightarrow$ `AI 프롬프트 생성 및 작성`.
    *   *Setup:*
        *   n8n installation.
        *   HTTP Request (for Jina AI - usually free/API key depending on usage).
        *   AI Node (though the JSON cuts off, it's implied an AI node follows the prompt construction).
    *   *Usage:* How to trigger the form and get the result.