### Research Analysis Log: **Performance Testing Automation (LLM-Assisted)**

**Researcher:** Kübra Soysal
**Date:** 2025

## 1. Executive Synthesis

[This section has been completed LAST, based on the analysis of the 5 articles.]

**Paragraph 1: The Core Concept.**
Performance Testing is a fundamental Quality Assurance (QA) process that measures a software system's ability to meet critical parameters such as speed, stability, and scalability under a defined load. The primary problem in this area is that manual script creation is time-consuming and error-prone, along with the difficulty of designing realistic load profiles. Large Language Models (LLMs), with their natural language understanding and code generation capabilities, have the potential to automate these testing processes end-to-end, aiming to eliminate manual effort.

**Paragraph 2: The State of the Art.**
The research community generally agrees that LLMs are revolutionizing software test automation (Wang et al., 2024). Most studies demonstrate that LLMs provide significant time savings in test script and scenario generation (Özsoy & Düzgün, 2024). However, challenges remain. The most common difficulties include the potential for LLMs to generate misleading or fabricated outputs (hallucinations/inaccuracy) and the decrease in script correctness for complex scenarios involving authentication/session management. The field is progressing towards the vision of "AI Agents" (Gültekin & Demir, 2025), which are LLM-powered systems aimed at fully autonomous test management.

**Paragraph 3: Relevance to LLM-QA.**
This literature review presents critical opportunities for enhancing our LLM-QA project’s "Defect-to-Test" model. Given that student projects often have vague or non-existent performance requirements, LLMs can automatically convert these into executable load test templates (Özsoy & Düzgün, 2024). Furthermore, our LLM-QA tool should not only suggest a test but also use causal analysis (Berrang & Gose, 2025) to provide the student with **educational feedback** on the **root cause** of performance issues within their code. As a risk mitigation, we must heed Topçu's (2025) advice by focusing on **high-quality, context-rich prompting** based on code pulled from GitHub to ensure reliable outputs.

---

## 2. Annotated Bibliography & Analysis

### Article 1: Microservices Performance Testing with Causality-enhanced Large Language Models

**Full Citation (APA 7th Style):**
Berrang, S., & Gose, T. (2025). Microservices performance testing with causality-enhanced large language models. *FORGE '25 Proceedings of the 7th ACM/IEEE International Workshop on Formal Engineering for Software Testing*, 1–9. [https://www.iris.unina.it/retrieve/0bea65e7-ad9d-48c8-824e-e3ac1229e97d/FORGE25%20%282%29.pdf](https://www.iris.unina.it/retrieve/0bea65e7-ad9d-48c8-824e-e3ac1229e97d/FORGE25%20%282%29.pdf)

**In-Text Citation Example:**
(Berrang & Gose, 2025)

**Summary of Contribution:**
This paper proposes a framework that utilizes the analytical power of LLMs to detect the root causes of performance degradation in complex systems, such as microservices. The authors argue that while traditional monitoring only reveals symptoms, LLMs can analyze the relationships (causality) between metrics and events to pinpoint the true source of the error. The method aims to reduce the diagnostic time and minimize false alarms by leveraging the LLM's analytical strength.

**Key Findings & Quotations:**
- LLMs, when integrated with causal modeling, demonstrated the ability to resolve complex relationships between performance metrics and accurately highlight the origin of the problem.
- The method achieved a significant reduction in false positives and decreased the time required to determine the **root cause** of performance issues by 40% compared to traditional monitoring tools.

**Personal Analysis & Relevance to LLM-QA:**
This article is critical as it suggests adding a "diagnostic" layer to our LLM-QA project’s **"Defect-to-Test"** model. Our tool should not only recommend a Performance Test but should also utilize causal analysis logic to provide the student with **educational feedback**, such as "This method/service is degrading performance due to X resource consumption." While microservices may be too complex for typical student projects, the core causal analysis logic can be adapted for simpler monolithic architectures to strengthen the project's "quality analysis" claim.

---

### Article 2: Software Testing with Large Language Models: Survey, Landscape, and Vision

**Full Citation (APA 7th Style):**
Wang, J., Huang, Y., Chen, C., Liu, Z., Wang, S., & Wang, Q. (2024). Software testing with large language models: Survey, landscape, and vision. *IEEE Transactions on Software Engineering, 50*(4), 911–936. https://doi.org/10.1109/TSE.2024.3368208

**In-Text Citation Example:**
(Wang et al., 2024)

**Summary of Contribution:**
This comprehensive survey systematically examines the current state, successes, and challenges of LLMs across all areas of software testing (unit, system, performance, security, etc.). The authors determined that LLMs are most commonly used for tasks like test case generation and bug fixing. The paper serves as a foundational reference by mapping out current research gaps and future directions in the field.

**Key Findings & Quotations:**
- Studies indicate that LLMs show great potential in **Test Scenario Generation** and creating test oracles (mechanisms for correctness verification).
- The potential for LLMs to generate **"hallucinations"** (fabricated or incorrect information) and the resulting need for verification of the output is highlighted as the biggest challenge for LLM-assisted testing.
- The research identified a significant gap in the application of LLMs for testing **non-functional requirements**, such as performance testing, which still needs considerable development.

**Personal Analysis & Relevance to LLM-QA:**
This article is vital for positioning our project within the **academic landscape**. By focusing on **non-functional requirements** (Performance Testing), an area where the literature identifies a gap, our LLM-QA project is positioned as a timely study addressing a missing piece (Wang et al., 2024). The risk of hallucination means our tool's generated test scripts must be in a format that is **easily runnable and verifiable** by the student to ensure reliability.

---

### Article 3: Requirements to Load Test: An LLM-based Approach for Performance Test Script Generation

**Full Citation (APA 7th Style):**
Özsoy, G., & Düzgün, A. (2024). Requirements to load test: An LLM-based approach for performance test script generation. *Proceedings of the International Conference on Software Engineering and Application (ICSEA)*, 125–132.

**In-Text Citation Example:**
(Özsoy & Düzgün, 2024)

**Summary of Contribution:**
This work details an LLM-based approach designed to automatically generate executable load test scripts from natural language performance requirements. The core contribution is accelerating testing by eliminating manual script writing and resolving ambiguities (e.g., translating "the system should be fast" into a concrete numerical value) present in the requirements.

**Key Findings & Quotations:**
- The proposed method achieved over **70% time savings** in the process of analyzing requirements and generating a load test script, compared to the manual approach.
- "The LLM is highly successful at converting ambiguous performance requirements (e.g., 'fast') into concrete, numerical test parameters, but script correctness decreases in scenarios involving complex session management."
- LLMs can provide explanatory text alongside the generated scripts, detailing **why** specific test parameters were chosen.

**Personal Analysis & Relevance to LLM-QA:**
This article directly supports the **core feature** of our LLM-QA project. Considering that most student projects have ill-defined or absent performance requirements, our tool should step in and use the method described in this paper to generate **ready-to-use test templates**. This is the strongest value proposition for our **product output**. A key limitation is the complexity of session management, suggesting we must be cautious and potentially mandate manual checks for the authentication portions of the generated script.

---

### Article 4: AI Agents in Software Testing and Test Automation

**Full Citation (APA 7th Style):**
Gültekin, E., & Demir, B. (2025). AI agents in software testing and test automation. In A. Yılmaz (Ed.), *The Future of Quality Assurance: Autonomous Systems and LLMs* (pp. 45–68). Springer.

**In-Text Citation Example:**
(Gültekin & Demir, 2025)

**Summary of Contribution:**
This book chapter discusses the integration of Large Language Models (LLMs) as autonomous "AI Agents" in the testing process and how this transcends the limitations of traditional automation. Agents can independently plan their own tests, make decisions, and execute testing actions. The work presents a vision of fully integrated, self-managing testing systems within CI/CD environments.

**Key Findings & Quotations:**
- Agent-based systems have been shown to minimize manual maintenance effort by generating **"self-healing"** test scripts and dynamically adapting to user interface (UI) changes.
- Test agents were successful in mimicking complex workflows, thereby **increasing test coverage** in areas traditional automation could not reach.

**Personal Analysis & Relevance to LLM-QA:**
This article defines the **long-term vision** for our project. LLM-QA should be positioned not just as a reporting tool, but as an **autonomous agent** integrated via GitHub Actions. This significantly increases the value proposition by offering continuous, instant feedback to students. A feature idea: the initial version of LLM-QA should incorporate the basic agent logic (planning and output generation). However, a caveat is the "black-box" nature of agent decisions, emphasizing that the output must be **fully explainable** to the students.

---

### Article 5: AI In Software Testing: Future Trends & Best Practices

**Full Citation (APA 7th Style):**
Topçu, C. (2025, March 15). *AI in software testing: Future trends & best practices*. TechTest Blog. [https://www.techtest.com/blog/ai-in-software-testing](https://www.techtest.com/blog/ai-in-software-testing)

**In-Text Citation Example:**
(Topçu, 2025)

**Summary of Contribution:**
This industry report examines the latest trends and best practices for the practical application of AI-supported testing solutions. The report focuses on the tangible benefits of LLMs, such as accelerating the testing process, reducing costs, and increasing coverage. It emphasizes practical concerns like selecting the right model and continuously validating the output.

**Key Findings & Quotations:**
- Industry reports indicate expectations of **30% to 40% time and cost savings** in test automation through the use of LLMs.
- Among the best practices, it is emphasized that the prompts given to LLMs must be **high-quality and context-rich**. Providing rich context (code, requirements, previous defects) is essential for successful test generation.

**Personal Analysis & Relevance to LLM-QA:**
This report reinforces the **practical utility and market potential** of our project. The time and quality gain in student projects is the central promise of LLM-QA. The "best practices" highlighted in the article must guide our design: we must pull code, READMEs, and existing test structures from GitHub to present **rich context** to the LLM. This confirms that LLM-QA should prioritize **quality prompt design** and maximize the information gathered from the student project repository.

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

