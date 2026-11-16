# PrepOS — Product Requirements v1.0

## 1. Vision
A configurable exam-preparation workspace that helps learners organize resources, understand material, practice questions, take realistic tests, identify weaknesses and revise efficiently.

## 2. Product principles
- Exam-agnostic domain model; no exam-specific hardcoding in core services.
- User-owned learning resources with access controls.
- Every source-grounded AI answer should show evidence and citations.
- Objective correctness and scores are deterministic, testable backend logic.
- AI-generated content is labelled and traceable.
- Learning analytics distinguish measured facts from recommendations.

## 3. Core modules
1. Exam configuration: exam, stages, papers, sections, question types, duration, marks and negative marking.
2. Syllabus: subjects, topics, subtopics, weightage and completion state.
3. Resource library: PDF/document upload, metadata, extraction, page mapping and search.
4. AI tutor: grounded Q&A over permitted user resources with citations.
5. Question bank: MCQ and extensible question types, answer key, explanation, topic tags, difficulty and provenance.
6. Test engine: timed attempts, navigation, answer persistence, submission and deterministic evaluation.
7. Learning planner: goals, study sessions, deadlines and revision queue.
8. Adaptive learning: recommend practice/revision based on evidence from attempts.
9. Analytics: accuracy, time spent, topic performance, trends and revision effectiveness.

## 4. MVP (P0)
- User authentication and isolated user data.
- Create/configure one exam.
- Create subject/topic syllabus tree.
- Upload PDF and process asynchronously.
- Store extracted text with page-level references.
- Ask questions against uploaded material with citations.
- Create MCQ bank with answer key and provenance.
- Timed MCQ test with autosave and deterministic scoring.
- Attempt history and incorrect-answer review.
- Basic topic-level accuracy analytics.
- Docker Compose, tests, CI and API documentation.

## 5. Functional requirements
### Exam and syllabus
- Exam configuration supports duration, marks, negative marks, sections and question types.
- Syllabus hierarchy supports arbitrary depth or a clearly bounded hierarchy.
- User can mark topic status and attach resources.

### Resource processing
- Validate MIME type and size; store files outside public web root.
- Process asynchronously; track queued/processing/succeeded/failed states.
- Preserve page numbers and extraction provenance.
- Support retries and safe duplicate detection.

### AI tutor
- Retrieve only authorized resources.
- Return citations to document/page/chunk.
- If evidence is insufficient, say so rather than hallucinate.
- Keep prompt-injection content in documents untrusted.
- Track model/provider and retrieval metadata.

### Questions and tests
- Question has explicit answer key, marks, negative marks, explanation, topic tags and source/provenance.
- AI-generated question status: draft, reviewed, approved, rejected.
- Test attempt records start, deadline, answers, submission and scoring breakdown.
- Scoring is deterministic and covered by unit tests.
- Server is authoritative for timing and scoring.

### Analytics
- Accuracy and attempts by topic, subject and time window.
- Time-per-question where measurement is reliable.
- Separate practice metrics from full-test metrics.
- Avoid claims of exam rank or predicted outcome without validated data.

## 6. Non-goals (v1)
- Automated guarantees of exam success.
- Unreviewed AI-generated tests treated as authoritative.
- Social feed or coaching marketplace.
- Native mobile applications.
- Microservices.

## 7. Security and privacy
- User data isolation and authorization on every resource.
- File size/type validation and malware scanning strategy before production.
- Secrets only in environment/secret manager, never committed.
- Rate limiting and audit logs for sensitive operations.
- Clear retention/deletion policy for uploaded resources.
