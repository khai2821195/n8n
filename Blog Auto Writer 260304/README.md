# Blog Auto Writer 260304

> **Category:** 공통  
> **Workflow ID:** `L6uRu2oqasHrOIQR`  
> **자동 생성:** Gemini AI  

---

n8n Workflow Expert.
Analyze the provided JSON and write a GitHub `README.md` in Korean.
"Blog Auto Writer 260304" (📚 Math4U 학원 블로그 자동작성).
`L6uRu2oqasHrOIQR`.
Common.

        *   `node-form` (Form Trigger): User inputs topic, target audience, tone, reference URLs, and additional notes.
        *   `node-parse` (Set): Parses form inputs into variables (`blog_topic`, `target_reader`, `tone`, `url_list`, `memo`, `date_str`).
        *   `node-url-prep` (Code): Splits the `url_list` by newline and prefixes them with `https://r.jina.ai/` to convert web pages to LLM-friendly text.
        *   `node-jina` (HTTP Request): Fetches the content of the URLs via Jina AI.
        *   `node-url-merge` (Code): Aggregates the fetched content into a single string (`url_contents`).
        *   `node-prompt` (Code - partially provided): Constructs a detailed prompt for an LLM (acting as a blog writer for "대치Math4U 동탄캠").

    *   *Purpose:* Automate the creation of Naver Blog drafts for a math academy (Math4U).
    *   *Key Feature:* Uses Jina AI to scrape reference URLs to provide context to the LLM, ensuring the generated content is based on actual data or specific references.
    *   *User Interface:* n8n Form Trigger allows non-technical users to input requirements.

    *   *Title:* 📚 Math4U 학원 블로그 자동작성 워크플로우
    *   *Description:* A workflow that takes a topic and options via a form and generates a professional blog draft using AI and web scraping.
    *   *Workflow Flow:*
        1.  **Form Trigger:** User inputs (Topic, Audience, Tone, URLs, Memo).
        2.  **Data Parsing:** Organizing input data.
        3.  **URL Processing:** Using Jina AI to extract text from provided links.
        4.  **Content Aggregation:** Merging all scraped data.
        5.  **Prompt Engineering:** Creating a persona-based prompt for the AI.
        6.  **AI Generation (Implied):** Although the JSON cuts off at the prompt construction, the logic clearly leads to an LLM node.
    *   *Requirements:* n8n, Jina AI (public API), LLM API (OpenAI/Anthropic/etc. - implied).

    *   Ensure a professional and clear tone.
    *   Use emojis for readability.
    *   Structure with clear headings.