# Architecture decision records

## ADR-001: Exam-agnostic configuration
Exam structures and marking rules are data/configuration, not hardcoded per exam.

## ADR-002: Deterministic scoring
Objective correctness and marks are computed by backend code, never delegated to an LLM.

## ADR-003: Source-grounded tutor
Tutor responses use authorized retrieved material and cite document/page provenance.

## ADR-004: Modular monolith
A modular monolith minimizes operational overhead while preserving clear domain boundaries.
