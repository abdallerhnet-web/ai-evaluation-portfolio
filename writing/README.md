# Technical Writing Samples

Four professional writing samples covering product documentation,
how-to guides, knowledge base articles, and AI workflow guides.

---

## Sample 1 — API Documentation

### CloudVault API — Getting Started Guide

**Document type:** Developer onboarding documentation
**Audience:** Developers with basic REST API experience

---

#### Overview

The CloudVault API allows you to programmatically manage files, folders,
and user permissions. This guide covers authentication, making your first
request, and handling responses.

**Base URL:** `https://api.cloudvault.io/v2`
**Protocol:** HTTPS only
**Authentication:** Bearer token (OAuth 2.0)

---

#### Prerequisites

Before you begin, ensure you have:
- A CloudVault account (Pro or Enterprise tier)
- An API key from your dashboard (Settings → Developer → API Keys)
- A tool for making HTTP requests (curl, Postman, or similar)

---

#### Step 1: Authenticate

All API requests require a valid Bearer token in the Authorization header.

Authorization: Bearer YOUR_API_KEY
Example request:
curl -X GET "https://api.cloudvault.io/v2/files" 
-H "Authorization: Bearer YOUR_API_KEY" 
-H "Content-Type: application/json"

> **Security note:** Never expose your API key in client-side code or
public repositories. Store it as an environment variable.

---

#### Step 2: List Your Files

GET /v2/files

Parameters:

| Parameter | Type | Required | Description |
|---|---|---|---|
| folder_id | string | No | Filter by folder |
| limit | integer | No | Results per page. Default: 20. Max: 100 |
| offset | integer | No | Pagination offset. Default: 0 |

Example response:

{
"status": "success",
"total": 143,
"files": [
{
"id": "file_8f3k2j",
"name": "quarterly_report.pdf",
"size_bytes": 204800,
"created_at": "2024-09-15T14:32:00Z"
}
]
}

---

#### Error Handling

| HTTP Status | Meaning |
|---|---|
| 401 | Invalid or missing API key |
| 403 | Insufficient permissions |
| 404 | File or folder does not exist |
| 429 | Rate limit exceeded |
| 500 | Internal error — retry with exponential backoff |

---

#### Rate Limits

| Tier | Requests/minute |
|---|---|
| Pro | 100 |
| Enterprise | 1,000 |

Exceeding the limit returns HTTP 429. Implement exponential backoff:
wait 1s, 2s, 4s, 8s between retries.

---

## Sample 2 — How-To Guide

### How to Evaluate an AI Response for Factual Accuracy

**Audience:** New AI evaluators and data annotators

---

Evaluating an AI response for factual accuracy is more than checking
whether something "sounds right." This guide walks you through a
repeatable verification process.

---

#### Step 1: Read the Full Response Before Evaluating

Resist checking the first sentence immediately. Read everything first to:
- Understand the overall claim structure
- Spot internal contradictions before checking external sources
- Identify which claims are factual vs. opinion

---

#### Step 2: List All Factual Claims

Go sentence by sentence. List every claim that is:
- A specific date, number, or statistic
- An attribution (who said or did something)
- A causal claim ("X causes Y")
- A historical or scientific fact

---

#### Step 3: Check Each Claim Against Independent Sources

For each factual claim:
1. Search using quotation marks and key terms
2. Find at least 2 independent sources that confirm or contradict it
3. Prefer primary sources over secondary sources
4. If sources conflict, note the disagreement

**High-trust sources:** Academic journals, government websites,
established news organizations, official publications

**Low-trust sources:** Wikipedia (starting point only), forums,
social media, undated articles

---

#### Step 4: Classify Each Claim

| Label | Meaning |
|---|---|
| ✅ VERIFIED | Confirmed by 2+ independent sources |
| ⚠️ PARTIALLY CORRECT | Core claim true but contains inaccuracy |
| ❌ INCORRECT | Contradicted by reliable sources |
| ❓ UNVERIFIABLE | Cannot be confirmed or denied |
| 🚨 HALLUCINATION | Appears fabricated |

---

#### Step 5: Write Your Feedback

For each non-verified claim, write:
1. What the claim says
2. What you found when you checked
3. What the correct information is
4. Your label and why

Example:
> Claim: "The Eiffel Tower was built in 1889 for the 1890 World's Fair."
> Check: Sources confirm it was built for the 1889 World's Fair, not 1890.
> Label: ⚠️ PARTIALLY CORRECT

---

#### Common Mistakes to Avoid

- Assuming plausibility equals accuracy
- Using only one source
- Confusing opinion with fact
- Overlooking numbers — statistics and dates are the most common AI
  error points

---

## Sample 3 — Knowledge Base Article

### Understanding RLHF: What It Is and Why It Matters

**Audience:** New team members at an AI evaluation platform

---

#### What is RLHF?

RLHF stands for **Reinforcement Learning from Human Feedback**. It is
a training technique used to align AI language models with human
preferences — making them more helpful, accurate, and safe.

---

#### Why Does It Matter?

Without RLHF, language models optimize for statistical plausibility —
producing text that looks like a good answer without necessarily being
one. RLHF shifts the optimization target from "sounds reasonable" to
"is actually preferred by humans."

This is why ChatGPT, Claude, and Gemini behave differently from raw
language models — they have been shaped by human feedback at scale.

---

#### How the Process Works

**Phase 1 — Supervised Fine-Tuning (SFT):**
Human trainers write example responses to prompts. The model learns
to imitate this style as a starting point.

**Phase 2 — Reward Model Training:**
Human evaluators compare pairs of AI responses and select the better
one. These preference signals train a reward model.

**Phase 3 — Reinforcement Learning:**
The main model is trained using the reward model as a signal —
rewarding responses humans prefer, penalizing those they don't.

---

#### Your Role in This Process

As an AI evaluator, you contribute directly to Phase 2. Every
preference label you assign feeds into the reward model's training
signal. Precise, consistent evaluations improve model quality.
Careless labels degrade it.

---

#### Key Terms

| Term | Definition |
|---|---|
| RLHF | Reinforcement Learning from Human Feedback |
| RLAIF | Reinforcement Learning from AI Feedback |
| Reward model | Trained on human preferences to score outputs |
| Preference pair | Two responses evaluated against each other |
| SFT | Supervised Fine-Tuning |
| Inter-rater reliability | Agreement rate between different annotators |

---

## Sample 4 — AI Workflow Guide

### Prompt Iteration: From First Draft to Production-Ready

**Audience:** Prompt engineers and AI evaluators

---

#### Introduction

A first-draft prompt rarely performs well. Prompt engineering is
iterative — the goal is to move systematically from a vague idea
to a precisely specified instruction that produces consistent results.

---

#### Stage 1: Define the Objective

Before writing anything, answer:
1. What task do I want the model to complete?
2. Who is the output for?
3. What does a perfect output look like?

Write these answers down. They become your success criteria.

---

#### Stage 2: Write the First Draft

Write a minimal prompt that communicates the task:

Draft 1: "Summarize the following article."

This is your baseline. Run it. Note what's wrong.

---

#### Stage 3: Identify Failure Modes

Run the draft 3–5 times. Document what goes wrong:
- Is the output too long or too short?
- Is the tone wrong?
- Is the model missing required elements?
- Is the model making wrong assumptions?

Each failure mode becomes a constraint to add next.

---

#### Stage 4: Add Constraints Systematically

Address each failure with a specific instruction:

This is your baseline. Run it. Note what's wrong.

Run again. Document new failures.

---

#### Stage 5: Validate Against Success Criteria

When output consistently meets your Stage 1 criteria:
1. Run on at least 5 diverse inputs
2. Check edge cases
3. Document the final prompt with version notes
4. Archive earlier drafts for regression testing

---

#### Prompt Version Log Template

Prompt: [Name]
Version: 1.3
Last updated: 2024-11-15
Task: Summarize news articles for general readers
Current Prompt:
[Full prompt text here]
Known Limitations:
Occasionally too brief on articles over 2,000 words
Changelog:
v1.3 — Added word count range
v1.2 — Added "general audience" instruction
v1.1 — Added "facts only" constraint
v1.0 — Initial draft

---

→ [Back to Portfolio](../README.md) | [Research & Fact-Checking →](../research/)
