### Experimental Implementation Log

Researcher: Kübra SOYSAL
Date: November 27, 2025
Task: Performance Test
***

## 1. Executive Summary

Paragraph 1: The Outcome.
The primary goal of this task was to **prove the existence of a performance defect** on the "Large & Deep DOM" page by creating an automated test. The objective was achieved, though only through trial-and-error. The initial performance budget set ($p95 < 1500ms$) succeeded unexpectedly. To obtain proof of failure, the test threshold was tightened to $p95 < 500ms$. Under a load of 5 Virtual Users (VUs), the test definitively **FAILED** with an actual $p95 = 664.52ms$, thereby confirming the defect.

Paragraph 2: The Experience.
The implementation process proved to be quite **complex and time-consuming** due to **non-coding issues**, including installation errors, terminal incompatibility, and manual file path management. The single biggest "pain point" encountered was **terminal and file path incompatibility**. The MINGW64 (Git Bash) terminal repeatedly failed to correctly process Windows directory paths, making it necessary to switch to **PowerShell** to successfully execute the core test script.

***

## 2. Setup & Configuration

Tool(s) Used: **k6 v1.4.1**, **Windows PowerShell**, **Visual Studio Code**

Estimated Time for Setup: **~1.5 hours** (Mostly spent fixing installation and path errors, not core coding)

Setup & Configuration Log:
The initial attempt to install k6 using the recommended **Chocolatey** package manager failed with the error `choco: command not found`. This necessitated switching to the manual **MSI installer**. Following installation, approximately one hour was spent struggling with **terminal incompatibility**, as MINGW64/Git Bash could not correctly read Windows file paths (e.g., `C:\...`). Even a simple typo in the script file name (`perfonmance_test.js`) caused the tool to fail to locate the file. These issues were eventually resolved by switching to **PowerShell**.

***

## 3. Implementation Log: "The Journey"

Target Defect: **The 95th Percentile Response Time of the Large & Deep DOM page exceeds the $500ms$ performance budget under a load of 5 Virtual Users.**

Process Log:
1.  **Script Preparation:** A basic k6 script was written targeting the `/large` endpoint with 5 VUs for 30 seconds.
2.  **Path Errors:** Execution attempts using the MINGW64/Git Bash terminal continuously resulted in **"File not found"** errors due to incorrect path resolution and a typo in the file name. This highlighted the need to understand the terminal's path parsing rules.
3.  **Terminal and Path Correction:** Switched to PowerShell and navigated to the correct folder (`cd C:\Users\msi\Desktop\k6Test`).
4.  **Initial Test Success:** The first test run, using the initial budget of $p95 < 1500ms$, **succeeded** (with $p95 = 809.44ms$). This demonstrated that the initial budget was flawed.
5.  **Budget Tightening:** To achieve proof of failure, the performance budget was manually adjusted to $p95 < 500ms$.
6.  **Final Failure:** The re-executed test **FAILED** with an actual result of $p95 = 664.52ms$, successfully meeting the task's objective.

Biggest "Pain Point" / "Struggle":
**(Tool/Environment Incompatibility):** The most significant time loss was due to the **sensitivity of terminal and file path management outside of the code itself.** The failure of basic Windows directory navigation in a Bash-based tool like MINGW64, and the lack of tolerance for simple typos, were the main factors prolonging the process.

***

## 4. Final Artifacts

Link to Code Repository/Gist: [k6 Performance Defect Test Code](https://github.com/kubrasoysal/k6-Performance-Proof-of-Failure)

***

## 5. Reflection & Relevance to LLM-QA

Analysis of the Manual Process:
The manual "defect-to-test" process is **fragile** and requires a test specialist to possess deep IT/system administration knowledge regarding setup, terminal compatibility, and debugging, in addition to core tool knowledge. It is intolerant of simple human errors and is therefore inefficient.

How LLM-QA Could Have Helped:
LLM-QA could have played a critical role by reducing the need for specialized knowledge and time loss:
1.  **Configuration Suggestion:** It could have immediately suggested the most suitable terminal/installation method for the user's system (e.g., MSI installer and PowerShell) following the Chocolatey failure.
2.  **Debugging:** It could have instantly diagnosed file path errors or typos in the run command, preventing hours of user frustration.
3.  **Test Design:** For a known vulnerable page, it could have generated a performance budget **tight enough** (e.g., $p95 < 500ms$) to prove the defect directly, eliminating the need for manual trial-and-error.