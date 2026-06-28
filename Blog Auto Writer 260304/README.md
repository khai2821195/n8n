# Blog Auto Writer 260304

> **Category:** 공통  
> **Workflow ID:** `L6uRu2oqasHrOIQR`  
> **자동 생성:** Gemini AI  

---

n8n Workflow Expert.
Analyze provided JSON and write a GitHub `README.md` in Korean.
"Blog Auto Writer 260304" (Math4U 학원 블로그 자동작성).

        *   `n8n-nodes-base.formTrigger`: User inputs topic, target audience, tone, reference URLs, and additional notes.
        *   `n8n-nodes-base.set` (입력값 파싱): Maps form inputs to variables.
        *   `n8n-nodes-base.code` (URL 콘텐츠 수집): Splits multiple URLs and prepares them for Jina AI (r.jina.ai).
        *   `n8n-nodes-base.httpRequest` (Jina URL 읽기): Fetches content from the URLs using Jina AI's reader.
        *   `n8n-nodes-base.code` (URL 자료 통합): Merges fetched content into a single string.
        *   `n8n-nodes-base.code` (Prompt construction - partial in JSON but clear): Builds a prompt for an LLM (though the LLM node itself is cut off in the JSON, the logic is clearly heading towards an AI generation step). *Correction: The JSON cuts off at the prompt construction, but the intent is clear: it's an AI-powered blog writer.*

    *   *Purpose:* Automate the creation of Naver Blog drafts for "Math4U" math academy.
    *   *Flow:* Form $\rightarrow$ Parsing $\rightarrow$ URL Scraping (via Jina AI) $\rightarrow$ Data Integration $\rightarrow$ Prompt Generation $\rightarrow$ (Implicitly) AI Generation.

    *   *Title:* 📚 Math4U 학원 블로그 자동작성 워크플로우
    *   *Introduction:* A tool to generate high-quality Naver Blog drafts based on specific topics and reference materials.
    *   *Key Features:*
        *   Customizable target audience and tone.
        *   Web scraping of reference URLs using Jina AI.
        *   Structured prompt generation for consistent branding.
    *   *Workflow Steps:*
        1.  **Form Trigger**: Input topic, audience, tone, URLs, and notes.
        2.  **Parsing**: Organize input data.
        3.  **URL Processing**: Split URLs and use `r.jina.ai` to convert web pages to markdown/text.
        4.  **Data Integration**: Combine all scraped content.
        5.  **Prompting**: Create a detailed prompt for the AI writer.
    *   *Requirements:*
        *   n8n installation.
        *   (Implicitly) An LLM node (OpenAI, Anthropic, etc.) to actually generate the text (though the JSON ends at the prompt, the user expects a full README for the *intent* of the workflow).
    *   *Notes:* Mention Jina AI's role in cleaning web content.

    *   Use professional yet accessible Korean.
    *   Use emojis for readability.
    *   Ensure the structure follows the requested rules.