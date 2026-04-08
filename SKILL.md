---
name: elder-factcheck
description: Review links, screenshots, pasted text, or article summaries shared by an older family member. Classify the content, assess credibility and manipulation risk, optionally verify important claims with trustworthy sources, and produce a gentle reply the user can send back.
version: 2
tags:
  - fact-checking
  - misinformation
  - family-communication
  - elder-care
  - article-review
license: MIT
---

# Elder FactCheck

## Purpose

`elder-factcheck` helps users review content shared by an older family member, especially public-account articles, screenshots, forwarded warnings, health tips, policy claims, and emotionally manipulative essays.

This skill has two goals:

1. assess the quality and credibility of the content
2. help the user reply in a respectful, dignity-preserving way

This is a family communication skill with a fact-checking core.

## When To Use

Use this skill when the user:

- explicitly asks to use `elder-factcheck`
- shares a link, screenshot, pasted article, or summary and asks whether it is trustworthy
- says the content came from a parent, grandparent, or older relative
- wants help replying to a family elder about suspicious content

Do not use this skill as a substitute for:

- emergency medical care
- legal advice
- investment advice
- urgent official policy interpretation without confirmation from authoritative sources

## Core Principles

- Protect dignity: do not mock or shame the elder family member.
- Preserve agency: provide evidence and context, not orders.
- Prefer calm over confrontation: avoid blunt accusations unless evidence is overwhelming.
- Be honest about uncertainty: if access or verification is limited, say so.
- Prefer authoritative or primary sources for factual checks.

## Accepted Inputs

This skill can work with:

- article links
- pasted text
- screenshots or screenshot transcription
- user summaries of the content
- quoted claims from chat messages

If direct access to the source fails, continue with the best available material and lower confidence accordingly.

## Conversation State

Maintain a lightweight preference for the family member the user is replying to.

Supported targets:

- `grandmother`
- `grandfather`
- `mother`
- `father`
- `other`

Rules:

- if the user names the target person, use that
- otherwise reuse the last target person if known
- otherwise default to `grandmother`
- if the user changes the target person later, update the preference

Tone mapping:

- `grandmother`: warm, soft, caring
- `grandfather`: respectful, steady, concise
- `mother`: affectionate, reassuring
- `father`: relaxed, rational, direct
- `other`: adapt to the relationship the user gives

## Content Categories

Assign one primary category and, if useful, one secondary category.

### 1. Health And Wellness

Examples:

- miracle remedies
- diet restrictions
- anti-medicine claims
- exaggerated prevention advice

Typical risks:

- pseudoscience
- unsafe self-treatment
- fear-driven persuasion

### 2. Politics And Public Policy

Examples:

- "new national policy"
- "important central government notice"
- "leaders already announced this"

Typical risks:

- fabricated policy claims
- misleading interpretation
- unofficial reposts posing as official announcements

### 3. Finance And Consumer Safety

Examples:

- pension updates
- bank rule changes
- guaranteed returns
- payment and fraud warnings

Typical risks:

- scams
- false urgency
- harmful financial misinformation

### 4. Social Events And Breaking News

Examples:

- local incidents
- public safety warnings
- emergency notices
- celebrity scandals presented as breaking news

Typical risks:

- old stories reshared as new
- fake screenshots
- missing context

### 5. Emotion, Relationships, And Aging

Examples:

- "children must read this"
- "people in old age should understand this"
- guilt-heavy family advice

Typical risks:

- emotional pressure
- absolutist framing
- moral blackmail

### 6. Life Advice And Conduct

Examples:

- "never do this after 60"
- "wise people always avoid that"

Typical risks:

- overgeneralization
- false certainty
- anxiety farming

## Evaluation Framework

Always assess the content across these five dimensions:

### 1. Source Reliability

Ask:

- who published this?
- is the source official, expert, or established?
- does it cite a real origin?

### 2. Factual Accuracy

Ask:

- are the main claims specific and checkable?
- can dates, names, numbers, and institutions be verified?
- is old information being presented as current?

### 3. Bias And Framing Risk

Ask:

- is the piece one-sided or absolute?
- does it generalize from anecdotes?
- does it hide uncertainty?

### 4. Emotional Manipulation Risk

Ask:

- does it use fear, guilt, anger, or urgency?
- does it push phrases like "must read" or "share immediately"?

### 5. Incentive Or Hidden Agenda Risk

Ask:

- is it selling, collecting leads, or driving traffic?
- is it encouraging follows, purchases, or reposts for unclear reasons?

Use `Low`, `Medium`, or `High`.

Direction matters:

- `Source Reliability` and `Factual Accuracy`: `High` is good
- the three risk dimensions: `High` means higher risk

## Verification Rules

### Verification Is Required For

- health and medical claims
- public policy claims
- finance and banking claims
- public safety warnings
- breaking-news style claims
- celebrity or public-figure claims presented as facts

### Verification Is Optional But Helpful For

- life advice
- relationship essays
- opinion-heavy writing

In those cases, focus more on framing quality, extremeness, and emotional manipulation.

### Preferred Source Hierarchy

Prefer:

1. official institutions, regulators, hospitals, or government sources
2. established reporting with clear sourcing
3. reputable professional or expert sources
4. established debunking platforms

Avoid treating low-credibility reposts as evidence.

Example sources:

- China Internet Joint Rumor Refutation Platform
- Xinhua
- People's Daily
- CCTV News
- State Council and ministry websites
- CSRC and official bank websites
- DingXiang Doctor
- Tencent debunking channels
- verified official accounts or official studios for celebrity claims

If reliable verification is unavailable, say so explicitly.

## Execution Flow

### Step 0. Resolve The Target Person

- use the stated target person if given
- otherwise reuse the last one
- otherwise default to `grandmother`

### Step 1. Gather The Content

Try to read the original material.

If direct access fails:

- use the pasted excerpt, screenshot text, or user summary
- ask for more content only if necessary
- continue with limited confidence if enough substance is already available

### Step 2. Classify The Content

Assign a primary category and optional secondary category.

### Step 3. Summarize The Core Claims

Extract up to 3 concise, checkable claims or takeaways.

### Step 4. Perform Initial Assessment

Rate all five dimensions and note obvious warning signs.

### Step 5. Verify The Most Consequential Claims

Prioritize claims involving:

- physical safety
- money
- official rules
- time-sensitive public information

### Step 6. Reach A Conclusion

Choose one:

- `High-Risk Misinformation`
- `Low-Quality Or Misleading`
- `Ordinary Content`
- `High-Quality Content`

### Step 7. Draft A Respectful Reply

Write a natural reply that:

- acknowledges the elder's concern or good intention
- avoids humiliation
- mentions the review in plain language
- points toward safer or more reliable information when useful

## Reply Strategy

Universal guidance:

- do not open with "This is fake"
- prefer "I checked this a little" over "You were fooled"
- acknowledge that the elder likely shared it out of care
- give them a graceful exit
- if the content is mixed, separate what is reasonable from what is misleading

## Output Format

Use this structure unless the user asks for a shorter answer.

```md
## Elder FactCheck Review

**Target Person:** grandmother / grandfather / mother / father / other

**Content Type:** primary category
**Secondary Type:** optional

**Core Claims**
- claim 1
- claim 2
- claim 3

**Assessment**
- Source Reliability: Low / Medium / High
- Factual Accuracy: Low / Medium / High
- Bias And Framing Risk: Low / Medium / High
- Emotional Manipulation Risk: Low / Medium / High
- Incentive Or Hidden Agenda Risk: Low / Medium / High

**Conclusion:** High-Risk Misinformation | Low-Quality Or Misleading | Ordinary Content | High-Quality Content

**Why**
- short reason 1
- short reason 2
- short reason 3

**Verification**
- checked source or claim 1
- checked source or claim 2
- if verification was limited, say so clearly

**Suggested Reply**
<a short, natural-language message adapted to the target person>
```

If evidence is weak or access is partial, add:

`Confidence: Limited, because the original content could not be fully accessed or independently verified.`

## Safety And Boundaries

- Do not replace doctors, lawyers, banks, regulators, or official agencies.
- For health claims with treatment implications, urge confirmation from a qualified doctor.
- For money-related claims, urge confirmation from the official bank or regulator.
- For policy claims, prefer the official publication over reposts and commentary.
- If the user asks for a mocking or humiliating reply, refuse that tone and offer a respectful alternative.

## Failure Handling

If content cannot be fully accessed or verified:

- state what is unavailable
- provide a partial review based on available material
- lower confidence
- avoid strong factual conclusions unless clearly supported

If the content is satire, personal storytelling, or mostly opinion:

- do not overstate it as misinformation
- focus on framing, emotional pull, and the difference between anecdote and evidence

## Success Standard

A strong response should help the user:

- understand what the content is actually claiming
- see whether the claims are trustworthy
- notice manipulation or low-quality framing
- reply to the elder family member without damaging the relationship
