# Initial API contracts (draft)

Base prefix: `/api/v1`

## Exams and syllabus
- `POST /exams`
- `GET /exams`
- `GET /exams/{exam_id}`
- `POST /exams/{exam_id}/subjects`
- `POST /subjects/{subject_id}/topics`
- `GET /exams/{exam_id}/syllabus`

## Resources
- `POST /resources` — multipart upload.
- `GET /resources`
- `GET /resources/{resource_id}`
- `GET /resources/{resource_id}/processing-status`

## Tutor
- `POST /tutor/ask` — question + resource/exam scope.
- Response includes answer, citations, evidence status and model metadata.

## Questions and assessments
- `POST /questions`
- `GET /questions?topic_id=&difficulty=`
- `POST /assessments`
- `POST /assessments/{assessment_id}/attempts`
- `PUT /attempts/{attempt_id}/answers/{question_id}`
- `POST /attempts/{attempt_id}/submit`
- `GET /attempts/{attempt_id}/result`

## Analytics
- `GET /analytics/exams/{exam_id}/overview`
- `GET /analytics/topics/{topic_id}`

All endpoints require authorization and user-scoped access checks. Exact request/response schemas are to be defined with Pydantic models during implementation.
