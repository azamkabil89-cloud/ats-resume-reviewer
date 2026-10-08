# ATS Resume Analyzer

A Streamlit app that lets a user upload a resume and receive an ATS-focused score plus practical improvement suggestions using Google's Gemini Flash model.

## Files

- `app.py` — Streamlit application.
- `requirements.txt` — Python dependencies.
- `README.md` — setup, GitHub, and Streamlit deployment instructions.

## 1. Run locally

Use Python 3.10+.

```bash
pip install -r requirements.txt
```

Set your Gemini API key.

### Windows PowerShell

```powershell
$env:GEMINI_API_KEY="YOUR_GEMINI_API_KEY"
streamlit run app.py
```

### macOS/Linux

```bash
export GEMINI_API_KEY="YOUR_GEMINI_API_KEY"
streamlit run app.py
```

The app supports PDF, DOCX, and TXT resumes. If Gemini is unavailable, it falls back to a basic local ATS check instead of crashing.

## 2. Push to GitHub using the GitHub website UI

1. Sign in to GitHub.
2. Click **+** in the top-right and choose **New repository**.
3. Give it a name such as `ats-resume-analyzer` and create the repository.
4. Open the repository and click **Add file → Upload files**.
5. Upload exactly these three files:
   - `app.py`
   - `requirements.txt`
   - `README.md`
6. Click **Commit changes**.

**Never upload your Gemini API key or a `.env` file containing the key.**

## 3. Deploy on Streamlit Community Cloud

1. Open Streamlit Community Cloud and sign in with GitHub.
2. Choose **Create app**.
3. Select your GitHub repository, branch (usually `main`), and file path `app.py`.
4. Open the app's **Secrets** settings.
5. Add:

```toml
GEMINI_API_KEY = "YOUR_GEMINI_API_KEY"
```

6. Save the secret and deploy/reboot the app.

The app reads the key from Streamlit Secrets first and from `GEMINI_API_KEY` locally.

## 4. What the app checks

The AI review considers:

- ATS readability
- Section structure
- Keyword coverage
- Measurable achievements
- Clarity
- Formatting issues
- Missing keywords
- Practical improvement actions

The score is an estimate and is not an official score from any employer's ATS.

## 5. Important notes

- The app analyzes extracted text. Scanned/image-only PDFs may need OCR.
- The code currently uses `gemini-2.5-flash`. If your Google AI account does not offer that model, replace the model name in `app.py` with a currently available Flash model.
- Keep API keys private and never commit them to GitHub.
