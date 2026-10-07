---
name: product-context
description: "Gather and validate context before reasoning about a work or personal product problem. Use when the user states a product problem, requests a product decision or design, or proposes a material product change and relevant evidence may exist in code, documentation, or connected external sources. Inspect relevant sources first, assess their claim-specific authority, surface conflicts and gaps, then stop and ask whether the context is sufficient and the authority assessment is correct. Do not use for dotfiles, environment setup, general tooling, routine maintenance, or isolated fixes unless explicitly framed as product work."
---

# Product context

Ground product reasoning in available evidence before decomposing the problem,
considering solutions, or designing behavior.

Do not provide a generic solution when relevant context can reasonably be inspected
first.

## When to run

Run before `decompose-problem`, `consideration`, `product-design`, or `design-doc`
when no accepted context checkpoint exists for the current problem.

When `technical-design` is invoked directly, run this skill unless an accepted context
checkpoint already establishes the product requirements and relevant implementation
context.

Reuse an accepted checkpoint while its scope and evidence remain applicable. Reopen it
when new information contradicts it, the problem changes materially, or important
evidence may have become stale.

## 1. Frame the search

Identify without solving:

- the product and affected users
- the stated problem or decision
- relevant behaviors, concepts, teams, and likely search terms
- the period or version that matters

Do not require the user to repeat context that can be found in available sources.

## 2. Inspect available sources

Search narrowly and read the underlying sources rather than relying only on titles,
snippets, or search summaries.

### Local sources

Inspect relevant:

- product documentation and decision records
- implementation code
- tests and fixtures
- configuration affecting product behavior
- issue or change history when available and material

### Connected external sources

Use read-only connected sources when:

- the user names the source, or
- the source description clearly matches the product and problem

Examples include Notion, Slack, email, issue trackers, customer-feedback systems, and
internal documentation.

Do not search every connected account indiscriminately. Keep searches bounded to the
product, problem, likely owners, and relevant period. State which sources were not
available or could not be accessed.

Use public web research only when external facts, standards, vendor behavior, or current
official documentation matter.

### Follow important gaps with deeper research

Initial discovery and deeper research are one workflow, not separate mandatory passes.
Scale the depth to the problem. Follow material gaps, contradictions, and uncertain
constraints back to relevant code, original documents, or primary external sources
before presenting the checkpoint. Do not stop at superficial discovery when an
accessible source could answer a decision-critical question.

When delegation is authorized and available, use focused parallel agents for independent
research questions. Give each a bounded question, relevant context, source scope, and
stopping condition. Use `scout` for local implementation evidence and `researcher` for
public external evidence; inspect private connected sources through authorized tools.
Ask for source references, findings, uncertainty, and remaining gaps. Verify material
claims against the underlying evidence when synthesizing their results. Do not launch
overlapping lanes or require subagents for a small investigation.

Stop investigating when the problem is grounded well enough for a useful checkpoint,
additional searches are unlikely to change that understanding, or remaining gaps require
user input or unavailable access. State those gaps rather than researching indefinitely.
You may recommend what evidence to inspect next, but do not recommend a product solution
before the user accepts the context checkpoint.

## 3. Assess evidence and authority

Authority is specific to the claim being supported. Do not assign authority solely from
the source type.

For every material source, record:

- what claim or question it addresses
- ownership or authorship, when known
- approval or publication status, when known
- recency
- whether it is direct evidence or interpretation
- the initial authority assessment and its reason

Use these provisional levels:

- **Confirmed authority** - explicitly accepted by the user or clearly designated as the
  governing source.
- **Likely authority** - strong ownership, approval, scope, and recency signals, but not
  yet confirmed by the user.
- **Supporting evidence** - relevant direct evidence that informs but does not govern the
  decision.
- **Lead / unverified** - points toward useful context but has not been adequately read
  or validated.
- **Unknown** - authority cannot be inferred safely.

Code, tests, and runtime behavior can be authoritative for what the system currently
does. They are not automatically authoritative for what the product should do.

Slack messages, emails, and meeting notes may record a governing decision, but do not
assume that they do without evidence of ownership, finality, and scope.

## 4. Reconcile without deciding

Before product reasoning:

- separate confirmed facts from interpretations and assumptions
- identify contradictions between sources
- identify missing perspectives or evidence
- explain material freshness or access limitations
- do not silently choose which conflicting source wins

## 5. Stop at the context checkpoint

Present:

### Problem understood

One sentence describing the problem being investigated, without proposing a solution.

### Sources inspected

| Source | What it supports | Authority | Reason |
|---|---|---|---|

### Conflicts and gaps

List contradictions, missing evidence, inaccessible sources, and important uncertainty.

### Confirmation

Ask the user:

1. Are these sources sufficient to proceed?
2. Is the authority assessment correct?
3. Which source should govern any conflict?
4. Should any additional source be searched first?

Do not proceed to decomposition, consideration, or design until the user confirms the
checkpoint or explicitly asks to continue with the stated uncertainty.

## 6. Continue

After confirmation, carry the accepted context forward to the next product workflow.

Do not repeat the checkpoint unless:

- the problem scope changes
- later evidence contradicts it
- a previously unavailable governing source becomes available
- freshness materially affects the decision
