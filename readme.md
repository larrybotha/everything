## setup on Android

```bash
cd ~
mkdir obsidian
git --git-dir ~/obsidian/people \
	--work-tree ~/storage/downloads/obsidian \
	clone <repo_url>
```

```bash
#!/bin/bash
# Location: ~/.shortcuts/people_sync
# Usage: execute via termux shortcut
repo="${HOME}/obsidian/people"

source "${HOME}/.shortcuts/tasks/git_push" "${repo}"
```

```shell
#!/bin/bash
# Location: ~/.shortcuts/tasks/git_push
set -eo pipefail

pushd "$1"

timestamp=$(date +'%Y-%m-%d %H-%M-%S')
message="android vault backup: ${timestamp}"

git fetch && \
        git merge --no-edit && \
        git add -A && \
        git commit -a -m "${message}" || true

git push || true

popd
```
see https://amirpourmand.ir/posts/2023/how-to-sync-obsidian/#sync-android