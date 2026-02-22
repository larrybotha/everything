---
tags:
  - resource/article
---

Link: https://www.reddit.com/r/PromptEngineering/comments/1nt7x7v/after_1000_hours_of_prompt_engineering_i_found/

## Takeaways

### KERNEL prompts

- Keep it simple
  - state in one sentence
- Easy to verify
  - quantifiable results
  - success criteria
  - measurable criteria
  - objectively verifiable criteria
- Reproducible
  - works consistently regardless of when it is run
- Narrow scope
  - single primary goal
- Explicit constraints
  - standards
  - what to avoid
  - technical requirements
- Logical structure
  - context provided
  - task clearly stated
  - constraints listed
  - format specified

```
Task: [task description]
Input: [source data]
Constraints: [constraints to impose on LLM]
Output: [desired output]
Verify: [instructions for verifying output]
```

e.g.

```
Task: Python script to merge CSVs
Input: Multiple CSVs, same columns
Constraints: Pandas only, <50 lines
Output: Single merged.csv
Verify: Run on test_data/
```

### PRISM prompts

1. create PRISM template for specific outcome, e.g. research, planning, implementation, etc.
2. prime/seed agent with PRISM appropriate template
3. follow up with task

Treat PRISM as a thin routing layer and pair it with verifiable, single-goal tasks.

- Seed the chat once with a compact PRISM:

  - P = business reasoning
  - R = modular blocks + criteria-first
  - I = inputs you’ll supply
  - S = output sections
  - M = how to verify

  Keep it under 5 lines.

- For each task, add a mini spec right after: Goal, Inputs, Constraints, Format, Verify. Example for a proposal: Goal: 2-page B2B proposal. Inputs: client brief, pricing guardrails. Constraints: 600–700 words, 3 options, DACI roles. Format: Exec summary, Problem, Options, Cost, Risks, Next steps. Verify: list assumptions and a yes/no checklist.
- Chain - each step is one prompt with clear pass/fail:
  1. outline
  2. fill sections
  3. risk pass
  4. executive summary
- Store reusable kernels/templates and tag triggers; I keep them as snippets and reuse across chats.

Keep PRISM short, tie every task to clear criteria, and chain small steps for consistent results.

e.g. for template

```
///▙▖▙▖▞▞▙▂▂▂▂▂▂▂▂▂▂▂▂▂▂▂▂▂▂▂▂▂
▛///▞ PRISM KERNEL :: BUSINESS.STRATEGY.OP ⫸
//▞▞〔Purpose · Rules · Identity · Structure · Motion〕

P:: Fires on prompt with goal-setting, strategic planning, or business logic development
R:: Strategic Engine — A modular logic form for business reasoning and output pattern design
I:: Solve business problems, propose system upgrades, and write reusable prompt templates
S:: Output in modular blocks; use Codex structure when possible; enforce clarity, reusability, and symbolic tags
M:: Activated by tags like `#business`, `#strategy`, `#template`, or commands invoking “generate,” “build,” or “solve” in a business context

:: ∎ //▚▚▂▂▂▂▂▂▂▂▂▂▂▂▂▂▂▂▂▂▂▂▂▂▂▂
```

or for specific task

```
///▙▖▙▖▞▞▙▂▂▂▂▂▂▂▂▂▂▂▂▂▂▂▂▂▂▂▂▂▂
▛///▞ PRISM KERNEL ::
//▞▞〔Purpose · Rules · Identity · Structure · Motion〕
P:: merge.csv.files ∙ write.single.output
R:: use.pandas.only ∙ under.50.lines ∙ strict.schema
I:: input.folder.test_data/
S:: read.all.csvs → concat.dataframes → export.merged.csv
M:: output: merged.csv ∙ verify.success ∙ reuse.pipeline
:: ∎
```

## Links and resources

- https://dev.to/zetao_qin_906c7471abc999c/a-practical-guide-to-prompt-engineering-6-essential-patterns-every-beginner-should-master-1g0h
