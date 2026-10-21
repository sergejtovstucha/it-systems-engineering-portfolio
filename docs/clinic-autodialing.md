# Clinic Autodialing — Appointment Confirmation IVR

**Project status:** Implemented and tested; the solution was moved to a customer cloud environment. Details of its current operation are not asserted here.

**Technologies:** Asterisk Dialplan, Python, automated outbound calling, DTMF, speech-to-text, OpenAI API / LLM-based intent classification, voice prompts.

## Business requirement

A clinic needs to contact patients before their appointments and find out whether they will attend, cancel, or need a return call. The aim is to reduce repetitive staff work and collect responses in a structured form.

## Implemented workflow

1. The system creates outbound calls before the scheduled appointment.
2. Asterisk plays an IVR prompt and asks whether the patient plans to attend.
3. The system accepts keypad input and, in later iterations, spoken answers.
4. Speech recognition converts the answer to text; an LLM classifies the intent.
5. Depending on the result, the call flow handles **CONFIRM**, **CANCEL**, **CALLBACK**, **REPEAT**, or **UNSURE**.
6. Unclear responses trigger a clarification or repeat path rather than forcing a confident classification.

## Simplified call flow

```text
Scheduled patient appointment
            |
            v
Asterisk outbound call
            |
            v
Appointment confirmation prompt
            |
            v
DTMF or recorded voice answer
            |
            v
STT (for speech) -> LLM intent classification
            |
     +------+------+--------+-------+
     |      |      |        |       |
 CONFIRM CANCEL CALLBACK REPEAT  UNSURE
     |      |      |        |       |
     v      v      v        +-------+
Handle result            Clarify / ask again
```

## Important engineering decision: language handling

The project included experiments with recognizing the patient's language and adapting the robot's speech. During testing, confusion between Latvian and Lithuanian reduced the reliability of automatic language selection. After discussion with the customer, we decided to use **Latvian as the sole IVR dialogue language** in the relevant production configuration.

This decision illustrates a practical rule: a more advanced AI feature is not necessarily a better production feature when its error rate affects customer experience.

## Lessons learned

- Separate the speech-to-text stage from intent classification to make failures easier to diagnose.
- Model uncertain responses explicitly (`UNSURE`) and provide a retry path.
- Test real accents, short replies, background noise, and similar language variants.
- Agree on acceptable behavior with the customer before production deployment.

## Confidentiality

No patient information, private API credentials, customer database structure, or production recordings are included.
