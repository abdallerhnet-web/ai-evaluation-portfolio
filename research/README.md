# Research & Fact-Checking

This section documents my verification workflow, source validation
process, and three example fact-checking investigations applied to
AI-generated content.

---

## My Verification Workflow

STEP 1: EXTRACT
Read full response. Identify all verifiable factual claims.
List them separately before checking any.
STEP 2: TRIAGE
Sort by risk: numbers, dates, citations first (highest AI error rate)
Flag anything suspiciously specific
STEP 3: SOURCE
Search each claim using specific terms
Find minimum 2 independent sources per claim
Prefer: .gov, .edu, peer-reviewed, official publications
Avoid: single-source, undated, anonymous, AI-generated
STEP 4: CLASSIFY
✅ VERIFIED — 2+ sources confirm
⚠️ PARTIALLY CORRECT — core claim true, detail wrong
❌ INCORRECT — contradicted by reliable sources
❓ UNVERIFIABLE — cannot confirm or deny
🚨 HALLUCINATION — appears fabricated
STEP 5: DOCUMENT
Write evidence note for each non-verified claim
Record sources checked
Assign overall accuracy score
STEP 6: REPORT
Summary: overall accuracy rating
Detail: per-claim findings
Recommendation: approve / revise / reject

---

## Source Validation Criteria

| Tier | Source Type | Examples | Trust Level |
|---|---|---|---|
| 1 | Government & official bodies | CDC, WHO, NASA, NIST | Highest |
| 2 | Peer-reviewed academic | PubMed, Google Scholar, Nature | Highest |
| 3 | Established journalism | Reuters, AP, BBC | High |
| 4 | Official org publications | NGO reports, UN data | High |
| 5 | Wikipedia | Starting point only — verify its sources | Medium |
| 6 | Specialist blogs | MIT Tech Review, Ars Technica | Medium |
| 7 | Social media, forums, AI output | Twitter, Reddit, ChatGPT | Disqualified |

**Rule:** A claim is only marked ✅ VERIFIED if confirmed by Tier 1–4 sources.

---

## Investigation 01 — Climate Change Statistics

**Claim extracted from AI response:**
"Global average temperatures have risen by 1.2°C since the pre-industrial
era, and scientists predict a further 1.5°C rise will occur by 2030 if
current emissions continue."

---

**Claim A:** "Risen by 1.2°C since pre-industrial era"

- Source 1: NASA Global Climate Change — confirms approximately 1.1–1.2°C
  warming above pre-industrial baseline as of 2023
- Source 2: IPCC Sixth Assessment Report (2021) — confirms 1.09°C (±0.1°C)
  average warming above 1850–1900 baseline

**Finding:** ✅ VERIFIED (exact figure depends on baseline year; 1.1–1.2°C
accurate for 2023 data)

---

**Claim B:** "Scientists predict a further 1.5°C rise will occur by 2030"

- Source 1: IPCC AR6 — projects 1.5°C above pre-industrial *total* (not
  additional) is likely reached in early 2030s under high-emission scenarios
- Source 2: WMO (2023) — states 66% chance of *temporarily* exceeding 1.5°C
  in at least one year between 2023–2027

**Finding:** ⚠️ PARTIALLY CORRECT — The 1.5°C figure refers to total warming
above pre-industrial baseline, not an *additional* 1.5°C. The AI response
misrepresents the projection significantly.

**Recommendation:** Flag Claim B for revision. The error is about what the
number measures, not the number itself.

---

## Investigation 02 — Technology History Claim

**Claim extracted from AI response:**
"The internet was invented by Tim Berners-Lee in 1989 at CERN in Switzerland."

---

**Parsing the claim — three sub-claims:**
1. The internet was invented by Tim Berners-Lee
2. It was invented in 1989
3. It happened at CERN

---

**Sub-claim 1:** Tim Berners-Lee invented the internet

- Source 1: CERN official history — Berners-Lee invented the **World Wide
  Web** (WWW), not the internet
- Source 2: Internet Society history — The internet (as ARPANET) predates
  Berners-Lee by two decades; key milestones include 1969 (ARPANET) and
  1983 (TCP/IP adoption)

**Finding:** ❌ INCORRECT — Berners-Lee invented the Web, not the internet.
These are distinct technologies. The internet is the global network
infrastructure; the Web is the document-sharing system that runs on top of it.

**Sub-claims 2 & 3:** 1989 at CERN
- W3C confirms Berners-Lee's proposal was submitted in March 1989 at CERN ✅
  (for the Web, not the internet)

**Overall finding:** ❌ INCORRECT — significant factual error that conflates
the internet with the World Wide Web.

**Recommended corrected text:**
"The World Wide Web was invented by Tim Berners-Lee in 1989 at CERN in
Switzerland. The internet itself is older — it grew from ARPANET, a US
government research network established in 1969."

---

## Investigation 03 — Hallucination Detection: Fabricated Citation

**Claim extracted from AI response:**
"According to a 2021 study published in The Lancet by Dr. Priya Mehta at
Stanford University, adults who consume 30g of dietary fiber daily reduce
their risk of colorectal cancer by 47%."

---

**Red flags identified before searching:**
- Very specific percentage (47%) — hallucinated statistics often use
  suspiciously specific values
- Named researcher + institution + journal + year combination
- Any of these elements could be fabricated

---

**Step 1: Search for Dr. Priya Mehta + Stanford + fiber + Lancet**
- Google Scholar: No results for this specific study
- PubMed: No results matching this author + journal + topic
- The Lancet website: No accessible study matching this description

**Step 2: Verify the statistical claim independently**
- Source 1: World Cancer Research Fund — literature supports fiber and
  colorectal cancer link but figures range from 10–25% risk reduction,
  not 47%
- Source 2: A 2019 Lancet study (Aune et al.) found approximately 22%
  risk reduction per 10g/day increment

**Step 3: Verify the researcher**
- Stanford Medicine faculty directory: No Dr. Priya Mehta in nutrition
  or oncology departments

---

**Finding:** 🚨 HALLUCINATION — The named researcher, the 47% figure, and
the cited study appear entirely fabricated. The general topic is real but
this specific attribution does not exist.

**Severity:** HIGH. This response uses the structure of a credible citation
to lend false authority to an invented statistic.

**Recommendation:** Reject immediately. Flag as hallucination pattern
example. Do not use as training positive under any circumstances.

---

→ [Back to Portfolio](../README.md) | [Quality Assurance →](../qa/)

