# QuestionGen AI

A modern, responsive AI-powered web application that generates high-quality educational questions and answers from any topic. Inspired by contemporary AI chat interfaces with a clean, spacious design.

## Features

- **Topic → 10 Questions**: Enter any educational topic and receive exactly 10 questions with answers.
- **Difficulty & Type mix**: Easy / Medium / Hard + varied question types (Definition, Conceptual, Application, etc.).
- **Conversational UI**: Chat-style interface with collapsible answers for practice.
- **Professional PDF Question Papers**: Download a clean A4 question paper containing **only questions** (no answers). Optional “with answers” version.
- **Local history**: Recent topics stored in localStorage; reopen any past conversation.
- **Dark / Light mode**.
- **Responsive**: Sidebar collapses on mobile; full-width cards.
- **Secure**: API key stays on the server; never exposed to the browser.

## Tech Stack

- **Frontend**: React 19 + TypeScript + Vite + Tailwind CSS v4
- **Backend**: Express (Node.js) — `/api/generate`
- **AI**: OpenAI-compatible API (optional). Falls back to a high-quality offline mock generator when no key is present.
- **PDF**: jsPDF (A4, multi-page, print-friendly)
- **Storage**: localStorage

## Quick Start

```bash
cd questiongen-ai
npm install
npm run dev
```

This starts:
- Frontend at http://localhost:5173
- Backend at http://localhost:3001

Open the app in your browser and try a topic such as **Photosynthesis**, **Newton’s Laws**, or **Python**.

### Optional: Real AI

1. Copy `.env.example` to `.env`
2. Set `AI_API_KEY` (or `OPENAI_API_KEY`) to an OpenAI-compatible key
3. Optionally set `AI_BASE_URL` and `AI_MODEL` (defaults work with OpenAI)
4. Restart the server

Without a key the app still works fully using the built-in educational mock generator (curated banks for common subjects + sensible templates for any other topic).

## Project Structure

```
questiongen-ai/
├── server/
│   ├── index.js          # Express API + rate limiting
│   └── mockGenerator.js  # Offline high-quality question banks
├── src/
│   ├── components/       # UI components
│   ├── types/
│   ├── utils/            # PDF + localStorage
│   ├── App.tsx
│   └── ...
├── .env.example
└── package.json
```

## Usage Flow

1. Open QuestionGen AI
2. (Optional) Choose Difficulty / Question Type
3. Enter a topic or click a suggestion
4. AI returns 10 questions in chat cards
5. Expand answers when ready to check
6. **Download Question Paper** → clean exam-style PDF (questions only)
7. Or use “More → Download with Answers”
8. Regenerate, copy, or start a new topic
9. Revisit past topics from the sidebar

## Security Notes

- Never put API keys in frontend code
- Server rate-limits the generation endpoint
- User input is sanitized and length-limited
- PDF generation uses only the already-displayed questions (no second AI call)

## License

MIT
