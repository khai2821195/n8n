# DCT 트렌드 기반 블로그 자동작성 260314

> **Category:** DCT  
> **Workflow ID:** `ovShsLWKGcrOOgnE`  
> **노션 메뉴얼:** https://www.notion.so/323c6a06e17e818ba6d1f28ccacaeed0  
> **자동 생성:** Gemini AI  

---

n8n Workflow Expert.
Analyze a provided n8n workflow JSON and create a GitHub `README.md` in Korean.
"DCT 트렌드 기반 블로그 자동작성 260314" (DCT Trend-based Blog Auto-Writer).
`ovShsLWKGcrOOgnE`.
DCT.

        *   `node-schedule`: Trigger every Sunday at 9 AM.
        *   `node-season`: Code node calculating current date, season, special events, and generating a blog title.
        *   `node-trend`: HTTP Request to Naver DataLab API (Shopping categories: Promotional items, Gift sets, Return gifts).
        *   `node-merge`: Code node combining season info and trend data.
        *   `node-prompt1`: Code node constructing a prompt for an AI (DCT Company blog marketer persona).
        *   `node-ai1`: HTTP Request to Google Gemini API (`gemma-3-12b-it`) to generate the blog content.
        *   `node-extract1`: (Cut off in JSON, but clearly for extracting the AI response).

    *   *Purpose:* Automatically generate a weekly Naver blog post for "DCT Company" (a promotional goods supplier) based on current seasonal trends and real-time Naver shopping search data.
    *   *Flow:* Schedule $\rightarrow$ Season Calculation $\rightarrow$ Naver Trend Data $\rightarrow$ Data Merging $\rightarrow$ Prompt Engineering $\rightarrow$ AI Generation $\rightarrow$ Extraction.

    *   *Title:* DCT 트렌드 기반 블로그 자동작성 워크플로우.
    *   *Description:* A system that analyzes seasonal events and Naver shopping trends to create SEO-optimized blog posts for promotional products.
    *   *Key Features:*
        *   Automatic weekly scheduling.
        *   Seasonal context awareness (Spring/Summer/Autumn/Winter).
        *   Real-time data integration via Naver DataLab API.
        *   AI-powered content generation using Google Gemini (Gemma).
    *   *Workflow Steps:*
        1.  **Trigger:** Every Sunday 09:00.
        2.  **Season Info:** Calculate month, week, and relevant events (e.g., graduation, Chuseok).
        3.  **Trend Collection:** Fetch search ratios for "Promotional items," "Gift sets," and "Return gifts" from Naver.
        4.  **Data Merge:** Combine seasonal context and trend numbers.
        5.  **Prompting:** Create a detailed persona-based prompt for the AI.
        6.  **AI Generation:** Call Gemini API to write the post (Title, Body, Hashtags).
        7.  **Extraction:** Parse the JSON response.
    *   *Requirements:*
        *   Naver API Client ID & Secret.
        *   Google Gemini API Key (Environment variable: `GEMINI_API_KEY`).

    *   Use professional and clear Korean.
    *   Use Markdown formatting (headers, lists, code blocks).
    *   Ensure the structure follows the user's "README 작성 규칙".