---
tags:
  - resource/article
---

Link: https://simonwillison.net/2023/Mar/27/ai-enhanced-development/

- author managed to do the following using ChatGPT faster than it took to write the article:
	- write a script that monkey-patched `fetch` to intercept requests in the browser
	- build a proxy server in Python which handled CORS requests, to forward data server-side to a database service
		- this service was written in Python, and deployed to Vercel
	- used Copilot to generate code for transforming data into the expected sql schema
	- rewrote the generated PoC into a working application