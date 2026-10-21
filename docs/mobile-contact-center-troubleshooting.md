# Mobile Contact Center — SIP, Android and ARI Troubleshooting

**Project type:** Technical investigation and integration testing  
**Technologies:** Asterisk, SIP/PJSIP, Asterisk Dialplan, ARI, Kamailio, RTPengine, React Native, PJSUA2, Android, Node.js, Pusher, Firebase/APNs  
**Status:** Investigation and recommendations documented; do not interpret this case study as confirmation that every issue was fixed in production.

## Context

I investigated a mobile contact center solution in which smartphone applications communicated with a SIP/VoIP platform and an application backend. The environment combined mobile clients, SIP registration and media processing, Asterisk call control, and push/presence components.

## Problems investigated

- Android SIP registrations becoming unreliable when the application was backgrounded, including suspected Doze/background-execution effects.
- Incorrect operator presence after Pusher disconnect events; the backend contained logic that marked users offline when a connection dropped.
- Audio initialization failures reported as `PJMEDIA_EAUD_INIT`.
- Incoming call notifications disappearing before users could answer.
- SIP/NAT and registration parameters that could contribute to unstable connectivity.

These were separate hypotheses and symptoms; no single root cause was assumed for all of them.

## My hands-on investigation

### 1. Independent SIP testing on my own PBX

I used my own Asterisk PBX as an independent test environment. I configured test SIP accounts and dialplan call scenarios to observe registration and call behavior outside the customer's full application stack.

This separated basic SIP/dialplan behavior from application/backend effects and made comparisons possible.

### 2. Customer-platform tests using ARI

I then tested with the customer's Asterisk environment, where application-controlled call handling used **Asterisk REST Interface (ARI)** and a backend integration. This helped distinguish behavior on a direct Asterisk dialplan route from behavior involving ARI and the application service.

### 3. Learning Android fundamentals for troubleshooting

To investigate the Android-specific symptoms, I studied practical Android application fundamentals: application lifecycle, background execution/Doze, notification handling, and how they affect embedded SIP clients and incoming call behavior. This was targeted technical learning, not a claim of having been the project's full-time Android developer.

### 4. AI-assisted investigation, verified against documentation

I used ChatGPT to help analyze logs and code, organize hypotheses, and explore possible changes. I checked important technical details against official Asterisk, PJSIP/PJSUA2, Android, and relevant integration documentation, and treated actual test results as the deciding evidence.

## Recommendations developed

Areas examined included registration refresh/keepalive behavior, SIP NAT settings (`rewrite_contact`, `rtp_symmetric`, `force_rport`, `direct_media`), separating reliable agent presence from transient Pusher connection state, and investigating Android push/audio initialization paths.

These settings were evaluated as troubleshooting options, **not universal recommended values**: production choices depend on topology, transport, platform versions, and testing.

## Engineering value

The project required working across multiple layers rather than treating a SIP call failure as an isolated PBX problem:

**Mobile operating system → SIP client → SIP proxy/media path → Asterisk dialplan or ARI → application backend → push and presence services.**

My contribution was reproducible testing, cross-layer analysis, technical recommendations, and independent verification of assumptions.

## Confidentiality and limitations

Customer-specific credentials, private repository code, infrastructure addresses, and identifying logs are not published. This document describes investigation and testing experience, not a completed independent rebuild or a verified end-to-end production fix.
