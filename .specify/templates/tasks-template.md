# Tasks: [FEATURE NAME]

**Input**: Design documents from `/specs/[###-feature-name]/`
**Prerequisites**: plan.md (required), research.md, data-model.md, contracts/

## Execution Flow (main)
```
1. Load plan.md from feature directory
   → If not found: ERROR "No implementation plan found"
   → Extract: tech stack, libraries, structure
2. Load optional design documents:
   → data-model.md: Extract entities → model tasks
   → contracts/: Each file → contract test task
   → research.md: Extract decisions → setup tasks
3. Generate tasks by category:
   → Setup: project init, dependencies, linting
   → Tests: contract tests, integration tests
   → Core: models, services, CLI commands
   → Integration: DB, middleware, logging
   → Polish: unit tests, performance, docs
4. Apply task rules:
   → Different files = mark [P] for parallel
   → Same file = sequential (no [P])
   → Tests before implementation (TDD)
5. Number tasks sequentially (T001, T002...)
6. Generate dependency graph
7. Create parallel execution examples
8. Validate task completeness:
   → All contracts have tests?
   → All entities have models?
   → All endpoints implemented?
9. Return: SUCCESS (tasks ready for execution)
```

## Format: `[ID] [P?] Description`
- **[P]**: Can run in parallel (different files, no dependencies)
- Include exact file paths in descriptions

## Path Conventions
- **Single project**: `src/`, `tests/` at repository root
- **Web app**: `backend/src/`, `frontend/src/`
- **Mobile**: `api/src/`, `ios/src/` or `android/src/`
- Paths shown below assume single project - adjust based on plan.md structure

## Phase 3.1: Setup
- [ ] T001 Create project structure per implementation plan
- [ ] T002 Initialize [language] project with [framework] dependencies
- [ ] T003 [P] Configure linting and formatting tools

## Phase 3.2: Tests First (TDD) ⚠️ MUST COMPLETE BEFORE 3.3
**CRITICAL: These tests MUST be written and MUST FAIL before ANY implementation**
- [ ] T004 [P] Contract test POST /api/users in backend/tests/contract/test_users_post.py
- [ ] T005 [P] Contract test GET /api/users/{id} in backend/tests/contract/test_users_get.py
- [ ] T006 [P] Integration test user registration in backend/tests/integration/test_registration.py
- [ ] T007 [P] Integration test auth flow in backend/tests/integration/test_auth.py
- [ ] T008 [P] Frontend form validation test in app/components/__tests__/user-form.test.tsx

## Phase 3.3: Core Implementation (ONLY after tests are failing)
- [ ] T009 [P] Pydantic models in backend/app/models/user.py
- [ ] T010 [P] Service layer in backend/app/services/user_service.py
- [ ] T011 [P] React components in app/components/user-form.tsx (Server Component)
- [ ] T012 FastAPI router POST /api/users in backend/app/routers/users.py
- [ ] T013 FastAPI router GET /api/users/{id} in backend/app/routers/users.py
- [ ] T014 Next.js API proxy in app/api/users/route.ts
- [ ] T015 Input validation (Zod frontend + Pydantic backend)
- [ ] T016 Error handling and structured logging

## Phase 3.4: Integration
- [ ] T017 Connect services to PostgreSQL database
- [ ] T018 CORS configuration for Next.js → FastAPI communication
- [ ] T019 Rate limiting middleware (per IP and endpoint)
- [ ] T020 Background task setup for long-running operations
- [ ] T021 Environment variable configuration (.env.local + .env)

## Phase 3.5: Polish
- [ ] T022 [P] Unit tests for validation in backend/tests/unit/test_validation.py
- [ ] T023 [P] Frontend component tests in app/components/__tests__/
- [ ] T024 Performance tests (API response times <200ms)
- [ ] T025 [P] Update FastAPI Swagger documentation
- [ ] T026 Accessibility audit (WCAG 2.1)
- [ ] T027 Remove code duplication and refactor

## Dependencies
- Tests (T004-T008) before implementation (T009-T016)
- T009 blocks T010, T017
- T018 blocks T019, T020
- Implementation before polish (T022-T027)

## Parallel Example
```
# Launch T004-T008 together (TDD phase):
Task: "Contract test POST /api/users in backend/tests/contract/test_users_post.py"
Task: "Contract test GET /api/users/{id} in backend/tests/contract/test_users_get.py"
Task: "Integration test registration in backend/tests/integration/test_registration.py"
Task: "Integration test auth in backend/tests/integration/test_auth.py"
Task: "Frontend form validation test in app/components/__tests__/user-form.test.tsx"
```

## Notes
- [P] tasks = different files, no dependencies
- Verify tests fail before implementing
- Commit after each task
- Avoid: vague tasks, same file conflicts

## Task Generation Rules
*Applied during main() execution*

1. **From Contracts**:
   - Each contract file → contract test task [P]
   - Each endpoint → implementation task
   
2. **From Data Model**:
   - Each entity → model creation task [P]
   - Relationships → service layer tasks
   
3. **From User Stories**:
   - Each story → integration test [P]
   - Quickstart scenarios → validation tasks

4. **Ordering**:
   - Setup → Tests → Models → Services → Endpoints → Polish
   - Dependencies block parallel execution

## Validation Checklist
*GATE: Checked by main() before returning*

- [ ] All contracts have corresponding tests
- [ ] All entities have model tasks
- [ ] All tests come before implementation
- [ ] Parallel tasks truly independent
- [ ] Each task specifies exact file path
- [ ] No task modifies same file as another [P] task