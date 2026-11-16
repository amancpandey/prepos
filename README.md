# PrepOS

**Prepare smarter. Score higher.**  
An exam-agnostic preparation platform combining configurable exam structures, source-grounded learning assistance, question banks, timed assessments, deterministic scoring, adaptive revision and learning analytics.

## Product boundaries
- Exam-agnostic core; exam-specific configuration is data, not hardcoded application logic.
- AI assists learning and content workflows; deterministic code owns objective answer keys, scoring, timing and test evaluation.
- Source-grounded answers must cite uploaded material with page/section references where available.
- AI-generated questions carry provenance and verification status.
- Start with one clearly defined exam configuration for the first usable slice; do not attempt every exam workflow at once.

## Architecture
- Frontend: Next.js + TypeScript.
- Backend: FastAPI modular monolith.
- Data: PostgreSQL; pgvector for retrieval.
- Async work: Redis + Celery.
- Document processing: extraction pipeline with page-level provenance.
- AI: retrieval-augmented tutor; model/provider abstraction.
- Assessment: deterministic question, attempt, timing and scoring services.

## First vertical slice
Configure one exam → create subject/topic tree → upload a PDF → process it asynchronously → ask a question with cited source passages → create/attempt MCQs → deterministic scoring → review incorrect answers.

## Documentation
- `docs/PRODUCT_REQUIREMENTS.md`
- `docs/ROADMAP.md`
- `docs/ARCHITECTURE.md`
- `docs/ASSESSMENT_RULES.md`
- `docs/AI_GOVERNANCE.md`
- `docs/API_CONTRACTS.md`
- `docs/DECISIONS.md`
