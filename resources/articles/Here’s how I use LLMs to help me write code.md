---
tags:
  - resource/article
---
Link: https://simonwillison.net/2025/Mar/11/using-llms-for-code/#context-is-king

## takeaways

- think of LLMs as over-confident pair programmers - they _will_ need to be corrected
- take note of things that LLMs fail to do; an indicator of a strong model is when it can solve problems that others couldn't
- training cut-off dates are important with respect to the ability of LLMs to solve problems with different libraries - boring technology is useful here, ad APIs are usually more stable and more likely to have been indexed by LLMs
	- popularity and age of libraries are important to consider
- context is the most important thing to bare in mind
	- each new chat is a new context
	- providing working examples or other projects for context before code is generated is effective in getting better results
- use LLMs for initial research
	- ask which libraries are available for the problem, and request examples
	- LLMs can be used for PoCs, and can be done via a mobile phone
- be specific when requesting production code to be generated
	- provide function signatures
	- specify file names
	- specify the technologies to use
	- specify expectations and conditions
- validate that what was generated works - it _has_ to be tested by a human
- remember that it's a conversation
	- expect there to be errors at first, and that your job is to guide the LLM to what you want
	- build initial results are starting points, not failures
- use tools that can run the generated code
	- consider how to isolate the code from your machine to prevent disastrous fs consequences
		- remote service
		- virtual machines
		- etc.
	- chatGPT code interpreter
	- Claude Artifacts
	- ChatGPT Canvas
	- Cursor Agents
	- Aider
	- Claude Code
- vibe-coding
	- great way to learn about how to use LLM models
	- author has a repo on GitHub containing multiple projects that are almost entirely vibe-coded - tools he actually uses
	- it costs only a few cents for the author to build things that they would otherwise find difficult to justify the time to invest to build
- LLMs are no replacement for intuition and experience
- LLMs amplify existing experience
	- knowing how technologies work allows one to create prompts that someone without experience would have no idea how to do
- LLMs are good for evaluating codebases
	- parse files, send to LLM for context, interrogate LLM 
		- e.g. "provide an architectual overview in markdown"

## links and resources

- https://simonwillison.net/2023/Mar/27/ai-enhanced-development/
- https://simonwillison.net/series/using-llms/