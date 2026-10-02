# Suspicious Phishing Email Triage

**Applies to:** Any user report of a suspicious email. Act quickly but
calmly — speed matters, panic doesn't.

## Symptoms (what the user reports)
- Unexpected email asking to click a link, open an attachment, or send
  money / gift cards / credentials.
- Sender address looks "almost right" (e.g. `support@micorsoft.com`).
- Urgent tone: "act now", "account suspended", "you've been selected".

## Quick checks (do NOT click links or open attachments)
1. **Reassure the user**: praise them for reporting instead of clicking.
   Ask: "Did you click anything or enter credentials?" — this decides urgency.
2. Expand the sender details: hover (don't click) to see the real
   `From` address and any `Reply-To` mismatch.
3. Check for the classics: misspellings, generic greeting ("Dear Customer"),
   urgency, unexpected attachment types (`.html`, `.iso`, `.scr`, `.zip`).
4. If they clicked: note **what** (link? attachment? credentials entered?)
   and **when**.

## Step-by-step fix
1. Tell the user: **do not forward it to colleagues** — forward as an
   attachment to the security/IT mailbox (or use the "Report phishing"
   button if deployed).
2. If **credentials were entered**: treat as a compromised account —
   reset the password immediately (see `account-unlock-password-reset.md`),
   revoke active sessions, enable/check MFA.
3. If an **attachment was opened**: isolate the machine from the network
   (unplug / disable Wi-Fi), do **not** power it off (memory forensics),
   and escalate to security.
4. If only **previewed, no click**: delete the message, confirm no rules
   were created in the mailbox (Attackers add inbox rules to hide replies:
   check Outlook Rules), close the ticket as contained.
5. Search the mail system for the same sender/subject to find other
   recipients; warn them proactively.
6. Log everything: sender address, subject, timestamp, who received it,
   whether anyone clicked, actions taken.

## Escalation criteria
- Anyone entered credentials or ran an attachment → **security incident**,
  escalate immediately with the log from step 6.
- Multiple recipients across the company → potential campaign; escalate
  even if nobody clicked.
- Suspected business-email compromise (a real internal account sending the
  phish) → escalate urgently; that mailbox must be contained.
