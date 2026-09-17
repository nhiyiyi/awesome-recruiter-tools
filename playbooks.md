# Recruiter AI Playbooks

> Four deep-dive playbooks with complete prompt chains, guardrails, and channel-specific rules. Goes deeper than the [prompt library](./prompts.md) — each playbook is a step-by-step workflow, not a menu of options.

**Built by [NinjaHire](https://ninjahire.co)**

---

## Playbooks

| Playbook | What It Covers |
|----------|----------------|
| [1 — Outreach by Channel](#playbook-1-outreach-by-channel) | LinkedIn InMail, cold email, SMS, phone — rules and prompts for each |
| [2 — Voice & Phone Screen Scripts](#playbook-2-voice--phone-screen-scripts) | AI voice agent scripts, human phone screen guides, post-call summaries |
| [3 — Evaluate a Candidate Against a Job](#playbook-3-evaluate-a-candidate-against-a-job) | Five-step prompt chain from JD extraction to hire/no-hire summary |
| [4 — Boolean & X-Ray Search Generator](#playbook-4-boolean--x-ray-search-generator) | Build LinkedIn Boolean, Google X-ray, GitHub, and resume DB strings from scratch |

---

## How to Use These Playbooks

Each playbook follows the **PRIDE framework** (from SocialTalent / Maisha Cannon):

- **P**urpose — know what you want before you open the chat
- **R**equest — be specific about format, length, tone, audience
- **I**dentity — assign the AI a persona ("You are a senior technical recruiter...")
- **D**etail — give it context: JD, resume, company, market data
- **E**xamine — always review, edit, and humanize before sending

Prompts below are written to be copy-paste ready. Replace `[brackets]` with your specifics. All prompts are validated to work with Claude, ChatGPT, and Gemini.

---

## Playbook 1: Outreach by Channel

Different channels have different rules. The same message sent via LinkedIn InMail, cold email, and SMS will perform completely differently — and each channel has hard constraints (character limits, platform policies, legal requirements) that should be baked into the prompt, not added as an afterthought.

### Channel Rules at a Glance

| Channel | Hard Limit | Tone | First Contact? | Legal Watch |
|---------|-----------|------|----------------|------------|
| LinkedIn Connection Request | 300 chars | Casual, personal | Yes (warm) | No automation bots |
| LinkedIn InMail | ~2,000 chars | Conversational | Yes | No spam patterns |
| Cold Email | No hard limit | Direct, professional | Yes | CAN-SPAM / GDPR opt-out required |
| Follow-up Email | No hard limit | Value-add, brief | No | — |
| SMS / Text | 160 chars per segment | Ultra-brief, name-only | **No** — never first touch | TCPA opt-in required first |
| Phone Intro Call | 2–3 min | Human, warm | Yes (inbound sourced) | State recording consent laws |

---

### LinkedIn Outreach

#### Guardrails
- **Never** open with "I came across your profile and was impressed" — every recruiter sends this
- **Never** mention the role name in a connection request — too transactional for a first touch
- InMail should reference exactly one specific thing from their profile (not a generic compliment)
- Character limit for connection requests: **300 characters** — no room for pleasantries
- If using InMail: front-load value in the first sentence; most people read only that before deciding to engage
- Avoid: "exciting opportunity," "I'd love to connect," "are you open to opportunities?"

#### Prompt 1.1 — LinkedIn Connection Request (300 chars max)

```
Write a LinkedIn connection request to [candidate name], a [current title] at [current company]. 

I'm reaching out because: [one specific reason — e.g., "we're both in fintech compliance" / "I saw your talk at SourceCon" / "you've built teams at exactly the stage we're at"].

Hard rules:
- Under 300 characters total (including spaces)
- No mention of a job opening
- No "exciting opportunity"
- End with a genuine question or shared observation, not "let's connect"

Output: the message text only, nothing else.
```

**Example output target:**
> "Saw your post on scaling BDR teams without SDR burnout — exactly what we're wrestling with. Building something similar and would love your perspective."
*(212 characters)*

---

#### Prompt 1.2 — LinkedIn InMail (First Touch, Passive Candidate)

```
Write a LinkedIn InMail to [candidate name], [title] at [company], about a [role title] opportunity at [my company].

Context about them: [one specific detail from their profile — a project, publication, promotion, company they built, or skill they're known for]
Why this role is genuinely relevant to their career: [1-2 sentences of actual relevance, not "perfect fit"]
One soft question to end on: [e.g., "Curious whether you've explored moving from agency to in-house?" or "Open to hearing about the scope?"]

Hard rules:
- Under 150 words
- First sentence must be about THEM, not about me or the role
- No "I hope this message finds you well"
- No "I came across your profile"
- No "exciting opportunity"
- End with one question, not a calendar link

Output format: Subject line on line 1, blank line, then message body.
```

---

#### Prompt 1.3 — LinkedIn InMail (Executive / Senior Passive)

```
Act as an executive recruiter with 15 years of C-suite search experience. Write a LinkedIn InMail to [name], [title] at [company], about a [C-level/VP title] opportunity.

Important context:
- They are not actively looking and receive 10+ recruiter messages per week
- Opportunity: [2-sentence description — company, scope, why it's genuinely significant]
- What makes them specifically right for this: [1 specific thing from their background]

Structure:
1. Open with a market observation or industry trend relevant to their domain (not about them or the role)
2. Reference one specific thing from their career in 1 sentence
3. Introduce the opportunity briefly — 2 sentences max
4. Ask one genuine question that invites dialogue, not a pitch

Hard rules:
- Under 200 words
- No urgency language ("I'd love to connect ASAP")
- No flattery ("I've been following your career")
- Must feel like it came from a peer, not a vendor
```

---

#### Prompt 1.4 — LinkedIn Follow-Up (No Response, 5 Days Later)

```
Write a LinkedIn follow-up message to [candidate name] who hasn't responded to my InMail sent 5 days ago about the [role title] role.

The original message was about: [1-sentence summary of original pitch]
New angle to add (pick one):
- A market data point they'd find interesting
- A recent company milestone or news item
- A question about their career direction (not about the role)

Hard rules:
- Under 75 words
- Must add value — not just "just checking in"
- Different subject line / opening than the original
- Do NOT repeat the original message
- End with a soft close: acknowledge they may not be interested and that's okay
```

---

### Cold Email

#### Guardrails
- **Subject line is everything** — it determines whether the email gets opened. Test it on yourself: would you open it?
- First line should NOT be about you. It should be about them or a shared context.
- Emails over 150 words lose 60%+ of readers before the CTA
- Always include one-click unsubscribe or opt-out language to comply with CAN-SPAM (US) and GDPR (EU)
- Never send the same email to a candidate you've already InMail'd — reference that touchpoint
- Best send times: Tuesday–Thursday, 7–9am or 1–3pm (recipient's local time)
- Never use HTML-heavy email for cold outreach — plain text converts better

#### Prompt 1.5 — Cold Email (First Touch, Under 120 Words)

```
Write a cold recruiting email for [candidate name], [title] at [company], about the [role title] role at [my company].

What I know about them that's relevant: [specific detail — skill, company they worked at, project, publication, or career pattern]
Why this role maps to their career trajectory: [1 honest sentence]
CTA: [soft ask — "15 minutes?" / "open to hearing more?" / one question]

Hard rules:
- Under 120 words (count them)
- Do NOT open with "I hope this finds you well" or any pleasantry
- First sentence must reference the specific detail about them
- One CTA only — not multiple asks
- Conversational tone, not corporate
- Include a subject line that does NOT say "Exciting opportunity" or "Quick question"

Output: Subject line, then email body. Label them clearly.
```

---

#### Prompt 1.6 — 3-Touch Email Sequence (10 Days)

```
Write a 3-email outreach sequence for [candidate name] for the [role title] role at [my company]. 

Candidate background: [2-sentence summary]
Role selling points: [2-3 genuine differentiators]
Sequence structure:
- Email 1 (Day 0): Personalized first touch — lead with something specific about them
- Email 2 (Day 4): New value — market insight, salary data, or team context NOT in email 1
- Email 3 (Day 9): Graceful close — acknowledge they may not be interested, leave the door open genuinely

Hard rules for ALL three emails:
- Each under 100 words
- Each must have a different subject line
- Email 2 must add genuinely new information — no rephrasing of email 1
- Email 3 must not guilt-trip or pressure — it should feel like a genuine close, not a manipulation tactic
- No "just following up" or "circling back"

Output: Label each email with Day, Subject, and Body.
```

---

#### Prompt 1.7 — Follow-Up Email After a Previous LinkedIn InMail

```
Write a follow-up email to [candidate name] who did not respond to a LinkedIn InMail I sent [X days] ago about the [role].

Context: I've already made one LinkedIn touchpoint. This email should:
1. Reference the LinkedIn message briefly (shows persistence without being creepy)
2. Add a new angle or piece of information not in the InMail
3. Make the email feel like a natural continuation, not a copy-paste

Hard rules:
- Under 100 words
- Acknowledge you've already reached out — pretending you haven't is worse
- New value in this email vs. InMail
- One CTA only
```

---

### SMS / Text Outreach

#### Guardrails
- **SMS is never the first touchpoint** — only use after the candidate has opted in or already spoken with you
- US law (TCPA): written consent required before sending recruiting-related texts. Fines up to $1,500 per unauthorized message.
- Keep under 160 characters to avoid splitting into two messages (which looks unprofessional)
- Use the candidate's first name — nothing else personal (no company, no salary, no role details)
- Always include an opt-out option ("Reply STOP to unsubscribe") for compliance
- Never send between 9pm–8am in the recipient's local time zone
- SMS is best for: interview confirmations, urgent follow-ups, day-of logistics. Not for first outreach or complex role conversations.

#### Prompt 1.8 — SMS Confirmation After Phone Screen Scheduled

```
Write an SMS message confirming an interview or phone screen with [candidate name].

Details:
- Interview type: [phone screen / video interview / in-person]
- Date and time: [date, time, timezone]
- Who they're meeting: [name and title]
- Link or dial-in: [link or "I'll call you at [number]"]

Hard rules:
- Under 160 characters total (count carefully)
- First name only — no last name in SMS
- Include date, time, and one action (link or "I'll call you")
- Include: "Reply STOP to opt out"
- Do NOT include salary, company details, or persuasion language

Output: Message text only. Then show the character count.
```

---

#### Prompt 1.9 — SMS Day-Of Interview Reminder

```
Write a brief SMS reminder to [first name] for their [interview type] today at [time].

Hard rules:
- Under 100 characters
- Confirm: name, time, and one action (link or "watch for my call")
- Warm but brief — this person already knows about the interview
- No opt-out needed (they've already consented via scheduling)

Output: Message text only. Character count below.
```

---

### Phone / Intro Call

#### Guardrails
- **Always identify yourself immediately** — "Hi [name], this is [your name] from [company], I'm a recruiter..." — never make them guess who's calling
- Get to the point within 30 seconds — passive candidates have low tolerance for preamble
- Ask for permission before pitching: "Do you have 2 minutes?" before launching into a pitch
- Pre-call research is not optional — know their current role, tenure, and one reason they might be open before you dial
- Never call from a blocked number — candidates won't answer and won't call back
- Have a voicemail script ready — if they don't answer, leave a message under 30 seconds that gives them a reason to call back (not just "give me a call back")
- Check recording consent laws by state/country before recording calls

#### Prompt 1.10 — Pre-Call Research Brief

```
I'm about to call [candidate name], [current title] at [current company]. 

Based on what I know about them: [paste LinkedIn summary or resume excerpt]

Give me:
1. Three potential reasons they might be open to a conversation right now (think: tenure, company trajectory, market signals)
2. Two things to reference that show I've done my homework (without being creepy)
3. The most likely objection they'll raise ("I'm not looking," "I'm happy where I am," "Send me more info") and a brief natural response to each
4. One genuine question to ask that opens a conversation rather than triggering a defensive "no"

Output: A bulleted 1-page brief I can read in 60 seconds before dialing.
```

---

#### Prompt 1.11 — Cold Call Opening Script

```
Write a 60-second cold call opening script for me to reach [candidate name] about the [role title] role.

I'm: [your name, company, 1-sentence on what makes this role worth their time]
What I know about them that's relevant: [1 specific thing]

The script should:
1. Introduce me clearly in 10 seconds
2. Ask permission to take 2 minutes (so they don't feel trapped)
3. Hook with one specific and genuine reason this call is relevant to their career
4. End with one question that opens a dialogue

Hard rules:
- Conversational — write it how I'd actually say it, not how it reads on paper
- No corporate speak
- If they say "I'm not interested," give me a one-sentence bridge to keep the conversation alive without being pushy
- Total read time: under 60 seconds

Output: The script itself, with stage directions in [brackets] (e.g., [pause], [wait for answer]).
```

---

#### Prompt 1.12 — Voicemail Script (30 Seconds)

```
Write a voicemail script to leave for [candidate name] about the [role title] role.

Hard rules:
- Under 30 seconds when read aloud (roughly 75 words)
- State your name and company clearly at the start AND at the end with your number
- Give them one specific reason to call back — make it about an opportunity for THEM, not about filling my req
- Do NOT leave a long pitch — the goal of a voicemail is to get a callback, not to sell the role
- Speak in first person as if leaving the message in the moment

Output: The script with timing guidance (e.g., "[say slowly]" or "[pause]").
```

---

## Playbook 2: Voice & Phone Screen Scripts

This playbook covers two scenarios:
1. **Human-run phone screen** — prompts to help you prepare, run, and summarize a screening call
2. **AI voice agent script** — structured dialogue for AI voice tools (Paradox, NinjaHire, Bland.ai, etc.) to run automated pre-screening

---

### Guardrails for Phone & Voice Screening

**Legal must-knows:**
- Record only with consent — laws vary by state (California requires two-party consent)
- Never ask about: age, race, gender, national origin, religion, disability, pregnancy, marital status, or salary history (in ban states)
- Structured screening = legally safer — ask the same questions to all candidates for the same role

**What phone screens should accomplish:**
- Confirm basic qualifications (the non-negotiables from the JD)
- Surface availability and timeline
- Get compensation alignment before wasting time on both sides
- Create a positive candidate experience — they're evaluating you too

**AI voice agent guardrails:**
- Script must handle unexpected responses gracefully (candidate goes off-script)
- Build in explicit consent capture at the start ("This call will be recorded for quality purposes. Do you consent?")
- AI agent should always offer a human escalation path ("Would you prefer to speak with a person instead?")
- Never have the AI agent impersonate a human — it must identify as AI

---

### Human-Run Phone Screen

#### Prompt 2.1 — Generate Phone Screen Questions for a Role

```
Act as a senior recruiter. Create a structured phone screen guide for a [job title] candidate.

Role requirements: [paste top 5 from JD]
Deal-breakers to screen for: [list 2-3 hard non-negotiables]
Compensation range: [$X–$Y]
Timeline to start: [X weeks / immediately / flexible]
Location/remote requirement: [fully remote / hybrid X days / onsite in City]

Generate:
1. Opening script (15 seconds — name, company, purpose of call)
2. 6 screening questions covering: [required experience], availability, compensation, logistics, and one opener about what they're looking for in their next move
3. For each question: what a qualifying answer sounds like vs. a disqualifying answer
4. A closing script that sets clear next steps

Format: A printable one-page guide I can have open during the call.

Hard rules:
- All questions must be legally compliant (no age, disability, family status, salary history in ban states)
- "Qualifying" criteria must map to the JD requirements, not cultural assumptions
- Compensation discussion framing: ask for their range first, not mine
```

---

#### Prompt 2.2 — Post-Screen Call Notes to Structured Summary

```
Convert my rough notes from a phone screen into a structured candidate summary.

My raw notes: [paste messy notes or bullet points exactly as taken during the call]
Role: [job title]
Key requirements: [3-5 from JD]

Output format:
**Candidate:** [name]
**Role:** [job title]
**Screen date:** [date]
**Screened by:** [name]

**Qualifications Summary:**
- [Requirement 1]: [Evidence from call — what they said]
- [Requirement 2]: [Evidence from call]
- [Requirement 3]: [Evidence from call]

**Logistics:**
- Available start: [date]
- Compensation expectation: [$X or range]
- Location/work arrangement: [confirmed/issue]

**Strengths from call:** [2-3 bullets]
**Concerns / gaps:** [2-3 bullets]
**Interviewer recommendation:** [Advance / Hold / Reject]
**Reasoning:** [2 sentences]

**Suggested next step:** [specific action with timeline]
```

---

#### Prompt 2.3 — Objection Handling During a Call

```
I'm on (or preparing for) a phone screen and the candidate said: "[exact objection]"

Common objections and their context:
- "I'm happy where I am" — they're passive, not hostile
- "I'm not really looking right now" — open but cautious
- "What's the salary?" — they want to qualify before engaging
- "Can you just send me more info?" — deflection; they want to disengage without saying no
- "I'm in the middle of another process" — leverage situation
- "I don't want to work for [company type]" — specific concern

For this objection, give me:
1. A one-sentence acknowledgment (not defensive)
2. A bridge that keeps the conversation alive without pressure
3. A question that re-engages them around THEIR interests, not mine

Tone: natural, peer-level, not salesy.
```

---

### AI Voice Agent Script

#### Prompt 2.4 — Write an AI Voice Agent Screening Script

```
Act as a conversational AI designer with experience building voice agent scripts for recruiting.

Write a structured AI voice screening script for the [job title] role.

The AI agent will:
- Identify itself as an AI at the start
- Capture consent for recording
- Screen for 4-5 specific requirements
- Handle common unexpected responses (confusion, no answers, requests to speak to a human)
- Close with next steps and a positive experience

Requirements to screen for:
1. [Requirement 1 — e.g., "Must have active RN license in [state]"]
2. [Requirement 2 — e.g., "Available to start within 30 days"]
3. [Requirement 3 — e.g., "Comfortable with pay rate of $[X]/hr"]
4. [Requirement 4 — e.g., "Willing to work [shift type]"]

Script format:
- [AGENT]: what the AI says
- [CANDIDATE SAYS YES]: branch A
- [CANDIDATE SAYS NO]: branch B  
- [CANDIDATE CONFUSED / OFF-SCRIPT]: recovery branch
- [DISQUALIFIED]: graceful close
- [QUALIFIED]: handoff to human / scheduling

Include at start:
- AI identification statement
- Recording consent capture
- Option to speak to a human instead

Target length: 5-8 minutes max for a qualified candidate who answers concisely.
```

---

#### Prompt 2.5 — Generate Screening Criteria from a Job Description

```
Extract screening criteria from this job description and format them as yes/no qualification gates for an automated screening system.

For each criterion:
- State the criterion as a yes/no question the AI can ask
- Define what "yes" sounds like (qualifying answer)
- Define what "no" sounds like (disqualifying answer)
- Assign priority: P1 (dealbreaker), P2 (important), P3 (nice-to-have)

Output as a table: Question | Qualifying Answer | Disqualifying Answer | Priority

Limit to 5-6 questions maximum — any more and candidates disengage.

[Paste job description]
```

---

## Playbook 3: Evaluate a Candidate Against a Job

This is a five-step prompt chain. Run these in sequence — the output of each step feeds into the next.

---

### Guardrails

**Privacy first:**
- Do NOT paste real candidate names, email addresses, phone numbers, or government IDs into a public AI tool (ChatGPT free/Plus)
- Use ChatGPT Team ($25/user/mo), Claude Team, or your own API deployment if processing real resumes — these do not train on your data
- Anonymize: replace "John Smith" with "Candidate A" before pasting

**What makes a good evaluation:**
- Evidence-based, not impression-based — cite specific lines from the resume
- Separates must-have from nice-to-have — don't fail candidates on nice-to-haves
- Identifies gaps without assuming they're fatal — a gap in the resume is not the same as a gap in ability
- Surfaces what to probe in interviews, not just a pass/fail verdict

**Legal:**
- Never evaluate candidates on protected characteristics (age, gender, race, disability, etc.)
- Evaluation criteria must map directly to role requirements — no "culture fit" without specific behavioral definition
- Keep evaluation notes — they may be needed to defend a hiring decision

---

### Step 1 — Extract Structured Requirements from a JD

```
Act as a hiring manager. Extract the requirements from this job description into a structured format.

Categories:
- Must-Have (role fails without these): [list]
- Important (preferred, disadvantage to be missing): [list]
- Nice-to-Have (bonus, not decision factor): [list]
- Red Flags to watch for (e.g., specific tools they must know, compliance requirements): [list]

Remove marketing language — keep only things that are actually evaluable from a resume or in an interview.
Flag any requirement that seems artificially restrictive (e.g., "10 years of experience in a tool that's 6 years old").

[Paste job description]
```

---

### Step 2 — Map Resume to Requirements

```
Map this resume against the requirements below. For each requirement:

Column 1: Requirement (from Step 1 output)
Column 2: Evidence in resume (exact quote or section reference — or "Not found")
Column 3: Confidence level: Strong match / Partial match / No evidence

Do not score or rank yet. Do not infer — only cite evidence that is present.
Do not evaluate on: age, gender, graduation year (as age proxy), employer prestige, or school name.

Requirements:
[Paste Step 1 output]

Resume (anonymized):
[Paste resume with name/contact info removed]
```

---

### Step 3 — Score the Candidate

```
Based on the requirement mapping below, score this candidate.

Scoring:
- Must-Have requirements: each scores 0 (not met) or 10 (met). Candidate fails if any Must-Have scores 0.
- Important requirements: each scores 0–7 based on depth of match
- Nice-to-Have requirements: each scores 0–3

Calculate:
- Must-Have score: [X/total possible]
- Important score: [X/total possible]
- Nice-to-Have score: [X/total possible]
- Overall fit: [weighted percentage — suggest 60% Must-Have, 30% Important, 10% Nice-to-Have]

Then: 
- Overall recommendation: Strong Advance / Advance / Hold / Reject
- One-sentence justification
- Top 2 strengths (evidence-backed)
- Top 2 concerns (evidence-backed, be specific about what's missing and why it matters)

Mapping from Step 2:
[Paste Step 2 output]
```

---

### Step 4 — Generate Interview Probes for Gaps

```
Based on the gaps identified in the candidate evaluation, generate targeted interview questions to probe whether each gap is real or a resume artifact.

For each gap:
- State the gap (what's required, what's missing from the resume)
- Write 2 questions that would reveal whether they have the capability despite not showing it on the resume
- Describe what a strong answer looks like (2-3 elements)
- Describe a red flag answer (1-2 elements)

Gaps to probe:
[Paste gaps from Step 3 output]

Role context:
[Paste job title and 2-3 sentence role description]
```

---

### Step 5 — Write the Hiring Manager Summary

```
Write a concise, evidence-based candidate summary for the hiring manager for [role title].

Use the evaluation data below. The summary should:
1. Open with a 2-sentence bottom-line assessment (advance or don't, and the primary reason)
2. List 3 strengths with specific evidence from their background
3. List 2 concerns with specific evidence and suggested interview probes
4. State logistics: availability, compensation expectation (if known), location match
5. End with a clear recommended next step

Format: should fit on half a page. No fluff. Hiring managers read these in 60 seconds.

Evaluation data:
[Paste Steps 1-4 outputs]
```

---

### Bonus: Compare Multiple Candidates in One Pass

```
I have [N] candidates for the [role title] role. Evaluate and rank them.

For each candidate, provide a row in this table:
Candidate | Must-Have Met (Y/N) | Overall Score (0-100) | Top Strength | Top Concern | Recommendation

Then: a paragraph on the top 2 candidates — what makes them differentiated, and what each needs to prove in the next interview.

Job requirements:
[Paste Step 1 output]

Candidate resumes (anonymized as Candidate A, B, C...):
[Paste each resume]
```

---

## Playbook 4: Boolean & X-Ray Search Generator

Building Boolean strings by hand takes experience and produces inconsistent results. These prompts turn any role into a production-ready search string in minutes.

---

### Guardrails

**Know your syntax before you prompt:**
- LinkedIn Recruiter uses: `AND`, `OR`, `NOT` (must be uppercase), parentheses `()`, and quotes `""`
- LinkedIn free search is less powerful — some Boolean operators don't work in all fields
- Google X-ray uses: `site:`, `intitle:`, `inurl:`, `-` for exclusion, `"exact phrase"`
- Boolean strings can't see non-indexed information — a candidate with a hidden LinkedIn won't appear
- Longer strings = more precise but smaller pool. Start broad, then tighten.
- Test every string before sending to the AI for refinement — know what it produces

**Common mistakes to avoid:**
- Using too many `OR` options without `()` — results become unpredictable
- Searching for the exact job title only — many strong candidates have different titles
- Not excluding irrelevant results (recruiters, students, the role itself if posted on LinkedIn)

---

### LinkedIn Boolean Generator

#### Prompt 4.1 — Generate LinkedIn Boolean String from a Job Description

```
Act as an expert Boolean search specialist. Generate a LinkedIn Recruiter Boolean search string for this role.

Role: [job title]
Must-have skills/experience: [list 3-5]
Nice-to-have skills: [list 2-3]
Location: [city/region / "remote US" / "EMEA"]
Seniority: [e.g., 5-10 years experience / senior / staff level]
Exclude: [e.g., recruiters, students, current employees of competitors we're not targeting]
Company types to target: [e.g., Fortune 500 / Series A-C startups / consulting firms]

Generate:
1. A broad string (wider net — more candidates, less precise)
2. A targeted string (smaller pool, higher relevance)
3. A niche string (if the market is thin — use more synonyms and adjacent titles)

For each string:
- Show the full string formatted for copy-paste into LinkedIn Recruiter
- Explain what it's optimized for
- Estimate approximate result set size (rough order of magnitude)

Use proper LinkedIn Boolean syntax: AND, OR, NOT (uppercase), parentheses, quotes.
```

**Example output (targeted string):**
```
("software engineer" OR "backend engineer" OR "backend developer") AND 
("Python" OR "Django" OR "FastAPI") AND 
("PostgreSQL" OR "MySQL" OR "relational database") AND 
("AWS" OR "GCP" OR "Azure") AND 
("San Francisco" OR "Bay Area" OR "remote") NOT 
("recruiter" OR "talent" OR "student")
```

---

#### Prompt 4.2 — Expand Title and Skill Synonyms

```
Act as a sourcing specialist. I'm building a Boolean string and need comprehensive synonyms.

Role I'm hiring: [job title]
Core skills to search for: [list 3-5]

For each element, give me:
1. All common title variations (how this person might list their title on LinkedIn)
2. All synonyms for each core skill (tools, frameworks, certifications, adjacent terms)
3. Any certification or credential names that signal this expertise
4. Company types or industries where this skill is commonly found

Output as a structured list, not a Boolean string — I'll compose the string separately.
```

---

#### Prompt 4.3 — Refine a Boolean String That's Returning Too Many or Too Few Results

```
Act as a Boolean search expert. My LinkedIn search string is returning [too many irrelevant results / too few results].

Current string:
[paste current Boolean string]

Problem:
[describe what's wrong — e.g., "Getting too many students and entry-level people" / "Only returning 12 results for a large market" / "Not finding people with niche certification X"]

Suggest:
1. Two modifications to fix the problem
2. What the new string will do differently
3. What tradeoffs to expect (more precision = fewer results; more recall = more noise)

Show the revised string(s) ready to copy-paste.
```

---

### Google X-Ray Search Generator

X-ray searches let you search within a specific site (like LinkedIn, GitHub, or Behance) using Google's full text indexing — often finding profiles that LinkedIn's own search misses.

#### Prompt 4.4 — Google X-Ray Search (LinkedIn)

```
Act as a sourcing specialist. Generate Google X-ray search strings to find [job title] candidates on LinkedIn.

Target profile:
- Title/role: [job title and common variations]
- Skills: [3-5 core skills]
- Location (if specified): [city, region, or "remote"]
- Seniority signals: [years of experience / leadership keywords]
- Exclude: [recruiters / students / junior roles]

Generate three X-ray search variations:
1. By title and skills — broadest approach
2. By company type and skills — for niche company targeting
3. By specific skill combination — for rare skill sets

Use this syntax:
- `site:linkedin.com/in` — searches LinkedIn public profiles
- `"exact phrase"` — for required terms
- `intitle:` — terms that should appear in the page title
- `-term` — exclusions (no space after dash)

Show each string formatted for copy-paste into Google.
```

**Example output:**
```
site:linkedin.com/in "machine learning" ("PyTorch" OR "TensorFlow") 
("senior" OR "staff" OR "principal") "San Francisco" -recruiter -student
```

---

#### Prompt 4.5 — GitHub X-Ray Search (Developers)

```
Generate Google X-ray search strings to find developers on GitHub who have experience with [technology/framework].

Target:
- Technology/language: [e.g., Rust, Go, Solidity, React Native]
- Type of work: [e.g., open-source contributor / built production apps / active committer]
- Location signal (if any): [city or "US-based" if they mention it in bio]
- Recency: [active in last 6 months / has recent commits]

Generate:
1. Search by language + location bio signal
2. Search by repo topics
3. Search by README or profile keywords that signal strong practitioners

Use: `site:github.com`

Include example output of what a strong result looks like and how to evaluate it.
```

**Example output:**
```
site:github.com "Rust" ("systems programming" OR "embedded") 
"San Francisco" -site:github.com/topics -site:github.com/explore
```

---

#### Prompt 4.6 — X-Ray Search for Academic / Research Talent

```
Generate Google X-ray search strings to find researchers or academics with expertise in [domain] who may be open to industry roles.

Target:
- Domain: [e.g., computational biology / NLP / computer vision / materials science]
- Institution type: [e.g., "any university" / Ivy League / national lab]
- Signals of industry-readiness: [publication count / patents / conference talks / GitHub activity]

Generate:
1. Google Scholar search for recent publication authors in this domain
2. LinkedIn X-ray for researchers now in industry (shows transition path)
3. University lab page X-ray to find students and postdocs by advisor/lab

Use appropriate `site:` prefix for each.
```

---

### Resume Database Boolean (ATS / Job Board)

#### Prompt 4.7 — Generate Resume Database Boolean for ATS or Job Board

```
Act as a sourcing specialist. Generate a Boolean search string optimized for [ATS name / job board] resume search.

Note: ATS/job board Boolean syntax differs from LinkedIn. Key differences:
- Most use standard SQL-like Boolean: AND, OR, NOT
- Resume databases search full text, not profile fields — include more synonyms
- No field-specific operators (unlike LinkedIn's "title:" field)

Role: [job title]
Skills: [list]
Experience level: [X-Y years]
Certifications: [if relevant]
Location radius: [city + X miles / state / remote]

Generate:
1. A full-text Boolean string for the resume body
2. Title field search (if the ATS has separate title search)
3. A skills/tags search (if supported)

Optimize for: [high precision / high recall] — tell me which tradeoff you want and I'll adjust accordingly.
```

---

### The Complete Search Workflow

When building a search from scratch, run these prompts in order:

```
Step 1 → Run Prompt 4.1 (generate initial LinkedIn Boolean from JD)
Step 2 → Run Prompt 4.2 (expand synonyms for any thin result sets)
Step 3 → Run the string in LinkedIn. If results are off, run Prompt 4.3 to refine
Step 4 → Run Prompt 4.4 (Google X-ray to find profiles LinkedIn misses)
Step 5 → For developers: run Prompt 4.5 (GitHub X-ray)
Step 6 → Run Prompt 4.7 (ATS/resume database search in parallel)
```

Typical time to a production-ready multi-source search: 15-20 minutes vs. 1-2 hours manually.

---

## Quick Reference: Prompt Quality Checklist

Before submitting any prompt to an AI, verify:

- [ ] **Role assigned** — "Act as a [specific persona]..." not just asking a question
- [ ] **Hard rules included** — character limits, word counts, what to avoid
- [ ] **Context provided** — enough about the candidate / role / company to get a specific answer
- [ ] **Output format specified** — table, list, email format, labeled sections
- [ ] **PII removed** — no real names, email addresses, or contact info if using public AI tools
- [ ] **Bias check** — no protected characteristics in the prompt criteria
- [ ] **Human review planned** — AI output is a draft, not a final product

---

## Related Resources

### In this repo
- [Prompt Library →](./prompts.md) — 150+ individual copy-paste prompts organized by use case
- [Outreach Sequences →](./outreach-sequences.md) — 16 NinjaHire playbooks, 12 channel strategies, 42 template variables, and Hanzo AI rules
- [Awesome Recruiter Tools →](./README.md) — Free tools, platforms, and resources for recruiters

### Related repos
- [Autonomous Recruiter](https://github.com/ninjahire/autonomous-recruiter) — Run these playbooks end-to-end using NinjaHire's MCP server and any LLM
- [HRTech Landscape](https://github.com/ninjahire/hrtech-landscape) — Boolean and sourcing vendors, ATS platforms, outreach tools referenced in these playbooks
- [Recruitment Taxonomy](https://github.com/ninjahire/recruitment-taxonomy) — Definitions for every stage and metric referenced in the evaluation and voice-screen playbooks

### NinjaHire
[NinjaHire](https://ninjahire.co) is the autonomous AI recruiter that executes these playbooks natively — running multi-channel outreach sequences, AI voice screens, candidate scoring, and Boolean sourcing without manual steps. [Get started free →](https://app.ninjahire.co/auth/signup)

---

**Built by [NinjaHire](https://ninjahire.co)** — Autonomous AI Recruiter for staffing teams and high-volume hiring operations.

[![NinjaHire](https://img.shields.io/badge/Maintained%20by-NinjaHire-brightgreen)](https://ninjahire.co)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](http://makeapullrequest.com)
