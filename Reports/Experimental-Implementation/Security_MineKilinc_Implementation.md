

### Experimental Implementation Log

**Researcher:** Mine Kılınç
**Date:** 26.11.2025
**Task:** Security Test

---

## 1. Executive Summary


- **The Outcome.** The primary objective of this experiment was to create an automated security test that proves the existence of a reflected Cross-Site Scripting (XSS) vulnerability in the OWASP Juice Shop's search functionality. The final test successfully demonstrated the vulnerability using a Cypress-based “Variable Injection” technique: the payload injected through the ?q= parameter executed inside the DOM and created a new variable (window.hacked = true) in the parent window. The automated test then verified this state change, conclusively proving the defect.

- **The Experience.** The overall implementation process was challenging and at times frustrating due to tool limitations. The single biggest pain point was that Cypress failed to capture the alert() event triggered by the injected XSS payload, caused by timing issues and iframe context isolation—forcing me to redesign the entire exploit strategy.


---

## 2. Setup & Configuration

**Tool(s) Used:**
    Cypress v13.x
    Node.js v20.x
    OWASP Juice Shop (Local Instance)

**Estimated Time for Setup:**
    5 hours

**Setup & Configuration Log:**
    Setting up Cypress was easy; the difficulty started once I attempted to run automated tests against the Juice Shop UI. The application displays multiple onboarding overlays, banners, and cookie prompts, which prevented Cypress from interacting with elements like the search bar. Additionally, catching UI-generated alert() events turned out to be unreliable because Cypress attaches event listeners later than the page executes the injected script. After spending significant time debugging these behavioral inconsistencies, I switched to a more stable approach: bypassing UI interaction entirely and injecting the XSS payload directly through the URL.

---

## 3. Implementation Log: "The Journey"

**Target Defect:**
    Reflected Cross-Site Scripting (XSS) vulnerability in the search query parameter (/search?q=), allowing untrusted input to be directly interpreted by the browser without sanitization.
    
**Process Log:**
    1.Initial Test – Alert Capture Attempt
        I first attempted to trigger a simple payload such as <img src=x onerror=alert(1)>. Although I could visually see the alert pop up in the browser, Cypress consistently failed to capture it. I later discovered this was because the alert fired before Cypress attached its window:alert listener.

    2.Payload Sanitization Issues
        The Angular frontend of Juice Shop sanitizes onerror attributes aggressively, meaning several classic payloads were stripped before execution. This made some approaches completely ineffective.

    3.UI Interaction Failures
        I attempted to automate searching by typing the payload into the UI search bar. However, multiple components (welcome banner, cookie layers, scrolling animations) caused Cypress to fail with errors like “element is not visible” or “element is disabled.”

    4.Understanding the Race Condition
        Even when using URL-based payloads, the injected JavaScript executed inside an iframe before Cypress had the chance to intercept it. This race condition made classical alert-based verification unreliable.

    5.Breakthrough – Variable Injection Strategy
        I replaced alerting with a different payload:

        <iframe src="javascript:window.parent.hacked=true"></iframe>


        This technique sets a stable and persistent flag on the parent window.
        Cypress can reliably assert:

        cy.window().should('have.property', 'hacked', true);

        This provided a consistent and trustworthy method to prove the XSS vulnerability.

**Biggest "Pain Point" / "Struggle":**

    The most frustrating challenge was that Cypress cannot reliably detect alert() events from XSS payloads executed inside iframes. The event fired before Cypress registered its listeners, resulting in false negatives even when the exploit worked. Understanding and working around this timing issue required significant debugging and rethinking of the test strategy.

---

## 4. Final Artifacts

**Link to Code Repository/Gist:**
    https://github.com/mineekilincc/LLM-QA-SecurityTestingOWASP/tree/main
---

## 5. Reflection & Relevance to LLM-QA

**Analysis of the Manual Process:**
    My experience showed that the manual “defect-to-test” process is both powerful and extremely demanding. Even though the vulnerability itself (a reflected XSS in the q parameter) was relatively simple, proving it with an automated test required deep knowledge of several different areas: browser behavior, Angular’s sanitization logic, iframe execution contexts, and Cypress’s internal event-handling limitations.
    The biggest realization was that manual security test creation is not just “writing a test” — it requires switching between security expertise, debugging skills, and test automation knowledge. This makes the workflow expensive, slow, and very difficult to reproduce across open-source projects.
**How LLM-QA Could Have Helped:**
    LLM-QA is designed to automatically analyze GitHub repositories using LLM reasoning and produce high-quality findings and tests. In this task, LLM-QA could have reduced my effort dramatically. It could have identified the vulnerable code path directly from the repository, classified the issue as a reflected XSS, and suggested the correct payload technique—bypassing Angular’s sanitization and avoiding Cypress’s race condition with alert().
    Instead of trial-and-error debugging for several hours, I could have simply stated: “There is an XSS risk in the search feature; generate a defect-proving test.” LLM-QA would have produced the correct, stable version of the test—including the variable-injection approach that finally worked—saving significant time, frustration, and context-switching.

---
