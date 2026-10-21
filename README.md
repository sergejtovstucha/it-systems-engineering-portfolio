# IT Systems Engineering | Applied AI & Integrations

**Sergej Tovstucha** — VoIP Systems Engineer | IT Systems Integration | Linux Infrastructure | Business Automation

I design, integrate, troubleshoot, and maintain practical IT solutions. My experience includes more than 20 years in IP telephony, alongside Linux servers, networking, virtualization, web applications, and integrations with external APIs.

This repository is a **portfolio of selected real projects and technical investigations**, not a turnkey product. Customer source code, credentials, and confidential infrastructure details are not published. Some examples are adapted for documentation and have not been revalidated against current software versions.

## Selected engineering projects

| Project | Business or technical result | Technologies | Details |
| --- | --- | --- | --- |
| **Multilingual AI IVR + Telegram** | Handles incoming requests and call events; adapts IVR language and routes Telegram messages to an appropriate employee or group | Asterisk, Google STT/TTS, LLM, Telegram Bot API | [Case study](docs/multilingual-ai-telegram-ivr.md) |
| **Clinic Autodialing** | Automated patient appointment confirmation, cancellation, and callback handling; ambiguous speech responses prompted clarification. After testing, the customer chose a Latvian-only IVR workflow | Asterisk, Python, STT, OpenAI API, IVR | [Case study](docs/clinic-autodialing.md) |
| **Multitenant Asterisk PBX** | Shared call-processing architecture, tenant-specific contexts, MariaDB Realtime, and web-based provisioning; historical solution documented with illustrative examples | Asterisk, MariaDB/ODBC, PHP, AMI | [Separate repository](https://github.com/sergejtovstucha/asterisk-pbx) |
| **AI Job Search Agent** | Working ChatGPT-based vacancy discovery and suitability evaluation against defined criteria and exclusions; not a proprietary crawler or AI model | ChatGPT, AI-assisted research, workflow configuration | [Case study](docs/ai-job-search-agent.md) |
| **Asterisk + WhatsApp via Twilio** | Implemented an Asterisk-to-WhatsApp API integration in a Twilio trial environment; subject to provider restrictions and approvals | Asterisk, Twilio API, WhatsApp | [Case study](docs/asterisk-whatsapp-twilio.md) |
| **VMware → Hyper-V Migration** | Migrated a production Asterisk system, database, and web application after staged testing; approximately 20 minutes of planned downtime | VMware, Hyper-V, Linux, Asterisk, MariaDB/MySQL, Apache | [Case study](docs/vmware-to-hyperv-migration.md) |

## Troubleshooting & Technical Investigations

These investigations demonstrate how I work with unfamiliar systems: reproduce a problem, establish a baseline, collect logs and traces, consult official technical documentation, use ChatGPT as an engineering assistant, and verify hypotheses with practical tests.

- **[Mobile Contact Center — SIP, Android & ARI Troubleshooting](docs/mobile-contact-center-troubleshooting.md)** — independent SIP/Dialplan tests on my own Asterisk PBX followed by customer-side ARI integration tests; investigation of Android background behavior, registration, push notifications, audio, and presence. I studied Android development fundamentals to understand and investigate the client application.
- **[Browser-to-Browser WebRTC — Cross-Network Diagnostics](docs/webrtc-b2b-cross-network-diagnostics.md)** — successful LAN calls compared with failed cross-network calls; analysis of ICE, STUN, TURN, DTLS-SRTP, browser logs, SDP, and WebSocket signaling, supported by official documentation.

**Investigation status:** Diagnostic observations and recommendations are distinguished from verified fixes. These case studies do not claim that every issue was resolved in production.

## AI-Assisted Engineering Approach

I use ChatGPT for code generation, technical research, log analysis, and documentation. I take responsibility for defining system behavior, understanding integration points, checking solutions against official vendor documentation, and testing results in real environments.

My main specialization is **systems integration and VoIP engineering**, rather than full-time software development.

[Read about my engineering approach](docs/ai-assisted-engineering.md)

## Additional engineering experience

- **Asterisk AMD + Whisper:** answering machine detection, recording human responses, and queuing audio for asynchronous transcription.
- **Infrastructure:** Debian Linux, Apache, MariaDB/MySQL, Cisco/MikroTik, VPN, firewall and network troubleshooting, virtualization, and web application administration.
- **Microsoft 365:** administration exposure and ongoing practical learning, including Teams; not presented as a primary specialization.

## Working method

I start with requirements and the existing architecture. I isolate the relevant subsystem, reproduce the issue, compare expected and observed behavior, examine logs and traces, and test changes before recommending a production rollout. I document important limitations and work with the customer to make practical reliability decisions.

## Links

- [GitHub profile](https://github.com/sergejtovstucha)
- [Asterisk Multitenant PBX](https://github.com/sergejtovstucha/asterisk-pbx)
- [Upwork profile](https://www.upwork.com/freelancers/~0159777018e9000e93)
