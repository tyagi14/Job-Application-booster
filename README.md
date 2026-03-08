# 🚀 Job Application Booster using CrewAI

An intelligent multi-agent AI system that automates and supercharges your entire job application process — from analyzing job postings to tailoring your resume and preparing you for interviews — built with [CrewAI](https://github.com/crewAIInc/crewAI).

## 🧠 Overview

This project uses **4 specialized AI agents** that collaborate sequentially to:
1. Analyze a job posting URL and extract key requirements
2. Build a detailed personal & professional profile from your GitHub and bio
3. Tailor your resume to perfectly match the job
4. Generate interview questions and talking points based on your tailored resume

## 🏗️ Architecture

```
Job Posting URL + Candidate Info
        │
        ▼
┌─────────────────────────┐
│  🔍 Tech Job Researcher  │  → Extracts skills, experience & qualifications from job posting
└────────────┬────────────┘
             ▼
┌──────────────────────────────────┐
│  👤 Personal Profiler for Engineers │  → Builds profile from GitHub + personal write-up
└────────────────┬─────────────────┘
                 ▼
┌──────────────────────────────────┐
│  📝 Resume Strategist for Engineers │  → Tailors resume to match job requirements
└────────────────┬─────────────────┘
                 ▼
┌──────────────────────────────────────┐
│  🎤 Engineering Interview Preparer   │  → Generates interview Q&A and talking points
└──────────────────────────────────────┘
        │
        ▼
  📄 tailored_resume.md  +  📋 interview_materials.md
```

## 🤖 Agents & Tasks

| Agent | Role | Output |
|-------|------|--------|
| **Tech Job Researcher** | Scrapes and analyzes job posting URL | Skills, qualifications & requirements breakdown |
| **Personal Profiler for Engineers** | Scans GitHub profile + personal bio | Comprehensive candidate profile |
| **Resume Strategist for Engineers** | Aligns resume with job requirements | `tailored_resume.md` |
| **Engineering Interview Preparer** | Builds interview prep from resume + job | `interview_materials.md` |

Each agent uses:
- `SerperDevTool` — web search
- `ScrapeWebsiteTool` — scrape job postings & GitHub
- `FileReadTool` — read local resume/profile files
- `MDXSearchTool` — search markdown documents

## 🔄 Workflow

```
Inputs:
  - job_posting_url        → URL of the job you're applying to
  - github_url             → Your GitHub profile URL
  - personal_writeup       → Short bio about yourself

Outputs:
  - tailored_resume.md     → Resume tailored to the specific job
  - interview_materials.md → Interview questions + talking points
```

## 🚀 Getting Started

### Prerequisites

- Python >= 3.10 and <= 3.13
- OpenAI API Key
- Serper API Key (for web search)

### Installation

```bash
# Clone the repository
git clone https://github.com/your-username/Job-Application-Booster-CrewAI.git
cd Job-Application-Booster-CrewAI

# Install dependencies
pip install -r requirements.txt
```

### Environment Variables

Create a `.env` file in the root directory:

```env
OPENAI_API_KEY=your_openai_api_key_here
OPENAI_MODEL_NAME=gpt-4-turbo
SERPER_API_KEY=your_serper_api_key_here
```

> ⚠️ **Never commit your `.env` file or API keys to GitHub!**

### Prepare Your Files

Place the following files in the project root before running:
- `fake_resume.md` — your current resume in Markdown format

### Configure Your Inputs

In the notebook, update the `job_application_inputs` dictionary:

```python
job_application_inputs = {
    'job_posting_url': 'https://jobs.example.com/your-target-job',
    'github_url': 'https://github.com/your-username',
    'personal_writeup': """Your name and a short professional bio describing
    your experience, skills, and what kind of roles you are targeting."""
}
```

### Run the Notebook

Open `Job_Application_booster_practice.ipynb` in Jupyter or Google Colab and run all cells.

### View Outputs

After the crew finishes, two files will be generated:

```bash
tailored_resume.md        # Your resume tailored to the specific job
interview_materials.md    # Interview questions & talking points
```

## 📦 Dependencies

| Package | Purpose |
|---------|---------|
| `crewai` | Multi-agent orchestration framework |
| `crewai_tools` | SerperDev, ScrapeWebsite, FileRead, MDXSearch tools |
| `openai` | GPT-4 / GPT-3.5 API |
| `python-dotenv` | Environment variable management |
| `langchain-openai` | LLM integration |

Install all with:

```bash
pip install -r requirements.txt
```

## 📁 Project Structure

```
Job-Application-Booster-CrewAI/
│
├── Job_Application_booster_practice.ipynb  # Main notebook
├── fake_resume.md                           # Your input resume (you provide this)
├── tailored_resume.md                       # Output: tailored resume (auto-generated)
├── interview_materials.md                   # Output: interview prep (auto-generated)
├── requirements.txt                         # Python dependencies
├── .env.example                             # Example environment variables
├── .gitignore                               # Files excluded from Git
└── README.md                                # Project documentation
```

## 💡 Use Cases

- **Job seekers** who want to tailor their resume for every application automatically
- **Career switchers** who need help aligning their existing skills to new roles
- **Developers** learning how to build agentic AI pipelines with CrewAI
- **Anyone** who wants AI-powered interview preparation

## ⚠️ Disclaimer

This project is for **educational and personal productivity purposes**. Always review and verify AI-generated resume content before submitting to employers. Do not fabricate experience or qualifications.

## 📜 License

This project is licensed under the MIT License. See [LICENSE](LICENSE) for details.
