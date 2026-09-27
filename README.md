# CareerLens AI — Streamlit Prototype

A simple portfolio prototype for resume NLP analysis and company-style interview practice.

## Scope

This is intentionally **not a full website** and does not contain an AI chatbot/assistant.

Flow:

Home
→ Resume Upload/Paste
→ NLP Resume Analysis
→ ATS Compatibility Score
→ Interview Dashboard
→ Timed/Practice Interview
→ Speech-to-Text
→ Question-wise Analysis
→ Interview Report

## Main technologies

- Python
- Streamlit
- NLTK
- spaCy
- Gensim
- Scikit-learn
- Matplotlib
- Regex
- PyMuPDF
- Pillow + Tesseract OCR
- faster-whisper

## Setup

### 1. Create environment

```bash
python -m venv .venv
```

Windows:

```bash
.venv\Scripts\activate
```

### 2. Install packages

```bash
pip install -r requirements.txt
```

### 3. Download NLTK resources

Run:

```bash
python -c "import nltk; [nltk.download(x) for x in ['punkt','punkt_tab','stopwords','wordnet','omw-1.4','averaged_perceptron_tagger','averaged_perceptron_tagger_eng']]"
```

### 4. Download spaCy model

```bash
python -m spacy download en_core_web_sm
```

### 5. Tesseract

For JPG/PNG OCR, install Tesseract OCR separately and make sure it is available on PATH.

### 6. Run

```bash
streamlit run app.py
```

## Prototype notes

- ATS score is a transparent heuristic created for this prototype. It is not an actual employer ATS score.
- Company questions are practice questions, not official interview questions.
- Speech-to-text is optional. If faster-whisper cannot initialize, the user can type the transcript.
- Browser SpeechSynthesis is used for interviewer text-to-speech.
- The application intentionally avoids databases, authentication, chatbot features, job-description matching, and unnecessary pages.


## Interview voice + timer
- The interview microphone uses Streamlit's browser `st.audio_input`.
- Audio is passed to `faster-whisper` with the correct browser container type.
- The Whisper model is cached after first use, so later questions do not reload it.
- The transcript is shown for review and is then evaluated against the question's expected concepts.
- Timed mode displays a 60-second per-question countdown and resets when the next question begins.
- The report aggregates concept coverage, relevance, filler words, answer length, strengths and improvement areas.
