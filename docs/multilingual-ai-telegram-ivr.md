# Multilingual AI IVR + Telegram Service Workflow

**Project status:** Implemented and operational historically; current compatibility with external APIs has not been revalidated.

**Technologies:** Asterisk, IVR, Google Speech-to-Text (STT), Google Text-to-Speech (TTS), LLM/OpenAI API integration, Telegram Bot API, backend scripting.

## Business requirement

A business receives calls from customers who prefer different languages. Not every team member can answer every call, and service requests or missed calls must be delivered quickly to a responsible employee or group.

## Implemented solution

I connected an Asterisk IVR with speech recognition, language interpretation, speech output, and Telegram notifications.

1. A customer calls the PBX and hears the IVR.
2. The caller can indicate a preferred language by speaking; a DTMF-based choice is also possible as a design alternative.
3. Speech is processed through STT, and an LLM interprets the language choice.
4. **The IVR continues in the caller's selected language**, using the corresponding speech output.
5. The service request is forwarded through a Telegram bot to a responsible employee or group.
6. If a specialist for the caller's language is available, the notification is directed to that specialist in that language. Otherwise the message can be translated into English before delivery.

The integration also generated Telegram notifications about call events, including `BUSY` and `NOANSWER`. A separate service scenario could acknowledge a request to the caller and notify an assigned employee for follow-up.

**Languages implemented:** Russian, English, Lithuanian, and Latvian.

## Simplified call flow

```text
Incoming call
     |
     v
 Asterisk IVR -- call events (BUSY / NOANSWER) ---> Telegram notification
     |
     v
Ask for preferred language
     |
     v
Google STT -> LLM interprets language selection
     |
     v
Continue IVR in selected language (TTS/prompts)
     |
     v
Collect / acknowledge customer request
     |
     v
Find appropriate agent or Telegram group
     |
     +--> Language-matched agent --> Telegram in caller's language
     |
     +--> No language match --> Translate to English --> Telegram
```

## Engineering value

- End-to-end integration between PBX, speech services, LLM processing, and messaging APIs.
- Practical multilingual interaction, not just translated static IVR menus.
- Routing requests to an appropriate person rather than only producing a generic call notification.
- A simple channel (Telegram) for distributing service requests and missed-call information.

## Production considerations

Speech recognition and automatic language selection require real-world testing. For ambiguous responses or closely related languages, explicit DTMF selection or confirmation prompts may be more dependable. API pricing, policy, and compatibility can change; historic functionality does not imply a currently supported deployment.

## Confidentiality

This page documents the behavior and architecture. Original customer-specific code, bot tokens, phone numbers, and infrastructure details are not published.
