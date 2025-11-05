## Before the Template

### Naming of your document:

When you upload your document to **`Firat-Kalite-Güvencesi/Management`** repository. Make sure it's under the **Reports** file.

Also,

Naming of your document should be: `your-test_your-name_literature-review.md`

- **Example:** `Performance_Kubra_LR.md`

---

### Research Analysis Log: [Insert Test Type, e.g., Mutation Testing]

**Researcher:** [Your Name]
**Date:** [Date of Completion]

## 1. Executive Synthesis

[This section must be completed **LAST**. After analyzing all 5+ articles, write a 3-paragraph synthesis.

- **Paragraph 1: The Core Concept.** What is [Test Type]? What is the primary problem it solves?
- **Paragraph 2: The State of the Art.** What are the main findings, common challenges, or open questions the research community has identified? (e.g., "Most research agrees that X is effective, but it suffers from Y and Z.")
- **Paragraph 3: Relevance to LLM-QA.** How does this information impact our "Defect-to-Test" project? What opportunities or risks does it present? (e.g., "This suggests our LLM-QA tool should focus on X, as it seems to be the biggest pain point...")]

---

## 2. Annotated Bibliography & Analysis

[Complete one section for each article you review. This is the main body of your work.]

### Article 1: [Title of the Article]

**Full Citation (APA 7th Style):**
[Insert full citation here. See "How to Cite" section below.]

**In-Text Citation Example:**
(Author(s), Year)

**Summary of Contribution:**
[In your own words, what is the central argument or contribution of this paper? What research question did the authors ask, what method did they use, and what did they find? (Max 4-5 sentences)]

**Key Findings & Quotations:**
[List 2-3 of the most important findings as bullet points. If you copy a direct quote, it **must** be in "quotation marks" and include the page number (Author, Year, p. #).]

- [Finding 1, e.g., "The authors proved that this test method found 30% more critical defects than traditional unit tests (Smith & Jones, 2021)."]
- [Finding 2]

**Personal Analysis & Relevance to LLM-QA:**
[This is the most important section. This is _your_ analysis.

- Do you agree with the authors' conclusions?
- What are the limitations of this study?
- How does this paper directly relate to our LLM-QA project?
- Does it give you an idea for a feature? Does it warn you about a potential failure mode?
- e.g., "This paper is critical because it provides a benchmark for 'high-risk defect patterns,' which is exactly what our abstract claims LLM-QA will target. Their list of patterns could be a starting point for our LLM prompts."]

---

### Article 2: [Title of the Article]

**Full Citation (APA 7th Style):**
[...]

**In-Text Citation Example:**
[...]

**Summary of Contribution:**
[...]

**Key Findings & Quotations:**
[...]

**Personal Analysis & Relevance to LLM-QA:**
[...]

---

[Repeat for all 5+ articles]

---

### 3. Appendix: How to Cite (A Brief Guide)

You must cite your resources in your work. This is non-negotiable for academic work.

**What is Citing and Why Do We Do It?**

Citation is the practice of giving credit to the sources you use. In research, failing to cite is considered **plagiarism**, which is the theft of intellectual property and the most severe academic offense.

We cite for two reasons:

1.  **To give credit:** To acknowledge the work of the researchers who came before us.
2.  **To provide a trail:** To allow your reader (me, or the reviewers of our paper) to find the exact source you used and verify your claims.

**Two Types of Citation:**

We are using both in articles.

1.  **In-Text Citation:** A brief note _inside_ your sentence to show where the idea came from.

    - **Example:** The "Defect-to-Test" model is superior because it provides a "permanent safety net" (Your Team's Abstract, 2025).
    - **Example:** Smith (2021) argues that mutation testing is too slow for CI/CD pipelines.

2.  **Full Citation (Bibliography/Reference List):** The full details of the source, listed at the end of your document. This is what allows the reader to find the source.

**How to Format a Full Citation (APA 7th Edition)**

Use these templates based on the source type.

> **Template 1: Journal/Conference Article**
> Author, A. A., Author, B. B., & Author, C. C. (Year). Title of the article: Subtitle if any. _Title of the Journal or Conference Proceedings, Volume_(Issue), pages. DOI (Digital Object Identifier)
>
> **Example:** De Millo, R. A., Lipton, R. J., & Perlis, A. J. (1979). Social processes and proofs of theorems and programs. _Communications of the ACM, 22_(5), 271–280. [https://doi.org/10.1145/359104.359106](https://doi.org/10.1145/359104.359106)

> **Template 2: Website or Blog Post**
> Author, A. A. (Year, Month Day). Title of the work. _Website Name_. URL
>
> **Example:** Fowler, M. (2014, January 21). TestCoverage. _Martin Fowler's Blog_. [https://martinfowler.com/bliki/TestCoverage.html](https://martinfowler.com/bliki/TestCoverage.html)

> **Template 3: Book**
> Author, A. A. (Year). _Title of work_ (Edition, if any). Publisher.
>
> **Example:** Hunt, A., & Thomas, D. (2000). _The Pragmatic Programmer: From Journeyman to Master_. Addison-Wesley Professional.

---

## | This template is prepared by Ali Bulut and Google Gemini
