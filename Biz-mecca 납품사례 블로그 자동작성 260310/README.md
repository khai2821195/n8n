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

        *   `node-form` (Form Trigger): Collects product name, description, client name, client type, quantity, product URL, and notes.
        *   `node-set-inputs` (Set): Organizes the form inputs into clean variables.
        *   `node-jina` (HTTP Request): Crawls the product URL (currently disabled).
        *   `node-parse-product` (Code): Parses the crawled HTML/text to extract product info (incomplete JSON provided, but the intent is clear).

        1.  Clear purpose and operation method.
        2.  Sequential node flow (Trigger $\rightarrow$ Process $\rightarrow$ Output).
        3.  Environment variables/Credentials.
        4.  Precautions/Special notes.
        5.  Markdown format.
        6.  Output *only* the README.md content.

    *   *Purpose:* To automate the creation of Naver Blog drafts based on delivery case information entered via a form.
    *   *User Journey:* User fills out a form $\rightarrow$ Data is cleaned $\rightarrow$ (Optional) Product page is crawled for more detail $\rightarrow$ (Implied) AI generates a blog post (though the JSON cuts off, the name says "Auto-Writer").
    *   *Key Inputs:* Product name, description, client, client type, quantity, URL, memo.

    *   *Title:* Biz-mecca 납품사례 블로그 자동작성 (Biz-mecca Delivery Case Blog Auto-Writer).
    *   *Overview:* A workflow that transforms delivery data into a blog draft.
    *   *Workflow Steps:*
        1.  **Form Trigger:** User input.
        2.  **Set Node:** Data mapping.
        3.  **HTTP Request (Optional):** Web scraping of the product page.
        4.  **Code Node:** Text cleaning and parsing.
    *   *Requirements:* n8n instance, (likely) an LLM API key (though not explicitly in the snippet, "Auto-Writer" implies AI), and a Naver Blog API or just a final text output.

    *   *Header:* # Biz-mecca 납품사례 블로그 자동작성
    *   *Description:* 납품 정보를 입력하면 네이버 블로그 포스팅 초안을 자동으로 생성하는 n8n 워크플로우입니다.
    *   *Flow:*
        1.  `납품사례 폼 입력`: 사용자로부터 제품명, 거래처, 수량 등의 정보를 입력받습니다.
        2.  `입력값 정리`: 입력된 데이터를 표준 변수명으로 매핑하여 후속 노드에서 사용하기 쉽게 정리합니다.
        3.  `제품 URL 크롤링` (선택적): 비즈메카 제품 상세 페이지의 내용을 가져와 더 풍부한 정보를 확보합니다.
        4.  `제품 정보 파싱`: 크롤링된 HTML 데이터에서 불필요한 태그를 제거하고 텍스트를 정제합니다.
    *   *Credentials:* HTTP Request (if using specific proxies), AI API (if integrated later).
    *   *Notes:* The crawling node is currently disabled.

    *   Ensure professional tone.
    *   Use clear bullet points.
    *   Check against the JSON provided.