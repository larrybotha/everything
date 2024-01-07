1. Install Termux and Termux:Widget
2. Install Obsidian
3. In Termux
	1. configure access to shared storage
	2. Install packages in Termux:
		- git
		- nnn
		- lazygit
		- openssl
	3. Configure `~/.gitconfig` with user details
	4. Clone Obsidian repos to `~/storage/shared/Obsidian Vaults`
	5. Add sync script to `~/.shortcuts/tasks/git_push`:

		```bash
		#!/bin/bash
		
		set -eo pipefail
		
		pushd "$1"
		
		timestamp=$(date +'%Y-%m-%d %H-%M-%S')
		message="android vault backup: ${timestamp}"
		
		git pull && \
				git add -A && \
				git commit -a -m "${message}" || true
		
		git push || true
		
		popd
		```
	1. For each repo, add a sync script to `~/.shortcuts`:
		```bash
		#!/bin/bash
		# e.g. filename is 'sync_some_vault'
		repo="${HOME}/storage/shared/Obsidian Vaults/[vault-folder]"
		
		source "${HOME}/.shortcuts/tasks/git_push" "${repo}"
		```
	1. Run each sync script from inside Termux, following any instructions provided by Git - Git doesn't trust the repos by default
1. In Android:
	1. Add a widget to each script using `Termux:Widget`
	2. In Obsidian, open each vault by navigating to the folder in the file explorer 

To sync a vault:

1. Tap the associated widget
2. Open the Termux session that becomes available from the pull-down menu

If the sync fails, open Termux, and resolve using Git manually