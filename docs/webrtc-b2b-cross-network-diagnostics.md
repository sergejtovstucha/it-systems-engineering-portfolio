# Browser-to-Browser WebRTC — Cross-Network Connectivity Investigation

**Project type:** Technical diagnostics  
**Technologies:** WebRTC, `RTCPeerConnection`, ICE, STUN, TURN, DTLS-SRTP, WebSocket signaling, Chrome DevTools, `chrome://webrtc-internals`  
**Status:** Reproducible failure and evidence collected; definitive root cause and production resolution were not confirmed.

## Context

I investigated a browser-to-browser voice calling application. Calls worked between two users on the same LAN, but a cross-network call could appear as active in the UI without working audio.

The goal was to distinguish signaling errors from ICE connectivity, TURN relay, and secure media establishment problems rather than guessing from the on-screen call status.

## Reproducible tests

| Test | Observation |
| --- | --- |
| Two devices on the same Wi-Fi/LAN | Two-way audio worked. |
| One device on Wi-Fi, another on mobile 4G/5G | Call UI indicated an active call, but neither party heard audio. |
| WebRTC ICE state during failing calls | Progressed from `new`/`checking` to `disconnected`/`failed`. |
| Peer connection state | Progressed from `new`/`connecting` to `failed`. |
| Signaling state | Reached `stable` after offer/answer negotiation. |

These observations showed that signaling progress and a successful user-interface transition were **not proof of a working media path**.

## Evidence collected and examined

- Browser console output from call attempts.
- `chrome://webrtc-internals` PeerConnection updates and statistics.
- SDP offer/answer exchange and WebSocket signaling messages.
- ICE server configuration, including STUN/TURN transport and port options.
- Comparisons between successful same-LAN calls and unsuccessful cross-network calls.

The observed ICE failure strongly implicated the connectivity/transport stage. It did **not**, on its own, prove a specific TURN configuration error or a DTLS defect.

## How I approached the problem

1. Defined repeatable scenarios using two genuinely different network connections.
2. Compared the browser signaling state with actual ICE and connection state.
3. Inspected SDP, candidates, and ICE server configuration instead of relying only on application logs.
4. Studied the roles of **ICE**, **STUN**, **TURN**, and **DTLS-SRTP** in browser-to-browser call establishment.
5. Used ChatGPT to organize evidence, review possible causes and code paths, and formulate focused follow-up tests.
6. Validated concepts and configuration assumptions through relevant official WebRTC/browser documentation and implementation documentation, rather than treating AI suggestions as authoritative.

## Important technical distinction

In WebRTC, signaling coordinates offer/answer and candidate exchange; ICE checks whether a viable peer-to-peer or relayed path exists; STUN assists candidate discovery; TURN can provide a relay when direct paths are unavailable; and DTLS-SRTP secures the media session.

A browser can report signaling state `stable` while ICE connectivity fails. A suspected DTLS problem must be distinguished from the inability to establish a viable ICE candidate pair.

## Engineering value

This project demonstrated practical, evidence-led debugging of a system outside my traditional SIP/Asterisk stack, including browser network diagnostics, real cross-network test design, protocol analysis, and targeted research using official technical documentation with ChatGPT as an assistant.

## Confidentiality and limitations

No customer name, private URL, user identity, access credentials, or confidential logs are published. The investigation reproduced a failure and narrowed the diagnostic area; it is **not presented as a completed production repair**.
