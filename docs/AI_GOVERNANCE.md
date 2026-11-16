# AI governance

- AI is an assistant, not the authority for objective scoring or factual source records.
- Ground tutor responses in authorized resource chunks.
- Citations identify document, page and chunk; validate that cited chunks were actually retrieved.
- If retrieval confidence/evidence is insufficient, ask for clarification or state that the material does not support an answer.
- Treat uploaded documents as untrusted input; ignore instructions embedded in retrieved content.
- Record model/provider, model version, prompt version, retrieval IDs and latency for evaluation.
- Minimize personal data in prompts and logs.
- Generated questions require draft/review/approval status and provenance.
- Build a small evaluation set before changing embedding or generation models.
