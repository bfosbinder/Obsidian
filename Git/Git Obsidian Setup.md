## 1. Core → Commit-and-Sync section

|Setting|Recommended value|Why|
|---|---|---|
|**★ Auto-pull on startup**|**ON**|Guarantees you start each Obsidian session on the latest commit [github.com](https://github.com/Vinzent03/obsidian-git)|
|**★ Pull before push**|**ON**|Plugin does a `git pull` _first_ so you don’t push on top of stale history|
|**Pull strategy**|**Rebase** (not merge)|Keeps a straight line of commits and avoids those ugly “Merge branch ‘master’” bubbles|
|**Auto commit & push interval**|5–10 min _or_ “On vault idle ≥ 60 s”|Lets you forget about manual commits without spamming GitHub. (Reddit crowd uses 1 min; I’ve found 5 min kinder on battery + network) [reddit.com](https://www.reddit.com/r/ObsidianMD/comments/18dt1ok/obsidian_git_tips_on_how_to_use_it_for_reliable/?utm_source=chatgpt.com)|
|**Commit message template**|`{hostname}: {now:YYYY-MM-DD HH:mm} – {numFiles} files`|Quick glance tells you _where_ and _when_ the change came from|

---

## 2. Core → Pull section

|Setting|Recommended value|Why|
|---|---|---|
|**Stash local changes before pull**|**ON**|If you’ve half-edited a note and click _Sync_ you won’t lose work|
|Max concurrent retries|3|Leaves room for flaky hotel Wi-Fi without hanging forever|

---

## 3. Ignore Rules (one-time edit)

Add these lines to `.gitignore` in the root of your vault — commit them once and forget:

bash

CopyEdit

`# Obsidian UI chatter .obsidian/workspace.json .obsidian/workspace-mobile.json .obsidian/cache/* # Git plugin’s own state .obsidian/plugins/obsidian-git/data.json # Temp & trash .trash/`

`workspace.json` is the #1 source of merge hell; ignoring it removes the problem entirely.

---

## 4. Source-Control View section (optional candy)

|Setting|Value|Why|
|---|---|---|
|Show status bar summary|ON|Tiny green ✓/red ● icon tells you if anything is out of sync at a glance|
|Enable diff view|ON|One-click side-by-side diff inside Obsidian; great for quick reviews|

---

## 5. Advanced bits (toggle only if you need them)

|When to flip it|Setting|Value|
|---|---|---|
|You keep separate “Personal” and “Work” folders inside the same vault|“Treat folders as sub-repositories”|ON (desktop only)|
|You _never_ want the plugin to ask for commit text|“Skip commit message prompt”|ON|
|Your repo is > 50 k files or > 200 MB|“Chunk size for status/commit”|Drop to 100–200 to reduce memory spikes|

---

### One-liner manual fallback

If you ever want to bypass the plugin:

bash

CopyEdit

`git pull --rebase && git add -A && git commit -m "quick update" && git push`

That mirrors the plugin’s logic (pull → add → commit → push) with rebase, so history stays tidy.

---

**Bottom line**

1. **Turn on Auto-pull at startup, pull-before-push, and rebase.**
    
2. **Ignore `workspace.json` and the plugin’s own `data.json`.**
    
3. Let the 5-minute auto “commit-and-sync” run in the background – you’ll almost never see another merge warning. Happy writing!