### Experimental Implementation Log

Researcher: Elif Eslem Özkan Date: 09 November 2025 Task: Security Headers / Configuration Testing

---

## 1. Executive Summary

**Paragraph 1: The Outcome.** My specific goal was to prove the defect of a **Missing Critical Security Header (Content-Security-Policy/CSP)**, as identified in the literature review, against known vulnerable targets. I successfully achieved this goal by utilizing a Python script that asserts the absence of the `Content-Security-Policy` header on the OWASP Juice Shop (Port 3000) root endpoint. This defect-proving test confirms that the application's default configuration lacks a fundamental defense layer, leaving it vulnerable to common Cross-Site Scripting (XSS) attacks.

**Paragraph 2: The Experience.** The implementation process was efficient due to the robust Docker setup but was unexpectedly time-consuming when translating the security requirement into executable Python code. The single biggest "pain point" I encountered was the **Domain Knowledge vs. Implementation Gap**: I had to decide between proving the *missing* CSP header (a high-priority defect per the literature) and proving the more complex *Hard-Coded Secrets* (CWE-798) defect found directly in the `docker-compose.yml` file (`MYSQL_PASSWORD=p@ssw0rd`). This decision process required substantial non-coding time.

---

## 2. Setup & Configuration

Tool(s) Used: **Docker Compose v2.0+, Python v3.11, Python `requests` library**
Estimated Time for Setup: **45 minutes (Environment) + 30 minutes (Test Script)**
Setup & Configuration Log: The environment setup using Docker Compose (as detailed in the `docker-compose.yml` file) was highly efficient, enabling the simultaneous deployment of five vulnerable applications. The initial 45 minutes were dedicated to verifying all containers (DVWA, bWAPP, Juice Shop, etc.) were running and accessible on their designated ports (`8081`, `3000`, etc.). The friction started during the script writing phase, as I spent 30 minutes ensuring the Python `requests` library correctly handled the non-standard ports and that the assertion logic correctly parsed the HTTP response headers for the specific absence of the CSP header.

---

## 3. Implementation Log: "The Journey"

**Target Defect:** Missing **Content-Security-Policy (CSP)** Header (TC002) on the OWASP Juice Shop root endpoint (Port 3000).

**Process Log:**
1.  **Setup & Verification (20 min):** Confirmed all containers were up and running using `docker compose ps` and confirmed connectivity to the Juice Shop via port 3000.
2.  **Initial Script (15 min):** Wrote a basic Python function using `requests.get()` to hit the target URL and print the headers. Confirmed the `Server` and `X-Powered-By` headers were present.
3.  **Stuck Point: Assertion (40 min):** The main struggle was formalizing the test failure. Using Python's `unittest` or simple `if` statements, I initially struggled to create a clean, reportable failure when checking if the key `'Content-Security-Policy'` was **not present** in the dictionary of response headers. This took significant time to ensure the test was robust and wouldn't break if another header was added.
4.  **Finalizing the Proof (20 min):** Finalized the test code to explicitly throw an assertion error if the `Content-Security-Policy` header was found to be missing, thereby proving the defect. This also led to the realization that the application was simultaneously vulnerable to **Hard-Coded Secrets** (CWE-798) in the Docker file (`MYSQL_PASSWORD=bug`), confirming the literature findings (Perry et al., 2024).

**Biggest "Pain Point" / "Struggle":** **(Security Tool Choice & Focus):** The most frustrating part was the internal debate over which defect to prove. Proving the **Missing CSP Header** was technical and clean, but the **Hard-Coded Secrets** in the Docker file (`MYSQL_PASSWORD=bug`) was a much higher-impact *Configuration Security* flaw. I chose the header test for simplicity but recognized the LLM-QA system should be designed to catch both.

---

## 4. Final Artifacts

Link to Code Repository/Gist: **[Security Headers Defect Proof Test (Python/Requests)](https://github.com/eslemozkan/yazilim-kalite-config)**

---

## 5. Reflection & Relevance to LLM-QA

**Analysis of the Manual Process:** The manual defect-to-test process, while valuable for generating "golden data," suffers from severe **context-fragmentation**. The process requires the security analyst to manually aggregate information from three places: the configuration file (Docker), the test plan (Target Defect), and the testing tool's documentation (Python/Requests assertion logic). This switch between domain knowledge, tool syntax, and configuration files makes the process prohibitively slow and error-prone.

**How LLM-QA Could Have Helped:** Our tool could have been revolutionary here. I could have prompted the LLM-QA system with: "Analyze the `docker-compose.yml` and the `Test Plan.md`. Generate a Python test that verifies all endpoints in the config are missing the CSP header." The LLM could have instantly: 1) Read the target ports (`8081`, `3000`, etc.), 2) Understood the security requirement (CSP missing), and 3) **Generated the correct, robust Python/Requests assertion code**, saving me the hour spent debugging the correct header-checking logic.