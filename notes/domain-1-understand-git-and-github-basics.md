# Domain 1: Understand Git and GitHub basics (28%)

The heaviest domain (official range 25–30%), and the base the rest of the exam builds on. Questions are short scenarios: a team problem that version control solves, a capability you must sort into Git or GitHub, a step in the GitHub flow, a piece of text to format in Markdown, or a person who needs the right account, plan or app. Read each scenario for exactly what happened locally and what reached GitHub.

## 1.1 Version control fundamentals

- **Version control** records every change to a project's files: who made it, when, and why. It lets you restore or compare any committed version and lets several people work at once.
- **Four benefits** (map scenarios to these):
  - **History and accountability**: each commit has an author, timestamp and message (`git log`).
  - **Restore and compare**: bring back or diff any committed version (`git diff`) without keeping backup copies.
  - **Parallel work**: separate branches, combined later by merging, instead of locking files or taking turns.
  - **Safe experimentation**: try an idea on a branch, then merge it or delete it.
- **Only committed content is recoverable.** Uncommitted edits, untracked files, paths in `.gitignore`, and a file's life before it was first added leave no trace in history.
- **A cloud drive's file history is not version control in this sense.** It keeps old copies of single files but has no project-wide branches to develop side by side and merge.

|                 | Git                                                                                         | GitHub                                                                         |
| --------------- | ------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------ |
| What it is      | Free, open-source, distributed version control software                                     | Cloud platform that hosts Git repositories and adds collaboration              |
| Where it runs   | Your computer, online or offline                                                            | github.com / Enterprise Cloud, or self-hosted Enterprise Server                |
| Account needed? | No                                                                                          | Yes to contribute (browsing and cloning public repos needs none)               |
| Provides        | Repositories, commits, staging, branches, merge, diff, log, blame, clone, push, fetch, pull | Hosting, web UI, pull requests and review, issues, Actions, permissions, plans |

- **Git works without GitHub.** `git init`, commit, branch and merge all work on a laptop with no internet and no account. A remote is needed only to share (clone, push, fetch, pull). Any Git server works with the same commands.
- **Test:** "Could I do this on a plain clone with only Git installed?" Yes → Git. No → a hosting platform such as GitHub.
- **Merging is Git.** A pull request _ends_ in a merge, but the merge itself is a Git operation. Reviews, approvals, status checks and PR numbers are GitHub data that sit _around_ commits, not inside them.
- **Distributed** = every clone holds the full repository and full history:
  - Local work (history, commit, branch, merge) needs no server.
  - If the server is down, push/pull/fetch/clone from it wait; local work continues.
  - An up-to-date clone can rebuild a lost server repository. Other people's branches exist as remote-tracking refs (`origin/feature`) and must be pushed explicitly.
  - Nothing is broadcast. You push to share; others fetch or pull to receive.
- **Repository** = files plus their full history. On disk: the working directory (files you edit) and the hidden **`.git`** directory (commits, branches, remotes, config). Delete `.git` and you have plain files with no history. Create with `git init` (empty history) or `git clone <url>` (copy with full history).
- **Three local areas:**

| State     | Where                | Command that gets it there |
| --------- | -------------------- | -------------------------- |
| Modified  | Working directory    | Edit the file              |
| Staged    | Staging area (index) | `git add`                  |
| Committed | Local history        | `git commit`               |
| Pushed    | Remote, e.g. GitHub  | `git push`                 |

- **`git add` stages a snapshot of the content at that moment.** Edit the file again and commit without re-adding, and the commit holds the earlier version. The later edit stays unstaged.
- **Staging lets you commit part of your work**: edit three files, add two, commit two.
- **Committing is local.** Teammates see it only after `git push`. Use `git status` to see what is modified, staged or untracked.
- **Commit** = snapshot of all tracked files + author, committer, dates, message, parent ID(s). First commit has no parent. A merge commit has two or more.
- **Commit ID** = a hash (SHA-1 by default, SHA-256 possible) computed from all of that data, including the parent's ID. Often shortened to about seven characters.
  - Same ID in two clones → same snapshot **and** the same history back to the first commit.
  - It guarantees nothing about uncommitted changes, other branches, remotes or local config.
  - Changing anything, even just the message with `git commit --amend`, creates a **new** commit with a new ID. Amend before pushing, not after.
- **Branch** = a lightweight, movable pointer to a commit that advances with each new commit. Not a copy of the files. Default branch is usually `main`.

| Term   | What it is                                                | Moves?                |
| ------ | --------------------------------------------------------- | --------------------- |
| Branch | Pointer to the latest commit of a line of work            | Yes, with each commit |
| Tag    | Fixed label on one commit, e.g. `v1.0`                    | No                    |
| Remote | Named link to another copy of the repo (default `origin`) | n/a                   |
| Fork   | A GitHub copy of the whole repo under another account     | Separate repository   |

- **Branches are independent.** Commits on `feature` are not on `main` until merged. `git push origin main` sends only `main`.
- **Merging** applies both branches' changes relative to their common ancestor. Different lines, even in the same file, combine automatically.
- **Merge conflict** only when both branches changed the **same lines** (or one edited a file the other deleted). Git stops, marks the sections (`<<<<<<<`, `=======`, `>>>>>>>`), and a person resolves and commits.

| Command           | Direction                      | Effect                                                      |
| ----------------- | ------------------------------ | ----------------------------------------------------------- |
| `git clone <url>` | Remote → new local repo        | Full history, sets up `origin`                              |
| `git push`        | Local → remote                 | Sends a branch's commits                                    |
| `git fetch`       | Remote → local, not integrated | Updates `origin/main`; your branches and files unchanged    |
| `git pull`        | Remote → local, integrated     | Fetch + merge (or rebase if configured) into current branch |

- **After a fetch**, new commits are in `origin/main`, not `main`. `git log main` won't show them until you merge or pull.
- **Traps:**
  - "Merge" belongs to Git, "pull request review" to GitHub.
  - Fetch is the safe, look-first option. Pull changes your branch.
  - A matching commit ID does not mean matching working directories.
  - Recovering "the version I never committed" is impossible from Git history.

📖 Full lesson: [Git vs GitHub: Version Control Fundamentals for GitHub Foundations (GH-900)](https://www.savemycert.com/revision/github-foundations/git-vs-github-version-control-fundamentals/?utm_source=github&utm_medium=readme&utm_campaign=gh-900-study-guide)

## 1.2 Working with GitHub

- **Three account types:**

| Account         | What it is                                                                     | Sign in to it?                                           | Owns                           |
| --------------- | ------------------------------------------------------------------------------ | -------------------------------------------------------- | ------------------------------ |
| Personal (user) | A person's identity; every action comes from one                               | Yes                                                      | Own repos, packages, projects  |
| Organization    | Shared account for a group; access managed through teams                       | No, members use personal accounts                        | Repos that belong to the group |
| Enterprise      | Sits above organizations (Enterprise Cloud/Server); central policy and billing | No, owners are personal accounts with an enterprise role | Organizations                  |

- **Why an organization:** ownership doesn't depend on one person. Repos in one member's personal account leave with that member; others can only be collaborators. In an org there can be several owners, and access goes through teams.
- **No shared logins.** A shared "team login" breaks accountability. Machine users are for automation, not people.
- **One personal account per person** (GitHub's recommendation), for open source and paid work alike. Extra accounts can be merged.
  - Join an employer: an org owner invites your existing account.
  - Leave: you're removed from the org. Your account, repos and public history stay. You lose the org's private repos, and your **private forks of them are deleted**. Commits you made stay in the org's history.
  - One account can belong to several orgs at once.
  - Exception: **Enterprise Managed Users**, where the company IdP creates separate managed accounts (Domain 6).
- **Plans follow the account type:**

| Plan                          | For                              | Adds                                                                                                                                             |
| ----------------------------- | -------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------ |
| GitHub Free                   | Personal                         | Unlimited public repos (full features), unlimited private repos (limited features)                                                               |
| GitHub Pro                    | Personal                         | Advanced tools on private repos: protected branches, required/multiple reviewers, code owners, wikis, Pages; more Actions minutes; email support |
| GitHub Free for organizations | Orgs                             | Shared ownership, teams, unlimited collaborators; private repos limited                                                                          |
| GitHub Team                   | Orgs                             | The advanced private-repo tools for an org, per user                                                                                             |
| GitHub Enterprise             | Orgs under an enterprise account | Team + SAML SSO, SCIM provisioning, internal repos, enterprise-wide policies, Cloud or Server                                                    |

- **Features follow the repository owner's plan.** A personal private repo gets advanced tools on **Pro**. An org-owned private repo gets the **org's** plan; members' personal plans don't carry over. Team is the cheaper org step; Enterprise when you need SSO, SCIM, internal repos or many orgs.
- Public repos already get the full feature set on every plan, so paid plans matter mostly for private work. Learn what each plan is _for_, not prices or quotas.

| Enterprise option                    | Run by        | Data lives                              | Fits when                                         |
| ------------------------------------ | ------------- | --------------------------------------- | ------------------------------------------------- |
| Enterprise Cloud                     | GitHub        | GitHub.com                              | Enterprise controls, no servers, no location rule |
| Enterprise Cloud with data residency | GitHub        | Chosen region, own subdomain of GHE.com | Data must stay in a region (e.g. EU)              |
| Enterprise Server                    | Customer's IT | Customer's data center or private cloud | Policy requires self-hosted infrastructure        |

- **GitHub Connect** links Enterprise Server to Enterprise Cloud to share selected features/data (such as license usage). **Self-hosted runners** decide where Actions jobs run, not where GitHub is hosted.
- **The GitHub flow** (branch-based; keeps the default branch deployable):
  1. **Create a branch** from the default branch, with a descriptive name. No write access → fork first, branch in the fork.
  2. **Make changes**: commit (isolated, complete changes with clear messages) and push.
  3. **Open a pull request**: describe what and why, link issues.
  4. **Address review comments** by pushing more commits to the **same branch**. The PR updates itself.
  5. **Merge** once approved and required checks/protection pass.
  6. **Delete the branch**. Nothing is lost; it can be restored from the PR page.
- **Order matters:** review before merge. Merging first, committing to `main` then branching, or opening a PR before any branch exists are all wrong.
- **One branch and one PR per unrelated change**, each created from the default branch.
- **Draft pull request**: full PR experience (conversation, line comments, checks) but **GitHub blocks merging** until marked ready. Enforced by GitHub, not convention. Public repos on every plan; private repos depend on the owner's plan.
- **Undo a merged PR with Revert**: GitHub opens a **new PR** with a revert commit. Add history; never rewrite a shared branch (force-push bypasses review and breaks others' copies).
- **GitHub Flavored Markdown** renders in issues, PRs, comments, discussions, wikis and `.md` files:

| Want                      | Write                                                                 |
| ------------------------- | --------------------------------------------------------------------- |
| Heading                   | `# Title`, `## Section`                                               |
| Bold / italic / strike    | `**bold**`, `_italic_`, `~~struck~~`                                  |
| Inline code               | `` `npm test` ``                                                      |
| Code block + highlighting | ` ```python ` … ` ``` `                                               |
| Quote                     | `> quoted text`                                                       |
| Link / image              | `[text](url)` / `![alt](path)` (the `!` makes it an image)            |
| Task list                 | `- [ ] open`, `- [x] done` (clickable; progress shows in issue lists) |

- **Relative links** (`docs/flow.png`) resolve against the branch or fork being viewed. An absolute URL naming one branch always shows that branch. A leading `/` resolves from the repo root.
- **References and mentions:**

| Syntax               | Means                                           |
| -------------------- | ----------------------------------------------- |
| `#42`                | Issue/PR 42 in the same repo                    |
| `owner/repo#118`     | Issue/PR in another repo                        |
| `owner/repo@a5c3785` | A commit in another repo (bare SHA = same repo) |
| `@sam`               | Notify a user                                   |
| `@org/team`          | Notify a team's members                         |

- **A mention notifies only people with read access** to the repo (and org membership, for org-owned repos). That stops private content leaking via notifications.
- **Advanced formatting:**
  - **Alerts**: blockquote starting `> [!NOTE]`, `[!TIP]`, `[!IMPORTANT]`, `[!WARNING]`, `[!CAUTION]` → coloured callout with icon.
  - **Collapsed section**: `<details><summary>…</summary>` → hidden until clicked (add `open` to start expanded).
  - **Mermaid**: fenced block with language `mermaid` → diagram from text, edits show in diffs. GeoJSON, TopoJSON and ASCII STL also render.
  - **Footnotes**: `[^1]` → always displayed at the bottom.
  - **HTML comment**: `<!-- … -->` → never rendered. Used for guidance in templates.

|           | GitHub Desktop                                                                        | GitHub Mobile                                                                                                                       |
| --------- | ------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| Platforms | Windows, macOS (no official Linux)                                                    | Android, iOS                                                                                                                        |
| For       | GUI over local Git, good for Git newcomers                                            | Triage and review on the go                                                                                                         |
| Tasks     | Clone, branch, diffs, pick lines to commit, co-authors, commit, push/pull, start a PR | Notifications (push), read/comment/review issues and PRs, edit files in a PR, code search in a repo, approve sign-ins, Copilot Chat |
| Not for   | Notifications inbox, approving sign-ins                                               | Cloning and committing local work, running Actions jobs                                                                             |

- **Mobile + Enterprise Server** works only if an enterprise owner enables mobile support (and the version is supported).
- **When neither fits:** scripting and automation → **GitHub CLI** (`gh`). Quick browser edits → github.dev. Full cloud environment → Codespaces.
- **Confusions:**
  - Pro (personal) vs Team (organization): decided by who owns the repo.
  - Enterprise Cloud vs Server vs data residency: who runs it and where data lives.
  - Draft PR vs a "WIP" title: only the draft is enforced.
  - Collapsed section (hidden until clicked) vs HTML comment (never shown).

📖 Full lesson: [Working with GitHub: Accounts, Plans, the GitHub Flow, Markdown, Desktop and Mobile (GitHub Foundations GH-900)](https://www.savemycert.com/revision/github-foundations/github-accounts-flow-markdown-desktop-mobile/?utm_source=github&utm_medium=readme&utm_campaign=gh-900-study-guide)

[← Back to the study guide](../README.md)
