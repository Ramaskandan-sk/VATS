

---

# 🎬 VATS



![Python](https://img.shields.io/badge/Python-3.9+-blue.svg)
![Whisper](https://img.shields.io/badge/OpenAI-Whisper-green)
![Gemini](https://img.shields.io/badge/Google-Gemini-orange)
![Platform](https://img.shields.io/badge/Platform-Google%20Colab-yellow)
![License](https://img.shields.io/badge/License-MIT-lightgrey)

An AI-powered video processing pipeline that:

* Downloads YouTube videos
* Extracts audio using FFmpeg
* Transcribes speech using OpenAI Whisper
* Generates structured summaries using Google Gemini
* Exports results into a clean Markdown file

Designed for Google Colab with optional GPU acceleration.

---

## 🚀 Features

* YouTube video transcription
* Local video file upload support
* Automatic audio extraction (FFmpeg)
* GPU support (CUDA detection)
* Smart content classification:

  * Music/Lyrics detection (no summary generated)
  * Meeting detection → Generates structured MoM
  * Lecture/Vlog/Tutorial → Point-wise summary
* Clean Markdown export (`output.md`)
* Structured, readable AI formatting

---

## 🧠 Architecture Overview

```
User Input (YouTube URL / Upload)
            │
            ▼
     yt-dlp Download
            │
            ▼
      FFmpeg Audio Extract
            │
            ▼
     Whisper Transcription
            │
            ▼
   Gemini Content Analysis
            │
            ▼
      Structured Summary
            │
            ▼
        output.md Export
```

---

## 🏗 Tech Stack

| Layer            | Technology      |
| ---------------- | --------------- |
| Language         | Python          |
| Speech-to-Text   | OpenAI Whisper  |
| LLM              | Google Gemini   |
| Video Download   | yt-dlp          |
| Audio Processing | FFmpeg          |
| Hardware         | CUDA (optional) |
| Platform         | Google Colab    |

---

## 📦 Installation (Google Colab)

### 1️⃣ Install Dependencies

```python
!pip install -q -U yt-dlp openai-whisper ffmpeg-python google-generativeai
!apt-get -y install ffmpeg
```

---

### 2️⃣ Configure Gemini API Key

In Google Colab:

1. Open **Settings → Secrets**
2. Add:

```
Name: GEMINI_API_KEY
Value: your_api_key_here
```

The script will stop if the key is missing.

---

## ▶️ Usage

When executed, the program prompts:

```
1 - Transcribe YouTube URL
2 - Upload a video file
```

---

### Option 1 – YouTube Mode

* Enter video URL
* Duration validated (default: max 20 minutes)
* Video downloaded
* Audio extracted
* Transcription generated
* Optional AI summary
* `output.md` generated

---

### Option 2 – Upload Mode

* Upload local video
* Convert to audio
* Transcribe
* Optional summary
* `output.md` generated

---

## 🧾 Output Format

Generated file: `output.md`

```markdown
# Transcript Output

## Transcript
(full transcript)

---

## Summary
(structured AI summary)

---
```

---

## 🧠 Intelligent Content Handling

### 🎵 Music / Song Lyrics

If detected, system responds exactly:

```
This content appears to be music or song lyrics, so I will not summarize it.
```

---

### 🏢 Meetings

Generates structured **Minutes of Meeting** including:

* Agenda
* Key discussion points
* Decisions taken
* Action items
* Responsible persons (if available)

---

### 🎓 Other Content

Produces:

* Structured point-wise summary
* Bold important highlights
* Clean formatting
* No long transcript copying

---

## ⚙️ Configuration

### Change Whisper Model

```python
WHISPER_MODEL_NAME = "small"
```

Available options:

* tiny
* base
* small
* medium
* large

---

### Change Gemini Model

```python
GEMINI_MODEL = "gemini-flash-latest"
```

---

### Modify Duration Limit

```python
process_youtube(url, max_minutes=20)
```

---

## ⚡ GPU Acceleration

The system automatically detects CUDA:

```python
device = "cuda" if torch.cuda.is_available() else "cpu"
```

GPU significantly improves transcription speed.

---

## 🛑 Limitations

* Max YouTube duration default: 20 minutes
* Transcript truncated to 9000 characters before Gemini processing
* Requires internet access
* Large videos increase processing time

---

## 🔮 Future Enhancements

* Timestamp-based transcript export
* Speaker diarization
* Multi-language auto detection
* Chapter-wise summarization
* PDF export
* Web UI (Streamlit / Flask)
* Docker support
* REST API version

---

## 📁 Suggested Repository Structure

```
ai-video-transcriber/
│
├── notebook.ipynb
├── README.md
├── requirements.txt
└── sample_output.md
```

---

## 🧪 Example Use Cases

* Lecture summarization
* Meeting documentation automation
* Podcast summarization
* YouTube content analysis
* Educational content extraction
* Research video breakdown

---

