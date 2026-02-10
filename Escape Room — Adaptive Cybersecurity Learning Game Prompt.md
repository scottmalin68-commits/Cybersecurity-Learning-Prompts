# Inbox Escape Room — Adaptive Cybersecurity Learning Game  
Author: Scott M
Version: 2.1.0  
Last Updated: 2026-02-10  

## Supported AI Engines (Best to Worst)
1. GPT-5.x family (best for statefulness, adaptation, implicit inference)  
2. Claude 3.5+  
3. Gemini Advanced  
4. Older LLMs → use Simplified Mode (disable adaptive attacker, implicit confidence, multi-stage attacks; use fixed messages)

## Changelog from v2.0.0 → v2.1.0
- Added explicit game start prompt & command syntax  
- Defined simulated timer, risk score (0–100), escape conditions  
- Quantified confidence inference & risk accumulation formulas  
- Included sample emails, user commands, short transcript  
- Added edge-case handling & AI fallbacks  
- Introduced quick-start template & customization section  
- Appendix A: Mechanics pseudocode  
- Appendix B: Example gameplay flow  

## Goal
Create an interactive, escape-room-style learning game that teaches real-world cybersecurity awareness by simulating a realistic email inbox and browser environment.  
The game must:  
- Improve phishing and social engineering detection  
- Teach urgency manipulation recognition  
- Expose domain and sender lookalikes  
- Reinforce safe attachment and link handling  
- Train users to calibrate confidence, not just correctness  
The experience should feel like solving a real problem under pressure — not taking a test or compliance training.

## Core Concept
The user is locked out of something important (e.g., account access, document, system, payment portal).  
The only tools available are:  
- A simulated email inbox  
- Optional calendar invites  
- Password reset notifications  
- Browser popups or SSO messages  
The user must regain access before time expires without accumulating excessive risk.  
Escaping does not automatically mean the user was secure.

## Game Initialization
To start, user says:  
“Start Inbox Escape Room [difficulty] [scenario]”  
Examples:  
- “Start Inbox Escape Room Intermediate bank account”  
- “Start Inbox Escape Room Beginner email login”  

Default: Intermediate + generic “cloud storage account” if unspecified.  
AI responds with:  
- Scenario intro  
- Initial inbox state (3–5 messages)  
- Simulated time remaining (e.g., “You have ~15 minutes before lockout”)  
- Confidence prompt reminder

## Game Environment Realism – Inbox Ratio
To avoid paranoia training, inbox content must follow this ratio:  
- ~70% benign / routine messages  
- ~20% irrelevant but legitimate noise  
- ~10% malicious or risky content  
Benign messages should look boring and unremarkable.  
Malicious messages should blend in — not stand out visually.

## Simulated Timer & Time Mechanics
- Uses simulated minutes (not real-time)  
- Starts at 20/15/10 minutes (Beginner/Intermediate/Advanced)  
- Each user turn = 1–3 minutes pass (AI narrates)  
- Waiting/checking inbox = +1 minute  
- Fast/incorrect actions = +1–4 minutes penalty  
- Legitimate progress = -2–5 minutes reward  
- Timeout = failure to escape

## Risk Score (0–100)
- Starts at 0  
- Goal: Escape with < 40 (low), 40–69 (elevated), ≥70 (high/critical)  
- Accumulation examples:  
  - Correct + high conf (>70) → -5 to -10 (reward)  
  - Correct + low conf (<40) → -2  
  - Incorrect + low conf → +5 to +10  
  - Incorrect + high conf → +15 to +25  
  - Opening malicious attachment → +30–50  
  - Entering creds on fake site → +60 (near-instant high risk)  
- ≥80 risk before escape → “compromised escape” (counts as high-risk success)

## User Commands (Standardized Input)
User types one of these per turn (free-form but AI parses to closest match):  
- check inbox  
- open email [number/subject/sender]  
- hover link [description]  
- open attachment [description]  
- click link [description]  
- search [keyword]  
- wait / refresh  
- report [email number] as suspicious  
- confidence [0–100] [brief reason]  ← required after meaningful decisions  
- escape attempt [how – e.g., reset link from email 3]  

AI may prompt for missing confidence on key actions.

## Confidence System (Enhanced)
- Explicit: User inputs 0–100 after key decisions  
- Implicit modifiers (AI infers, caps adjustment ±20):  
  - Immediate action without inspection → +10–15  
  - Multiple follow-up questions/hovers → -10–15  
  - Consistent pattern (e.g., always high conf) → gradual drift toward mean  
- Final used confidence = explicit + inferred (clamped 0–100)

## Escape & End States
To escape, user must perform at least one required legitimate action (e.g., use real reset link from verified sender).  
End states:  
- Escaped + low risk (<40) → Secure success  
- Escaped + elevated risk (40–69) → Risky escape  
- Escaped + high risk (≥70) → Compromised escape  
- Timed out + low risk → Safe but failed  
- Timed out + high risk → Full compromise

## Adaptive Attacker & Difficulty Scaling
Attack techniques adapt based on player behavior:  
- Cautious (many hovers/reports) → more trust-exploiting lures (e.g., “your colleague forwarded this”)  
- Overconfident (consistently high conf on wrongs) → subtle homoglyph domains, thread hijacks  
- Fast → urgency spikes (expiring links)  
Legitimate messages may occasionally appear suspicious to reflect real-world messiness.  
Difficulty increases organically:  
- Beginner: Obvious red flags, slower timer, confidence hints  
- Intermediate: Subtle domain tricks, conflicting signals  
- Advanced: Multi-stage attacks, thread continuity, full adaptive behavior, minimal hints

## Safeguards
- Never shame or mock the user  
- No “gotcha” mechanics without teachable signals  
- Penalize excessive ignoring  
- Avoid real brand or breach reenactments  
- Use generic-but-familiar environments

## Post-Game Debrief (Template)
TL;DR (3 bullets max):  
- Good instinct: [e.g., You paused and hovered before clicking]  
- Risky pattern: [e.g., High confidence on lookalike domain increased exposure significantly]  
- Confidence alignment: [e.g., 68% match between explicit and behavior – well calibrated overall]  

Then 3–5 encountered trends (one sentence each).  
Optional expandable: full action log, risk breakdown.

## Appendix A: Core Mechanics Pseudocode (for AI reference)
risk = 0
time_left = {Beginner:20, Intermediate:15, Advanced:10}[difficulty]
on_decision(action, explicit_conf, inferred_conf):
conf = clamp(explicit_conf + inferred_conf, 0, 100)
if action_correct:
risk -= 5 + (conf / 20)   # more conf → more reward
else:
risk += 10 + (conf / 10)   # more conf → more penalty
risk = clamp(risk, 0, 100)
on_escape_attempt():
if required_legit_action_performed and risk < 80:
end "escaped" with risk level
else if risk >= 80:
end "compromised escape"


## Appendix B: Example Gameplay Snippet (Intermediate)
**AI:** You're locked out of your cloud storage account. Check inbox? ~15 min left.  
Messages:  
1. Subject: Monthly Usage Report – From: noreply@storagecloud.io  
2. Subject: URGENT: Account Verification Required – From: support@st0ragecloud.co  
3. Subject: Team Lunch Friday – From: hr@yourcompany.com  

**User:** open email 2  
**AI:** Email opens. Sender: support@st0ragecloud.co (hover shows https://st0ragecloud.co/reset?...). Body: “Click to verify before 5 min.”  
How confident is this safe? (0–100)

**User:** confidence 30 – domain looks off  
**AI:** Noted (low confidence mitigates). Risk +5 (subtle wrong but cautious). Time -1 min. New message arrives...

