---
name: design-conference-session
description: Design and challenge a conference-ready technical session from a rough idea, including session level (100/200/300), positioning, titles, CFP abstract, target audience, prerequisites, learning outcomes, story arc, demo plan, attendee resources, QR code plan, and speaker preparation checklist. Use when a speaker wants to develop, improve, evaluate, or prepare a conference or community-session idea.
---

# Design Conference Session

Turn a rough technical idea into a compelling, practical conference session.

The goal is not merely to produce a title and abstract. Help the speaker find the strongest story, identify what will make the session valuable to the audience, and design a realistic session that can be delivered effectively.

## When to use this skill

Use this skill when the user wants to:

- turn a technical idea into a conference or community session
- prepare a conference CFP submission
- improve or evaluate an existing session idea
- generate or refine a title and abstract
- determine whether a session is 100, 200, or 300 level
- identify prerequisites and learning outcomes
- structure a technical presentation
- turn an existing demo into a conference talk
- design a live demo
- plan attendee resources and QR codes
- create a speaker preparation plan
- challenge whether an idea is strong enough for a conference session

Typical requests include:

- "Help me design a conference session about..."
- "Turn this idea into a conference talk."
- "Help me submit this to a CFP."
- "Create a 45-minute technical session about..."
- "I have this demo. How can I turn it into a talk?"
- "Improve my session abstract."
- "Is this really a 300-level session?"
- "How should I structure this presentation?"
- "What resources and QR codes should I prepare?"

## How to do it

### 1. Understand the session idea

Identify from the user's request where available:

- topic
- intended audience
- audience experience level
- requested session level, if provided
- session duration
- technologies involved
- problem being solved
- whether the session includes a demo
- conference or event, if known
- prerequisite knowledge or technologies
- supporting resources that may be shared
- what the speaker wants attendees to remember or do afterwards

If information is missing, make reasonable assumptions when possible and clearly label them. Do not block progress unnecessarily.

### 2. Challenge the idea

Determine whether the idea currently describes:

- a technology
- a product demonstration
- a tutorial
- an architecture
- a problem and solution
- an experiment or lesson learned
- or a genuine conference story

If the idea is primarily a product feature or generic tutorial, strengthen it by identifying the problem, tension, architecture decision, experiment, unexpected result, trade-off, or practical outcome that gives the audience a reason to care.

Do not automatically praise the idea.

Identify when the proposed scope is:

- too broad
- too narrow
- too product-focused
- missing a meaningful audience problem
- unlikely to fit the available session duration
- dependent on a demo that is too risky or complex

### 3. Define the session promise

State clearly:

- who the session is for
- what problem it addresses
- what makes it interesting
- what attendees should be able to understand or do afterwards

The promise should describe attendee value, not merely the technologies or features being demonstrated.

### 4. Determine the appropriate session level

Classify the proposed session as:

- 100 - Beginner / Introductory
- 200 - Intermediate
- 300 - Advanced

Base the recommendation on expected attendee knowledge and the actual technical depth of the proposed content.

#### 100 - Beginner / Introductory

- assume limited prior knowledge
- explain terminology and core concepts
- prioritise foundations and accessible demonstrations
- avoid unnecessary architectural complexity
- establish confidence with the platform or topic

#### 200 - Intermediate

- assume familiarity with the underlying platform or technology
- focus on implementation patterns and practical decisions
- include meaningful configuration, architecture, or code where relevant
- explain trade-offs rather than merely demonstrating features
- expect attendees to understand foundational terminology

#### 300 - Advanced

- assume attendees already understand the fundamentals
- focus on architectural decisions and implementation depth
- explore advanced patterns, extensibility, debugging, optimisation, failure modes, or complex scenarios
- avoid spending significant session time on introductory concepts
- ensure the title and abstract clearly signal the expected technical depth

Do not classify a session as 300-level simply because it uses an advanced or emerging technology.

If the requested level does not match the content, recommend either:

- changing the advertised level, or
- increasing or decreasing the session's technical depth

### 5. Develop three title options

Provide:

- one clear and practical title
- one technically intriguing title
- one bold or memorable title

Select the strongest as the recommended title and explain why it works.

Avoid generic titles such as "Introduction to..." unless the session is explicitly introductory.

Do not create a dramatic or clickbait title that the content cannot support.

### 6. Create the CFP-ready abstract

The abstract should explain:

- the problem or situation
- why it matters to the target audience
- what the session will explore, demonstrate, or challenge
- what attendees will take away

Do not turn the abstract into a list of product features.

Do not promise content, demonstrations, or outcomes that the proposed session cannot realistically deliver.

### 7. Define three learning outcomes

Provide exactly three learning outcomes unless the user explicitly requests a different number.

Use concrete, outcome-oriented verbs such as:

- design
- build
- evaluate
- diagnose
- compare
- implement
- apply

Avoid vague outcomes such as:

- learn about
- become familiar with
- understand more about

The outcomes must match the advertised session level and the content that will actually be presented.

### 8. Create the session story and timing

Structure the session as a narrative rather than a list of features.

A useful pattern is:

- Hook
- Problem
- Why the obvious approach is insufficient
- Architecture or approach
- Build or implementation
- Demo
- Lessons learned
- Takeaways

Adapt this structure when a different narrative better suits the topic.

When session duration is known:

- recommend a time allocation for each major section
- include transitions and closing time
- ensure the total fits within the stated duration
- preserve sufficient time for the most valuable technical content
- avoid overloading the agenda

Prefer one memorable story over several disconnected mini-topics.

### 9. Design the demo

If the session includes a demo, define:

- demo scenario
- starting state
- what the audience sees first
- minimum steps required
- key reveal
- what the demo proves
- required environment
- required authentication
- required sample data
- likely failure points
- fallback approach

The demo should support the session's central argument.

Prefer one focused, cohesive demonstration over several disconnected feature demonstrations.

Where useful, recommend:

- pre-staged configuration
- backup screenshots
- a recorded fallback
- a known recovery point
- a reduced happy-path version of the demo

Do not assume every technical session requires a live demo.

### 10. Plan attendee resources and engagement

Determine which resources would genuinely improve the attendee experience.

Consider:

- GitHub repository
- sample code
- demo solution or project
- workshop or lab instructions
- architecture diagrams
- downloadable resources
- presentation slides
- related technical article or blog
- consolidated resource page
- speaker or professional profile
- conference feedback or evaluation link

For each useful resource, determine:

- its purpose
- when attendees need it
- what the speaker must prepare
- whether it must exist before the session

Assess whether resources should be accessible through QR codes.

For each useful QR code, determine:

- purpose
- destination
- suggested location in the presentation
- call to action
- whether it should appear on the final slide
- readiness status

Common examples include:

- Repository QR
- Consolidated resources QR
- Speaker or profile QR
- Feedback QR

Do not recommend QR codes merely for decoration.

Avoid multiple competing QR codes on the same slide.

Prefer one consolidated resource page or repository landing page when several resources would otherwise compete for attention.

Never invent repository, profile, resource, event, or feedback URLs.

When a destination is unavailable, use:

- `URL required from speaker`
- `Resource required`

If no QR code adds meaningful value, state:

- `No QR code required`

### 11. Create the speaker preparation checklist

Include only items relevant to the proposed session, such as:

- slides
- demo environment
- authentication
- sample data
- repository
- attendee resources
- architecture diagrams
- QR codes
- backup screenshots
- backup demo recording
- known recovery point
- rehearsal
- timing
- presentation transitions
- final takeaway
- resource availability
- link validation

## Required output format

Present the final result using these exact headings.

### Session verdict

Briefly assess the strength of the idea, whether it suits a conference audience, and any recommended repositioning.

### Recommended title

Provide the strongest title and explain briefly why it works.

### Alternative titles

Provide two alternative titles with different positioning.

### Session level

Include:

- recommended level: 100 / 200 / 300
- rationale
- expected attendee knowledge
- suggested prerequisites
- any mismatch between the requested level and actual technical depth
- any content changes required to support the recommended level

### Abstract

Provide the CFP-ready abstract.

### Target audience

Include:

- intended attendee profile
- expected experience level
- prerequisite technologies or concepts
- who may find the session too basic
- who may find the session too advanced

### Learning outcomes

Provide exactly three concrete and measurable learning outcomes unless the user requests otherwise.

### Session story

Provide:

- narrative structure
- major sections
- suggested time allocation when duration is known
- transitions
- final takeaway

Ensure that the proposed content fits within the session duration.

### Demo design

Include:

- scenario
- starting state
- important steps
- key reveal
- what the demo proves
- environment, authentication, and data requirements
- likely failure points
- fallback approach

### Attendee resources

For each recommended resource include:

- asset
- purpose
- when attendees need it
- preparation required
- whether it must exist before the session

### QR code plan

For each recommended QR code, always explicitly provide all six fields:

- Purpose
- Destination
- Presentation location
- Call to action
- Final-slide placement: Yes / No
- Status: Ready / URL required / Resource required

Do not omit a field.

### Speaker checklist

Provide a practical preparation checklist tailored to the proposed session.

### One thing I would change

End with the single most important improvement the speaker should make.

## Quality checks

Before returning the session design, verify that:

- the idea has been challenged rather than automatically praised
- the session has a clear audience problem or value proposition
- the proposed level reflects the actual technical depth
- exactly three title options are provided
- exactly three learning outcomes are provided unless requested otherwise
- the agenda fits the stated duration
- the demo supports the story rather than becoming a feature tour
- prerequisites match the expected audience
- attendee resources have a clear purpose
- QR codes provide genuine value
- one consolidated resources QR is preferred over competing QR codes where practical
- no repository, profile, resource, event, or feedback URL has been invented
- missing destinations are clearly marked
- every required output heading is present
- the final recommendation is practical and specific