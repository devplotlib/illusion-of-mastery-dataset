# Illusion of Mastery Dataset Schema

This document defines the formal schema for the Illusion of Mastery Longitudinal Error Corpus (IMLEC). It specifies the core tables, field types, relationships, and error taxonomy used to encode learner–task interactions across AI-assisted, human-guided, and solo learning contexts.

---

## 1. Overview

**Unit of observation:**  
One learner–task interaction event.

**Primary goals of the dataset:**  
- Track confidence–competence gaps  
- Identify misconception persistence  
- Detect transfer failures across timepoints  
- Analyze how AI fluency and feedback timing influence understanding  

---

## 2. Core Tables

---

## 2.1 `LearnerEvents`

| Field | Type | Description |
|-------|------|-------------|
| `event_id` | UUID | Unique identifier for each interaction event. |
| `session_id` | UUID | Groups multiple events occurring within the same study session. |
| `learner_pseudonym` | String | Irreversible randomized identifier assigned after anonymization. |
| `timestamp` | ISO-8601 | Time of interaction (may be jittered or floored for privacy). |
| `task_id` | String | Identifier for the specific task or problem attempted. |
| `task_domain` | Categorical | Domain classification (e.g., math, programming, writing, logic). |
| `context_mode` | Categorical | “AI-assisted”, “human-guided”, or “solo”. |
| `input_attempt` | Text | Learner’s answer or reasoning attempt. |
| `is_correct` | Boolean | Indicates whether the attempt is correct. |
| `error_type` | Categorical | Coded misconception or error category (see Error Taxonomy). |
| `confidence_rating` | Integer (1–5) | Self-reported confidence level, if collected. |
| `ai_usage_degree` | Integer (0–3) | Degree of AI reliance: 0 = none, 3 = heavy usage. |

---

## 2.2 `FeedbackEvents`

| Field | Type | Description |
|-------|------|-------------|
| `feedback_id` | UUID | Unique identifier for a feedback instance. |
| `event_id` | UUID | Foreign key linking to the associated learner event. |
| `feedback_source` | Categorical | “AI”, “human”, or “rubric”. |
| `feedback_timing` | Categorical | Immediate, delayed, or self-triggered. |
| `feedback_content` | Text | Sanitized feedback message. |
| `learner_revision` | Text | Post-feedback attempt. |
| `revision_is_correct` | Boolean | Indicates whether the revised attempt is correct. |

---

## 2.3 `LongitudinalTracking`

| Field | Type | Description |
|-------|------|-------------|
| `learner_pseudonym` | String | Same pseudonym used across all tables. |
| `task_family` | String | Concept cluster or skill category. |
| `timepoint` | Integer | Longitudinal checkpoint (T1, T2, T3...). |
| `performance_score` | Float (0–1) | Normalized performance metric. |
| `confidence_average` | Float (0–5) | Mean confidence across tasks in this timepoint. |
| `transfer_failure_flag` | Boolean | Indicates whether performance dropped on novel but structurally similar tasks. |

---

## 3. Error Type Taxonomy

This taxonomy standardizes error labeling to support reliable analysis.

### **3.1 Core Categories**

- **Conceptual Misconception**  
  Incorrect understanding of the underlying principle.

- **Procedural Slip**  
  Execution mistake despite correct conceptual understanding.

- **Misapplication of Prior Rule**  
  Applying a valid rule in an invalid context.

- **Overgeneralization**  
  Extending a rule or pattern beyond its appropriate scope.

- **Local Reasoning Error**  
  Incorrect step or inference that breaks an otherwise valid chain.

- **AI-Induced Hallucination Adoption**  
  Learner reproduces incorrect AI output or explanation.

- **Misinterpreted Prompt**  
  Task misunderstood due to unclear reading or framing.

- **Surface-Level Mimicry (AI Fluency)**  
  Learner produces syntactically polished but conceptually shallow answers aligned with AI style.

---

## 4. Relationships and Integrity Constraints

- `LearnerEvents.event_id` links to `FeedbackEvents.event_id` (one-to-many).
- `LearnerEvents.learner_pseudonym` links to `LongitudinalTracking.learner_pseudonym` (one-to-many).
- Error types must belong to the controlled taxonomy; otherwise they must be flagged for review.
- Timestamps may be jittered but must maintain ordering within a given `session_id`.

---

## 5. Versioning

Schema updates must be tracked using semantic versioning:
- **MAJOR:** structural changes to tables or fields  
- **MINOR:** new error types, new domains  
- **PATCH:** wording clarifications, documentation cleanup  

---

## 6. Notes

- All text fields must pass through the anonymization pipeline described in `anonymization_protocol.md`.  
- AI-generated content indicators (`ai_usage_degree`) should follow consistent heuristics across the dataset.  
- Transfer failure detection requires stable definitions of task families and concept clusters.

---

End of schema.
