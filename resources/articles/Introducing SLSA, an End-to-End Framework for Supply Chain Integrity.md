---
tags:
  - resource/article
---

Link: https://security.googleblog.com/2021/06/introducing-slsa-end-to-end-framework.html

- Supply Chain Levels for Software Artifacts, or SLSA
## Takeaways

- supply chain integrity attacks - unauthorised modifications to software packages
- there are numerous threats in the source > build > publish workflow
- Google proposes SLSA (pronounced "salsa") as a framework for ensuring the integrity of software artifacts, particularly in open source

![[16987318611086224618595608005836.png]]
- source integrity attacks
	- bad code accepted by maintainers
	- version control compromised, e.g. unauthorised users committing malicious code
- build integrity attacks
	- build process is working, but code is built from incorrect source
	- build platform compromised and used to inject malicious code during build
	- bad dependency added to dependencies - this dependency could be any of these source/build integrity attacks, recursively
	- bypassing CI/CD - i.e. packages are uploaded to package repository that were not built by CI/CD
	- compromising package repository, e.g. hosting malicious mirrors of package repositories 
	- tricking consumers into using her packages, e.g. by using existing or similar names for packages
- SLSA can be applied incrementally, with level 4 being the goal

![[1698732825083907137779332055644.png]]

- levels
	- SLSA level 1
		- build process is scripted / automated
		- provenance / metadata for build is generated
	- SLSA level 2
		- VCS is used
		- hosted build service is used
		- provenance is generated
	- SLSA level 3
		- use of accredited VCS and build services 
	- SLSA level 4
		- 2-person reviews of all changes
		- hermetic builds, i.e. all dependencies are specific upfront, and changes to the host have no impact on builds 
		- reproducible builds 
- provenance is metadata about how an artifact was built, including the build process, top-level source, and dependencies

## Links and resources

- https://about.gitlab.com/blog/2022/11/30/achieve-slsa-level-2-compliance-with-gitlab/