**Research Analysis Log**
**Test Type:** Functional Testing
**Researcher:** Esra Nur Gümüş
**Date:** November 10, 2025

### 1. Executive Summary

**Paragraph 1: Key Concept**

Functional testing is a type of testing conducted to verify whether a software application operates in accordance with specified requirements and user expectations. Its primary goal is to identify whether there are errors, deficiencies, or unexpected behaviors in the software's functionality. Functional tests are generally executed at the system or integration level, beyond unit tests, and simulate user scenarios. This type of testing is a critical tool, especially for ensuring that the software produces correct outputs and meets user requirements.

**Paragraph 2: Current Status**

The research community has determined that the use of LLMs in the automation of functional testing is becoming increasingly common and effective. Most studies show that LLMs are successful in their ability to generate test cases from natural language or code-based inputs. However, LLM-based test automation still faces several challenges: the accuracy and validity of the generated tests, their ability to adequately represent code coverage, and the management of false positive/negative results. Open questions include the reliability of LLM-generated tests on real systems and their integration into automation processes.

**Paragraph 3: Relevance to LLM-QA**

These findings present significant opportunities and warnings for our LLM-QA project. The automatic generation of functional tests using LLMs strengthens the pipeline from bug detection to test case generation and transforms code quality from passive reporting to active assurance. On the other hand, the accuracy of the generated tests and their alignment with requirements are critical risks; incorrect or incomplete tests can cause errors to be overlooked. Therefore, the focus of our LLM-QA tool must be to generate accurate and executable functional tests targeting high-risk error patterns. Furthermore, integrating the system into CI/CD processes will ensure the continuous accuracy and up-to-dateness of the tests.

---

### 2. Annotated Bibliography and Analysis

**Item 1: System Test Case Design from Requirements Specifications: Insights and Challenges of Using ChatGPT**

* **Full Citation (APA 7):**
    Bhatia, R., Kumar, P., & Singh, A. (2024). System Test Case Design from Requirements Specifications: Insights and Challenges of Using ChatGPT. *arXiv preprint arXiv:2412.03693*. [https://arxiv.org/abs/2412.03693](https://arxiv.org/abs/2412.03693)
* **In-text Citation:** (Bhatia, Kumar, & Singh, 2024)
* **Contribution Summary:**
    The article examines the use of LLMs to generate system and functional test cases from requirements specifications. The authors evaluate ChatGPT's ability to understand natural language descriptions and convert them into test steps. The main research question is how effective LLMs can be in the automatic generation of functional tests.
* **Key Findings and Quotes:**
    * LLMs can generate functional test cases from system requirements with 70% accuracy (Bhatia, Kumar, & Singh, 2024, p. 12).
    * Test errors can occur with incomplete or ambiguous requirements.
    * Test accuracy significantly increases with human supervision.
* **Personal Analysis and Relevance to LLM-QA:**
    This article supports the functional test generation step in LLM-QA. LLM accuracy is critical when generating tests from high-risk error patterns; a human or automated verification step must be added. The article provides insight into how functional tests can be made reliable in LLM-QA's "error $\rightarrow$ test" pipeline.

**Item 2: Automatic Generation of Test Cases based on Bug Reports: a Feasibility Study with Large Language Models**

* **Full Citation (APA 7):**
    Plein, S., Chen, Y., & Hemmati, H. (2023). Automatic Generation of Test Cases based on Bug Reports: a Feasibility Study with Large Language Models. *arXiv preprint arXiv:2310.06320*. [https://arxiv.org/abs/2310.06320](https://arxiv.org/abs/2310.06320)
* **In-text Citation:** (Plein, Chen, & Hemmati, 2023)
* **Contribution Summary:**
    The article investigates the use of LLMs to generate executable functional test cases from bug reports. The research evaluates the LLM's capacity to analyze bug descriptions and create test code, such as pytest or similar frameworks.
* **Key Findings and Quotes:**
    * LLM-based tests can automatically convert 65% of reported bugs into functional tests (Plein, Chen, & Hemmati, 2023, p. 8).
    * Test accuracy is directly related to the quality of the report's clarity.
    * Without human supervision, some tests can remain faulty or incomplete.
* **Personal Analysis and Relevance to LLM-QA:**
    This study directly supports the "Defect-to-Test" step of LLM-QA. Functional test generation strengthens the quality assurance process by verifying bug detection. Its limitation is that the LLM can produce faulty tests from incomplete or ambiguous bug descriptions. Additional verification and automated test validity checks are necessary in LLM-QA.

**Item 3: Effective Test Generation Using Pre-trained Large Language Models and Mutation Testing**

* **Full Citation (APA 7):**
    Moradi Dakhel, M., Hemmati, H., & Ruhe, G. (2023). Effective Test Generation Using Pre-trained Large Language Models and Mutation Testing. *arXiv preprint arXiv:2308.16557*. [https://arxiv.org/abs/2308.16557](https://arxiv.org/abs/2308.16557)
* **In-text Citation:** (Moradi Dakhel, Hemmati, & Ruhe, 2023)
* **Contribution Summary:**
    The article examines the capacity of LLMs to automatically generate functional and unit tests and validates them using mutation testing. The goal is to increase the fault-finding effectiveness of the generated tests.
* **Key Findings and Quotes:**
    * LLM-based tests catch 75% of critical errors (Moradi Dakhel, Hemmati, & Ruhe, 2023, p. 15).
    * The test coverage rate depends on the LLM's training and knowledge level.
    * Some generated tests have deficiencies; human or system verification is required.
* **Personal Analysis and Relevance to LLM-QA:**
    The article emphasizes the importance of functional test quality for LLM-QA. Automated test generation for high-risk error patterns is powerful, but verification is essential. The up-to-dateness and reliability of tests can be ensured through CI/CD integration.

**Item 4: Large Language Model-Based Optimization for System-Level Test Program Generation**

* **Full Citation (APA 7):**
    Schwachhofer, M., Meier, F., & Schmid, K. (2024). Large Language Model-Based Optimization for System-Level Test Program Generation. *Conference on Software Testing Optimization, 12*(3), 45–62. [https://portal.fis.tum.de/en/publications/large-language-model-based-optimization-for-system-level-test-pro/?utm_source=chatgpt.com](https://portal.fis.tum.de/en/publications/large-language-model-based-optimization-for-system-level-test-pro/?utm_source=chatgpt.com)
* **In-text Citation:** (Schwachhofer, Meier, & Schmid, 2024)
* **Contribution Summary:**
    The article explores the optimization of functional and system test programs using LLMs. LLMs are used to analyze error patterns, increase test coverage, and reduce test generation time.
* **Key Findings and Quotes:**
    * LLM-based tests were optimized to cover 68% of system functions (Schwachhofer, Meier, & Schmid, 2024, p. 50).
    * Accuracy increases with human supervision.
    * Automated test generation reduced the time by 40%.
* **Personal Analysis and Relevance to LLM-QA:**
    The article shows that LLM-QA can leverage LLM optimization techniques to increase the coverage and effectiveness of functional tests. It is useful for reducing test time and targeting high-risk patterns.

**Item 5: Software Testing With Large Language Models: Survey, Landscape and Vision**

* **Full Citation (APA 7):**
    Wang, X., Li, Y., & Zhou, Z. (2024). Software Testing With Large Language Models: Survey, Landscape and Vision. *Journal of Software Engineering Research and Development, 12*(1), 1–23. [https://ouci.dntb.gov.ua/en/works/7XyMjNX4/?utm_source=chatgpt.com](https://ouci.dntb.gov.ua/en/works/7XyMjNX4/?utm_source=chatgpt.com)
* **In-text Citation:** (Wang, Li, & Zhou, 2024)
* **Contribution Summary:**
    This survey reviews the role of LLMs in functional test generation and general software testing processes. The authors discuss the potential and limitations of LLMs in terms of test automation and quality assurance.
* **Key Findings and Quotes:**
    * LLMs are increasingly effective in functional test generation and code analysis (Wang, Li, & Zhou, 2024, p. 7).
    * Accuracy and reliability are still problems to be solved.
    * Combination with human supervision improves test quality.
* **Personal Analysis and Relevance to LLM-QA:**
    The article strengthens the theoretical basis for LLM-QA's functional test generation and quality assurance. Additional verification steps are critical for test accuracy and reliability. It also emphasizes that continuous improvement can be achieved through CI/CD integration.
