

#  Research Assistant (LangChain + OpenAI/Anthropic)

A lightweight **AI-powered research assistant** that can query the web, summarize findings, and save structured outputs.
Built with **LangChain**, **OpenAI**, and **Anthropic** LLMs, with extensible tools for search and Wikipedia lookups.

---

## Project Structure

```
.
├── main.py      # Core app logic (agent + execution)
├── tools.py     # Custom tools (search, wiki, save-to-file)
├── .env         # Environment variables (API keys)
└── research_output.txt  # Auto-saved research results
```

---

##  Features

* **Multi-LLM Support**
  Uses both `ChatOpenAI` and `ChatAnthropic` models for flexible reasoning.

* **Search Integration**

  * DuckDuckGo Search (`DuckDuckGoSearchRun`)
  * Wikipedia Lookup (`WikipediaQueryRun`)

* **Custom Tools**

  * `search_tool` → DuckDuckGo search
  * `wiki_tool` → Wikipedia query
  * `save_tool` → Appends research results with timestamp to `research_output.txt`

* **Structured Outputs**
  Responses parsed into a `ResearchResponse` model:

  ```python
  class ResearchResponse(BaseModel):
      topic: str
      summary: str
      sources: list[str]
      tools_used: list[str]
  ```

---

##  API Keys & Environment Setup

This project needs keys for OpenAI and (optionally) Anthropic.
They are loaded using `dotenv`.

Create a `.env` file in the root directory:

```ini
OPENAI_API_KEY=your_openai_api_key_here
ANTHROPIC_API_KEY=your_anthropic_api_key_here
```

> Only the keys you actually need must be set. If you use only OpenAI, Anthropic is optional.

Install dependencies:

```bash
pip install -r requirements.txt
```

Example `requirements.txt`:

```
langchain
langchain-community
langchain-openai
langchain-anthropic
python-dotenv
pydantic
duckduckgo-search
wikipedia
```

---

##  Usage

Run the research agent:

```bash
python main.py
```

Example flow:

1. You give the agent a **topic/question**.
2. It queries DuckDuckGo and/or Wikipedia.
3. Summarizes findings using OpenAI/Anthropic.
4. Saves results into `research_output.txt`.

---

##  Example Output

```
--- Research Output ---
Timestamp: 2025-08-30 21:10:22

Topic: Generative AI in Healthcare
Summary: GenAI is being applied to medical documentation, patient interaction...
Sources: [DuckDuckGo, Wikipedia]
Tools Used: ['search_tool', 'wiki_tool']
```


Do you want me to also **write the README.md file itself with code blocks** so you can directly push it to your repo?
