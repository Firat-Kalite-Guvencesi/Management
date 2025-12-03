# From Warnings to Safety Nets: A Defect-to-Test Approach using Large Language Models (LLM-QA)

### ABSTRACT (under development)

**[Context]** Modern Continuous Integration/Continuous Deployment (CI/CD) pipelines rely heavily on Static Code Analysis (SCA) to maintain software quality. While effective at identifying potential defects, SCA tools often suffer from high false-positive rates and produce transient warnings that lack immediate actionability. **[Problem]** Crucially, traditional SCA tools fail to provide a "safety net" against regression; they report issues but do not generate the artifacts required to prevent their recurrence. Furthermore, existing automated testing tools—particularly in accessibility and security—often lack the semantic understanding to verify complex logic flaws or "invisible" configuration omissions. **[Proposed Solution]** This paper introduces **LLM-QA**, a novel "Defect-to-Test" system that leverages Large Language Models (LLMs) to transform abstract code warnings into concrete, executable unit tests. **[Methodology]** Unlike standard test generation tools that prioritize coverage, LLM-QA operates on a two-stage pipeline: (1) semantic analysis to identify specific, high-risk defect patterns (e.g., XSS, accessibility violations, missing headers), and (2) the targeted generation of a "proving test" that reproduces the defect. **[Contribution]** Drawing on recent empirical findings regarding the superior readability of AI-generated code, we demonstrate that this approach not only validates defects with high precision but also automatically enriches the project's test suite with maintainable assets, effectively shifting quality assurance from passive reporting to active, permanent prevention.

---

### 1. INTRODUCTION (under development)

#### 1.1. The Context

The paradigm of modern software development has shifted decisively toward rapid iteration cycles. To maintain velocity without sacrificing quality, development teams increasingly rely on automated Quality Assurance (QA) tools. Static Code Analysis (SCA) has established itself as the first line of defense, allowing teams to scan codebases for vulnerabilities, "code smells," and anti-patterns without executing the program. Research consistently shows that early detection of defects significantly reduces the cost of software maintenance. Consequently, SCA tools have become ubiquitous in both industrial and academic software projects.

#### 1.2. The Problem: The "Transient Warning" Paradox

Despite their widespread adoption, SCA tools fail to prevent a significant number of bugs from reaching production due to two primary limitations. First, the "noise" problem: high false-positive rates lead to "alert fatigue," causing developers—especially novices—to desensitize to warnings (Casola et al., 2024).

Second, and more critically, the warnings provided by SCA are **transient**. A warning indicates a _potential_ problem, but it does not provide _proof_ of failure. Once a developer "fixes" the warning, the signal disappears, leaving behind no permanent artifact to ensure the bug does not re-emerge. This lack of a "safety net" is particularly detrimental in critical domains like security and accessibility, where manual verification is both expensive and prone to human error.

#### 1.3. The Solution (LLM-QA)

The purpose of this study is to bridge the gap between abstract static analysis and concrete dynamic verification. We propose **LLM-QA**, a system based on the "Defect-to-Test" principle. By utilizing the semantic reasoning capabilities of Large Language Models (LLMs), LLM-QA interprets static warnings not as text to be read, but as specifications for test generation. This study aims to demonstrate that converting a defect warning into an executable, failing unit test provides a superior QA mechanism than reporting alone. By automatically generating the test case that _proves_ the error, we provide developers with irrefutable evidence of the defect and a permanent asset for their test suite.

---

### 2. RELATED WORK (under development)

This section synthesizes recent advancements in automated testing, security verification, and the application of Large Language Models (LLMs) in Software Engineering, highlighting the gap that LLM-QA aims to address.

#### 2.1. The Limits of Automated Verification

While automated testing is a mature field, significant gaps remain in "Oracle" determination—knowing what the correct behavior should be without human intervention. In functional testing, Wang, Li, and Zhou (2024) note that while LLMs are increasingly effective at generating test cases, ensuring their reliability in complex scenarios remains an open challenge.

This limitation is even more pronounced in specialized domains like **Accessibility Testing**. Kodithuwakku and Wickramaarachchi (2025) demonstrated that industry-standard tools (e.g., Axe, Lighthouse) frequently miss context-dependent accessibility violations, covering only a fraction of WCAG guidelines. This suggests a need for an intelligent agent capable of understanding the _intent_ of the UI, rather than just parsing DOM elements. Similarly, in **Performance Testing**, defining baselines for distributed architectures is notoriously difficult. Mascia et al. (2025) propose causal-enhanced LLMs to identify "critical workloads" in microservices, validating our hypothesis that LLMs are necessary to define the "performance budget" that traditional scripts lack.

#### 2.2. Challenges in Security and Configuration Verification

Security testing imposes a higher burden of proof than functional testing, as it requires emulating an adversary. Early research by Kaksonen et al. (2001) established that effective security assessment requires "fault injection"—deliberately introducing malformed inputs to test robustness. However, manual fault injection is highly specialized and often neglected in rapid CI/CD cycles.

Recent findings indicate that modern development practices introduce new risks that traditional tools miss. The 2025 Veracode _State of Software Security_ report reveals that LLM-generated code is insecure 45% of the time, often due to the **simple omission** of security constraints rather than complex logic errors. This is corroborated by Fu et al. (2025), who found a high likelihood of Common Weakness Enumeration (CWE) vulnerabilities in AI-generated code.

Crucially, security flaws are not limited to code logic. Perry et al. (2024) note that developers frequently overlook "invisible" security configurations, such as HTTP headers (CSP, HSTS). LLM-QA addresses this by treating these missing configurations not as "best practice" suggestions, but as verifiable defects that demand a failing test case to prove their absence.

#### 2.3. Large Language Models in Software Engineering

The integration of LLMs into software engineering has accelerated rapidly. A critical hesitation in adopting AI-generated tests has been **maintainability**. However, contrasting with early skepticism, recent empirical studies by Fawareh et al. (2024) suggest that AI-generated code often exhibits _higher_ readability and better documentation than average human-written code. This finding is pivotal for LLM-QA, as it supports the viability of adding generated tests to a long-term regression suite without incurring excessive technical debt.

Current state-of-the-art systems, such as LLIFT (Li et al., 2025) and the work of Abtahi and Azim (2025), focus on _augmenting_ static analysis to find bugs or _repairing_ them. However, a gap remains: these systems generally skip the **verification** step. By moving directly from "Detection" to "Repair," they miss the opportunity to create a regression test. LLM-QA fills this gap by explicitly focusing on the "Defect-to-Test" pipeline, ensuring that for every defect identified, a permanent safety net is created.

---

### 3. METHODOLOGY (baseline for future)

#### 3.1. System Overview

The LLM-QA architecture is designed to operate as a middleware between static analysis and dynamic testing. It functions through a two-stage pipeline:

1.  **Semantic Defect Extraction:** The system ingests static warnings and source code context...
2.  **Targeted Test Generation:** Utilizing a specialized prompt strategy to generate "proving" tests...
