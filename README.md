# 📸 SnapAudit (`snap-audit`)

> An automated, multimodal AI agent built in **Python** that analyzes, categorizes, and cleans up cluttered Google Photos libraries using **Vision LLMs** (GPT-4o / Gemini Vision).

---

## 📊 Overview & Who It's For

* **What it does:** Automatically scans personal photo libraries via official APIs, generates lightweight thumbnail previews, and uses Vision LLMs to intelligently flag unneeded media (blurry shots, accidental screenshots, receipts, and near-duplicates).
* **Who it's for:** Smartphone users, shutterbugs, and professionals whose photo libraries have become cluttered with thousands of junk images and who want an automated way to stage them for review or deletion.

---

## 💡 Architecture & Key Features

* **Google Photos API Integration:** OAuth 2.0 authentication to scan photo metadata and stream lightweight thumbnail previews.
* **Multimodal Vision Analysis:** Evaluates photos across key criteria (blurry/out-of-focus, screenshots, receipts, near-duplicate burst shots).
* **Safe Human-in-the-Loop Review:** Creates a dedicated "Flagged for Cleanup" review album in Google Photos before taking any actions.
* **Batch Processing Engine:** Implements client-side throttling and API rate limiting to process thousands of images efficiently.

---

## 🛠 Tech Stack

* **Language:** Python 3.10+
* **AI Models:** OpenAI API (GPT-4o) / Google Gemini Vision API
* **APIs & Libraries:** Google Photos Library API, Google Auth OAuth2, Pillow (PIL), Pydantic
* **Storage:** Local metadata cache (SQLite / JSON)

---

## 📋 Environment Setup & Running

This repository contains no API keys or secrets[cite: 1]. To run or test the agent locally:

1. Clone the repository:
   ```bash
   git clone [https://github.com/](https://github.com/)<your-username>/snap-audit.git
   cd snap-audit

## 🚀 Development Roadmap (20+ Hours Planned Work)

### Phase 1: Authentication & Photos Ingestion (~5 Hours)
- [ ] Configure GCP OAuth 2.0 flow and local token refresh handling for Google Photos API.
- [ ] Implement media fetcher to paginate through library items and extract low-res image thumbnails.
- [ ] Build local SQLite metadata cache to prevent re-analyzing previously processed photos.

### Phase 2: Vision Model Pipeline & Classification (~6 Hours)
- [ ] Design structured JSON prompts for Vision LLMs to evaluate image quality, duplicates, and document types.
- [ ] Implement image feature extraction and perceptual hashing (pHash) for fast near-duplicate detection.
- [ ] Create confidence scoring thresholds to classify items as Keep, Review, or Junk.

### Phase 3: Action Execution & Review Album (~5 Hours)
- [ ] Build automated Google Photos API actions to construct a "SnapAudit - Review" staging album.
- [ ] Add Human-in-the-Loop CLI and interactive web dashboard for single-click approvals.
- [ ] Implement auto-archiving and trash staging for approved junk batches.

### Phase 4: Testing, Safety Guardrails & Optimization (~4 Hours)
- [ ] Build mock vision response tests for edge cases (e.g., photos of pets/family vs. document screenshots).
- [ ] Add strict DRY_RUN_MODE safety flags to test actions safely without modifying live albums.
- [ ] Optimize batch processing pipelines with async I/O to handle thousands of items efficiently.