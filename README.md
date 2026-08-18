# Hesabi AI (حسابي)

> **Arabic-first AI accounting SaaS targeting Saudi SMEs.**

[![Next.js](https://img.shields.io/badge/Next.js-15-black?logo=next.js)](https://nextjs.org/)
[![React](https://img.shields.io/badge/React-19-blue?logo=react)](https://react.dev/)
[![Node.js](https://img.shields.io/badge/Node.js-22-green?logo=node.js)](https://nodejs.org/)
[![MongoDB](https://img.shields.io/badge/MongoDB-Atlas-47A248?logo=mongodb)](https://www.mongodb.com/)
[![Claude](https://img.shields.io/badge/AI-Claude_Sonnet_3.5-D97757?logo=anthropic)](https://www.anthropic.com/)
[![Socket.io](https://img.shields.io/badge/WebSocket-Socket.io-black?logo=socket.io)](https://socket.io/)

**Developer:** [Ahmed ElKashif on GitHub](https://github.com/Ahmed-ElKashif) | [LinkedIn](https://www.linkedin.com/in/ahmed-elkashif/)

---

## 🚀 Overview

**Hesabi AI** is an intelligent accounting platform designed specifically for the Saudi Arabian market. Unlike traditional accounting software (like Qoyod or Daftra) that requires manual data entry, Hesabi AI operates as a conversational financial partner. It natively understands the Saudi dialect and allows business owners to log transactions seamlessly via a WhatsApp bot or web dashboard using natural language or receipt images.

## ✨ Key Features & Differentiators

- **Native Saudi Dialect NLP:** Understands unstructured colloquial Arabic (e.g., *"شريت قهوة من ستاربكس بـ٢٥"*).
- **WhatsApp-First UX:** Direct integration with Meta Cloud API for instant expense logging without a middleman.
- **Claude Vision Integration:** Snap a photo of a receipt via WhatsApp and the AI instantly extracts the merchant, amount, and category.
- **Smart Saudi Edge Cases:**
  - **Zakat Estimation:** *"بناءً على دخلك هالسنة، الزكاة التقديرية حوالي ١,٨٠٠ ريال."*
  - **Tamara/Tabby Installments:** Automatically tracks BNPL installment schedules.
  - **VAT Reminders:** Automated reminders before the 15th of the month.
  - **Ramadan Budget Alerts:** Adjusts spending alerts during high-expense seasons.

---

## 🏗️ Core Architecture (Phase 1)

Hesabi AI consists of 7 distinct, integrated systems:

1. **Landing Page:** Next.js (SSR/SSG) configured for optimal Arabic SEO on Google.
2. **Web Dashboard:** React SPA with Chart.js and Socket.io for live KPI updates (Revenue, Expenses, Net Balance).
3. **Admin Portal:** Protected `/admin` route with Role-Based Access Control (RBAC) to manage users and subscriptions.
4. **Backend API:** Node.js + Express with JWT authentication, 2FA, and rate-limiting.
5. **WhatsApp Bot:** Meta Cloud API webhook connecting directly to the Node.js backend.
6. **Payment Gateway:** Moyasar integration supporting Mada, Sadad, and Apple Pay, with automated webhook-driven subscription upgrades/downgrades.
7. **AI & RAG Pipeline:** Claude Sonnet backed by MongoDB Atlas Vector Search and `voyage-multilingual-2` embeddings. Seeded with ArBanking77 and AraFinNews datasets.

---

## 🛠️ Tech Stack Breakdown

| Layer | Technology | Purpose |
| :--- | :--- | :--- |
| **Frontend (Marketing)** | Next.js (SSR) | Full Arabic SEO crawlability |
| **Frontend (App)** | React (SPA) | Highly interactive, state-heavy dashboard |
| **Backend Core** | Node.js + Express | Async runtime ideal for AI streaming & webhooks |
| **Database** | MongoDB Atlas | Flexible schema for diverse transaction types |
| **Vector Search** | MongoDB Vector Search | Native RAG index (no Pinecone required) |
| **AI LLM** | Claude Sonnet API | Arabic-native NLP, streaming, and Vision OCR |
| **Embeddings** | voyage-multilingual-2 | Purpose-built Arabic/English embeddings |
| **Authentication** | JWT + bcrypt | Stateless horizontal scaling |
| **Real-time Engine** | Socket.io | Live dashboard updates without polling |
| **Payments** | Moyasar | Saudi-native (Mada/Sadad) |

---

## ⚙️ Local Setup & Installation

### Prerequisites
- [Node.js](https://nodejs.org/) (v20+)
- [MongoDB Atlas](https://www.mongodb.com/atlas) account
- [Anthropic Console](https://console.anthropic.com/) account (Claude API key)
- Meta Developer account (for WhatsApp Cloud API)

### 1. Clone & Install
```bash
git clone https://github.com/Ahmed-ElKashif/hesabi-ai.git
cd hesabi-ai
npm install
```

### 2. Environment Variables
Create a `.env` file in the root directory based on `.env.example`:
```env
PORT=3000
MONGODB_URI=mongodb+srv://<user>:<password>@cluster.mongodb.net/hesabi
JWT_SECRET=your_jwt_secret_key
CLAUDE_API_KEY=sk-ant-api03-...
VOYAGE_API_KEY=pa-...
META_WHATSAPP_TOKEN=EAAB...
META_VERIFY_TOKEN=your_custom_verify_token
MOYASAR_API_KEY=sk_test_...
```

### 3. Run Locally
```bash
# Run the backend API (Port 3000)
npm run dev:api

# Run the Next.js Frontend (Port 3001)
npm run dev:web
```

---

## ☁️ Deployment (Production)

The production infrastructure is designed for low overhead and high scalability:
- **Hosting:** [Render Web Services](https://render.com/) (Auto-deploys from GitHub `main` branch).
- **Database:** MongoDB Atlas Flex (Capped resources, handles both document storage and Vector Search).
- **Webhooks:**
  - `https://api.hesabi.com/webhooks/whatsapp` configured in Meta App Dashboard.
  - `https://api.hesabi.com/webhooks/moyasar` configured in Moyasar Dashboard.

---

<div align="center">
  <sub>Built for the Saudi Vision 2030 SME ecosystem.</sub>
</div>
