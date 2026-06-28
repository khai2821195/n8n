# Blog Auto Writer 260304

> **Category:** 공통  
> **Workflow ID:** `L6uRu2oqasHrOIQR`  
> **자동 생성:** Gemini AI  

---

n8n Workflow Expert.
Analyze a provided JSON workflow and write a GitHub `README.md` in Korean.
"Blog Auto Writer 260304" (Internal name: 📚 Math4U 학원 블로그 자동작성).

        *   `n8n-nodes-base.formTrigger`: User inputs blog topic, target reader, tone, reference URLs, and additional memos.
        *   `n8n-nodes-base.set`: Parses form inputs into variables (`blog_topic`, `target_reader`, etc.).
        *   `n8n-nodes-base.code` (URL Prep): Splits reference URLs and prepends `https://r.jina.ai/` (Jina Reader API) to fetch clean text content.
        *   `n8n-nodes-base.httpRequest` (Jina URL Reading): Fetches the content of the URLs.
        *   `n8n-nodes-base.code` (URL Merge): Aggregates the fetched content into a single string.
        *   `n8n-nodes-base.code` (Prompt Generation - partial in JSON but clear): Constructs a detailed prompt for an AI (likely an LLM node follows, though the JSON cuts off, the logic is clear: it's preparing a prompt for a "Math4U Dongtan Campus" blog writer).

    *   *Purpose:* Automate the creation of Naver Blog drafts for a specific math academy (Math4U Dongtan Campus) based on user input and reference URLs.
    *   *Key Feature:* Uses Jina Reader (`r.jina.ai`) to scrape web content and feed it into an AI prompt for high-quality, context-aware writing.

    *   *Title:* 📚 Math4U 학원 블로그 자동작성 워크플로우
    *   *Introduction:* A tool to generate professional blog drafts for a math academy.
    *   *Workflow Flow:*
        1.  **Form Trigger:** User inputs (Topic, Audience, Tone, URLs, Memos).
        2.  **Data Parsing:** Organizing input data.
        3.  **Web Scraping (Jina AI):** Converting URLs to readable text.
        4.  **Content Integration:** Merging scraped data.
        5.  **Prompt Engineering:** Creating a structured prompt for the AI.
    *   *Requirements:* n8n instance, (Implicitly) an LLM node (OpenAI/Anthropic/etc.) to process the final prompt.
    *   *Setup Guide:* Import JSON $\rightarrow$ Configure LLM $\rightarrow$ Run.

    *   Ensure the tone is professional and clear.
    *   Use appropriate Markdown formatting (tables, lists, code blocks).
    *   Highlight the "Jina AI" part as it's a clever way to handle URL content.