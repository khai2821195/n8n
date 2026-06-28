# Biz-mecca 납품사례 블로그 자동작성 260310

> **Category:** DCT  
> **Workflow ID:** `ruLfwzGZtsmLSD3k`  
> **노션 메뉴얼:** https://www.notion.so/323c6a06e17e8101b97ac00492a67ddd  
> **자동 생성:** Gemini AI  

---

n8n Workflow Expert.
Analyze provided JSON and write a GitHub `README.md` in Korean.
"Biz-mecca 납품사례 블로그 자동작성 260310" (Biz-mecca Delivery Case Blog Auto-writer).
`ruLfwzGZtsmLSD3k`.
DCT.

        *   `node-form` (Form Trigger): Collects product name, description, client name, client type, quantity, product URL, and notes.
        *   `node-set-inputs` (Set): Normalizes the form inputs into a structured format.
        *   `node-jina` (HTTP Request): Crawls the product URL (currently disabled in the JSON).
        *   `node-parse-product` (Code): Parses the crawled HTML/text to extract product info (handling encoding issues like EUC-KR).
        *   *Note:* The JSON is truncated at the end of the `node-parse-product` code, but the intent is clear: Form $\rightarrow$ Set $\rightarrow$ Crawl $\rightarrow$ Parse $\rightarrow$ (presumably) AI Generation $\rightarrow$ Output.

    *   *Purpose:* Automate the creation of Naver Blog drafts for delivery cases (case studies) for "Biz-mecca".
    *   *Workflow Flow:*
        1.  **Input:** User fills out an n8n form with delivery details.
        2.  **Data Normalization:** The `Set` node organizes the input for easier use in subsequent steps.
        3.  **Web Scraping (Optional/Disabled):** An HTTP request fetches the product page from the Biz-mecca website.
        4.  **Data Parsing:** A JavaScript code node cleans the HTML and extracts relevant text, handling potential character encoding issues.
        5.  **Output (Implicit):** Based on the form title and description, the final goal is to generate a blog draft (though the final LLM/Output nodes are missing from the truncated JSON, the logic is evident).

    *   *Title:* Biz-mecca 납품사례 블로그 자동작성 워크플로우
    *   *Description:* A tool to automatically generate blog drafts based on product delivery information.
    *   *Key Features:*
        *   Easy input via n8n Form.
        *   Automatic product page crawling.
        *   Data cleaning for better AI prompts.
    *   *Node-by-node breakdown:*
        *   `납품사례 폼 입력`: User interface for data entry.
        *   `입력값 정리`: Variable mapping.
        *   `제품 URL 크롤링`: Fetching product details from the web.
        *   `제품 정보 파싱`: Cleaning HTML and extracting text.
    *   *Requirements:* n8n instance, (likely) an LLM API key (OpenAI/Anthropic) though not explicitly in the JSON, it's implied by "자동작성".

    *   Use professional, clear Korean.
    *   Follow the requested Markdown structure.
    *   Ensure the "Disabled" status of the crawling node is mentioned.