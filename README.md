# illusion-of-mastery-dataset

The *Illusion of Mastery Project* investigates confidence–competence gaps, transfer failure, and how AI fluency can mask underlying misunderstanding. This repository contains the formal dataset schema, anonymization protocol, and supporting documentation for the longitudinal corpus used in the study.

The dataset focuses on learner–task interactions collected from AI-assisted, human-guided, and solo learning contexts. Each interaction is encoded with structured fields capturing domain, error type, accuracy, feedback timing, revision behavior, and confidence. The goal is to create a reliable analytic foundation for studying when learners *believe* they understand something vs. when they actually do.

## Contents
- `schema.md`  
  Formal specification of all core tables: `LearnerEvents`, `FeedbackEvents`, and `LongitudinalTracking`, including field definitions and error taxonomy.

- `anonymization_protocol.md`  
  Data handling and privacy specification covering ingestion, scrubbing, timestamp jittering, pseudonymization, retention rules, and release tiers.

- `examples/`  
  Sample entries illustrating the structure of an event, feedback instance, and longitudinal snapshot.

## Use Cases
This repository is intended for:
- Researchers studying metacognition, confidence calibration, and misconception persistence  
- Developers analyzing AI-assisted learning behavior  
- Reviewers evaluating methodological rigor for the *Illusion of Mastery Project*  
- Collaborators providing design, architecture, or data-model feedback  

## Status
Active development. Schema and protocol are stable but may undergo versioned refinement as the analysis pipeline evolves.

## License
Released under an open, permissive license (MIT recommended) unless you decide otherwise.
