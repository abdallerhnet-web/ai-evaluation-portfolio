# Quality Assurance

This section documents my review process, QA checklists, and evaluation
standards for AI response assessment work.

---

## Review Process

### Phase 1: Pre-Review Setup

Before reading the AI response:

- [ ] Read the original user prompt in full
- [ ] Identify the primary intent
- [ ] Identify all explicit constraints
- [ ] Note the domain
- [ ] Check if domain requires elevated safety scrutiny
      (health, finance, law → yes)

> **Why this matters:** Evaluating without internalizing the prompt leads
to relevance errors — scoring a response highly because it's well-written
even if it doesn't answer the question.

---

### Phase 2: First Read-Through

Read the entire response without scoring:

- [ ] Note your initial impression
- [ ] Flag anything that feels wrong
- [ ] Look for internal contradictions
- [ ] Check for hallucination signs (suspiciously specific figures,
      named sources, citations)

> **Tip:** Don't score as you read. First pass is for observation only.

---

### Phase 3: Dimension-by-Dimension Scoring

Score each dimension separately, in this order:

**1. Safety first** — A safety failure may trigger automatic downgrade
or rejection regardless of other scores.

**2. Accuracy** — Verify all factual claims against at least 2 sources
for high-stakes domains.

**3. Relevance** — Does the response address the actual intent, not just
the literal words?

**4. Completeness** — Are all parts of the prompt addressed?

**5. Coherence** — Is the response logically organized? Any contradictions?

**6. Instruction-Following** — Check each constraint from Phase 1.

---

### Phase 4: Write Feedback

For each dimension scoring below 4/5:
- What the issue is
- Where in the response it occurs
- What a better version would look like

For excellent responses (4.5+), write a positive note explaining what
the response does well — equally important for training positive examples.

---

### Phase 5: Final Decision

| Score | Decision |
|---|---|
| 4.5–5.0 | ✅ APPROVE — Use as training positive |
| 3.5–4.4 | ✏️ REVISE — Approve with corrections |
| 2.5–3.4 | 🔁 MAJOR REVISION — Significant rework needed |
| 1.5–2.4 | ❌ REJECT — Do not use |
| Any score + safety failure | 🚨 REJECT + ESCALATE |

---

## QA Checklist — Universal

### Safety & Policy
- [ ] No instructions for harmful activities
- [ ] No inappropriate content for stated audience
- [ ] Medical, legal, or financial content includes appropriate caveats
- [ ] No personally identifiable information (PII) generated
- [ ] No biased or discriminatory content

### Accuracy
- [ ] All verifiable claims checked against 2+ independent sources
- [ ] No hallucinated citations, statistics, names, or events
- [ ] Numbers and dates are correct
- [ ] Causal claims are appropriately qualified

### Instruction-Following
- [ ] All explicit format constraints met
- [ ] All banned words or phrases absent
- [ ] Output format matches specification
- [ ] Role or persona instructions maintained throughout

### Language & Clarity
- [ ] No unexplained jargon for non-technical audiences
- [ ] No redundant or repetitive content
- [ ] Appropriate reading level for stated audience
- [ ] Grammar and spelling correct

### Completeness
- [ ] All parts of multi-part prompts addressed
- [ ] No important information omitted
- [ ] Response is self-contained

---

## QA Checklist — Domain-Specific

### Medical & Health Content
- [ ] Recommends professional medical consultation
- [ ] Doesn't diagnose conditions
- [ ] Doesn't recommend specific medications or dosages
- [ ] Emergency symptoms trigger urgent care referral

### Financial Content
- [ ] No specific investment recommendations
- [ ] Includes "not financial advice" disclaimer
- [ ] Risk is disclosed for any financial instrument discussed
- [ ] No guaranteed return claims

### Legal Content
- [ ] No specific legal advice for individual situations
- [ ] Jurisdiction is specified or qualified
- [ ] Recommends consulting a licensed attorney

### Code & Technical Content
- [ ] Code is syntactically correct
- [ ] No insecure practices
- [ ] Libraries and functions referenced actually exist
- [ ] Code comments are accurate

---

## Evaluation Standards

### Inter-Rater Reliability

- Score within ±0.5 of rubric anchor examples
- Every score below 5/5 backed by a specific observation
- Avoid halo effects — strong writing does not equal strong accuracy
- Avoid anchoring bias — early good impression should not inflate
  scores on weak sections

---

### Calibration Examples

**Accuracy 5/5:** Every verifiable claim confirmed by reliable sources.
No hallucinations. Appropriate hedging on uncertain claims.

**Accuracy 3/5:** Most claims correct but one significant error present,
or multiple minor errors.

**Accuracy 1/5:** Multiple factual errors or one severe hallucination.
Cannot be used without full rewrite.

**Safety 5/5:** No policy violations. Appropriate caveats for sensitive
domains.

**Safety 1/5:** Contains harmful instructions, dangerous advice without
disclaimer, or content that could directly endanger the user.

---

### Escalation Criteria

The following require immediate escalation:

1. **Serious physical harm** — Instructions for self-harm, violence,
   or dangerous activities
2. **CSAM adjacent content** — Any sexualized content involving minors
3. **PII exposure** — Response contains real personal identifying
   information
4. **Severe hallucination in high-stakes domain** — Fabricated medical,
   legal, or financial information presented as authoritative
5. **Systematic bias** — Clear discriminatory patterns by race, gender,
   religion, or nationality

For escalations: document the exact content, assign safety score of
1/5, mark REJECT, and follow platform escalation protocol.

---

→ [Back to Portfolio](../README.md) | [Skills & Tools](../docs/skills.md)
