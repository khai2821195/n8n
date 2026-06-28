# DCT 트렌드 기반 블로그 자동작성 260314

> **Category:** DCT  
> **Workflow ID:** `ovShsLWKGcrOOgnE`  
> **노션 메뉴얼:** https://www.notion.so/323c6a06e17e818ba6d1f28ccacaeed0  
> **자동 생성:** Gemini AI  

---

n8n Workflow Expert.
Analyze a provided n8n workflow JSON and write a GitHub `README.md` in Korean.
"DCT 트렌드 기반 블로그 자동작성 260314" (DCT Trend-based Blog Auto-Writer).
`ovShsLWKGcrOOgnE`.
DCT.

        *   `node-schedule`: Schedule Trigger (Every Sunday at 9 AM).
        *   `node-season`: Code node (Calculates current date, season, special events, and generates a blog title).
        *   `node-trend`: HTTP Request (Naver DataLab Shopping API - fetches trends for promotional items, gift sets, and return gifts).
        *   `node-merge`: Code node (Combines seasonal info and Naver trend data).
        *   `node-prompt1`: Code node (Constructs a detailed prompt for the AI, acting as a DCT Company marketer).
        *   `node-ai1`: HTTP Request (Google Gemini API - `gemma-3-12b-it` model - generates the blog post content).
        *   `node-extract1`: Code node (Extracts the AI response - though the JSON is cut off, the intent is clear).

    *   *Purpose:* Automatically generate a weekly Naver blog post for "DCT Company" (a promotional goods supplier) based on current seasonal trends and real-time Naver shopping data.
    *   *Flow:*
        1.  Trigger: Weekly (Sunday 9 AM).
        2.  Context: Determine season/events (e.g., graduation, holidays).
        3.  Data: Fetch Naver Shopping trends for specific categories (Promotional items, etc.).
        4.  Prompting: Create a structured prompt for the AI (Role: Marketer, Goal: TOP 5 recommendations).
        5.  Generation: Use Gemini AI to write the post in JSON format.
        6.  Post-processing: Extract content (implied).

    *   *Title:* DCT 트렌드 기반 블로그 자동작성 워크플로우
    *   *Introduction:* Explain that this automates marketing content creation for DCT Company.
    *   *Key Features:* Seasonal analysis, Naver DataLab integration, AI-driven content generation.
    *   *Workflow Steps:*
        *   Step 1: Schedule Trigger.
        *   Step 2: Seasonal Info Calculation.
        *   Step 3: Naver Trend Collection.
        *   Step 4: Data Merging.
        *   Step 5: AI Prompting.
        *   Step 6: AI Content Generation.
    *   *Requirements:*
        *   Naver API (Client ID/Secret).
        *   Google Gemini API Key.
    *   *Technical Details:* Model used (`gemma-3-12b-it`), API endpoints.