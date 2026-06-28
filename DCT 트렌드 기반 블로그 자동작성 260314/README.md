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

        *   `node-schedule`: Schedule Trigger (Every Sunday at 9 AM).
        *   `node-season`: Code node (Calculates current date, season, special events, and generates a blog title).
        *   `node-trend`: HTTP Request (Naver DataLab API - Shopping categories: Promotional items, Gift sets, Return gifts).
        *   `node-merge`: Code node (Combines seasonal info and Naver trend data).
        *   `node-prompt1`: Code node (Constructs a detailed prompt for the AI, acting as a marketer for "DCT Company").
        *   `node-ai1`: HTTP Request (Google Gemini API - `gemma-3-12b-it` model).
        *   `node-extract1`: Code node (Extracts the response - though the JSON is cut off, the intent is clear: parsing the AI's JSON output).

    *   *Purpose:* Automatically generate a weekly blog post for "DCT Company" (a promotional goods supplier) based on current seasonal trends and real-time Naver shopping data.
    *   *Flow:*
        1.  Trigger: Weekly (Sunday 9 AM).
        2.  Context: Determine season/events (e.g., Graduation in March).
        3.  Data: Fetch Naver Shopping trends for specific categories.
        4.  Synthesis: Merge context and data.
        5.  Prompting: Create a structured prompt for a professional blog post.
        6.  Generation: Use Gemini AI to write the content.
        7.  Extraction: Parse the final blog post.

    *   *Title:* DCT 트렌드 기반 블로그 자동작성 워크플로우.
    *   *Description:* A system that analyzes seasonal trends and Naver shopping data to automatically draft promotional blog posts for DCT Company.
    *   *Key Features:*
        *   Automatic scheduling.
        *   Seasonal context awareness.
        *   Real-time Naver DataLab integration.
        *   AI-driven content generation (Gemini).
    *   *Workflow Steps:*
        1.  **Trigger**: Weekly schedule.
        2.  **Season Info**: JavaScript logic to define the current season and special events.
        3.  **Trend Collection**: Naver API call for "Promotional items", "Gift sets", "Return gifts".
        4.  **Data Merge**: Combining seasonal and trend data.
        5.  **Prompting**: Setting the persona (DCT Marketer) and rules.
        6.  **AI Generation**: Calling Gemini API.
        7.  **Extraction**: Parsing the JSON response.
    *   *Requirements:*
        *   Naver API (Client ID, Secret).
        *   Google Gemini API Key.
    *   *Notes:* Mention the specific model used (`gemma-3-12b-it`).

    *   Ensure professional tone.
    *   Use clear headings.
    *   Check for consistency with the provided JSON.