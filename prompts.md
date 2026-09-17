# AI Prompts for Recruiters

> 150+ copy-paste prompts for every stage of the recruiting workflow — job descriptions, sourcing, outreach, screening, interviews, offers, and more. Works with ChatGPT, Claude, Gemini, or any LLM.

**Curated by [NinjaHire](https://ninjahire.co)**

**Need deeper playbooks with guardrails?** → [playbooks.md](./playbooks.md) covers: outreach by channel (LinkedIn / email / SMS / phone), voice & phone screen scripts, 5-step candidate evaluation chain, and Boolean/X-ray search generator — each with channel rules, legal guardrails, and example outputs.

Replace everything in `[brackets]` with your specifics. Prompts are written to work without preamble — paste and go.

---

## Table of Contents

- [Job Descriptions](#job-descriptions)
- [Boolean Search & Sourcing](#boolean-search--sourcing)
- [Candidate Outreach](#candidate-outreach)
- [Resume Screening](#resume-screening)
- [Interview Questions & Scorecards](#interview-questions--scorecards)
- [Offer & Closing](#offer--closing)
- [Rejection & Candidate Communication](#rejection--candidate-communication)
- [Onboarding](#onboarding)
- [Business Development (Agency & Staffing)](#business-development-agency--staffing)
- [Employer Branding & Content](#employer-branding--content)
- [Reporting & Analytics](#reporting--analytics)
- [Productivity & Operations](#productivity--operations)

---

## Job Descriptions

### Write a standard job description

```
Act as a senior talent acquisition specialist. Write a compelling job description for a [job title] at a [company type/stage/size, e.g. Series B SaaS startup]. 

Include:
- 2-sentence role summary that leads with impact, not tasks
- 5–7 key responsibilities written as outcomes, not duties
- Must-have qualifications (max 5) separated from nice-to-haves
- Compensation range: [range or "competitive, DOE"]
- One paragraph on team culture and working style

Avoid: buzzwords like "rockstar," "ninja," "fast-paced," or "self-starter." Keep total length under 500 words.
```

---

### Write a technical role job description

```
Act as a technical recruiter with 10 years of experience hiring engineers. Write a job description for a [technical role, e.g. Senior Backend Engineer] at [company].

The role uses: [tech stack, e.g. Python, PostgreSQL, AWS, Kubernetes]

Include:
- What the candidate will build in their first 90 days
- The technical challenge they'll be solving (not just the tools they'll use)
- Honest seniority expectations (avoid "5+ years" if you mean "competent mid-level")
- Team structure and who they'll work with

Do not use clichés like "passion for technology" or "thrive in ambiguity."
```

---

### Write an executive/confidential role brief

```
Act as an executive search consultant. Write a confidential role brief for a [C-level/VP title, e.g. Chief Revenue Officer] search.

Context:
- Company: [brief description, revenue/ARR, stage]
- Reporting to: [CEO / Board]
- Scope: [P&L responsibility, team size, geography]
- Compensation framework: [base + equity + bonus range]

The brief should be readable in 3 minutes, communicate genuine opportunity (not hype), and be appropriate to share with a senior passive candidate who didn't apply.
```

---

### Audit a job description for bias

```
Act as a DEI recruiting specialist. Review this job description for language that may discourage qualified candidates from applying.

Flag:
- Gendered language (e.g. "aggressive," "nurturing," "dominant")
- Age-coded requirements (e.g. "digital native," "recent grad")
- Ability-coded requirements (e.g. physical demands irrelevant to role)
- Unnecessarily high credential bars (e.g. "MBA required" for a mid-level role)
- Cultural bias in "culture fit" language

For each flag: quote the original text, explain the issue, and suggest a neutral replacement.

[Paste job description here]
```

---

### Rewrite a job description to reduce barriers

```
Act as a recruiting strategist. This job description is getting low applicant volume. Rewrite it to attract more qualified candidates without lowering the bar.

Specifically:
- Remove requirements that aren't truly mandatory
- Lead with what the candidate gets, not just what they need to do
- Replace credential requirements (e.g. "degree required") with competency requirements where appropriate
- Make the first paragraph compelling enough to keep reading

[Paste job description here]
```

---

### Create two A/B versions of a job description

```
Act as a recruitment marketing specialist. Create two versions of this job description targeting different candidate profiles:

Version A: Targets actively searching candidates — clear, direct, emphasizes stability and scope
Version B: Targets passive candidates — leads with challenge, autonomy, and growth potential

Both versions must be factually identical in requirements. Vary only tone, framing, and headline.

[Paste original job description here]
```

---

### Convert an external JD to an internal mobility posting

```
Act as an HR business partner. Convert this external job description into an internal job posting for employees considering an internal move.

Adjust:
- Remove generic "about us" boilerplate (they already work here)
- Emphasize career development, cross-team exposure, and stretch opportunities
- Add context about how this role connects to the broader org strategy
- Keep the tone encouraging, not competitive

[Paste external job description here]
```

---

### Write a contractor/freelance role brief

```
Act as a staffing specialist. Write a contractor role brief for a [role, e.g. UX Researcher] engagement.

Include:
- Project scope and deliverables (what "done" looks like)
- Estimated time commitment (hours/week, duration)
- Working arrangement (remote/onsite, tools, meeting cadence)
- Rate range: [range]
- Who they'll work with and how decisions get made

Keep it under 300 words. Contractors evaluate clients as much as clients evaluate them.
```

---

### Build a job family framework

```
Act as a compensation analyst. Create a job family framework for [function, e.g. Engineering / Sales / Customer Success] with 4–5 levels.

For each level include:
- Level name (e.g. Associate, Mid, Senior, Staff, Principal)
- Scope of work and decision-making authority
- Typical years of experience (as a guide, not a gate)
- Key differentiator from the level below
- Sample titles used in the market

Format as a table.
```

---

## Boolean Search & Sourcing

### Generate Boolean strings for LinkedIn

```
Generate 5 Boolean search strings to find [job title, e.g. Senior Product Manager] candidates on LinkedIn.

Constraints:
- Must have experience with [skill/tool, e.g. B2B SaaS, 0-to-1 product development]
- Located in [city/region or "remote US"]
- Exclude: [exclusions, e.g. consultants, students, recent grads]

For each string: show the string itself, then a one-line explanation of what it prioritizes.
```

---

### Generate strings for niche or hard-to-fill roles

```
Act as a sourcing specialist. Create Boolean search strings for a [niche role, e.g. Computational Fluid Dynamics Engineer] search.

This role sits at the intersection of [domain A] and [domain B]. Candidates may not have the exact title — generate strings that find them by:
1. Exact title variations
2. Adjacent titles with transferable skills
3. Skill + company type combinations
4. GitHub / research paper / publication signals (for technical roles)

Include X-ray Google strings (site:linkedin.com/in) alongside LinkedIn Recruiter strings.
```

---

### Find candidates with transferable skills

```
I'm hiring a [target role] but the candidate pool with this exact title is too small.

List:
1. 10 adjacent job titles whose holders often have the required skills
2. 5 industries where this skill set is common but the title differs
3. 3 Boolean strings targeting these adjacent profiles

Target skills: [list the 3–5 skills that actually matter most]
```

---

### Build a candidate persona for a role

```
Act as a senior recruiter. Build a detailed ideal candidate persona for this role.

Include:
- Where they currently work (company types, not just titles)
- What their LinkedIn profile looks like (headline, activity, connections)
- What they care about in their next move (not just compensation)
- What objections they'll have to leaving their current role
- Which outreach channels they're most likely to respond to
- One thing most recruiters get wrong when approaching this profile

[Paste job description here]
```

---

### Identify companies to source from

```
I'm hiring a [job title] for [company context, e.g. a Series B fintech in NYC].

List 20 companies where I'm likely to find strong candidates. For each company include:
- Why candidates there would be a strong match (skills, culture, stage)
- Which team or department to target
- Any timing signals (recent layoffs, reorgs, funding, IPO lock-up expiry) that make now a good time to reach out

Prioritize companies where candidates are likely to be open — not just companies with the right profiles.
```

---

### Build a diversity sourcing strategy

```
Act as a diversity recruiting specialist. Create a sourcing strategy to build a more diverse candidate pipeline for a [role] in [location/remote].

Include:
- Professional associations and networks for underrepresented groups in this field
- HBCUs, HSIs, tribal colleges, and other institutions with strong programs
- Niche job boards and communities
- ERG and employee referral program adjustments
- Outreach message adjustments for this audience

Avoid: checkbox diversity tactics. Focus on genuine pipeline building.
```

---

### Build an X-ray search for GitHub or Behance

```
Create Google X-ray search strings to find [developer/designer] candidates on [GitHub / Behance / Dribbble / research databases].

Target:
- [Role, e.g. ML Engineers who have built transformer models]
- [Geography: "based in Europe" / signal: "available for hire"]

Generate 3 different string variations that approach the search from different angles (by repo topic, by language/tool, by org/company affiliation).
```

---

## Candidate Outreach

### Write a first-touch cold outreach email (under 120 words)

```
Act as a senior recruiter. Write a personalized cold outreach email for this candidate.

Candidate: [name, current title, current company]
Role I'm recruiting for: [title] at [company]
One specific thing from their background that's relevant: [detail from LinkedIn/resume]
What makes this role genuinely interesting: [1–2 sentences]

Rules:
- Under 120 words
- Lead with the specific detail about them, not about the role
- End with one low-pressure question, not a calendar link
- No clichés: "exciting opportunity," "perfect fit," "reaching out because..."
```

---

### Write a LinkedIn InMail (under 100 words)

```
Write a LinkedIn InMail under 100 words to a passive candidate for a [job title] role.

Candidate context: [title, company, one detail from their profile]
Why this role is relevant to them: [specific reason]

Tone: conversational, not sales-y. End with a soft question, not "are you open to opportunities?"
```

---

### Write a 3-touch outreach sequence

```
Act as a recruitment marketing specialist. Create a 3-message outreach sequence for a [job title] candidate who hasn't responded.

Message 1 (Day 1): Personalized first touch — specific to their background
Message 2 (Day 5): Add new value — a market insight, salary data, or team context not in message 1
Message 3 (Day 10): Graceful close — acknowledge they may not be interested, leave the door open

Each message: under 100 words. Different angle each time. Do not repeat message 1.

Candidate profile: [brief description]
Role: [title and key selling points]
```

---

### Write a passive candidate InMail (senior/executive)

```
Act as an executive recruiter. Write a LinkedIn InMail to a passive senior candidate ([title, e.g. VP of Engineering]) who is not actively looking.

Do not mention the job first. Instead:
- Open with a market observation or industry trend relevant to their domain
- Reference a specific thing from their career (publication, company exit, team they built)
- Introduce the opportunity as context, not the pitch
- Ask one genuine question that invites conversation

Total: under 150 words. This person gets 20 recruiter messages a week. Stand out.

Candidate: [name, title, company, one notable thing from their background]
```

---

### Re-engage a silver-medal candidate

```
Write an outreach message to a candidate who was a finalist for [role] [X months ago] but wasn't selected.

Context:
- Why they weren't selected then: [brief reason, e.g. went with someone with more direct experience]
- Why I'm reaching back out: [new role / different team / the role changed]
- Their name: [name]

Tone: warm, honest, respectful. Acknowledge the previous process directly. Don't pretend it didn't happen.
```

---

### Re-engage a former employee (boomerang)

```
Write an outreach message to a former employee ([name]) who left [company] [X years ago].

They left to: [reason if known, e.g. join a startup, relocate, pursue a different domain]
Why reaching out now: [what's changed at the company / new role / team they'd join]

Tone: genuine reconnection, not transactional. Reference something specific about their time at the company.
```

---

### Write a referral request to an employee

```
Write an email to [employee name] asking for referrals for our open [role] position.

Include:
- 2-sentence description of the role and ideal candidate
- 3 specific types of people who would be a great fit (to make it easy for them to think of names)
- Referral bonus details: [amount/policy]
- A shareable job link or 1-paragraph blurb they can forward

Keep it short and actionable — this person is busy.
```

---

### Write a follow-up after a career fair or event

```
Write follow-up messages for three candidates I met at [event name]:

Candidate A: Strong match — [name, role, specific thing we discussed]
Candidate B: Potential future fit — [name, background, role they'd fit]
Candidate C: Not a fit now but worth keeping warm — [name, background]

For each: one short message (under 75 words), personal to the conversation we had, with a clear next step.
```

---

### Write a "breakup" email for unresponsive candidates

```
Write a brief "breakup" email to a candidate who has not responded to 3 outreach attempts over [X weeks].

Tone: not passive-aggressive. Close the loop professionally and leave the door open genuinely.

Under 50 words. No guilt-tripping.

Candidate name: [name]
Role: [title]
```

---

## Resume Screening

### Summarize a resume against a job description

```
Summarize how this candidate's experience maps to each requirement in the job description below.

For each requirement: quote the most relevant evidence from the resume, or state clearly "no evidence found."

Do NOT score, rank, or recommend accept/reject. Only surface evidence. I'll make the judgment.

[Paste job description]

[Paste resume]
```

---

### Identify skill gaps between resume and JD

```
Identify gaps between this candidate's resume and the job description. 

For each gap: 
- State what's required vs. what's present
- Flag whether it's a hard gap (skill/experience absent) or a soft gap (less depth than ideal)
- Note any evidence that the gap might be bridgeable (adjacent experience, transferable skill)

[Paste job description]

[Paste resume]
```

---

### Extract structured data from a resume

```
Extract the following from this resume as structured JSON:

{
  "name": "",
  "current_title": "",
  "current_company": "",
  "years_total_experience": 0,
  "skills": [],
  "work_history": [{"company": "", "title": "", "start": "", "end": "", "key_accomplishments": []}],
  "education": [{"school": "", "degree": "", "field": "", "year": 0}],
  "certifications": []
}

[Paste resume]
```

---

### Create a resume screening checklist for a role

```
Create a resume screening checklist for a [job title] position.

Format as a table with three columns:
- Criterion
- Must-Have or Nice-to-Have
- How to spot it on a resume (what to look for)

Include 8–12 criteria. Prioritize things that are visible on a resume and actually predictive of success, not proxies like university prestige.
```

---

### Score and compare multiple candidates

```
Compare these [X] candidates for the [job title] role. For each candidate:

1. Score 1–10 on: technical fit, scope/seniority match, industry relevance
2. One sentence on their biggest strength for this role
3. One sentence on their biggest risk or gap
4. Overall recommendation: Advance / Hold / Pass

Be direct. Use evidence from the resumes, not generic observations.

[Paste job description]

[Paste candidate 1 resume]
[Paste candidate 2 resume]
...
```

---

### Generate interview questions from a resume

```
Review this candidate's resume against the job description. Identify 3 areas where their experience is thin, ambiguous, or worth probing deeper.

For each area: write 2 interview questions that would surface whether the gap is real or just a resume artifact.

[Paste job description]
[Paste resume]
```

---

## Interview Questions & Scorecards

### Generate behavioral interview questions

```
Generate 8 behavioral interview questions for a [job title] using the STAR format.

Cover these competencies: [list 4–5, e.g. stakeholder management, ambiguity tolerance, technical decision-making, cross-functional influence]

For each question:
- The question itself
- A follow-up probe
- What a strong answer sounds like (2–3 bullets)
- A red flag answer (1–2 bullets)
```

---

### Generate technical interview questions

```
Act as a [domain] expert and hiring manager. Create a technical interview question set for a [role] candidate.

Include:
- 3 conceptual questions (assess understanding of fundamentals)
- 2 scenario questions (apply knowledge to realistic situations)
- 1 "how would you approach" question (assess problem-solving process, not just answer)

For each question: include the correct answer or key elements of a strong response.

Focus area: [specific skills, e.g. distributed systems, financial modeling, growth marketing]
```

---

### Create a case study interview

```
Act as a hiring manager. Design a 45-minute case study interview for a [role, e.g. Product Manager / Strategy / Operations] candidate.

The case should:
- Mirror a real problem this role would face at [company type]
- Be solvable with reasonable assumptions (no trick answers)
- Test: [skills you want to assess, e.g. structuring ambiguity, prioritization, quantitative reasoning]

Include:
- The case prompt (candidate-facing)
- Interviewer guide (what to look for at each stage)
- Follow-up questions to go deeper
- Evaluation rubric (what separates a 1 from a 4)
```

---

### Create values-based interview questions

```
Create 6 interview questions that assess alignment with these company values:
[list 3–4 values, e.g. "customer obsession," "bias for action," "intellectual honesty"]

Rules:
- Behavioral format ("Tell me about a time...") — no hypotheticals
- Avoid leading language (don't telegraph the desired answer)
- Each question should surface a genuine story, not a rehearsed answer
- Include what a green flag and red flag response looks like for each
```

---

### Build a structured interview scorecard

```
Create a structured interview scorecard for evaluating [job title] candidates.

Include 6–8 competencies. For each:
- Competency name and definition (1 sentence)
- Rating scale 1–4 with behavioral descriptions at each level
- 2 interview questions that generate evidence for this competency

Format as a table: Competency | 1 (Below) | 2 (Meets) | 3 (Exceeds) | 4 (Exceptional)
```

---

### Write an interviewer briefing document

```
Create a 1-page interviewer briefing document for a panel interview for [role].

Panelists:
- [Interviewer 1] — assessing: [competency]
- [Interviewer 2] — assessing: [competency]
- [Interviewer 3] — assessing: [competency]

For each panelist include:
- Their assigned competency with a definition
- 2 recommended questions
- What to note (green flags, red flags)
- A reminder about legally compliant vs. off-limits questions

Keep to 1 page. They have 5 minutes to read this before the interview.
```

---

### Review interview questions for legal compliance

```
Review these interview questions and flag any that are legally risky in US hiring (or [country] if specified).

For each flagged question:
- Quote the question
- Explain why it's problematic (what protected class it may violate)
- Suggest a compliant replacement that assesses the underlying concern

[Paste list of interview questions]
```

---

### Synthesize post-interview feedback

```
Act as a recruiting coordinator. Synthesize these interview panel notes into a structured debrief summary.

Include:
- Overall recommendation (Hire / No Hire / More Info Needed)
- Key strengths with supporting evidence from interviews
- Key concerns with supporting evidence
- Competency-by-competency summary
- Any conflicting signals between panelists and how to resolve

[Paste interviewer notes / feedback]
```

---

### Generate reference check questions

```
Create 10 reference check questions for a candidate being considered for [job title].

Questions should:
- Assess actual performance, not just whether the person was liked
- Surface the candidate's strengths and development areas
- Ask about situations relevant to this specific role's challenges
- Include one question about their management style (if applicable)
- Close with: "Is there anything else I should know?" and "Would you rehire this person?"

Avoid: generic questions that get generic answers.
```

---

## Offer & Closing

### Draft an offer letter

```
Act as an HR specialist. Draft a formal offer letter for:

Candidate name: [name]
Role: [title]
Department: [department]
Reports to: [manager name/title]
Start date: [date]
Base salary: [$X / year or hour]
Bonus target: [X% / $X]
Equity: [X shares/options, vesting schedule]
Benefits: [brief summary or "standard package per employee handbook"]
Contingencies: [background check, reference checks, work authorization]

Tone: warm and professional. This is their first official touchpoint as a new hire.
```

---

### Prepare for a verbal offer call

```
Prepare me for a verbal offer call with [candidate name] for the [role] position.

Compensation I'm extending: [details]
What I know about their current situation: [current salary if known, competing offers if any]
Their likely concerns: [list 1–3]

Provide:
- Opening script (first 60 seconds)
- How to present the compensation package positively
- Talk track for each anticipated concern
- How to handle "can I have a few days to think?"
- Escalation guidance if they push back on salary
```

---

### Handle a competing offer

```
Act as a recruiting closer. The candidate for [role] has received a competing offer from [Company X] for [$ amount / package details if known].

Our offer: [details]

Help me prepare a response that:
- Acknowledges the competing offer without panic
- Highlights our genuine differentiators (not just spin)
- Creates appropriate urgency without pressure tactics
- Gives them the right questions to ask themselves when comparing offers

Talking points only — I'll make it conversational.
```

---

### Handle a counter-offer from their current employer

```
Act as an experienced recruiter. A candidate just told me their current employer counter-offered.

Their current offer: [details]
Our offer: [details]
Counter from current employer: [details if known]

Prepare me for the conversation:
- Statistics/context on how counter-offers usually play out (briefly)
- Questions to help them think clearly (not manipulate them)
- What factors beyond compensation they should weigh
- How to respect their decision while keeping the door open

I want to help them make the right decision, not just win the placement.
```

---

### Write a sign-on bonus justification

```
Act as a compensation analyst. Write a business case for approving a sign-on bonus of [$X] for [candidate name] for the [role] position.

Context:
- Their current unvested equity/bonus being forfeited: [$X or unknown]
- Market comp for this role: [range]
- Our offer vs. market: [at/below/above]
- Strategic importance of this hire: [1–2 sentences]

Address: total cost of hire, expected tenure, ROI justification, and clawback terms recommended.
```

---

## Rejection & Candidate Communication

### Write an empathetic rejection email (post-application)

```
Write a rejection email for a candidate who applied for [role] but did not make it to the phone screen.

Tone: warm, brief, genuine. Do not use "we received a high volume of applications" language — everyone knows it means nothing.

Include:
- Genuine acknowledgment of their application
- One honest, non-generic reason (if possible)
- Encouragement to apply again if appropriate

Under 100 words.
```

---

### Write a rejection email (post-final interview)

```
Act as a recruiter. Write a rejection email for [candidate name] who reached the final interview stage for [role] but was not selected.

Context:
- Why they weren't selected: [brief, honest reason — e.g. "the other finalist had more direct experience in X"]
- Genuine positive: [1 specific thing they did well]

Do:
- Be honest and specific (candidates who got to finals deserve real feedback)
- Leave the door genuinely open for future roles
- Not use boilerplate ("we'll keep your resume on file")

Under 150 words.
```

---

### Write a process delay update

```
Write a short, honest email to [candidate name] letting them know there's a delay in the hiring process for [role].

New timeline: [expected decision date]
Reason (if shareable): [brief reason or "internal scheduling"]

Do: set a specific new expectation, not "soon" or "a few weeks."
Don't: apologize excessively or over-explain.

Under 75 words.
```

---

### Write a graceful response to a candidate who declined

```
Write a response to [candidate name] who declined our offer for [role].

Their reason (if given): [reason]

Tone: genuinely gracious, not bitter. Keep the relationship warm. If the reason is addressable, acknowledge it briefly — don't re-pitch the role unless they've signaled openness.

Under 75 words.
```

---

### Write application confirmation auto-reply

```
Write an automated application confirmation email for candidates who apply to any role at [company].

Include:
- Confirmation of receipt
- Honest timeline for when they'll hear back: [X business days]
- What the next steps look like
- One genuine human touch that reflects company culture

Avoid: corporate tone, over-promising, vague timelines like "we'll be in touch."
```

---

## Onboarding

### Write a 30-60-90 day onboarding plan

```
Create a 90-day onboarding plan for a new [job title] joining [team/company].

Structure:
- Days 1–7: Orientation, setup, relationship-building, listening mode
- Days 8–30: Shadow, learn, contribute to ongoing work, identify quick wins
- Days 31–60: Take ownership of [specific deliverables], build credibility
- Days 61–90: Independent work, first performance conversation, set 6-month goals

Include: who they meet with each week, key documents to read, one milestone per phase.

Keep it practical — this should be a real schedule, not a principles list.
```

---

### Write a pre-start welcome email

```
Write a welcome email to [new hire name] who starts as [role] on [start date].

Include:
- Genuine excitement about them joining (1–2 specific sentences about why you're glad it's them)
- First-day logistics: [time to arrive / Zoom link / who to ask for]
- Any prep they can do (or explicitly say "nothing — just show up fresh")
- Who their buddy/onboarding contact is

Tone: warm, specific, not corporate. Under 200 words.
```

---

### Build a first-week schedule

```
Create a Monday–Friday first-week schedule for a new [role] starting at [company].

For each day include:
- Morning block (what they're doing)
- Afternoon block
- Who they're meeting and why
- What they should know or have access to by end of day

Balance: enough structure that they're not lost, enough space that they can absorb. Don't pack every hour.
```

---

## Business Development (Agency & Staffing)

### Research a prospect before a BD call

```
Act as a recruitment business development consultant. Prepare me for a BD call with [company name] in the [industry] sector.

Provide:
- Company overview (stage, size, revenue if public, recent news)
- Hiring signals: open roles, Glassdoor trends, recent headcount changes
- Who I should be speaking with (title, why they're the right contact)
- 3 pain points this company likely has that my firm can solve
- 2 questions to ask that position me as a strategic advisor, not a vendor

I want to walk in knowing more about their talent situation than they expect.
```

---

### Write a BD cold email that doesn't sound like a cold email

```
Write a cold email to a hiring manager at [company] introducing my recruiting services.

Rules:
- No "I wanted to reach out" / "I hope this finds you well" / "excited to connect"
- Lead with a specific observation about their company (hiring trend, open role, news)
- One sentence on what I do
- One low-pressure ask

Under 100 words. If I could send 50 of these, would I? If not, it's too long.

My firm specializes in: [your niche, e.g. fintech engineering, healthcare staffing, legal]
```

---

### Handle a common BD objection

```
A prospect just said: "[exact objection, e.g. 'We have a preferred supplier list' / 'We handle recruiting in-house' / 'Your fees are too high']"

Help me respond in a way that:
- Doesn't get defensive
- Acknowledges their position genuinely
- Opens a door to further conversation without being pushy
- Feels like something a confident consultant would say, not a salesperson trying to save the deal

Give me 2–3 different response options with different approaches.
```

---

### Analyze a company earnings call or announcement for hiring signals

```
Extract every signal from this text that implies a hiring need, headcount change, or recruitment opportunity.

For each signal:
- Quote the relevant text
- Explain the implied hiring need
- Suggest the most likely roles affected
- Rate the strength of the signal (Strong / Moderate / Weak)

[Paste earnings call transcript, press release, or company announcement]
```

---

### Build a 30-day BD plan

```
Create a practical 30-day business development plan for a recruiter specializing in [sector/role type].

Week 1: Research and target list building
Week 2: Initial outreach
Week 3: Follow-up and first meetings
Week 4: Proposals and pipeline review

Include: daily activity targets, channels to use, how to prioritize which companies to approach first.

Current pipeline: [brief description or "starting from scratch"]
```

---

### Stress-test a job brief before starting a search

```
Act as a skeptical senior recruiter reviewing this job brief before accepting the assignment.

Identify:
- Any contradictions between requirements (e.g. "startup experience" + "Fortune 500 company")
- Requirements that will eliminate 95%+ of candidates unnecessarily
- Compensation range vs. market reality
- Red flags about the role, team, or company that could make it hard to fill
- Questions I should ask the client before starting

[Paste job brief]
```

---

## Employer Branding & Content

### Write an EVP pitch for a specific audience

```
Write a compelling Employer Value Proposition (EVP) pitch for attracting [candidate type, e.g. senior engineers / recent graduates / healthcare workers] to [company].

The EVP should be:
- Specific enough to be credible (not "great culture and competitive pay")
- Differentiated from competitors in our space
- 2 paragraphs max

Honest differentiators we can claim: [list 2–3 genuine things that make working here different]
```

---

### Generate 30 LinkedIn content ideas for a recruiter

```
Suggest 30 LinkedIn post ideas for a recruiter specializing in [sector].

Mix of:
- Market insights and salary data
- Behind-the-scenes of recruiting
- Candidate advice
- Hiring manager advice
- Opinion/takes on industry trends
- Success stories (anonymized)
- Myths/misconceptions in [sector] hiring

Format: one-line idea per post. I'll write the posts myself.
```

---

### Write a LinkedIn post announcing a role

```
Write 3 versions of a LinkedIn post announcing we're hiring a [role] at [company].

Version 1: Conversational — first-person, feels like a real recruiter talking
Version 2: Candidate-first — leads with what makes this role interesting to do
Version 3: Social proof — leads with the team, growth, or company milestone

Each post: under 150 words. Include a call to action. No hashtag spam.
```

---

### Write a Glassdoor review response

```
Write a professional response to this Glassdoor review.

Review: [paste review]

Tone: genuine, not defensive, not corporate PR. Acknowledge the feedback directly. If the concern is legitimate, say so. If it's not representative, you can note that without dismissing the reviewer.

Under 100 words.
```

---

### Build a 90-day LinkedIn content strategy

```
Act as a personal branding expert. Create a 90-day LinkedIn content strategy for a recruiter specializing in [sector].

Include:
- Weekly posting cadence (how many posts, what types)
- Month 1 theme (building credibility / introducing expertise)
- Month 2 theme (demonstrating market knowledge)
- Month 3 theme (community building / inbound generation)
- 10 specific post ideas to start with

Goal: generate inbound leads from hiring managers and candidates without being spammy.
```

---

## Reporting & Analytics

### Design a weekly recruiting dashboard

```
Act as a recruiting analytics specialist. Design a weekly recruiting dashboard for a [company size/type, e.g. Series B startup / enterprise company].

For each metric include:
- Metric name
- Why it matters (not just what it is)
- How to calculate it
- Healthy benchmark range (if known)

Cover: pipeline health, time-to-fill, time-to-hire, source of hire, offer acceptance rate, interview-to-offer rate, and pipeline diversity.

Format as a table.
```

---

### Write a quarterly recruiting report for leadership

```
Act as a Head of Talent Acquisition. Write a quarterly recruiting report for the leadership team for Q[X] [year].

Data provided: [paste your data or describe it]

Structure:
- Executive summary (3 bullets: what went well, what didn't, what we're changing)
- Volume: headcount hired vs. target
- Quality: time-to-fill, offer acceptance rate, 90-day retention of new hires
- Efficiency: cost-per-hire, recruiter capacity
- Pipeline diversity metrics
- Q[X+1] plan and resource needs

Tone: direct and data-led. Leadership doesn't need narrative filler.
```

---

### Analyze pipeline drop-off

```
Analyze this recruiting funnel data. Identify:
1. Which stage has the highest drop-off rate and why (based on the numbers)
2. Whether the drop-off indicates a sourcing problem, screening problem, or process problem
3. The 2–3 highest-leverage interventions to improve conversion
4. Any benchmarks I should compare against

[Paste funnel data: e.g. applications → screen → interview → offer → accept]
```

---

### Calculate and analyze cost-per-hire

```
Act as a recruiting operations analyst. Calculate our cost-per-hire for [time period] and identify where money is being wasted.

Data: [paste spend breakdown: agency fees, job boards, internal recruiter time, tools, referral bonuses]
Hires made: [number]

Compare against SHRM benchmarks. Flag any spend category that seems high relative to hires generated. Recommend where to reallocate budget.
```

---

## Productivity & Operations

### Plan your day like a top recruiter

```
Act as a recruitment agency manager. Based on my current situation, build me a prioritized day plan.

My open roles: [list with urgency/stage]
Candidates in active process: [list with status]
Client meetings/calls today: [list]
Biggest bottleneck right now: [describe]

Output: time-blocked schedule that prioritizes revenue-generating activities. Flag anything I should delegate or drop.
```

---

### Turn messy meeting notes into action items

```
Review these meeting notes and produce:
1. A 3-bullet summary of what was decided
2. A list of action items with owner and due date
3. Any open questions that need follow-up

[Paste raw meeting notes]
```

---

### Push back on unrealistic hiring requirements

```
Help me draft a message to [hiring manager name] about unrealistic requirements for the [role] position.

The problem: [e.g. "They want 10 years of experience in a technology that's 4 years old" / "The salary is $30k below market for this profile" / "They want 6 'must-have' skills that almost no candidate has in combination"]

Tone: professional, data-led, collaborative — not adversarial. My goal is to get to a realistic brief, not win an argument.
```

---

### Write a weekly hiring update to a hiring manager

```
Write a concise weekly hiring update for [hiring manager name] for the [role] search.

Cover:
- Candidates in active process (stage, status, expected next step)
- New candidates sourced this week (brief description)
- Any blockers or decisions needed from them
- Expected timeline to next milestone

Under 200 words. No fluff. Hiring managers want to know what's happening and what they need to do.
```

---

### Create a hiring manager intake questionnaire

```
Act as a senior recruiter. Create an intake meeting questionnaire for a new [role] requisition.

Cover:
- Why this role is open and why now
- What success looks like at 6 months and 12 months
- The dealbreaker skills/experiences (max 3)
- Team dynamics and working style
- Compensation flexibility and approval process
- Interview panel and process they want to run
- Timeline and urgency

Format as questions I'll ask the hiring manager, not a form they fill out.
```

---

### Estimate a salary range

```
Based on the following context, estimate a competitive salary range for this role:

Role: [title]
Location: [city/remote]
Company stage: [startup / growth / enterprise]
Industry: [industry]
Seniority: [level]

Provide:
- Realistic range (25th–75th percentile)
- Top of market for a unicorn candidate
- Factors that would push toward higher or lower end

Acknowledge if your data for this specific market may be limited.
```

---

### Run a weekly business review

```
Act as my weekly accountability coach. Based on this week's activity, give me:

1. A summary of what I accomplished (placements, submissions, BD calls, new roles signed)
2. What's trending up vs. down in my pipeline
3. The biggest risk in my pipeline right now
4. One thing I should do differently next week
5. The single most important activity for next week

[Paste weekly activity summary / CRM data]
```

---

## Tips for Better Prompting

**Be specific, not verbose.** "Write a job description for a Product Manager at a Series B fintech in NYC, targeting senior candidates with payments experience" produces better output than a 500-word background.

**Give it a role.** Starting with "Act as a [relevant expert]" improves output quality significantly — it sets the frame for the model.

**Set constraints.** Word limits, tone restrictions ("no clichés"), and format requirements ("as a table") reduce editing time.

**Iterate, don't start over.** After the first output, follow up with: "Make the opening stronger," "Cut 30%," "Change the tone to be more conversational." Treat it like editing, not a one-shot task.

**Tool selection:**
- **Claude** — best for long documents, nuanced tone, reasoning through complex candidate comparisons
- **ChatGPT / GPT-4o** — fast, good for structured outputs and templates
- **Gemini** — best when you're working inside Gmail, Docs, or Google Sheets
- **Perplexity** — best for market research, salary data, and anything that needs cited sources

---

## Related Resources

- [Awesome Recruiter Tools — Main List](./README.md)
- [Autonomous Recruiter](https://github.com/ninjahire/autonomous-recruiter) — Run AI recruiting workflows end-to-end with MCP
- [HRTech Landscape](https://github.com/ninjahire/hrtech-landscape) — 1,500+ HR technology vendors
- [NinjaHire](https://ninjahire.co) — AI recruiter that executes these workflows autonomously

---

**Curated by [NinjaHire](https://ninjahire.co)** — Autonomous AI Recruiter for staffing teams and high-volume hiring operations.

[![NinjaHire](https://img.shields.io/badge/Maintained%20by-NinjaHire-brightgreen)](https://ninjahire.co)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](http://makeapullrequest.com)
