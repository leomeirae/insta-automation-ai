<!--
Sync Impact Report:
- Version change: [TEMPLATE] → 1.0.0
- Added sections: Core Principles (5), Architecture Standards, Development Standards, Governance
- Templates requiring updates: ✅ All templates compatible with new constitution
- Follow-up TODOs: None - all placeholders filled
-->

# Instagram Automation AI Constitution

## Core Principles

### I. Hybrid Architecture Separation
Frontend (Next.js) MUST focus exclusively on user experience and interface logic. Backend (FastAPI) MUST handle all data processing, AI analysis, and external integrations. Communication MUST occur only through well-defined REST API contracts. No business logic in frontend components; no UI concerns in backend services.

### II. Type Safety & Code Quality (NON-NEGOTIABLE)
TypeScript strict mode MUST be enabled for all frontend code with zero `any` types in production. Python MUST use type hints with Pydantic models for all API contracts. Server Components MUST be default; Client Components only for interactivity. All async operations MUST use proper async/await patterns.

### III. Test-Driven Development
Contract tests MUST be written before API implementation. Integration tests MUST validate user scenarios before feature completion. Frontend validation with Zod MUST complement backend Pydantic validation. All tests MUST pass before deployment. Red-Green-Refactor cycle strictly enforced.

### IV. Performance & User Experience
Loading states MUST be implemented for all async operations. Rate limiting MUST be applied to both internal APIs and external services (Apify, OpenAI). Background tasks MUST be used for long-running operations. Cache strategies MUST be implemented for expensive operations. Mobile-first responsive design MUST be maintained.

### V. Security & Compliance
Environment variables MUST be separated between frontend (.env.local) and backend (.env). CORS MUST be properly configured. Input sanitization MUST occur at both layers. HTTPS MUST be enforced in production. Rate limiting MUST protect against abuse. All external API costs MUST be logged and monitored.

## Architecture Standards

**Technology Stack Requirements:**
- Frontend: Next.js 14+ with App Router, TypeScript strict mode, shadcn/ui or Tailwind CSS
- Backend: Python 3.11+ with FastAPI, Pydantic models, async/await for I/O
- Communication: REST API only, no direct database access from frontend
- External Services: Apify SDK for scraping, OpenAI/Anthropic SDKs for AI analysis
- Database: PostgreSQL with proper connection pooling
- Deployment: Vercel (frontend) + Railway/Render (backend)

**Modular Structure Requirements:**
- Backend: Separate routers, services, and schemas directories
- Frontend: Component-based architecture with clear separation of concerns
- API Routes: Used only as proxies to FastAPI backend
- Shared Types: Generated from Pydantic models for frontend consumption

## Development Standards

**Code Organization:**
- Structured logging MUST be implemented for debugging and monitoring
- Error handling MUST use HTTPException with proper status codes
- Retry logic with exponential backoff MUST be implemented for external APIs
- Prompts MUST be versioned in separate files, not hardcoded
- Documentation MUST be auto-generated via FastAPI Swagger (/docs)

**Quality Gates:**
- All PRs MUST pass TypeScript compilation with zero errors
- All PRs MUST pass Python type checking with mypy or similar
- Integration tests MUST validate API contracts
- Performance benchmarks MUST be maintained (API response times, token usage)
- Accessibility MUST meet WCAG 2.1 standards

**Development Workflow:**
- Feature branches MUST follow naming convention: `feature/###-description`
- Environment setup MUST be documented in README with clear prerequisites
- Local development MUST support hot reload for both frontend and backend
- Database migrations MUST be versioned and reversible

## Governance

Constitution supersedes all other development practices. All code reviews MUST verify compliance with these principles. Complexity that violates these standards MUST be justified in writing or refactored. Performance degradation below established benchmarks MUST trigger immediate investigation.

Amendments require documentation of impact, approval from project maintainers, and migration plan for existing code. Emergency exceptions require post-incident review and constitutional amendment if pattern should be permanent.

Use this constitution as the foundation for all planning, specification, and implementation decisions. When in doubt, prioritize user experience, type safety, and maintainability over development speed.

**Version**: 1.0.0 | **Ratified**: 2025-10-02 | **Last Amended**: 2025-10-02