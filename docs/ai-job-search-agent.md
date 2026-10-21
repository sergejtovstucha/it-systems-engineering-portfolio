# AI-Assisted Job Search & Vacancy Matching

**Project type:** Working AI-assisted research and filtering workflow  
**Platform:** ChatGPT, CVbankas.lt  
**Focus:** Requirements engineering, AI workflow configuration, relevance assessment and recurring research

## Business problem

A conventional keyword-based job search can return many vacancies that do not fit an applicant's actual experience. Similar job titles may require very different technologies, language skills or levels of specialization. Reviewing each advertisement manually is time-consuming.

## Implemented workflow

I configured and use a ChatGPT-based job-search workflow focused on vacancies published on CVbankas.lt. The workflow is driven by my professional background, explicit job categories, inclusion/exclusion rules and a required relevance threshold.

The workflow:

1. Searches for relevant vacancies in specified technical fields.
2. Compares job responsibilities and mandatory requirements with documented, real-world skills.
3. Excludes positions that require experience or communication skills outside the selected criteria.
4. Retains only matches meeting a defined suitability threshold (70% in my current setup).
5. Produces a short assessment with reasons for the match, important gaps and a link to the original vacancy.
6. Uses publication date and previous results to prioritize new opportunities and avoid repeated recommendations where possible.

## Example selection criteria

**Target roles:**
- VoIP Systems Engineer / Unified Communications Engineer
- IT Systems / Systems Integration Engineer
- Network / Telecommunications Infrastructure Engineer

**Relevant technologies:** Asterisk, Kamailio, RTPengine, SIP/WebRTC, Debian Linux, Apache, MariaDB, Cisco, MikroTik and IT/network infrastructure.

**Exclusion examples:** positions requiring deep production BGP/OSPF experience or fluent spoken English where these are mandatory.

## Example workflow

```text
Defined skills, experience and constraints
                  |
                  v
       CVbankas.lt vacancy search
                  |
                  v
      Requirements extraction
                  |
                  v
       Skill/constraint matching
                  |
           +------+------+
           |             |
       Not a fit      Potential fit
           |             |
        Exclude       Explain match
                         |
                         v
                 Include source URL
                         |
                         v
                 Structured shortlist
```

## My engineering contribution

This is **not** a claim that I trained an AI model, wrote a custom web crawler or developed ChatGPT itself.

My contribution is defining the operational task, translating my professional profile into actionable selection rules, tuning and validating the results, identifying incorrect recommendations and refining the workflow based on actual use.

I use ChatGPT as a major coding and research assistant in my projects. I remain responsible for architecture, requirements, technical decisions, testing, validation and resolving integration problems. When generated code is incorrect, I troubleshoot it against software logs and official vendor documentation.

## Current status and limitations

**Status:** Working and used for personal job discovery.

- Match percentages are heuristic AI assessments, not formally calibrated recruitment scores.
- Availability, publication dates and requirements must be checked against the original vacancy.
- Results depend on the information accessible during each search and can miss relevant postings.
- This workflow illustrates configurable AI-assisted research; adapting it to other industries requires new sources, constraints and validation.

## Broader applications

The same **workflow design pattern** can be adapted to supplier discovery, procurement searches, technical product comparison, monitoring publicly available announcements and other recurring information-filtering tasks, subject to source access and accuracy requirements.

## Source code and access

This project is a configured ChatGPT workflow rather than a standalone software application. Private account settings, personal information and conversation history are not published in this repository.
