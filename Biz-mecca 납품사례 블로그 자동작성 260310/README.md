# Biz-mecca 납품사례 블로그 자동작성 260310

> **Category:** DCT  
> **Workflow ID:** `ruLfwzGZtsmLSD3k`  
> **노션 메뉴얼:** https://www.notion.so/323c6a06e17e8101b97ac00492a67ddd  
> **자동 생성:** Gemini AI  

---

n8n Workflow Expert.
Analyze a provided n8n workflow JSON and write a GitHub `README.md` in Korean.
"Biz-mecca 납품사례 블로그 자동작성 260310" (Biz-mecca Delivery Case Blog Auto-Writer).
`ruLfwzGZtsmLSD3k`.
DCT.

        *   `node-form` (Form Trigger): User inputs product name, description, client name, client type, quantity, product URL, and notes.
        *   `node-set-inputs` (Set): Organizes the form inputs into clean variables.
        *   `node-jina` (HTTP Request): Crawls the product URL (currently disabled in JSON, but intended for data gathering).
        *   `node-parse-product` (Code): Parses the HTML/Text from the URL to clean up data (handles encoding issues like EUC-KR).
        *   *Note: The JSON is truncated at the end of the `node-parse-product` code, but the intent is clear: Form $\rightarrow$ Data Cleaning $\rightarrow$ Crawling $\rightarrow$ Parsing $\rightarrow$ (presumably) AI generation $\rightarrow$ Output.*

    *   *Purpose:* Automate the creation of Naver Blog drafts based on delivery case data for "Biz-mecca".
    *   *Flow:*
        1.  User fills out a form.
        2.  Inputs are standardized.
        3.  (Optional/Disabled) Product page is crawled for more details.
        4.  Crawled data is cleaned and parsed.
        5.  (Implicitly) The resulting data is used to generate a blog post.

    *   *Title:* Biz-mecca 납품사례 블로그 자동작성 워크플로우.
    *   *Overview:* A tool to convert delivery case details into blog drafts.
    *   *Workflow Steps:*
        *   Step 1: `납품사례 폼 입력` (Form Trigger) - User input.
        *   Step 2: `입력값 정리` (Set) - Data mapping.
        *   Step 3: `제품 URL 크롤링` (HTTP Request) - Fetching product info.
        *   Step 4: `제품 정보 파싱` (Code) - Cleaning HTML/Encoding.
    *   *Requirements:* n8n instance, (potentially) AI API keys (though not explicitly in the snippet, usually implied for "auto-writing").
    *   *Notes:* Mention the disabled node and the encoding handling.