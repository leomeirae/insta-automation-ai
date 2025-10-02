# Instagram Automation AI 🤖

Hybrid Next.js + FastAPI platform for Instagram content analysis and AI-powered social media automation. Features web scraping, content generation, and intelligent social media management.

## 🏗️ Architecture

- **Frontend**: Next.js 15 with App Router, TypeScript, and Tailwind CSS
- **Backend**: Python FastAPI with async support and Pydantic models
- **AI Integration**: OpenAI/Anthropic for content analysis and generation
- **Scraping**: Apify SDK for Instagram and social media data collection
- **Database**: PostgreSQL with proper connection pooling

## 🚀 Getting Started

### Frontend (Next.js)

```bash
npm run dev
# or
yarn dev
# or
pnpm dev
# or
bun dev
```

Open [http://localhost:3000](http://localhost:3000) with your browser to see the result.

### Backend (FastAPI)

```bash
cd backend
source venv/bin/activate  # On Windows: venv\Scripts\activate
pip install -r requirements.txt
uvicorn main:app --reload
```

API documentation available at [http://localhost:8000/docs](http://localhost:8000/docs)

## 📋 Constitutional Principles

This project follows strict architectural and quality principles:

- **Hybrid Architecture Separation**: Clear separation between frontend (UX) and backend (processing)
- **Type Safety**: TypeScript strict mode + Python type hints with Pydantic
- **Test-Driven Development**: Contract tests before implementation
- **Performance & UX**: Loading states, rate limiting, background tasks
- **Security & Compliance**: Environment separation, input sanitization, monitoring

## 🛠️ Development Workflow

Use the Spec Kit commands for structured development:

- `/constitution` - View project principles
- `/specify` - Create feature specifications
- `/plan` - Generate implementation plans
- `/tasks` - Break down into actionable tasks
- `/implement` - Execute implementation

## 📁 Project Structure

```
├── app/                    # Next.js App Router
│   ├── components/         # React components (Server Components default)
│   ├── lib/               # Utilities and API clients
│   └── api/               # API routes (proxy to FastAPI only)
├── backend/
│   ├── app/
│   │   ├── models/        # Pydantic models
│   │   ├── services/      # Business logic
│   │   ├── routers/       # FastAPI routes
│   │   └── schemas/       # API contracts
│   └── tests/
│       ├── contract/      # API contract tests
│       └── integration/   # Service integration tests
└── .specify/              # Spec Kit configuration
    ├── memory/            # Project constitution
    └── templates/         # Development templates
```

## 🔧 Tech Stack

- **Frontend**: Next.js 15, React 19, TypeScript, Tailwind CSS, Zod
- **Backend**: FastAPI, Python 3.11+, Pydantic, Uvicorn
- **AI/ML**: OpenAI SDK, Anthropic Claude
- **Scraping**: Apify SDK, Beautiful Soup
- **Database**: PostgreSQL, SQLAlchemy
- **Testing**: Jest (frontend), pytest (backend)
- **Deployment**: Vercel (frontend), Railway/Render (backend)

## 📝 License

This project is licensed under the MIT License.

## 🤝 Contributing

Contributions are welcome! Please follow the constitutional principles and use the Spec Kit workflow for feature development.