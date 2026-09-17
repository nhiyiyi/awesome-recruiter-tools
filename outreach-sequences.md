# Recruiting Outreach Sequence Reference

> A canonical reference for AI-native recruiting outreach: 16 playbooks, 12 channel strategies, 16 communication types, sequence designs, template variables, and AI personalization rules.

**Built by [NinjaHire](https://ninjahire.co)** — used internally to power the NinjaHire autonomous recruiter.

This document covers the *architecture* of outreach sequences — which playbook to use, which channel combination, which communication types in what order, and what rules govern AI content generation. For the actual prompt templates and copy, see [playbooks.md](./playbooks.md).

---

## Contents

- [Canonical Playbook Catalog](#canonical-playbook-catalog)
- [Channel Strategy Library](#channel-strategy-library)
- [Communication Type Taxonomy](#communication-type-taxonomy)
- [Playbook × Channel Matrix](#playbook--channel-matrix)
- [Seed Sequences (Detailed)](#seed-sequences-detailed)
- [Template Variable Reference](#template-variable-reference)
- [AI Personalization Rules](#ai-personalization-rules)
- [Fallback & Stop Rules](#fallback--stop-rules)
- [Channel Seed Content](#channel-seed-content)

---

## Canonical Playbook Catalog

16 playbooks covering every candidate type, employment type, and audience state. Each playbook specifies aggressiveness, channels, duration, and stop conditions.

| ID | Playbook | Audience | Employment | Touches | Days | Channels | Aggressiveness | Primary CTA |
|----|----------|----------|-----------|---------|------|----------|---------------|-------------|
| PB-01 | Contract – Passive Talent | Sourced / cold | Contract | 6 | 4 | Email + SMS + AI Call | Medium-High | Open to hearing more? |
| PB-02 | Contract – Urgent Requirement | Sourced / cold | Contract | 6 | 3 | Email + SMS + AI Call | High | Are you available? |
| PB-03 | Contract-to-Hire | Sourced / cold | C2H | 5 | 5 | Email + SMS + AI Call | Medium | Open to a C2H conversation? |
| PB-04 | Full-Time – Passive Talent | Sourced / cold | Full-Time | 6 | 7 | Email + SMS + AI Call | Medium | Open to hearing what the team is building? |
| PB-05 | Hard-to-Fill Technical | Sourced / cold | Any | 7 | 8 | Email + SMS + AI Call | Medium | Worth a technical conversation? |
| PB-06 | Executive / Leadership | Sourced / cold | Full-Time | 4 | 10 | Email + Call | Low | Open to a confidential conversation? |
| PB-07 | Applicant – New Application | Applied | Any | 3 | 2 | Email + SMS + AI Call | High | Complete the next step |
| PB-08 | Applicant – Unresponsive | Applied | Any | 4 | 5 | Email + SMS | Medium | Still interested? |
| PB-09 | ATS Talent Rediscovery | ATS / known talent | Any | 5 | 6 | Email + SMS + AI Call | Medium | Open to taking another look? |
| PB-10 | Past Contractor | Known talent | Contract | 4 | 4 | Email + SMS + Call | Medium | Are you currently on assignment? |
| PB-11 | Silver Medalist | Previously interviewed | Any | 4 | 5 | Email + SMS | Low-Medium | Would you be open to reconnecting? |
| PB-12 | Talent Pool Nurture | Talent pool | Any | Recurring | Long-running | Email + SMS | Low | Stay connected |
| PB-13 | Referral / Warm Candidate | Referred / warm | Any | 3 | 4 | Email + SMS + Call | Low | Open to a quick conversation? |
| PB-14 | Location-Specific / Relocation | Sourced / cold | Any | 5 | 6 | Email + SMS | Medium | Would this location work for you? |
| PB-15 | Remote Opportunity | Sourced / cold | Any | 5 | 6 | Email + SMS + AI Call | Medium | Open to hearing more? |
| PB-16 | Previously Contacted – New Job | Known talent | Any | 4 | 5 | Email + SMS | Low-Medium | Worth revisiting? |

### Playbook Selection Guide

| Candidate State | Employment | Use |
|----------------|-----------|-----|
| Cold sourced, fast-moving contract req | Contract | PB-01 or PB-02 (urgent) |
| Cold sourced, converting contract to permanent | C2H | PB-03 |
| Cold sourced, full-time role | Full-Time | PB-04 |
| Cold sourced, rare/niche technical skills | Any | PB-05 |
| Cold sourced, VP+ or C-level | Full-Time | PB-06 |
| Just applied, first contact | Any | PB-07 |
| Applied but went silent | Any | PB-08 |
| In your ATS but hasn't engaged recently | Any | PB-09 |
| Worked with you before as a contractor | Contract | PB-10 |
| Was a finalist for a role, not selected | Any | PB-11 |
| Keeping warm, no active req | Any | PB-12 |
| Referred by someone you know | Any | PB-13 |
| Right profile, wrong location | Any | PB-14 |
| Right profile, role is remote | Any | PB-15 |
| Contacted before about a different role | Any | PB-16 |

---

## Channel Strategy Library

12 channel combination strategies. Each specifies typical motion (touch order), cadence, design rule, and stop conditions.

| ID | Strategy | Channels | Best For | Touches | Cadence | Typical Motion |
|----|----------|---------|----------|---------|---------|----------------|
| CS-01 | Email Only | Email | Fallback | 3–5 | 4–8 days | Email → Email → Email |
| CS-02 | Email + SMS | Email, SMS | Contract; FTE; Applicant | 4–6 | 4–7 days | Email → SMS → Email → SMS → Email |
| CS-03 | Email + Phone | Email, AI Phone | Contract; FTE; Applicant | 4–5 | 3–7 days | Email → Email → AI Call → Email |
| CS-04 | Email + SMS + Phone | Email, SMS, AI Phone | Contract; Applicant; ATS | 5–6 | 3–6 days | Email → SMS → Email → AI Call → SMS → Email |
| CS-05 | Email + LinkedIn | Email, LinkedIn | FTE; Executive; Hard-to-Fill | 4–6 | 6–10 days | Email → LinkedIn Connect → LinkedIn Message → Email → Call/Email |
| CS-06 | LinkedIn First | LinkedIn, Email, SMS/Phone | FTE; Executive; Hard-to-Fill | 4–6 | 6–10 days | Connect → Post-Connect → Email → SMS/Call → Email |
| CS-07 | Full Multichannel | Email, SMS, AI Phone, LinkedIn | Contract; FTE; Hard-to-Fill | 6–8 | 5–10 days | Email → LinkedIn Connect → SMS → Email/LinkedIn → AI Call → Final Email |
| CS-08 | WhatsApp Enabled | Email, WhatsApp, AI Phone | Contract; Applicant; ATS | 4–6 | 3–7 days | Email → WhatsApp → AI Call → WhatsApp → Email |
| CS-09 | WhatsApp + Email + SMS | Email, WhatsApp, SMS | Contract; Applicant | 4–5 | 3–6 days | Email → WhatsApp → Email → SMS → Final |
| CS-10 | LinkedIn + Email + Phone | LinkedIn, Email, AI/Recruiter Phone | Executive; FTE | 4–5 | 8–12 days | Connect → Email → Call → Post-Connect → Email |
| CS-11 | Phone-First Applicant | AI Phone, Email, SMS | Applicant | 3–4 | 1–2 days | Expectation Email → AI Call → SMS fallback → Email |
| CS-12 | Mobile Only | SMS, AI Phone | Contract; Applicant (fallback) | 3 | 2–4 days | SMS → AI Call → SMS |

### Channel Strategy Design Rules

| Strategy | Key Rule |
|----------|----------|
| CS-01 | Use progressively different purpose each email — no repetitive bumps |
| CS-03 | Email must establish context before an AI call — never cold-call first |
| CS-04 | Recommended default for passive contract. Avoid same-day channel pileup |
| CS-05 | Useful for professional passive talent who's less likely to respond to cold email |
| CS-06 | Connection request must optimize for acceptance, not job pitch |
| CS-07 | Coordinate touch purposes — do not duplicate content across channels same day |
| CS-08 | WhatsApp is conversational/mobile-first — do not copy email content |
| CS-09 | Never duplicate the same message across both SMS and WhatsApp |
| CS-10 | Lower frequency, higher personalization — executive motion |
| CS-11 | Always send an expectation-setting email before the AI call fires |

---

## Communication Type Taxonomy

16 distinct communication purposes. Every touch in every sequence maps to exactly one communication type, which determines its objective, content rules, and eligible channels.

| ID | Type | Purpose | Primary CTA | Eligible Channels | Typical Position |
|----|------|---------|-------------|------------------|-----------------|
| CT-01 | INTRODUCTION | Initial outreach | Low-commitment reply | Email, SMS, LinkedIn, WhatsApp | 1 |
| CT-02 | CONNECTION_REQUEST | LinkedIn connection | Accept connection | LinkedIn | 1 |
| CT-03 | POST_CONNECTION | LinkedIn follow-up after connect | Reply / hear more | LinkedIn | 2–4 |
| CT-04 | INMAIL | Direct LinkedIn outreach | Reply | LinkedIn | 1–3 |
| CT-05 | FOLLOW_UP | Follow-up (not repeating) | Reply | Email, SMS, LinkedIn, WhatsApp | 2–5 |
| CT-06 | VALUE_ADD | Add new reason to care | Reply / conversation | Email, LinkedIn | 2–4 |
| CT-07 | AVAILABILITY_CHECK | Check timing / availability | Availability answer | SMS, Email, Phone, WhatsApp | 1–5 |
| CT-08 | COMPENSATION_CHECK | Rate / salary alignment | Rate / salary answer | Phone, Email, SMS | 2–5 |
| CT-09 | AI_CALL | AI recruiting conversation | Conversation / qualified | AI Phone | 2–5 |
| CT-10 | RECRUITER_CALL | Human recruiter call | Conversation | Phone | 2–5 |
| CT-11 | VOICEMAIL | Voicemail after unanswered call | Callback / reply | Phone | 2–5 |
| CT-12 | SCREENING_INVITE | Move to screening | Start screen | Email, SMS, WhatsApp | 1–4 |
| CT-13 | SCHEDULING | Book or reschedule | Booked time | Email, SMS, WhatsApp | 1–5 |
| CT-14 | REENGAGEMENT | Known candidate reactivation | Reply | Email, SMS, LinkedIn, WhatsApp | 1–3 |
| CT-15 | FINAL_CLOSE | Close the loop / breakup | Final reply or clean stop | Email, SMS | Last |
| CT-16 | NURTURE | Talent pool maintenance | Engagement | Email, LinkedIn, WhatsApp | Recurring |

### Content Rules by Type

| Type | Rule |
|------|------|
| INTRODUCTION | Candidate relevance + concise opportunity context |
| CONNECTION_REQUEST | Minimal pitch; one reason to connect (never mention the job first) |
| POST_CONNECTION | Never repeat the connection note content |
| FOLLOW_UP | Must add context or simplify the decision — not just "checking in" |
| VALUE_ADD | Must add genuinely new information — not a restatement |
| AVAILABILITY_CHECK | Especially useful for contract; direct and brief |
| AI_CALL | Use objective + facts + boundaries — not a rigid script to read |
| REENGAGEMENT | Acknowledge prior relationship truthfully |
| FINAL_CLOSE | Explicitly final; make "not now" easy — no guilt trip |
| NURTURE | Value/content driven; low frequency; not tied to a specific req |

---

## Playbook × Channel Matrix

Cross-reference showing which channel strategy each playbook uses by default and what communication type flow it follows.

| ID | Playbook | Default Strategy | Default Motion | Communication Type Flow | Aggressiveness |
|----|----------|-----------------|---------------|------------------------|---------------|
| PB-01 | Contract – Passive | CS-04 | Email + SMS + Phone | INTRODUCTION → FOLLOW_UP → AI_CALL → AVAILABILITY_CHECK → FINAL_CLOSE | Medium-High |
| PB-02 | Contract – Urgent | CS-04 | Email + SMS + Phone | INTRODUCTION → AVAILABILITY_CHECK → AI_CALL → FOLLOW_UP → FINAL_CLOSE | High |
| PB-03 | Contract-to-Hire | CS-04 | Email + SMS + Phone | INTRODUCTION → VALUE_ADD → AI_CALL → FOLLOW_UP → FINAL_CLOSE | Medium |
| PB-04 | Full-Time Passive | CS-05 | Email + LinkedIn | INTRODUCTION → CONNECTION_REQUEST → POST_CONNECTION → VALUE_ADD → AI_CALL → FINAL_CLOSE | Medium |
| PB-05 | Hard-to-Fill Technical | CS-07 | Full Multichannel | INTRODUCTION → CONNECTION_REQUEST → VALUE_ADD → POST_CONNECTION → AI_CALL → FOLLOW_UP → FINAL_CLOSE | Medium |
| PB-06 | Executive / Leadership | CS-10 | LinkedIn + Email + Phone | CONNECTION_REQUEST → INTRODUCTION → RECRUITER_CALL → POST_CONNECTION → FINAL_CLOSE | Low |
| PB-07 | Applicant – New | CS-11 | Phone-First | SCREENING_INVITE → AI_CALL → SCHEDULING / FOLLOW_UP | High |
| PB-08 | Applicant – Unresponsive | CS-02 | Email + SMS | FOLLOW_UP → SMS FOLLOW_UP → SCHEDULING → FINAL_CLOSE | Medium |
| PB-09 | ATS Rediscovery | CS-04 | Email + SMS + Phone | REENGAGEMENT → FOLLOW_UP → AI_CALL → VALUE_ADD → FINAL_CLOSE | Medium |
| PB-10 | Past Contractor | CS-04 | Email + SMS + Phone | REENGAGEMENT → AVAILABILITY_CHECK → AI_CALL → FINAL_CLOSE | Medium |
| PB-11 | Silver Medalist | CS-05 | Email + LinkedIn | REENGAGEMENT → VALUE_ADD → FOLLOW_UP → FINAL_CLOSE | Low-Medium |
| PB-12 | Talent Pool Nurture | CS-01 | Email-led | NURTURE → NURTURE → REENGAGEMENT (when job matches) | Low |
| PB-13 | Referral / Warm | CS-03 | Email + Phone | INTRODUCTION → RECRUITER_CALL → FOLLOW_UP | Low |
| PB-14 | Location / Relocation | CS-02 | Email + SMS | INTRODUCTION → AVAILABILITY_CHECK(location) → VALUE_ADD → FINAL_CLOSE | Medium |
| PB-15 | Remote Opportunity | CS-05 | Email + LinkedIn | INTRODUCTION → CONNECTION_REQUEST → POST_CONNECTION → FOLLOW_UP → FINAL_CLOSE | Medium |
| PB-16 | Previously Contacted | CS-05 | Email + LinkedIn | REENGAGEMENT → VALUE_ADD → FOLLOW_UP → FINAL_CLOSE | Low-Medium |

---

## Seed Sequences (Detailed)

Full touch-by-touch sequences for the four highest-volume playbooks.

### PB-01: Contract – Passive Talent (6 touches, 4 days)

| Touch | Day | Time | Channel | Type | Purpose | Subject / Message | CTA | Conditional Logic |
|-------|-----|------|---------|------|---------|-------------------|-----|------------------|
| 1 | 1 | 10:00 AM | Email | INTRODUCTION | Personalized opportunity hook | `{{first_name}}, open to a {{position}} contract?` | Open to hearing more? | Suppress rate/salary line when unavailable |
| 2 | 1 | +3 hrs | SMS | INTRODUCTION | Lightweight awareness | `Hi {{first_name}}, this is {{recruiter_name}} with {{company_name}}. I sent you a note about a {{position}} contract in {{job_location}} that looks relevant to your background. Open to hearing more?` | Open to hearing more? | — |
| 3 | 2 | Morning | Email | FOLLOW_UP | Add useful role context | `Re: {{position}} opportunity` | Worth a quick conversation? | Render bullets conditionally when values exist |
| 4 | 2 | Afternoon | AI Call | AI_CALL | Recruiting conversation | *(see AI Call objective below)* | Establish interest + availability + compensation | If interested but unavailable, offer `{{reschedule_link}}` |
| 5 | 3 | Afternoon | SMS | AVAILABILITY_CHECK | Simple timing check | `Hi {{first_name}} — just checking whether the {{position}} contract might be worth a conversation. If the timing isn't right, no worries. – {{recruiter_name}}` | Is the timing right? | — |
| 6 | 4 | Morning | Email | FINAL_CLOSE | Close the loop | `Should I close this out?` | Reply if interested | Do not use fake 'bumping inbox' language |

**Touch 1 — Email Body (seed):**
```
Hi {{first_name}},

{{personalized_message_for_candidate}}

I'm working on a {{position}} opportunity in {{job_location}} that looks relevant to your background.

{{rate_salary_range}}

Not sure if you're open to contract work at the moment, but happy to share more details if the timing works.

Open to hearing more?

{{recruiter_name}}
```

**Touch 3 — Email Body (seed):**
```
Hi {{first_name}},

Wanted to follow up on the {{position}} opportunity I sent over.

{{highlight_1}}

A few details:
• Location: {{job_location}}
• Compensation: {{rate_salary_range}}
• Key focus: {{highlight_2}}

Worth a quick conversation?

{{recruiter_name}}
```

**Touch 4 — AI Call Objective:**
> Contact `{{first_name}}` regarding the `{{position}}` opportunity. Establish whether the candidate is open to contract opportunities. Briefly explain why their background appears relevant using `{{highlight_1}}`, `{{highlight_2}}`. Confirm availability and compensation expectations where appropriate. Do not pressure candidate to apply. If interested but unavailable now, offer `{{reschedule_link}}`.

**Touch 6 — Email Body (seed):**
```
Hi {{first_name}},

I'll make this my last note regarding the {{position}} opportunity.

Based on your experience with {{highlight_1}}, I thought it was worth reaching out.

If you're interested, reply here and I'll send over the details. If the timing isn't right, no worries — I'll keep you in mind for future opportunities.

{{recruiter_name}}
```

---

### PB-04: Full-Time – Passive Talent (6 touches, 7 days)

| Touch | Day | Time | Channel | Type | Purpose | CTA |
|-------|-----|------|---------|------|---------|-----|
| 1 | 1 | Morning | Email | INTRODUCTION | Create curiosity / reason to move | Open to hearing what the team is building? |
| 2 | 1–2 | — | LinkedIn | CONNECTION_REQUEST | Earn connection acceptance | Accept connection |
| 3 | 3 | — | LinkedIn | POST_CONNECTION | Introduce opportunity after connecting | Hear more |
| 4 | 4 | Morning | Email | VALUE_ADD | Add team/role specifics | Worth a conversation? |
| 5 | 6 | — | AI Call | AI_CALL | Recruiting conversation | Curiosity + conversation |
| 6 | 7 | Morning | Email | FINAL_CLOSE | Close the loop | Reply if interested |

**Touch 1 — Email Subject:** `{{first_name}} — quick question about {{position}}`

**Touch 1 — Email Body (seed):**
```
Hi {{first_name}},

{{personalized_message_for_candidate}}

We're hiring a {{position}} with {{end_client}}, and your background stood out for a couple of specific reasons.

I'm not assuming you're looking — just thought it was worth a quick note.

Open to hearing what the team is building?

{{recruiter_name}}
```

*Conditional: suppress `{{end_client}}` when client disclosure is not allowed.*

---

### PB-07: Applicant – New Application (3 touches, 2 days)

| Touch | Day | Time | Channel | Type | Purpose | CTA |
|-------|-----|------|---------|------|---------|-----|
| 1 | 1 | Immediate | Email | SCREENING_INVITE | Set expectation and move forward | Prepare for screening / reschedule |
| 2 | 1 | +x minutes | AI Call | AI_CALL | Conduct screening | Qualify / screen |
| 3 | 2 | Morning | SMS | SCHEDULING | Follow up if no-show | Reschedule |

**Touch 1 — Email Subject:** `Next step for your {{position}} application`

**Touch 1 — Email Body (seed):**
```
Hi {{first_name}},

Thanks for your interest in the {{position}} opportunity.

Based on your application, we'd like to move you to the next step.

Our recruiting agent {{agent_name}} can give you a quick call in about {{x_minutes}} minutes to discuss the role. If that timing doesn't work, you can choose another time here: {{reschedule_link}}

{{recruiter_name}}
```

*Conditional: use `{{x_minutes}}` only when an actual call is scheduled.*

**Rule:** Do not ask an applicant whether they are interested in the job they applied to — assume interest and move toward screening.

---

### PB-09: ATS Talent Rediscovery (5 touches, 6 days)

| Touch | Day | Time | Channel | Type | Purpose | CTA |
|-------|-----|------|---------|------|---------|-----|
| 1 | 1 | Morning | Email | REENGAGEMENT | Re-engage known candidate | Open to taking another look? |
| 2 | 2 | — | SMS | FOLLOW_UP | Lightweight follow-up | — |
| 3 | 3 | — | AI Call | AI_CALL | Recruiting conversation | Reconnect + qualify |
| 4 | 5 | Morning | Email | VALUE_ADD | Add new context | — |
| 5 | 6 | Morning | Email | FINAL_CLOSE | Close the loop | — |

**Touch 1 — Email Subject:** `A new {{position}} opportunity`

**Touch 1 — Email Body (seed):**
```
Hi {{first_name}},

We've connected before regarding opportunities with {{company_name}}, and I wanted to reach back out.

We're currently working on a {{position}} opportunity that looks particularly relevant to your background — specifically {{highlight_1}}.

Would you be open to taking another look?

{{recruiter_name}}
```

**Rule:** Never say "I came across your profile" for a candidate already in your ATS — you have relationship history, use it.

---

### PB-10: Past Contractor (4 touches, 4 days)

| Touch | Day | Time | Channel | Type | Purpose | CTA |
|-------|-----|------|---------|------|---------|-----|
| 1 | 1 | Morning | Email | REENGAGEMENT | Check current assignment | Current assignment / availability |
| 2 | 1–2 | — | SMS | AVAILABILITY_CHECK | Quick availability check | — |
| 3 | 2–3 | — | AI Call | AI_CALL | Warm conversation + availability | Availability + rate |
| 4 | 4 | Morning | Email | FINAL_CLOSE | Close the loop | — |

**Touch 1 — Email Body (seed):**
```
Hi {{first_name}}, it's {{recruiter_name}} from {{company_name}}.

We're working on another {{position}} engagement and I wanted to check with you before going to the broader market.

Are you currently on assignment? If you're wrapping up or will be available soon, I'd love to connect.

{{recruiter_name}}
```

**Rule:** Warm relationship — tone should reflect prior history, not cold outreach.

---

## Template Variable Reference

All variables use `{{double_curly_braces}}` syntax. Variables are resolved at runtime; missing optional variables suppress their surrounding sentence or bullet cleanly.

### Candidate Variables

| Variable | Description | Required | Notes |
|----------|-------------|----------|-------|
| `{{first_name}}` | Candidate first name | Yes | Core greeting token |
| `{{candidate_name}}` | Full candidate name | No | |
| `{{candidate_email}}` | Candidate email | No | Not needed in message body |
| `{{candidate_phone}}` | Candidate phone | No | Not needed in message body |

### Job Variables

| Variable | Description | Required | Notes |
|----------|-------------|----------|-------|
| `{{position}}` | Job / position title | Yes | Core playbook token |
| `{{job_location}}` | Job location or remote context | Yes | |
| `{{short_job_description}}` | Brief job description | No | Prefer concise content |
| `{{long_job_description}}` | Full job description | No | Never dump into outreach |
| `{{job_description_link}}` | Link to JD | No | |
| `{{rate_salary_range}}` | Contract rate or salary range | No | Suppress if unavailable |

### AI Personalization Variables

| Variable | Description | Required | Notes |
|----------|-------------|----------|-------|
| `{{personalized_message_for_candidate}}` | 1–2 evidence-based candidate-specific sentences | Recommended | Most important personalization token; avoid generic flattery |
| `{{highlight_1}}` | Strongest candidate/job fit highlight | Recommended | Evidence-based |
| `{{highlight_2}}` | Second highlight | No | Evidence-based |
| `{{highlight_3}}` | Third highlight | No | Evidence-based |
| `{{primary_skills}}` | Primary skills | No | Use as AI input, not raw list in copy |
| `{{secondary_skills}}` | Secondary skills | No | Advanced |

### Company / Sender Variables

| Variable | Description | Required | Notes |
|----------|-------------|----------|-------|
| `{{company_name}}` | Recruiting company name | Yes | |
| `{{end_client}}` | End client name | No | Respect client disclosure rules |
| `{{recruiter_name}}` | Recruiter display name | Yes | |
| `{{recruiter_email}}` | Recruiter email | No | |
| `{{recruiter_phone}}` | Recruiter phone | No | |
| `{{agent_name}}` | AI recruiting agent name | No | Use when agent is in workflow |
| `{{agent_phone_no}}` | AI agent phone number | No | |

### Action / CTA Variables

| Variable | Description | Required | Notes |
|----------|-------------|----------|-------|
| `{{video_screening_link}}` | Video screening link | No | |
| `{{reschedule_link}}` | Scheduling / rescheduling link | No | |
| `{{x_minutes}}` | Minutes until AI agent calls after email | No | Only render when call is actually scheduled |

### Compliance Variables

| Variable | Description | Required | Notes |
|----------|-------------|----------|-------|
| `{{consent_link}}` | Consent link | No | Prefer automatic append |
| `{{optout_link}}` | Opt-out link | No | Prefer automatic append |
| `{{disclaimer}}` | Required disclaimer | No | Prefer automatic append |

---

## AI Personalization Rules

12 rules that govern how an AI agent (Hanzo / any LLM) generates and renders outreach content.

| Rule ID | Category | Rule | Do | Avoid |
|---------|----------|------|-----|-------|
| AI-01 | Personalization | Evidence-based | Use concrete experience, technology, domain, project, employer, or achievement from candidate profile | "Impressive background," invented achievements, unsupported claims |
| AI-02 | Tone | No clichés | Keep messages concise, conversational, recruiter-like | "Bumping this to the top of your inbox," excessive enthusiasm, fake familiarity |
| AI-03 | CTA | First-touch commitment | For passive candidates, optimize first CTA for reply/conversation, not application | "Apply now" on a cold first touch |
| AI-04 | Contract | Contract CTA | Lead toward interest, availability, and rate | Treating contract outreach like full-time career-change messaging |
| AI-05 | Full-Time | Career-move framing | Sell the reason to consider a move and what the team is building before qualification | Immediate application request |
| AI-06 | Known Candidate | Relationship honesty | Acknowledge prior contact / ATS relationship | "I came across your profile" for known candidates |
| AI-07 | Applicant | Applicant intent | Assume interest exists and move toward screening | Asking an applicant if they're interested in the job they already applied to |
| AI-08 | Missing Variables | Conditional rendering | Remove sentences/bullets with missing optional variables cleanly | Blank tokens, empty bullets, double spacing |
| AI-09 | Client Disclosure | End-client control | Only render `{{end_client}}` when disclosure is allowed | Accidental client name disclosure |
| AI-10 | Compensation | Rate/salary control | Use `{{rate_salary_range}}` only when populated and allowed | Estimated or hallucinated compensation |
| AI-11 | AI Call | Call objective | Give voice agent objectives, facts, boundaries, and stopping behavior | Reading a long fixed script verbatim |
| AI-12 | Change Explanation | State consequence | When AI edits a playbook, summarize what changed and the effect on cadence/content | Silent AI edits |

---

## Fallback & Stop Rules

14 rules governing what happens when a channel becomes unavailable or a candidate responds. Compliance stops override all optimization.

| Rule ID | Applies To | Condition | Action | Guardrail |
|---------|-----------|-----------|--------|-----------|
| FR-01 | Any passive playbook | No email | Switch to Mobile Only or WhatsApp strategy | Do not fabricate email |
| FR-02 | Any passive playbook | No mobile phone | Use Email + LinkedIn | Redistribute timing — don't compress |
| FR-03 | Any passive playbook | No LinkedIn | Use Email + SMS + Phone or Email-only | Do not block campaign |
| FR-04 | WhatsApp strategy | WhatsApp unavailable | Replace with SMS | Do not copy WhatsApp text into SMS blindly |
| FR-05 | SMS strategy | SMS unavailable | Move SMS purpose to next email or LinkedIn touch | Do not add duplicate email bumps |
| FR-06 | Phone touch | Phone unavailable/invalid | Skip call, add value-add or availability-check touch | State consequence in UI |
| FR-07 | LinkedIn First | Connection not accepted | Continue email/mobile path; suppress post-connection message | Withdraw connection later only if configured |
| FR-08 | LinkedIn First | Connection accepted | Insert POST_CONNECTION message; suppress redundant email copy | Use connection acceptance as state change trigger |
| FR-09 | Contract Passive | Positive reply | Stop automated sequence, transition to conversation/qualification | No further cold touches |
| FR-10 | Applicant | Screen completed | Stop outreach, move to next pipeline state | No reminder after completion |
| FR-11 | Any | Negative reply / not interested | Stop campaign immediately | Record disposition where supported |
| FR-12 | Any | Opt-out | Stop all applicable outreach immediately | **Compliance stop overrides all optimization** |
| FR-13 | Any | Rate/salary missing | Suppress compensation sentence/bullet | Never invent compensation |
| FR-14 | Any | End-client cannot be disclosed | Suppress `{{end_client}}`, rewrite naturally | Never infer client from context |

---

## Channel Seed Content

Ready-to-use message seeds for each channel type. These are starting points — AI personalizes the `{{personalized_message_for_candidate}}` and `{{highlight_*}}` tokens at runtime.

### SMS — Contract Passive Introduction (CC-01)

```
Hi {{first_name}}, this is {{recruiter_name}} with {{company_name}}. I sent a note about a {{position}} contract in {{job_location}}. Open to hearing more?
```
*Constraint: one question; no JD dump; keep under character limit.*

---

### WhatsApp — Contract Passive Introduction (CC-02)

```
Hi {{first_name}}, {{recruiter_name}} here from {{company_name}}. I'm working on a {{position}} opportunity in {{job_location}} that looks relevant to your background. Would you be open to hearing more?
```
*Constraint: conversational/mobile-first; only use when workflow permits.*

---

### LinkedIn Connection Request — FTE Passive (CC-03)

```
Hi {{first_name}} — your {{highlight_1}} caught my attention. I'm recruiting for a {{position}} where that experience is relevant. Thought it would be good to connect.
```
*Constraint: hard character max from runtime; minimal pitch; never mention the job in detail on first touch.*

---

### LinkedIn Post-Connection Message — FTE Passive (CC-04)

```
Thanks for connecting, {{first_name}}. I'm working on a {{position}} opportunity, and {{highlight_1}} looks particularly relevant. Would you be open to hearing what the team is building?
```
*Constraint: do not repeat the connection request content.*

---

### LinkedIn InMail — FTE Passive (CC-05)

```
{{personalized_message_for_candidate}}

I'm recruiting for a {{position}} opportunity in {{job_location}}. Would you be open to a brief conversation about what the team is building?
```
*Constraint: candidate-specific; one CTA; more context allowed than connection note.*

---

### AI Phone Call — Contract Passive (CC-06)

**Objective (not script):**
> Contact `{{first_name}}` about `{{position}}`. Establish contract interest, availability, and compensation expectations where appropriate. Use `{{highlight_1}}`, `{{highlight_2}}`, `{{highlight_3}}` as evidence for relevance. Do not pressure candidate to apply. If interested but unavailable, offer `{{reschedule_link}}`.

*Constraint: objective + facts + boundaries — not a rigid script to read verbatim.*

---

### Recruiter Phone Call — Executive (CC-07)

**Briefing:**
> Recruiter task: call `{{first_name}}` for a discreet conversation regarding `{{position}}`. Lead with the specific relevance in `{{highlight_1}}`. Avoid a transactional screening tone. High-touch human-led motion.

---

### SMS — Applicant Screening Invite (CC-08)

```
Hi {{first_name}}, thanks for applying for {{position}}. {{agent_name}} can call you in about {{x_minutes}} minutes for a quick screening. Need another time? {{reschedule_link}}
```
*Constraint: only use `{{x_minutes}}` when call is truly scheduled.*

---

### WhatsApp — Applicant Screening Invite (CC-09)

```
Hi {{first_name}}, thanks for your interest in {{position}}. The next step is a quick conversation with {{agent_name}}. If now isn't convenient, you can choose another time here: {{reschedule_link}}
```
*Constraint: mobile-friendly; avoid email formatting conventions.*

---

## Related Resources

### In this repo
- [Playbooks →](./playbooks.md) — Prompt chains with guardrails for outreach, voice screening, candidate evaluation, and Boolean search
- [Prompt Library →](./prompts.md) — 150+ individual prompts organized by use case
- [Awesome Recruiter Tools →](./README.md) — Free tools and resources for recruiters

### Related repos
- [Autonomous Recruiter](https://github.com/ninjahire/autonomous-recruiter) — NinjaHire's MCP server that executes these 16 playbooks and 12 channel strategies end-to-end
- [HRTech Landscape](https://github.com/ninjahire/hrtech-landscape) — Job boards, ATS platforms, and VMS systems referenced in these channel strategies
- [Recruitment Taxonomy](https://github.com/ninjahire/recruitment-taxonomy) — Standard definitions for the communication types, candidate statuses, and workflow stages used in these sequences

### NinjaHire
[NinjaHire](https://ninjahire.co) is the autonomous AI recruiter that runs these exact outreach sequences — executing multi-touch email, SMS, LinkedIn, and AI phone call playbooks across staffing, MSP/VMS, and direct-hire workflows. The playbook architecture in this file is derived from NinjaHire's production system. [Book a demo →](https://calendly.com/bharatsigtia/30min)

---

**Built by [NinjaHire](https://ninjahire.co)** — Autonomous AI Recruiter for staffing teams and high-volume hiring operations.

[![NinjaHire](https://img.shields.io/badge/Maintained%20by-NinjaHire-brightgreen)](https://ninjahire.co)
