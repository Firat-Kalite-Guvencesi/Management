
### Experimental Implementation Log

**Researcher:** Elif Atas
**Date:** 12.11.2025
**Task:** Accessibility Test



## 1. Executive Summary

- **Paragraph 1: The Outcome.** The core objective of this task was to prove that the WCAG 2.1.1 Keyboard accessibility criterion was violated on the OWASP Juice Shop Login page. This objective was achieved; the manual keyboard test (navigating with the Tab key) revealed that the keyboard focus skips the Email and Password form fields, making them inaccessible. The preparation for the final evidence (automated test code) has been completed and uploaded to the public repository on GitHub.
- **Paragraph 2: The Experience.** The entire implementation process was quite demanding, particularly due to the setup difficulties and the lack of knowledge regarding automation tools. Approximately 1.5 hours were lost during the installation phase because of three different Git clone errors, followed by issues with the incorrect ZIP/folder structure. The biggest struggle encountered throughout this process was the lack of knowledge (Domain and Tool Knowledge) faced during the stage of writing the automated test code necessary to generate the proof of the defect.


## 2. Setup & Configuration

**Tool(s) Used:**
Node.js v22.15.0 and Google Chrome

**Estimated Time for Setup:**
1 hour 30 minutes

**Setup & Configuration Log:**
Git cloning attempts failed with three different addresses. For this reason, I had to set up the project by downloading the ZIP file from GitHub. When I unzipped the files after the download, two nested folders with the same name were created inside the main folder (juice-shop-master/juice-shop-master). This situation initially caused the npm install command to be unable to locate the package.json file. After identifying the error (ENOENT), the installation was successfully completed by moving into the correct folder. This detection and resolution process took approximately 1.5 hours.

## 3. Implementation Log: "The Journey"

[This is the most critical section. This is your qualitative log of the *process*. Be detailed. This is the data we need.]

**Target Defect:**
The inability to access the Email and Password form fields on the Login page using only the keyboard (Tab key). This situation is a clear violation of the WCAG 2.1.1 Keyboard success criterion.

**Process Log:**
After the application was successfully run, keyboard navigation (Tab key) testing was applied as the first step. Focus transitions were seamless between the page title, menu, and upper-section buttons. However, the keyboard focus was entirely skipped on the most critical areas, the Email and Password form fields, and it was determined that these fields could not be accessed using the keyboard. The error was identified as a violation of the WCAG 2.1.1 Keyboard standard.
**Biggest "Pain Point" / "Struggle":**
Deciding which tool (such as Axe-core or Cypress) to use to generate error evidence with an automated test and carrying out the integration of these tools into the Node.js project is the most challenging part with my current knowledge. The phase of writing the automated test code is the most expertise-demanding and challenging part of this task.

## 4. Final Artifacts


**Link to Code Repository/Gist:**
https://github.com/elifatass/LLMQA_Accessibility_Proof_ElifAtasss/blob/main/accessibility_test.js



## 5. Reflection & Relevance to LLM-QA


**Analysis of the Manual Process:**
This manual 'defect detection and test creation' process is extremely demanding, especially during the setup and automation tool integration phases. I lost approximately 1.5 hours during the installation phase due to three different Git clone errors, followed by issues with the ZIP/folder structure. Manually identifying the core defect (keyboard access) was easy, but the phase of writing an automated test code to prove the defect became the biggest hurdle that halted the process, as it required specific expertise (using tools like Cypress/Axe). This process requires significant time and niche expertise for a test engineer.

**How LLM-QA Could Have Helped:**
I wish the LLM-QA tool could have helped me specifically with these two points:

Automated Test Code Generation: When I informed the tool of a manually found defect (e.g., 'Keyboard focus is skipped on the Login form'), I wish the tool could have directly generated the automated test code to prove this error, without me needing any prior knowledge of the tools (like Cypress/Axe). This would eliminate my biggest current knowledge gap and struggle.

Setup Error Detection: If I had queried the Command Prompt about the initial git clone and ENOENT errors I encountered, I wish the tool had instantly provided the correct solution (downloading the ZIP, correcting the folder structure). This would have prevented the loss of approximately 1.5 hours.



