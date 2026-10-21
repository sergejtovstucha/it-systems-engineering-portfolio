# IT Systems Engineering | Applied AI & Integrations

**Sergej Tovstucha** — VoIP Systems Engineer | Linux Infrastructure | System Integration | Business Automation

I design, integrate, troubleshoot, and maintain practical IT solutions. My background includes over 20 years of work in IP telephony, alongside Linux servers, networks, web applications, and integrations with external APIs.

This repository is a **technical portfolio**, not a turnkey software package. It documents selected real projects and engineering decisions. Customer code, credentials, and private infrastructure details are not published.

## Featured projects

| Project | What it does | Core technologies | Documentation |
| --- | --- | --- | --- |
| **Multilingual AI IVR + Telegram** | Handles inbound calls, adapts the IVR language, and forwards requests or call-event notifications to the right person or Telegram group | Asterisk, IVR, Google STT/TTS, LLM, Telegram Bot API | [Project details](docs/multilingual-ai-telegram-ivr.md) |
| **Clinic Autodialing** | Calls patients before appointments and classifies responses such as confirm, cancel, or callback | Asterisk, Python, STT, OpenAI API, IVR | [Project details](docs/clinic-autodialing.md) |
| **Multitenant Asterisk PBX** | Database-driven provisioning and tenant-isolated dialplan architecture | Asterisk, MariaDB Realtime/ODBC, PHP, AMI | [Separate repository](https://github.com/sergejtovstucha/asterisk-pbx) |
| **AI Job Search Agent** | Searches and evaluates vacancies against a professional profile, filters unsuitable positions, and identifies skill gaps | ChatGPT, AI-assisted research, workflow automation | [Project details](docs/ai-job-search-agent.md) |
| **Asterisk + WhatsApp** | Integrates Asterisk telephony with WhatsApp messaging via Twilio API | Asterisk, Twilio API, WhatsApp | [Project details](docs/asterisk-whatsapp-twilio.md) |

## Other implemented integrations and engineering experience

- **Asterisk + WhatsApp via Twilio API:** implemented a working integration, subject to the Twilio environment's commercial and approval limitations. This is a historical implementation; current provider behavior has not been revalidated.
- **Asterisk call processing + Whisper:** used Asterisk `AMD()` to distinguish answering machines from human responses and queued audio recordings for asynchronous transcription.
- **AI-assisted vacancy discovery:** configured a working ChatGPT-based process to find and evaluate relevant vacancies on CVbankas.lt using explicit criteria, exclusions, suitability scores, and explanations. This demonstrates AI-assisted workflow automation, not a proprietary search engine.
- **Production migration:** migrated an Asterisk system from VMware to Hyper-V, including application, database, and configuration restoration, with approximately 20 minutes of planned downtime.
- **Infrastructure:** Debian Linux, Apache, MariaDB/MySQL, Cisco/MikroTik, VPN, network troubleshooting, virtualization, and web application administration.

## How I work

I start with the business requirement and the existing system. I build or adapt an integration, test failure paths and edge cases, review evidence from logs and traces, and choose reliable production behavior over unnecessary complexity. The Clinic Autodialing language decision is one example: automatic language handling was simplified after testing and customer discussion.

## Links

- [GitHub profile](https://github.com/sergejtovstucha)
- [Multitenant Asterisk PBX documentation](https://github.com/sergejtovstucha/asterisk-pbx)

*Status note: Some systems were operational historically but are not represented here as currently deployed or compatible with the latest third-party API versions. Project write-ups describe what was implemented, rather than claiming a public runnable demo.*
