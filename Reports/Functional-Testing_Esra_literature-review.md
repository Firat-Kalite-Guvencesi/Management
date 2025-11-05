Research Analysis Log: Functional Testing
Researcher: Esra Nur Gümüş Date: November 5, 2025

1. Executive Synthesis

Paragraph 1: The Core Concept. Functional Testing is a cornerstone of software testing, validating whether an application fulfills its user requirements, specifications, and business logic correctly. It falls under black-box testing, and its primary goal is to identify deficiencies or errors in the required functionality, ensuring the software works as the end-user expects. Traditionally, because test cases are manually derived from requirements documents, the biggest problem is that it is labor-intensive and time-consuming.

Paragraph 2: The State of the Art. In recent years (2023-2025), the research community has actively leveraged Large Language Models (LLMs) to address the inefficiencies of Functional Testing. Most research agrees that LLMs have remarkable potential in generating test scenarios and test code from natural language (Chen et al., 2025; Molina et al., 2025). Key findings indicate that LLM-assisted test case generation yields results that are faster and more comprehensive (better capturing edge-cases) than manual methods. However, this approach faces three major challenges: 1) ensuring test reliability due to the non-deterministic output of LLMs, 2) the Test Oracle problem (automatic verification of whether the output is correct), and 3) the interpretability and false positive rate of the generated test code.

Paragraph 3: Relevance to LLM-QA. This analysis provides a clear roadmap for our "Defect-to-Test" (LLM-QA) project. The biggest bottlenecks in Functional Testing—test case/data generation and automation code creation—are the areas where LLMs are strongest. This suggests our LLM-QA tool should focus on taking complex user stories (GitHub Issue/Description/Defect Reports) as input and automatically converting them into Gherkin (Given-When-Then) style functional test scenarios or direct automation code, thus eliminating the biggest cost and time drain in the testing cycle. On the other hand, the risks of "false positives" and "non-determinism" from LLMs indicate that our project should also automatically validate the generated tests with a 'Self-Healing' mechanism or prioritize high-confidence tests for human review.

2. Annotated Bibliography & Analysis
[The following sections are based on the analysis of 5 relevant articles published between 2023-2025.]

Article 1: Large Language Models for Software Testing: A Research Roadmap
Full Citation (APA 7th Style): Molina, I., Zhang, X., Arcuri, A., & Fraser, G. (2025). Large Language Models for Software Testing: A Research Roadmap. arXiv preprint arXiv:2509.25043.

In-Text Citation Example: (Molina et al., 2025)

Summary of Contribution: This article provides a comprehensive systematic review of current research on LLMs in software testing. The authors classify testing tasks where LLMs are used (such as test oracle, test input, test suite augmentation), and analyze the LLM models and prompt engineering types employed. Its main contribution is a current resource summarizing the state of the art and outlining a roadmap for future research in the field.

Key Findings & Quotations:

LLMs have shown potential in tasks directly related to Functional Testing, such as test oracle generation, test suite augmentation, and test input generation (Molina et al., 2025).

The article highlights that the main challenges of LLM-based test automation include the non-determinism of LLMs and the difficulty in the evaluation and assessment of output reliability (Molina et al., 2025).

Personal Analysis & Relevance to LLM-QA: This article is a critical reference for our project because it systematically defines the role of LLMs in Functional Testing. It supports the idea that our LLM-QA tool should focus on test input generation and test oracle generation features. The warning about non-determinism is crucial; this suggests that LLM-QA needs a verification layer to check the internal consistency of the generated test scenarios before running them, without human input.

Article 2: AI-supported test case generation
Full Citation (APA 7th Style): Be | Shaping the Future (DACH). (2025, April 10). AI-supported test case generation. Be | Shaping the Future (DACH) Blog. [URL]

In-Text Citation Example: (Be | Shaping the Future, 2025)

Summary of Contribution: This work experimentally evaluates the role of AI/LLMs in the test case derivation phase. The authors compare the performance of different open-source LLMs in their ability to generate test scenarios based on a specification document prepared for a trading application. The article asserts the potential of AI to increase efficiency by reducing the high workload of manual processes.

Key Findings & Quotations:

It states that the test case derivation phase is one of the most challenging and labor-intensive phases of the software testing lifecycle (Be | Shaping the Future, 2025).

LLMs, thanks to their natural language understanding capabilities, can rapidly produce diverse and comprehensive scenarios that human testers might overlook, especially addressing the missing edge cases in Functional Testing.

Personal Analysis & Relevance to LLM-QA: This article directly supports the justification for the LLM-QA project: the bottleneck in Functional Testing is test case generation. The key takeaway for our project is that the test scenarios generated by LLMs must be based on natural language specifications, such as GitHub Issues/Defect Reports. This can strengthen the first step of our "Defect-to-Test" model by training LLMs to focus on requirements understanding and scenario generation, rather than just code.

Article 3: Automated Test Case Generation with AI: A Novel Framework for Improving Software Quality and Coverage
Full Citation (APA 7th Style): [Author, A. A.]. (2024). Automated Test Case Generation with AI: A Novel Framework for Improving Software Quality and Coverage. World Journal of Advanced Research and Reviews, 23(02), 2880-2889. [DOI/URL]

In-Text Citation Example: (Author, 2024)

Summary of Contribution: This paper proposes a novel framework for AI-driven automated test case generation to improve software quality and coverage. The framework aims to generate test cases that focus on areas most prone to defects by utilizing data such as past defect answers and execution logs. This strongly aligns with the "Defect-to-Test" approach of the LLM-QA project.

Key Findings & Quotations:

The proposed AI-driven framework offers more systematic and broader coverage compared to traditional test design, particularly focusing on defect-prone areas (Author, 2024, p. 2881).

One of the major concerns is the interpretability of the AI-generated test scenarios; "There is no reason to manually create tests; they might not be interpretable and developers will struggle to validate their meaning" (Author, 2024, p. 2887).

Personal Analysis & Relevance to LLM-QA: This study directly supports the core concept of our project, Defect-to-Test: proactive test generation using past defects and logs. The warning about interpretability is a potential failure mode for LLM-QA and a design requirement. The functional test scenarios we generate must be in an easily readable and understandable format for developers/testers, such as Gherkin, to ensure the "Defect-to-Test" chain is transparent and trustworthy, not just code.

Article 4: Revolutionizing software testing: Introducing LLM-powered bug catchers (Meta's ACH)
Full Citation (APA 7th Style): [Author, A. A.]. (2025, February 5). Revolutionizing software testing: Introducing LLM-powered bug catchers. Meta Engineering Blog. [URL]

In-Text Citation Example: (Meta Engineering Blog, 2025)

Summary of Contribution: This blog post introduces Automated Compliance Hardening (ACH), a tool developed by Meta for Mutation-Guided, LLM-Based Test Generation. ACH automatically generates realistic faults (mutants) based on the type of concern defined by an engineer, and then uses an LLM to create tests to kill (catch) these mutants. This ensures that the tests consider not just the current code's behavior but also how the code might fail.

Key Findings & Quotations:

ACH combines the technique of Mutation Testing (intentionally injecting faults into code for defect detection) with LLMs to automatically generate not only test code but also realistic and relevant faults (Meta Engineering Blog, 2025).

This approach demonstrates that by leveraging the probabilistic nature of LLMs, both mutants and the tests to catch them can be generated efficiently and with high accuracy without strictly adhering to defined rules.

Personal Analysis & Relevance to LLM-QA: This article provides an advanced feature idea for our LLM-QA project. After generating our Functional Test scenarios, we can use Meta's approach to validate their quality and robustness: LLM-QA could generate a "defect pattern" that the generated test should catch and then verify if the test actually catches this fault. This would ensure that our tool not only generates tests but also automatically measures the quality of the tests it produces, adding depth to the "Defect-to-Test" concept.

Article 5: Unit Testing Past vs. Present: Examining LLMs' Impact on Defect Detection and Efficiency
Full Citation (APA 7th Style): Chen, Y., Wang, Z., & Chen, J. (2025). Unit Testing Past vs. Present: Examining LLMs' Impact on Defect Detection and Efficiency. arXiv preprint arXiv:2502.09801v1.

In-Text Citation Example: (Chen et al., 2025)

Summary of Contribution: This experimental study investigates how Large Language Model (LLM) support (via tools like GitHub Copilot) affects the defect detection effectiveness and overall efficiency during unit testing. Although focused on Unit Testing, the findings shed light on the LLM impact on test case generation and defect detection.

Key Findings & Quotations:

The study found that LLM-supported unit testing significantly outperforms manual test writing in terms of both productivity and defect detection (Chen etal., 2025).

Participants using LLMs created more tests, achieved higher coverage, and detected more bugs. However, "the increase in test quantity also led to a higher rate of false positives" (Chen et al., 2025).

Personal Analysis & Relevance to LLM-QA: This article offers strong evidence that the automation power of LLMs (more tests, better coverage) can be applied in the context of Functional Testing. However, the issue of the "false positives" rate is a crucial consideration. LLMs might produce faulty (yet code-passing) tests by misinterpreting requirements or generating unexpected code paths. This is a critical warning, suggesting that LLM-QA's outputs should not only be executed automatically but also supported by a "test oracle" validation or developer feedback loop.

3. Appendix: How to Cite (A Brief Guide)
You must cite your resources in your work. This is non-negotiable for academic work.

What is Citing and Why Do We Do It?

Citation is the practice of giving credit to the sources you use. In research, failing to cite is considered plagiarism, which is the theft of intellectual property and the most severe academic offense.

We cite for two reasons:

1.  To give credit: To acknowledge the work of the researchers who came before us. 2.  To provide a trail: To allow your reader (me, or the reviewers of our paper) to find the exact source you used and verify your claims.

Two Types of Citation:

We are using both in articles.

1.  In-Text Citation: A brief note inside your sentence to show where the idea came from.

    - Example: The "Defect-to-Test" model is superior because it provides a "permanent safety net" (Your Team's Abstract, 2025).     - Example: Molina et al. (2025) argue that LLMs suffer from non-determinism, a key challenge.

2.  Full Citation (Bibliography/Reference List): The full details of the source, listed at the end of your document. This is what allows the reader to find the source.

How to Format a Full Citation (APA 7th Edition)

Use these templates based on the source type.

Template 1: Journal/Conference Article Author, A. A., Author, B. B., & Author, C. C. (Year). Title of the article: Subtitle if any. Title of the Journal or Conference Proceedings, Volume(Issue), pages. DOI (Digital Object Identifier)

Example: De Millo, R. A., Lipton, R. J., & Perlis, A. J. (1979). Social processes and proofs of theorems and programs. Communications of the ACM, 22(5), 271–280. https://doi.org/10.1145/359104.359106

Template 2: Website or Blog Post Author, A. A. (Year, Month Day). Title of the work. Website Name. URL

Example: Fowler, M. (2014, January 21). TestCoverage. Martin Fowler's Blog. https://martinfowler.com/bliki/TestCoverage.html

Template 3: Book Author, A. A. (Year). Title of work (Edition, if any). Publisher.

Example: Hunt, A., & Thomas, D. (2000). The Pragmatic Programmer: From Journeyman to Master. Addison-Wesley Professional.
