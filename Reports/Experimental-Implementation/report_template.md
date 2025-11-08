## Before the Template

[This entire "Before the Template" section is instructional and must be deleted before you commit your file.]

### 1. File Location:

Upload your completed report to the following project repository **`Firat-Kalite-Guvencesi/Management`** and under the **`Reports/Experimental-Implementation`** directory.

### 2. File Naming Convention:

The file name **must** follow this exact structure to ensure proper sorting and identification:
**`[TestType]_[ResearcherName]_Implementation.md`**

- `[TestType]` should be a single, descriptive term (e.g., `Functional`, `Performance`, `SecurityHeaders`).
- `[ResearcherName]` should be your name (e.g., `Kubra`).

**Example:** `Performance_Kubra_Implementation.md`

### 3. Code & Artifact Publication:

Your "defect-proving test" code is a critical artifact. Please create a new, public **GitHub repository**. This way you also keep a proof of your work.

You will **link to this repository** in the `## 4. Final Artifacts` section of your report. This ensures we have a clean, verifiable copy of the "golden data" you generated.

### 4. Cleanup Before Committing

Before you commit your file to the repository, you **must** delete the following sections:

1.  This entire `## Before the Template` block (from the top of the file down to the horizontal rule below).
2.  The `This template is prepared by...` credit line at the very bottom of the file.

Your final file should **only** contain your analysis, starting from the `### Experimental Implementation Log` title.

---

### Experimental Implementation Log

**Researcher:** [Your Name]
**Date:** [Date of Completion]
**Task:** [e.g., Functional Test, Performance Test]

---

## 1. Executive Summary

[This section must be completed **LAST**. Write a 2-paragraph summary of your experience.]

- **Paragraph 1: The Outcome.** State your specific goal (e.g., "Prove an XSS vulnerability existed in the search bar"). Were you able to achieve it? Briefly describe the test you produced to prove the defect.
- **Paragraph 2: The Experience.** In one sentence, describe the implementation process (e.g., "The process was deeply frustrating due to unclear documentation."). What was the single biggest "pain point" or "struggle" you encountered?

---

## 2. Setup & Configuration

[The goal of this section is to document the "cost" of getting started.]

**Tool(s) Used:**
[List the primary tools and versions. e.g., Cypress.io v12.1, k6 v0.41.0, Node.js v18.1]

**Estimated Time for Setup:**
[e.g., "2.5 hours", "20 minutes"]

**Setup & Configuration Log:**
[Describe the steps and any friction you encountered during setup.
**Example:** "Installing k6 was easy, but I spent 1 hour trying to figure out how to write the script. The documentation for `thresholds` was confusing."]

---

## 3. Implementation Log: "The Journey"

[This is the most critical section. This is your qualitative log of the *process*. Be detailed. This is the data we need.]

**Target Defect:**
[Be specific about the defect you proved.
**Example:** "XSS vulnerability in the `q` parameter of the `/search` page."]

**Process Log:**
[Provide a brief, chronological log of your process and "stuck points."
**Example:** "I wrote a Cypress test to `visit()` the page and `type()` a payload. The test passed, but the alert didn't fire. I didn't know how to 'catch' an alert. This took 45 minutes to Google."]

**Biggest "Pain Point" / "Struggle":**
[Describe the single most frustrating or confusing part of this task.
**Example:** "(Domain Knowledge): I didn't know what a 'good' security header was. I had to spend 40 minutes on the OWASP site *before* I could even start to write the test."]

---

## 4. Final Artifacts

[This is the "proof" of your work. It serves as the "golden data" for our LLM-QA project.]

**Link to Code Repository/Gist:**
[Insert a name for your link here](Insert the full URL to your public GitHub repo or Gist here.)

---

## 5. Reflection & Relevance to LLM-QA

[This is your final analysis, connecting your experience to our project.]

**Analysis of the Manual Process:**
[Based on your experience, what is your opinion of this manual "defect-to-test" process?
**Example:** "It's powerful, but it requires too much expert knowledge in a specific tool (Cypress) and a specific domain (XSS)."]

**How LLM-QA Could Have Helped:**
[Be specific. Where in this process could our tool have saved you time or frustration?
**Example:** "I wish I could have just told the LLM, 'The search bar is vulnerable to XSS,' and it would have *generated* the correct Cypress test, including the `cy.on('window:alert')` part I got stuck on."]

---

`This template is prepared by Ali Bulut and Google Gemini`
