# Anonymization Protocol

This document outlines the data handling, sanitization, pseudonymization, and privacy-preserving transformations applied to all records in the Illusion of Mastery Longitudinal Error Corpus (IMLEC). The protocol ensures that no personally identifiable information (PII) is retained and that dataset releases meet ethical and methodological standards.

---

## 1. Objectives

The anonymization pipeline is designed to:
- Remove all direct and indirect identifiers
- Prevent reconstruction of individual identities
- Preserve analytic fidelity for metacognitive, longitudinal, and error-pattern analysis
- Standardize transformations across data sources and sessions

---

## 2. Data Ingestion

### 2.1 Removal of Direct Identifiers
The following are eliminated at the point of ingestion:
- Names or initials  
- Email addresses  
- Usernames or platform handles  
- Contact information  
- Raw system metadata linking back to individuals  
- Identifiable attachments or embedded content  

All such fields are discarded permanently and never written to disk.

### 2.2 Scrubbing Indirect Identifiers
Each text field undergoes automated and manual review for:
- Proper nouns  
- Location references  
- Institution names  
- Numerical identifiers (IDs, phone numbers, roll numbers)  
- Personal disclosures or sensitive attributes  

Detected items are replaced with generic placeholders, e.g. `[REDACTED]` or `[LOCATION]`.

---

## 3. Pseudonymization

### 3.1 Learner Pseudonyms
Each participant is assigned an irreversible identifier:
- Generated via SHA-256 hashing  
- Salted per session to prevent cross-dataset linkage  
- Never mapped back to real identities  

The salt and mapping keys are stored separately in an offline, non-networked environment.

### 3.2 Session and Event Identifiers
- `session_id` and `event_id` are generated as UUIDv4 tokens  
- IDs are globally unique but not traceable to any external system  

---

## 4. Text Sanitization

### 4.1 Regex-Based Scrubbing
All text fields (`input_attempt`, `feedback_content`, etc.) pass through:
- PII removal filters  
- Entity masking for rare or unique tokens  
- Normalization of formatting to prevent fingerprinting  

### 4.2 Sensitive Content Handling
If a text segment contains:
- Personal health information  
- Socioeconomic disclosures  
- Family background  
It is either removed or replaced with `[REDACTED]` depending on analytic relevance.

---

## 5. Timestamp Privacy

To prevent temporal triangulation, one of the following methods is applied consistently:

### **Option A: Time Flooring**
- Floor timestamps to the nearest 30 minutes

### **Option B: Random Jitter**
- Apply a ± 5–10 minute random offset  
- Ordering within a session is preserved  

The chosen method must remain consistent across the entire dataset version.

---

## 6. AI Usage Detection

To analyze AI fluency vs. understanding, each interaction is labeled with an AI usage degree (`ai_usage_degree`) using pre-defined heuristics:
- Recognizable AI-generated phrasing patterns  
- Overlap with known AI output templates  
- Usage metadata when available  

No raw AI logs containing identifiers are stored.

---

## 7. Data Retention Policy

### 7.1 Separation of Raw and Processed Data
- **Raw data**: stored offline in an encrypted vault  
- **Processed (anonymized) data**: used for analysis  
- **Mapping keys**: stored separately and never committed to the repository  

### 7.2 Access Restrictions
Only the project owner and designated reviewers may access raw data.

### 7.3 Deletion Requirements
- Raw data deleted after project completion or after a fixed retention horizon  
- Processed data maintained for reproducibility

---

## 8. Audit Logging

Every transformation operation is logged with:
```json
{
  "timestamp": "ISO-8601",
  "action": "scrub|hash|replace|jitter",
  "actor": "system|manual",
  "fields_modified": ["..."],
  "notes": "optional"
}
