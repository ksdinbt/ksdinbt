# Karol S. Danisz

**Senior Business Analyst · Business Intelligence · Inbet Online**

I work where data meets a decision. Most of my time goes into three things: making a number mean
the same thing to everyone who reads it, building the small pieces of infrastructure that let an
answer arrive before the question goes stale, and then sitting with the person who has to act on it.

The BI unit I work in is small and owns its stack end to end. There is no handover to an engineering
team between "we need to know X" and "here is X, and here is what it does not cover".

---

## How I work

- **One term, one meaning.** Metric ambiguity is not a documentation problem, it is a decision
  problem. If two teams can read a definition differently, the definition is wrong, even when both
  readings are defensible.
- **A number without provenance is a rumour.** Every figure I publish should be traceable to a
  source, a point in time and a definition. Stale data presented as current is the most expensive
  kind of error we make, because it looks exactly like a correct answer.
- **Anomaly, interpretation, next step.** A report that shows a movement without saying what it
  means and what to do about it is noise with a timestamp. If I cannot suggest an action, I say that
  explicitly instead of leaving the reader to invent one.
- **Build the smallest thing that survives contact.** A scheduled query and a plain page beat an
  elegant platform nobody maintains. Complexity has to pay rent.
- **Say what is uncertain.** In analysis, the difference between "we know", "we infer" and "we
  assume" is the whole value of the work. I try to keep that distinction visible in the output, not
  only in my head.

---

## Areas of work

**Metric definitions and governance.** Owning the definitions behind commercial reporting: turnover,
margin, active players, bonus cost, retention cohorts. Reconciling the same metric across source
systems that were never designed to agree, and writing down the version that wins.

**Analytical products.** Dashboards and recurring reports built for a specific decision rather than
for completeness: CRM handover and retention tracking, weekly performance recaps, executive summaries,
player lifecycle and segmentation views, market and competitor post-mortems.

**Commercial analysis.** Campaign and promo economics, betting-margin scenarios and odds repricing,
segment-level before-and-after studies, churn and reactivation targeting, market entry questions.

**Data engineering when it is the shortest path.** ETL and scheduled pipelines, internal web apps,
browser automation against systems that have no API, monitoring that tells us when something broke
before a stakeholder does.

**AI systems in production analytics.** Not model research for its own sake, but the unglamorous
part: which model, at what cost, with what memory, with what permissions, and how do we know it is
still right three months later.

---

## The AI agent pilot

The piece of work I am most invested in is the framework and implementation of an in-house AI agent
used as a member of the BI unit rather than as a demonstration.

It is a pilot in the literal sense. The agent has a role description, a memory model, a working
schedule, escalation rules and an audit trail. It is measured by whether the unit's work improves,
not by whether a demo looks impressive. Where it is wrong, the failure is written down like any other
incident.

What the framework covers:

- **Role and accountability.** Defined responsibilities and explicit boundaries on what the agent may
  decide alone, what it must propose first, and what it must escalate to a human. The distinction
  between proposing an action and being authorised to take it is treated as a first-class rule, not
  as a prompt instruction.
- **Memory architecture.** Short-term working state kept deliberately small, because a memory that
  grows without structure stops being memory. Long-term memory lives in a structured knowledge base:
  a daily journal, per-person notes, and durable how-tos written after the fact rather than before.
  Continuity across sessions is an engineering requirement, not a feature.
- **Procedural memory.** Reusable workflows are written as versioned skills that load only when a
  task needs them. Behaviour becomes reproducible and reviewable instead of improvised per session,
  and a correction made once stays corrected.
- **Scheduled operations and monitoring.** Recurring analytical jobs, watchdogs and health checks
  that report only when something is actually wrong, with a rule that every alert carries a
  suggested next step.
- **Communication harness.** The agent works through the same channels as the team, with explicit
  rules about when to reply, when to escalate to email, and when to stay quiet. Silence is a valid
  output.
- **Model selection and evaluation.** Vetting open-weight models against an incumbent on real tasks
  before switching, keeping inference local where data cannot leave the building, and documenting
  the decision so it can be revisited when the models change.
- **Honest limits.** The agent does not replace review of anything consequential. Its value is that
  routine work becomes faster and better documented, which is what frees a small team to do the work
  that actually needs a person.

---

## Featured open work: `agent-communication-language`

**[github.com/ksdinbt/agent-communication-language](https://github.com/ksdinbt/agent-communication-language)**
· public · Phase 0 complete

A research programme on whether agents should talk to each other in natural language at all, and
what a better representation would have to contain.

The premise is narrow and testable: a shared, typed representation of meaning, independent of model,
tokenizer, language and transport, might reduce the cost of communication without reducing the
quality of the result. The interesting part is not the syntax. It is the four properties that current
protocols do not carry: the **epistemic status** of a claim (observed, inferred, assumed, predicted,
unknown); its **provenance**, including when the data was observed; the **authority** behind it
(proposal versus request versus authorisation); and **progressive precision**, where the sender
transmits the minimum sufficient message plus resolvable references and the receiver asks for detail
only when it needs it.

What makes it a showcase rather than a manifesto is Phase 0. The first task was to establish what
already exists, and the answer was uncomfortable: a July 2026 Internet-Draft (SILP) already specifies
a reference semantic representation compiled into multiple interchangeable encodings with runtime
negotiation. That is most of the original thesis. The repository says so on its first page, in a
section called *What is actually new*, and the programme was reframed around what survived.

The repository contains the paper, a verified state-of-the-art review with a gap matrix, a
systematic literature sweep with its query log, an unambiguous MVP scope, and a benchmark design with
a pre-registered equivalence margin, a total-cost formula that counts decoding inference, and a
deliberately self-defeating hypothesis: that compact encodings may not save anything at all.

The benchmark includes the incumbent as an arm from day one. Comparing a new representation only
against natural language would manufacture a favourable result.

Phase 0 closed by doing rather than asserting: I installed and ran the incumbent's reference
implementation. It installs in a minute and compiles all of its example set, but its "lossless"
round trip preserves the full representation in 0 of 54 cases, because secondary entity identifiers,
constraint subjects and the entire metadata block are dropped on decode. That result is written up in
the repository, and it changed the benchmark design: every arm is now scored on one declared semantic
projection, and the extension cannot live in the metadata field where the incumbent keeps its only
confidence value. Two upstream bugs were found and recorded. This is the part of the work I care
about most: the gate was cheap, it was binary, and it changed the plan.

---

## Toolbox

SQL and ClickHouse for analytical work at scale · Python for everything around it · FastAPI and
lightweight internal web apps · Playwright for automation against systems without APIs · ETL,
scheduling and monitoring · Linux administration and service plumbing · Git and GitHub as the working
record · model evaluation, local inference, prompt and skill engineering

---

## Research interests

- **Agent communication.** Typed payloads, provenance and authority semantics between models, and how
  to evaluate them honestly instead of benchmarking a new format against prose.
- **Decision models.** Small, constrained, inspectable systems over large general ones, particularly
  where the cost of a wrong answer is asymmetric.
- **Memory and retrieval.** How a system stays coherent over months rather than over one session.
- **Measurement.** Metrics that survive contact with people who have an interest in how they read.

---

## Note on this profile

This is my company GitHub account. Most of my work lives in private repositories, so this page
describes the work rather than linking to it. Nothing here contains customer data, credentials or
internal infrastructure details. The one public project is published with its own evidence and its
own limitations, which is the only way research is worth reading.
