# feature-orchestrator

Agent skill to take a software feature from discovery to delivery through staged
subagent handoffs. The main agent is the orchestrator: it keeps the accepted state,
picks the next task, prepares the input context, checks the result, and talks to the
user at the points the model requires.

For a trivial, self-contained change, work directly instead of applying this process.

## Install

**Claude Code / OpenCode** — clone and point the agent at the folder, or copy it into
your skills directory:

```bash
git clone https://github.com/1arley/feature-orchestrator
```

**Codex / OpenAI** — `agents/openai.yaml` carries the interface metadata.

## What it does

1. Picks a delivery model based on clarity, expected change, risk, and feedback pace.
2. Records who decides open questions: **you**, **Jev**, or the **orchestrator**.
3. Runs the stages your model calls for, each with its own subagent and a bounded input
   and output contract, accepting the artifact before moving on.

## Delivery models

| Model | Use when |
| --- | --- |
| **Cascade** | Scope and acceptance are clear, decisions are simple and reversible, few unknowns. |
| **Incremental** | Requirements are general or will evolve, but the system allows small useful slices. |
| **Prototyping** | A feasibility or experience question is still unanswered. |
| **Risk-driven spiral** | Uncertainty or high risk, and direction should adjust as you learn. |
| **Formal methods** | You need mathematical proof of software properties, or assurance is elevated (avionics, medical imaging). |

Models can be combined — for example spiral cycles to reduce uncertainty with a formal
specification as the production gate.

Details: [references/workflow-models.md](references/workflow-models.md).

## Delegation

Each subagent gets a short task package: role and stage, goal, accepted context,
scope and limits, completion criteria, requested evidence, expected output.

| Stage | Minimum deliverable |
| --- | --- |
| Research and grilling | Relevant current state, requirements, unknowns, evidence, material questions |
| Planning | Scope, acceptance, slices, dependencies, risks, per-slice verification |
| Architecture/modeling | Decisions and alternatives, affected contracts/data/interfaces, migration risks |
| Build | Changes limited to the plan, file summary, implementation decisions |
| Tests/review | Checks run, results, gaps, bugs, or formal evidence per the model |
| Delivery | What was completed, how to verify, unfinished items, residual risks |

Reviewers and testers evaluate accepted artifacts independently, without being handed
the conclusion they are expected to confirm.

Details: [references/delegation-protocol.md](references/delegation-protocol.md).

## Honesty rules the skill enforces

The skill explicitly forbids claiming work that did not happen:

- Do not say you consulted Jev unless a Jev interface is actually reachable in the environment.
- Do not declare a test, proof, review, or approval that never ran.
- Distinguish a proof of concept from production-ready software, and formal evidence
  from a certification claim.
- If subagents are unavailable, run the same roles sequentially with explicit handoffs —
  do not invent delegations.

## License

MIT — see [LICENSE](LICENSE).