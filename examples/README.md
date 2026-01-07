# Examples

This folder contains sample records illustrating how data is structured within the Illusion of Mastery Longitudinal Error Corpus (IMLEC). These examples are synthetic and fully anonymized. They are intended to clarify field usage, table relationships, and expected formatting for contributors and reviewers.

---

## Files

### **`sample_event.json`**
Represents a single learner–task interaction encoded according to the `LearnerEvents` table.  
Demonstrates:
- Task metadata  
- Learner attempt  
- Error classification  
- Confidence rating  
- AI usage degree  

### **`sample_feedback.json`**
Represents a feedback instance linked to a specific event.  
Demonstrates:
- Feedback timing  
- Feedback source  
- Sanitized feedback message  
- Revised attempt and correctness  

### **`sample_longitudinal.json`**
Represents a longitudinal snapshot for a learner across a concept family.  
Demonstrates:
- Timepoint-based tracking  
- Performance progression  
- Confidence patterns  
- Transfer failure detection  

---

## Purpose

These examples provide:
- A reference for anyone reviewing or extending the dataset schema  
- A template for constructing additional sample entries  
- A sanity check for downstream tooling or analysis scripts  

They are not intended for analysis or evaluation and do not correspond to real learners or real data.

---

End of examples documentation.
