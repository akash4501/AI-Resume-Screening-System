🤖 AI Resume Screening & Candidate Shortlisting System

An AI-powered Resume Screening and Candidate Shortlisting System that helps recruiters analyze resumes, extract relevant candidate information, evaluate skills, and identify candidates based on job requirements.

The project uses Natural Language Processing (NLP), Machine Learning, and Python to automate parts of the traditional resume screening process.

<img width="1466" height="816" alt="Screenshot 2026-10-01 at 10 43 58 PM" src="https://github.com/user-attachments/assets/3e3243d1-b5a6-41a8-8861-66b9f3762a22" />


Live Demo : https://ai-based-resume-screening-and-candidate-shortlisting-system-je.streamlit.app/

📌 Project Overview

Recruiters often have to manually review a large number of resumes for a single job opening. This process can be time-consuming and may make it difficult to consistently compare candidates.

This project provides an automated resume analysis system where users can upload a resume and obtain useful information from it.

The system is designed to:

📄 Read and process resumes
🔍 Extract important information from resumes
🧠 Analyze candidate skills
🎯 Compare candidate information with job requirements
📊 Assist in evaluating candidates
👨‍💼 Support candidate shortlisting
⚡ Reduce manual resume screening effort


✨ Key Features

📄 Resume Upload

Users can upload a resume through the web interface for analysis.

🔎 Resume Text Extraction

The system processes the uploaded resume and extracts readable text for further analysis.

🧠 NLP-Based Analysis

Natural Language Processing techniques can be used to process resume text and identify meaningful information such as skills, qualifications, and experience.

🛠️ Skill Identification

The system analyzes resume content to identify relevant technical and professional skills.

🎯 Candidate Evaluation

Candidate information can be compared against job-related requirements to assist in identifying relevant candidates.

📊 Candidate Shortlisting

The analysis can be used as an initial screening mechanism to help recruiters focus on candidates whose profiles match the required criteria.

🌐 Interactive Web Application

The application is built using Streamlit, providing a simple interface without requiring a separate frontend framework.

🧰 Tech Stack

Programming Language
Python
Frontend / User Interface
Streamlit

Streamlit is used to create the interactive web interface for uploading resumes and displaying analysis results.

AI / Machine Learning
Natural Language Processing (NLP)
Machine Learning
Scikit-learn (if used in the implementation)
NLTK / spaCy (depending on the NLP implementation)
Data Processing
Pandas
NumPy
Resume Processing
PDFPlumber – PDF text extraction
PyPDF2 / pypdf (if used in the implementation)
Development Tools
VS Code
Jupyter Notebook (if used during experimentation)
Git
GitHub
Deployment
Streamlit Community Cloud

The application is deployed as a public Streamlit web application. Streamlit Community Cloud supports deploying applications directly from GitHub repositories.

## Optional Gemini Candidate Evaluation Summaries

This updated version preserves the original skill-match, TF-IDF, 60/40 overall score,
ranking, shortlisting threshold, and Screening Summary. It adds a separate
**Candidate Evaluation Summary** inside each Candidate Details expander.

Install dependencies with `pip install -r requirements.txt` and run `streamlit run app.py`.
To enable Gemini, create a Gemini API key in [Google AI Studio](https://aistudio.google.com/apikey).
For local development, set environment variable `GEMINI_API_KEY`; for Streamlit Cloud,
configure `GEMINI_API_KEY` as an app secret. Do not commit keys to GitHub.
Turn on **Use Gemini AI for candidate summaries** in the sidebar before analysis.
Gemini receives resume text and the job description, so obtain candidates' permission
and follow applicable data-handling requirements. The explanation is advisory, not a
validated hiring judgement; it never changes the shortlist score. With the option off,
missing key, or API failure, the system shows an explanatory local fallback.

Gemini model configured in `src/ai_feedback.py`: `gemini-flash-latest`; update if
this alias is unavailable for your API key. Provider charges and rate limits may apply.


## Gemini Candidate Evaluation Summary (updated version)

The original score calculation, ranking table, and shortlisting threshold have **not changed**. Under **Candidate Details**, each resume now has an explanatory evaluation: evidenced strengths, missing/insufficient evidence, project relevance, practical next steps, and assessment limits. If Gemini is disabled or its API request fails, a local evidence-based summary appears instead.

### Run on Windows (PowerShell)

1. Install Python 3.10+ and open this project directory in VS Code.
2. In the terminal run:

   ```powershell
   py -m venv .venv
   .\.venv\Scripts\Activate.ps1
   pip install -r requirements.txt
   streamlit run app.py
   ```

3. Paste a job description, upload a PDF resume, and click **Analyze Candidates**. Expand a candidate under **Candidate Details**.
4. For AI-generated commentary, check **Use Gemini AI for candidate summaries** in the sidebar and enter your **own** Gemini API key in the masked password field. Alternatively, set `GEMINI_API_KEY` as a local environment variable or put it in `.streamlit/secrets.toml` (never commit the real file).
5. Use **Google AI Studio** (https://aistudio.google.com/apikey) to obtain your key. An actual Gemini response requires a working key, quota, and internet access.

### Important

- Do not upload resumes to Gemini without permission: enabling Gemini shares the extracted resume and job description text with Google's API.
- All AI feedback is explanatory, not part of ranking or the shortlist decision. The screenshot/mockup is illustrative; actual Streamlit UI uses expandable headings and text.
- An absent word is **not proof** that a candidate lacks that skill. Project quality is not confirmed from resume descriptions alone.
- The existing keyword skill database and TF-IDF similarity have limitations; in particular, C++ detection remains a known issue in the original algorithm so the original displayed scores are not changed by this update.
