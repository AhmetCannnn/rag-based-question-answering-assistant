# RAG-Based Question-Answering Assistant

[🇹🇷 Türkçe](#türkçe) · [🇬🇧 English](#english)

---

## English

**[→ Live Demo](https://YOUR_DEMO_URL)** — Try it here.

RAG (Retrieval-Augmented Generation) based question-answering assistant. Upload PDFs/text files or add URLs (Wikipedia, Stack Overflow), then ask questions and get answers grounded only in those sources.

| Home | Upload & chat | Answers with sources |
|------|----------------|----------------------|
| ![Home](assets/screenshot0.png) | ![Upload](assets/screenshot1.png) | ![Chat](assets/screenshot2.png) |

### Features

- **Multiple sources:** PDF, TXT, DOCX upload and Wikipedia / Stack Overflow URLs
- **RAG pipeline:** Text chunking, embeddings, semantic search with pgvector
- **Dual providers:** OpenAI (GPT) or Gemini for chat; OpenAI or Gemini for embeddings
- **Session-based:** Chat and sources kept in browser session

### Tech stack

| Layer    | Technologies |
|----------|--------------|
| Backend  | Python, FastAPI, PostgreSQL + pgvector, OpenAI API, Google Gemini |
| Frontend | React, Vite |
| Embedding| OpenAI (text-embedding-ada-002, text-embedding-3-small), Gemini (models/gemini-embedding-001) |

### How it works

1. **Input:** User adds PDF/URL.
2. **Processing:** Text is chunked, embedded via API, stored in pgvector.
3. **Query:** User asks a question; question is embedded and similarity search runs in pgvector.
4. **Answer:** Top chunks are sent to the LLM as context; the model answers only from that context.

### Project structure

Code lives in two repositories:

| Repo      | Description | URL |
|-----------|-------------|-----|
| **Backend**  | FastAPI, pgvector, embedding & QA APIs | [answer_question_bot_backend](https://github.com/AhmetCannnn/answer_question_bot_backend) |
| **Frontend** | React UI | [answer_question_bot_frontend](https://github.com/AhmetCannnn/answer_question_bot_frontend) |

### Local setup

**Backend**

```bash
git clone https://github.com/AhmetCannnn/answer_question_bot_backend.git
cd answer_question_bot_backend
pip install -r requirements.txt
# Create .env with DATABASE_URL etc.
# Run db/schema.sql and db/seed_models.sql
uvicorn app:app --reload --port 8001
```

**Frontend**

```bash
git clone https://github.com/AhmetCannnn/answer_question_bot_frontend.git
cd answer_question_bot_frontend
npm install
npm run dev
```

Frontend runs at `http://localhost:5173`, backend at `http://localhost:8001`.

---

## Türkçe

**[→ Canlı demo](https://YOUR_DEMO_URL)** — Buradan deneyebilirsiniz.

RAG (Retrieval-Augmented Generation) tabanlı soru-cevap asistanı. PDF/metin yükleyebilir veya URL ekleyebilirsiniz (Wikipedia, Stack Overflow); sorularınız yalnızca bu kaynaklara dayalı yanıtlanır.

| Ana sayfa | Belge/URL yükleme ve sohbet | Kaynak gösterimli cevaplar |
|-----------|-----------------------------|----------------------------|
| ![Ana sayfa](assets/screenshot0.png) | ![Belge ve URL](assets/screenshot1.png) | ![Sohbet ve kaynaklar](assets/screenshot2.png) |

### Öne çıkan özellikler

- **Çoklu kaynak:** PDF, TXT, DOCX yükleme ve Wikipedia / Stack Overflow URL’leri
- **RAG pipeline:** Metin chunk’lama, embedding, pgvector ile semantik arama
- **İki sağlayıcı:** Sohbet için OpenAI (GPT) veya Gemini; embedding için OpenAI veya Gemini
- **Session tabanlı:** Sohbet ve kaynaklar tarayıcı oturumunda saklanır

### Teknoloji yığını

| Katman   | Teknolojiler |
|----------|---------------|
| Backend  | Python, FastAPI, PostgreSQL + pgvector, OpenAI API, Google Gemini |
| Frontend | React, Vite |
| Embedding| OpenAI (text-embedding-ada-002, text-embedding-3-small), Gemini (models/gemini-embedding-001) |

### Sistem nasıl çalışıyor?

1. **Giriş:** Kullanıcı PDF/URL ekler.
2. **İşleme:** Metin chunk’lanır, embedding API ile vektörlenir, pgvector’e yazılır.
3. **Sorgu:** Kullanıcı soru sorar; soru embed edilir, pgvector’de benzerlik araması yapılır.
4. **Cevap:** En alakalı chunk’lar LLM’e context olarak gider; model yalnızca bu bağlama dayalı cevap üretir.

### Proje yapısı

Kod iki ayrı repo’da:

| Repo       | Açıklama | URL |
|------------|----------|-----|
| **Backend**  | FastAPI, pgvector, embedding ve QA API’leri | [answer_question_bot_backend](https://github.com/AhmetCannnn/answer_question_bot_backend) |
| **Frontend** | React arayüzü | [answer_question_bot_frontend](https://github.com/AhmetCannnn/answer_question_bot_frontend) |

### Kurulum (yerel)

**Backend**

```bash
git clone https://github.com/AhmetCannnn/answer_question_bot_backend.git
cd answer_question_bot_backend
pip install -r requirements.txt
# .env oluşturup DATABASE_URL vb. doldur
# db/schema.sql ve db/seed_models.sql çalıştır
uvicorn app:app --reload --port 8001
```

**Frontend**

```bash
git clone https://github.com/AhmetCannnn/answer_question_bot_frontend.git
cd answer_question_bot_frontend
npm install
npm run dev
```

Frontend `http://localhost:5173`, backend `http://localhost:8001` üzerinde çalışır.
