# PrepOS — Architecture

## Logical flow
```mermaid
flowchart TD
  U[Next.js client] --> A[FastAPI modular monolith]
  A --> E[Exam and syllabus module]
  A --> R[Resource library]
  R --> Q[Async extraction worker]
  Q --> P[Page-aware chunks]
  P --> V[(PostgreSQL + pgvector)]
  A --> T[Grounded tutor service]
  T --> V
  A --> QB[Question bank]
  A --> TE[Deterministic test engine]
  TE --> S[Scoring service]
  S --> AN[Learning analytics]
  C[Redis] <--> W[Celery workers]
  W --> Q
```

## Module boundaries
- `users`: identity, sessions and authorization.
- `exams`: exam structures and marking schemes.
- `syllabus`: subjects, topics and progress.
- `resources`: upload, metadata, extraction and provenance.
- `retrieval`: chunking, embeddings and authorized retrieval.
- `tutor`: grounded answer generation and citations.
- `questions`: question bank, answer keys and provenance.
- `assessments`: test definitions, attempts, timing and deterministic scoring.
- `learning`: planner, revision queue and adaptive recommendations.
- `analytics`: aggregations and learner-facing performance metrics.

## Non-negotiable rules
- Objective scoring must not call an LLM.
- The server is authoritative for test timing and submitted answers.
- Retrieval must enforce user/resource authorization.
- AI answers cite the actual retrieved source chunks.
- AI-generated questions remain drafts until reviewed/approved.
- Start modular monolith; extract services only when operational evidence justifies it.
