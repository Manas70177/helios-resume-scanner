# 🌟 Helios Resume Scanner

**AI-powered resume screening tool** built with Google Gemini 2.0 Flash.  
Zero backend. Runs entirely in the browser. Free to use.

---

## 🚀 Live Demo

Open `helios_resume_scanner.html` in any browser. No installation needed.

---

## 🎯 Selected Problem

**Manual resume screening is slow, inconsistent, and biased.**  
Recruiters spend 6–8 seconds per resume. For 80 candidates, that's hours of work with subjective results.

---

## ✅ Solution

Helios automates the screening pipeline:

1. **Paste a Job Description** — any role, any company
2. **Add candidates** — upload `.docx` or `.pdf`, paste text, or import a CSV
3. **Click "Scan Resumes"** — Gemini AI scores each resume against the JD in seconds
4. **Review ranked results** — with scores, strengths, gaps and "Why this score?" AI explanations
5. **Export CSV** — for documentation and audit trail

---

## 📐 Approach

Each resume is compared to the JD using a **4-dimension structured prompt** sent to Gemini 2.0 Flash:

| Dimension | Weight |
|---|---|
| Technical Skills Match | 40% |
| Experience Relevance | 30% |
| Education & Certifications | 15% |
| Communication Quality | 15% |

Scores are 0–100. Candidates are banded into: Top Tier / Strong Fit / Good Fit / Moderate / Borderline / Not Fit.

The model returns structured JSON parsed directly into the UI — no regex, no parsing fragility.

---

## 🛠 Tools & Technologies

| Tool | Purpose |
|---|---|
| **Google Gemini 2.0 Flash API** | AI resume scoring engine |
| **mammoth.js** | Browser-based `.docx` text extraction |
| **PDF.js (Mozilla)** | Browser-based `.pdf` text extraction |
| **React 18** | Frontend UI (via CDN, zero build tools) |
| **Vanilla CSS** | Styling — no framework |
| **Browser Blob API** | CSV export |

---

## 📁 Files

```
helios_resume_scanner.html     ← The entire app (single file)
helios_80_candidates.csv       ← 80 sample candidates with resumes & pre-scores
README.md                      ← This file
```

---

## 🔑 Setup

1. Get a free Gemini API key from [aistudio.google.com](https://aistudio.google.com)
2. Open `helios_resume_scanner.html` in Chrome/Firefox/Edge
3. Paste your API key in the banner
4. Add candidates and click **Scan Resumes**

> **No API key needed** to explore pre-scored candidates — just click "Load 80 samples" and hit Scan.

---

## 📄 CSV Import Format

```csv
name,resume_text,score,recommendation,experience_years,top_skill,strength1,strength2,strength3,gap1,gap2,gap3,summary
Arjun Sharma,"Senior Data Analyst...",96,Strong Fit,...
```

- `name` + `resume_text` are **required**
- If `score > 0`, the candidate is pre-scored and **skips AI analysis**
- If no score, the candidate goes to the AI analysis queue

---

## 🏗 Architecture

```
Browser Only (no server)
├── React 18 (state management, UI)
├── mammoth.js (DOCX → text)
├── PDF.js (PDF → text)
├── Gemini API (resume analysis)
└── Blob API (CSV export)
```

---

## 📊 Sample Dataset

`helios_80_candidates.csv` contains 80 realistic Indian data analyst candidates:
- **36 Strong Fit** (score ≥ 75)
- **22 Moderate Fit** (score 50–74)  
- **22 Not Fit** (score < 50)

Score range: 5–96. All have detailed resume text, strengths, gaps and summaries.

---

## ⚖️ Ethics Note

AI scores are a **screening aid, not a final decision**. All scores must be reviewed by a human. The system evaluates skills and experience only — not names, gender, or location.

---

*Built with ❤️ using Google Gemini AI · Single-file, zero-dependency frontend*
