# Coding Framework for Error and Confidence Classification

This document defines the operational rules for classifying learner errors and confidence levels within the Illusion of Mastery Longitudinal Error Corpus (IMLEC). The framework ensures consistency, inter-rater reliability, and reproducibility across annotations.

---

## 1. Purpose

The coding framework is designed to:
- Standardize how misconception types are identified  
- Provide explicit decision rules for classifying responses  
- Reduce subjectivity in assigning error categories  
- Establish a calibrated confidence scale linked to observable indicators  

All coders must follow these rules when annotating learner events.

---

## 2. Error Classification Framework

Error types correspond to the taxonomy defined in the dataset schema. Each category below includes:  
- **Definition**  
- **Diagnostic signals**  
- **Exclusion criteria**  
- **Examples**

---

### 2.1 Conceptual Misconception

**Definition:**  
Learner demonstrates an incorrect understanding of the underlying principle or concept.

**Diagnostic Signals:**  
- Explanation reveals a flawed model of the concept  
- Error persists even when execution steps are corrected  
- Learner substitutes an unrelated rule  

**Exclusion:**  
Do not classify slips caused by arithmetic mistakes or notation errors.

**Example:**  
Believing derivative = exponent minus one for *all* functions, including products.

---

### 2.2 Procedural Slip

**Definition:**  
Learner applies the correct concept but executes one or more steps incorrectly.

**Diagnostic Signals:**  
- Local arithmetic errors  
- Sign mistakes  
- Dropped terms  
- Parentheses/notation errors  

**Exclusion:**  
Do not classify if the reasoning chain is conceptually incorrect.

**Example:**  
Correctly sets up product rule but multiplies terms incorrectly.

---

### 2.3 Misapplication of Prior Rule

**Definition:**  
A previously learned rule is applied in a context where it does not hold.

**Diagnostic Signals:**  
- Learner explicitly references the rule  
- Output structurally matches the misapplied rule  
- Mistake aligns with over-reliance on a familiar pattern  

**Exclusion:**  
Do not classify if the learner has no apparent conceptual anchor.

**Example:**  
Differentiating a product as if it were a sum.

---

### 2.4 Overgeneralization

**Definition:**  
Learner extends a correct rule beyond its appropriate boundaries.

**Diagnostic Signals:**  
- Applies a rule globally without checking constraints  
- Uses surface similarity as justification  

**Exclusion:**  
If the rule is genuinely applicable but executed incorrectly, classify as a slip.

**Example:**  
Assuming “multiply exponents when multiplying functions” because it works for monomials.

---

### 2.5 Local Reasoning Error

**Definition:**  
An isolated incorrect inference or logical step that breaks an otherwise valid process.

**Diagnostic Signals:**  
- Reasoning chain mostly correct  
- Single flawed step with no conceptual misunderstanding  
- Often disappears after minimal feedback  

**Exclusion:**  
Do not classify if the chain collapses due to conceptual misunderstanding.

**Example:**  
Incorrectly inferring that `3x^2 + x^2 = 4x^2` after correctly applying product rule.

---

### 2.6 AI-Induced Hallucination Adoption

**Definition:**  
Learner adopts incorrect content or structure directly from AI output.

**Diagnostic Signals:**  
- Strong similarity to known AI phrasing  
- Incorrect reasoning aligns with AI hallucination patterns  
- Learner expresses unjustified certainty  

**Exclusion:**  
If the error pre-dates AI interaction, classify using other categories.

**Example:**  
Replicating an AI-generated but incorrect explanation verbatim.

---

### 2.7 Misinterpreted Prompt

**Definition:**  
Learner misunderstands the task itself.

**Diagnostic Signals:**  
- Response solves a different problem  
- Response uses irrelevant methods  
- Learner exhibits confusion about the question’s intent  

**Exclusion:**  
Do not classify when the misinterpretation stems from a conceptual issue.

**Example:**  
Solving for derivative when task asks for tangent-line equation.

---

### 2.8 Surface-Level Mimicry (AI Fluency)

**Definition:**  
Response mimics polished AI-like structure but lacks conceptual depth.

**Diagnostic Signals:**  
- Polished explanation without correct core reasoning  
- Correct-sounding but vacuous statements  
- High linguistic fluency, low conceptual accuracy  

**Exclusion:**  
Do not classify if fluency matches actual understanding.

**Example:**  
A “step-by-step” explanation written in textbook style but executing the wrong rule.

---

## 3. Confidence Classification Framework

Confidence ratings use a standardized 1–5 scale. Coders assign the value based on learner metadata or self-report when available. If self-report is absent, use behavioral indicators.

---

### 3.1 Scale Definition

| Rating | Descriptor | Indicators |
|--------|------------|------------|
| **1** | Very Low | Hedge words, uncertainty markers, speculative language, request for confirmation |
| **2** | Low | Tentative reasoning, partial confidence, explicit caveats |
| **3** | Moderate | Neutral tone, procedural certainty without overclaiming |
| **4** | High | Assertive tone, confident reasoning, absence of uncertainty despite errors |
| **5** | Very High | Strong declarative statements, refusal to entertain alternative reasoning, explicit claims of certainty |

---

### 3.2 Behavioral Indicators (when self-report is absent)

Use the following cues:

**Lexical markers:**  
- High confidence: “obviously”, “clearly”, “the derivative is definitely…”  
- Low confidence: “maybe”, “I think”, “not sure”

**Structural markers:**  
- High confidence: clean, assertive steps with no hedging  
- Low confidence: scattered steps, checking with the system, asking “Is this right?”

**Interaction markers:**  
- High: ignoring feedback hints  
- Low: asking for validation after each step

---

## 4. Dual Coding Rules

When annotating an event:
1. Assign **exactly one** error type from the taxonomy.  
2. Assign a **confidence rating** using the 1–5 scale.  
3. If both conceptual and procedural errors are present, classify according to the **dominant causal error**.  
4. If AI-induced patterns are detected, they take precedence over generic categories.  

---

## 5. Reliability Guidelines

To maintain consistency:
- Coders must label a calibration set of 20 events before annotating full datasets.  
- Disagreements resolved via majority consensus or protocol revision.  
- Any new ambiguous error pattern must be appended to a “pending review” list.  

---

End of coding framework.
