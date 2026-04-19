# LLM Engineering Learning Repository

A hands-on portfolio demonstrating **production-grade LLM engineering techniques** through practical projects.

## 📋 Project: Company Brochure Generator

**What it does:** Automatically generates professional company brochures from website content using LLM intelligence.

### Architecture

```
User Input (URL) 
    ↓
Website Scraper (BeautifulSoup)
    ↓
LLM Link Analyzer (GPT-4o-mini + One-Shot Prompting)
    ↓
Multi-Page Content Extractor
    ↓
LLM Brochure Generator (Streaming Output)
    ↓
Formatted Markdown Brochure
```

### Key LLM Engineering Concepts

#### 1. **Prompt Engineering & One-Shot Learning**
- Uses structured JSON prompts with example outputs
- Teaches the model to filter links intelligently without extensive fine-tuning
- File: `week1day5.ipynb` cells 10-12

#### 2. **Structured API Outputs**
- Enforces JSON response format: `response_format={"type": "json_object"}`
- Ensures reliable parsing and error handling
- Demonstrates production-level API usage

#### 3. **Chaining LLM Calls (Agentic Pattern)**
- Step 1: Analyze links → Step 2: Extract content → Step 3: Generate brochure
- Shows how to compose multiple LLM requests into a cohesive workflow
- Real-world pattern used in multi-step reasoning tasks

#### 4. **Streaming & Real-Time Output**
- Uses `stream=True` for incremental response generation
- Implements dynamic display updates (typewriter effect)
- File: `week1day5.ipynb` cell 25-26
- Shows understanding of modern LLM API patterns

#### 5. **Production Patterns**
- **Environment Management:** Secure API key loading from `.env` with validation
- **Reusable Abstractions:** Website class for clean separation of concerns
- **Error Handling:** API key verification, fallback content extraction
- **HTTP Headers:** Proper User-Agent spoofing for web scraping reliability

---

## 🚀 Quick Start

### Prerequisites
- Python 3.8+
- OpenAI API key (GPT-4o-mini)
- Internet connection (for website scraping)

### Setup

```bash
# 1. Clone or open the repo
cd "/Users/nusratjahan/Desktop/8 weeks of llm engineering"

# 2. Create virtual environment
python -m venv .venv
source .venv/bin/activate

# 3. Install dependencies
pip install -r requirements.txt

# 4. Add your API key
# The .env file already contains OPENAI_API_KEY
# Verify it's set before running
```

### Run the Notebook

```bash
jupyter lab
# Open week1day5.ipynb and run all cells sequentially
```

### Example Usage

```python
# Generate a brochure for any company
stream_brochure("Anthropic", "https://anthropic.com")

# Or use the non-streaming version
create_brochure("HuggingFace", "https://huggingface.co")
```

**Output:** A formatted markdown brochure with:
- Company overview
- Culture & values
- Customer information
- Career opportunities

---

## 📚 Learning Outcomes

By studying this project, you'll understand:

- ✅ How to design multi-step LLM workflows
- ✅ Prompt engineering for intelligent decision-making
- ✅ Streaming APIs for real-time user experiences
- ✅ Production patterns: error handling, security, modularity
- ✅ Web scraping + NLP integration
- ✅ API orchestration (multiple calls in sequence)

---

## 🏗️ Project Structure

```
8 weeks of llm engineering/
├── week1day5.ipynb           # Main notebook with all implementations
├── requirements.txt          # Python dependencies
├── .env                       # API keys (git-ignored, local only)
├── .github/
│   └── copilot-instructions.md  # AI agent guidance for developers
└── README.md                 # This file
```

---

## 🔑 Key Files to Review

| File | Purpose |
|------|---------|
| `week1day5.ipynb` | Complete notebook with all code and explanations |
| `requirements.txt` | Dependencies: openai, langchain, requests, beautifulsoup4, etc. |
| `.github/copilot-instructions.md` | Developer onboarding guide for AI agents |

---

## 💡 Technical Highlights

### Web Scraping + LLM Intelligence
```python
# Scrapes website and extracts clean text
website = Website("https://example.com")

# Uses LLM to intelligently filter relevant links
relevant_links = get_links(url)
```

### Prompt Engineering Example
```python
# One-shot prompting: provide example, model follows pattern
link_system_prompt = """
You are provided with links. Respond in JSON like:
{
    "links": [
        {"type": "about page", "url": "https://..."},
        {"type": "careers page", "url": "https://..."}
    ]
}
"""
```

### Streaming Output
```python
# Real-time brochure generation
stream = openai.chat.completions.create(
    model="gpt-4o-mini",
    messages=[...],
    stream=True  # ← Key for real-time output
)
for chunk in stream:
    display_incrementally(chunk)
```

---

## 🎓 For Teachers / Evaluators

**This project demonstrates:**
- Understanding of LLM capabilities and limitations
- Ability to design reliable AI workflows
- Knowledge of production patterns (error handling, security, modularity)
- Practical skill with OpenAI API and modern Python practices
- Real-world problem-solving (web scraping + content generation)

**Skill Level:** Intermediate → Advanced LLM Engineering

---

## 📝 Notes

- All API calls use `gpt-4o-mini` for cost efficiency while maintaining quality
- The notebook can be easily adapted to generate different types of documents (marketing copy, technical specs, etc.)
- Streaming output demonstrates understanding of modern LLM patterns
- Project is self-contained and reproducible with standard dependencies

---

## 🔗 Related Concepts

- **Prompt Chaining:** Multi-step reasoning with sequential API calls
- **Structured Outputs:** Enforcing format compliance for downstream processing
- **Streaming APIs:** Real-time response generation
- **Web Scraping + LLM:** Combining traditional data extraction with AI analysis
- **Agentic AI:** Foundation for autonomous multi-step workflows

---

## ✨ Future Enhancements

- Add caching for repeated website fetches
- Support for other LLM providers (Anthropic, Google, Ollama)
- Export brochures to PDF/HTML formats
- Batch processing for multiple companies
- Fine-tuned prompt optimization for specific industries

---

**Last Updated:** April 2026  
**Maintainer:** Nusrat Jahan (@nj25suha)
