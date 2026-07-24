# Reinh

**Go backend & AI automation engineer.** I build systems where the model does the useful part and never gets to be the authority — server code, PostgreSQL constraints, and a human hold that.

Most "AI agent" projects let the model call a mutating API and hope the prompt holds. Mine treat it as an untrusted planner: it proposes, the server decides, the database enforces, and a person confirms anything that matters.

**Available for freelance work** — backend services, AI agents, document/RAG pipelines, business automation. → [timofeyfrol@gmail.com](mailto:timofeyfrol@gmail.com)

---

## Selected work

Five complete, runnable systems — not snippets. Each one ships with Docker Compose, tests, architecture docs, and an honest statement of what it does *not* do.

### 🗓 [Kontor](https://github.com/reinh2/Kontor) — AI front desk that books real appointments
A customer writes *"haircut Thursday evening?"* and gets a real slot — checked against catalogue, staff, hours, breaks, buffers and time zones. The model proposes; the booking only happens after an explicit customer *yes*, and the server executes its own frozen arguments, never what the model re-sends. Double-booking is prevented by a database exclusion constraint under serializable transactions, not by an `if` statement.
`Go` · `PostgreSQL` · `SSE` · `Docker` — **runs with no API key** (deterministic local model adapter)

### 📄 [InvoiceFlow](https://github.com/reinh2/Invoiceflow) — invoice → structured data, human in control
Upload a PDF or photo, get supplier, dates, tax and line items back — then review them beside the original before anything is exported. Every edit is a new immutable version, approval targets one exact version, exports are idempotent and audited, and money is integer minor units with an explicit currency. The AI cannot approve or export. It never touches a bank.
`Go` · `PostgreSQL` · `React/TypeScript` · `Poppler/Tesseract` · `Docker` — **runs fully offline, no API key**

### 📚 [DocMind](https://github.com/reinh2/Docmind) — answers grounded in your documents, or no answer
A support assistant that replies only from the company's own documents and shows the exact paragraph behind every sentence. When the evidence isn't there it says so and hands off to a human instead of inventing a price or a policy. Same brain on a website widget and in Telegram, with an admin console for reviewing conversations end to end.
`Go` · `PostgreSQL/pgvector` · hybrid retrieval + RRF · `React` · `SSE` · `Docker`

### ⚡ [AI Lead Pipeline](https://github.com/reinh2/Lead-pipeline) — first reply in ~30 seconds, not 4 hours
A landing page and Telegram bot capture enquiries; AI qualifies each one (hot / warm / cold / spam), the CRM gets the deal, the manager gets a one-tap action card, and the customer gets a personal reply immediately. Every lead is fsync-ed to an append-only log *before* the visitor sees "received" — if the AI provider, CRM, or Telegram is down, nothing is lost and the failure is replayable.
`Go` · `HubSpot` / `Google Sheets` · `Telegram` / `Slack` · `Docker` — **runs with no API key** (mock qualifier)

### 🥗 [MindBite AI](https://github.com/reinh2/Mindbite-ai) — a nutrition diary that fills itself in
Photograph a plate, send a voice note, or just type it — it's logged with calories and macros. A Telegram Mini App with a tamagotchi pet and streaks for retention, a CBT-grounded coach, 11 languages, and four independent payment channels. Designed, built, and operated solo, end to end.
`Go` · `PostgreSQL` · `React` · `Telegram Bot + Mini App` · `Stripe` / `YooKassa` / `CryptoBot` / `Stars`

---

## How I build

- **The model is an untrusted planner.** It cannot set identity, status, storage keys, approvals, destinations, or secrets. Every value it returns is re-validated server-side.
- **Invariants live in the database.** Exclusion constraints, composite foreign keys, serializable transactions, append-only audit tables — so a bug in application code can't violate them.
- **Durable work, not fire-and-forget.** PostgreSQL-backed job queues with leases, bounded retries, idempotency keys, and dead-letter states. Restarting a worker loses nothing.
- **Humans confirm anything consequential.** Booking, approval, export — an explicit action against an exact, immutable version.
- **Exact money.** Integer minor units and an explicit currency. Never a float.
- **It runs.** `docker compose up` and a demo you can drive yourself, with fictional data and, wherever possible, no API key at all.
- **Honest documentation.** Every README states its limitations and what the project deliberately doesn't do. No invented metrics, no fake customers.

## Stack

`Go` · `PostgreSQL` / `pgvector` · `React` + `TypeScript` / `Vite` · `Docker Compose` · `REST` / `SSE` · OpenAI & OpenRouter · Telegram, Slack, HubSpot, Google APIs

## Get in touch

Have a backend, AI agent, or automation project? **[timofeyfrol@gmail.com](mailto:timofeyfrol@gmail.com)**

<details>
<summary>🇷🇺 По-русски</summary>

<br>

**Go-разработчик бэкенда и AI-автоматизации.** Строю системы, где модель делает полезную работу, но никогда не становится источником полномочий — за это отвечают серверный код, ограничения PostgreSQL и человек.

Пять законченных проектов, каждый запускается одной командой `docker compose up`:

- **[Kontor](https://github.com/reinh2/Kontor)** — AI-администратор, который реально записывает клиентов. Модель только предлагает; запись создаётся после явного подтверждения, а двойное бронирование исключено ограничением в базе, а не проверкой в коде.
- **[InvoiceFlow](https://github.com/reinh2/Invoiceflow)** — счёт превращается в структурированные данные под контролем человека: неизменяемые версии, утверждение конкретной версии, идемпотентный экспорт, точные деньги в целых минорных единицах.
- **[DocMind](https://github.com/reinh2/Docmind)** — ассистент, который отвечает только по документам компании и показывает источник каждой фразы. Нет подтверждения в документах — честно говорит об этом и передаёт человеку.
- **[AI Lead Pipeline](https://github.com/reinh2/Lead-pipeline)** — первый ответ клиенту за ~30 секунд вместо 4 часов: квалификация заявки, запись в CRM, карточка менеджеру, мгновенный персональный ответ.
- **[MindBite AI](https://github.com/reinh2/Mindbite-ai)** — дневник питания, который заполняется сам: фото, голос или текст. Telegram Mini App, 11 языков, подписки.

Открыт для фриланс-проектов: бэкенд, AI-агенты, работа с документами и RAG, автоматизация бизнес-процессов. → **[timofeyfrol@gmail.com](mailto:timofeyfrol@gmail.com)**

</details>
