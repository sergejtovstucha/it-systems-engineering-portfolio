# AI-Assisted Engineering Approach

## My role

I am an IT systems integration and VoIP engineer, not a full-time software developer. My strength is understanding how systems work together, defining the expected behavior, designing practical integrations, configuring infrastructure, troubleshooting failures, and validating the final result.

I have built and maintained solutions around Asterisk, Kamailio, Linux, MariaDB, SIP/WebRTC, business web applications, and external APIs. Some projects began long before modern generative AI tools were available, including my multitenant Asterisk PBX work started in 2015.

## How I use ChatGPT

I use ChatGPT as a development and research assistant for tasks such as:

- Drafting PHP, Python, JavaScript, SQL, and Asterisk integration examples
- Reviewing call flows and API integration approaches
- Investigating logs, error messages, and alternative explanations
- Producing technical documentation and test checklists
- Comparing implementation choices against software documentation

AI-generated output is a **starting point, not proof that a solution works**. I review it against the target environment, vendor documentation, logs, and actual tests. I adjust or reject code when it does not fit the installed software versions or the system architecture.

## Example: diagnosing a PHP runtime mismatch

While working on a PHP script, the suggested code did not run as expected. The investigation initially focused on the script itself. I identified an important environment detail: the system's default PHP interpreter was **PHP 5.6**, while the proposed code assumed newer PHP behavior.

The issue illustrated a recurring engineering principle: before debugging application logic, verify the runtime and the versions of the dependencies actually being used.

**Useful checks in similar situations:**

```bash
php -v
which php
php -l path/to/script.php
```

These are illustrative diagnostic commands, not a transcript of that historical incident.

## My validation workflow

1. Clarify the business requirement and the expected end-to-end behavior.
2. Review the existing architecture, versions, constraints, and interfaces.
3. Use AI assistance to draft or compare possible solutions.
4. Verify critical details in official vendor documentation.
5. Test incrementally with real logs, protocol traces, and failure scenarios.
6. Correct issues, document the outcome, and distinguish tested behavior from assumptions.

For telephony projects, validation can include Asterisk CLI logs, SIP traces, `sngrep`, `tcpdump`, browser WebRTC diagnostics, database queries, and API responses.

## Production engineering matters more than code generation

A working integration is more than a code file. It includes correct configuration, authentication, network connectivity, permissions, service compatibility, error handling, testing, deployment, and support.

In an earlier patient appointment IVR project, automatic spoken-language selection was tested but confused Latvian and Lithuanian responses in some cases. After reviewing the results with the customer, we simplified the production language flow to Latvian. The priority was predictable service behavior rather than keeping an unreliable AI feature.

## Working independently and with specialists

I can deliver a substantial amount of system integration work independently and collaborate with developers or other specialists when needed. I am transparent about which parts I design, configure, test, and maintain myself, and where I use AI-generated code or specialist assistance.

## Related work

- [Multilingual AI IVR + Telegram](multilingual-ai-telegram-ivr.md)
- [Clinic Autodialing](clinic-autodialing.md)
- [AI Job Search Agent](ai-job-search-agent.md)
- [Asterisk Multitenant PBX](https://github.com/sergejtovstucha/asterisk-pbx)

*This document describes my engineering workflow and selected real experiences. It does not claim that AI-generated code is automatically production-ready.*
