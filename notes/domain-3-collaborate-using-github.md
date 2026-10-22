# Domain 3: Collaborate using GitHub (14%)

One topic: the tools a team uses to plan, discuss, review and document work around a repository. Expect "which tool or setting fits" scenarios with near-twin options: issue or discussion, Comment or Request changes, `review-requested:` or `reviewed-by:`, Participating or Ignore, secret gist or private repo. Linking questions test the exact closing-keyword rules.

## 3.1 Collaboration tools

|           | Issue                                                            | Pull request                                            | Discussion                                  |
| --------- | ---------------------------------------------------------------- | ------------------------------------------------------- | ------------------------------------------- |
| Purpose   | Track a bug, task or feature to closure                          | Propose and review changes from one branch into another | Questions, ideas, announcements, polls      |
| Ownership | Assignees (up to ten)                                            | Assignees + requested reviewers                         | No assignees                                |
| Planning  | Labels, milestones, projects, issue types                        | Labels, milestones, projects                            | Categories and labels                       |
| Ends      | Closed (completed, not planned, duplicate), often by a merged PR | Merged or closed                                        | Can stay open; Q&A can have a marked answer |

- **Deciding question:** is there concrete work with an owner and an end? Yes → issue. "How do I…?" or "should we…?" → discussion until it becomes work.
- All three support Markdown, @mentions, reactions and `#number` cross-references.
- **Discussions** are a forum per repo (or org), enabled in settings, organized into **categories** with a **format**:

| Format              | Behaviour                                                          |
| ------------------- | ------------------------------------------------------------------ |
| Open-ended          | General conversation                                               |
| Question and answer | A comment can be **marked as the answer**                          |
| Announcement        | Only **maintain or admin** can start threads; everyone can comment |
| Poll                | Community votes                                                    |

- **Pinning** puts a discussion at the top. Moderators can lock, edit or delete.
- **Triage** access can **convert an issue into a discussion** (comments move with it). An issue can also be created from a discussion.
- Discussions have **no assignees, no milestones, no closing keywords**: a merged PR cannot close one.
- **Review states**: **Comment** (feedback, no verdict), **Approve** (can merge), **Request changes** (must be addressed before merge).
- **Suggested change**: a `suggestion` block in a line comment proposes exact replacement text. The author **commits it from the PR page**, singly or in a batch. A plain comment leaves the edit to the author.
- **Draft PR**: cannot be merged; code owners aren't requested until it's ready.
- **Closing keywords** in a PR **description** link the PR and close the issue **on merge into the default branch**:
  - `close`, `closes`, `closed`, `fix`, `fixes`, `fixed`, `resolve`, `resolves`, `resolved`. Case-insensitive; colon optional (`Fixes: #42`).
  - "refs", "tracks", "relates to" only cross-reference.
  - **Default branch only.** A PR into `release-2.0` ignores the keywords: no link, no close.
  - **One keyword per issue**: `Resolves #10, resolves #123`. A comma list after one keyword closes only the first.
  - **Other repo** needs `OWNER/REPO#N`. A bare `#12` is always the PR's own repo.
  - **Keyword in a commit message** closes the issue when the commit reaches the default branch, but the PR is **not** listed as linked.
- Linked PRs show in the issue's **Development** section, and vice versa.
- **Manual linking** from the Development sidebar needs **write** access; up to ten issues per PR:

| Start from          | Can link                                                 |
| ------------------- | -------------------------------------------------------- |
| The PR's sidebar    | Issues in the **same repo** only                         |
| The issue's sidebar | A PR or branch from **any repo** (choose the repo first) |

- So a cross-repo link without editing the description must start **from the issue**. Manual links close the issue on merge just like keywords. A plain `#number` mention does neither.
- **Templates take effect only on the default branch.**
  - **Issue templates**: Markdown files in `.github/ISSUE_TEMPLATE/` → template chooser. YAML front matter: `name` and `about` (shown in the chooser), `title`, `labels`, `assignees`, `type` (applied automatically). YAML **issue forms** (typed fields, public preview) go in the same folder.
  - **`config.yml`** in that folder: `blank_issues_enabled: false` discourages blank issues (write/maintain/admin still see the option); `contact_links` (`name`, `url`, `about`) sends people elsewhere, e.g. a forum.
  - **PR template**: `pull_request_template.md` in root, `docs/` or `.github/`. Several → `PULL_REQUEST_TEMPLATE/` subfolder, chosen with the `template` query parameter.
  - **Org defaults** from a public `.github` repo apply only where the repo has no file of that type. A repo with anything in its own `ISSUE_TEMPLATE` uses no default issue templates.
- **Search qualifiers** (space = AND, leading `-` negates):

| Qualifier                                       | Finds                                       |
| ----------------------------------------------- | ------------------------------------------- |
| `is:issue` / `is:pr`                            | Only issues / only PRs                      |
| `is:open`, `is:closed`, `is:draft`              | State; drafts                               |
| `label:bug` / `no:label`                        | With that label / unlabelled                |
| `author:USER`                                   | Opened by user                              |
| `assignee:USER`, `assignee:@me` / `no:assignee` | Owned by someone / unowned                  |
| `no:milestone`                                  | Not in a milestone                          |
| `review-requested:USER`                         | PRs **waiting** on that reviewer            |
| `reviewed-by:USER`                              | PRs **already** reviewed by them            |
| `mentions:USER` / `involves:USER`               | Mentioning them / involving them in any way |
| `linked:pr`                                     | Issues with a linked PR                     |

- **Assignees** (up to ten per item): yourself, anyone who commented, anyone with write access, org members with read access. Assignment = ownership. An @mention only notifies. A review request asks for feedback on a PR.
- **Watch levels:**

| Level                                 | Notified about                                                                    |
| ------------------------------------- | --------------------------------------------------------------------------------- |
| Participating and @mentions (default) | Threads you're in, mentioned, assigned or review-requested on                     |
| All Activity                          | Every issue, PR, discussion and comment                                           |
| Ignore                                | Nothing, **not even @mentions**                                                   |
| Custom                                | Participating + chosen types: Issues, PRs, Releases, Security alerts, Discussions |

- "Only new versions of a library" → Custom with Releases. "Quiet a busy repo but keep mentions" → Participating, not Ignore.
- **Subscribe/unsubscribe** to a single thread from its sidebar without changing the repo's watch level. Starring is not a notification setting.
- **Inbox triage** (github.com/notifications):
  - **Done** clears it; **Unsubscribe** also stops future notifications from that thread.
  - **Save** keeps it **indefinitely** (`is:saved`). Unsaved notifications are kept five months.
  - Read/unread changes read state only.
  - Filters like `reason:participating`, `reason:review-requested`, `repo:`; custom filters can be saved.
- **Delivery**: web, GitHub Mobile, email, chosen per activity type. **Custom routing** sends email for a given org's repos to a different verified address (an org can require its verified domain).
- **Gists**: share snippets or small files by URL. Every gist is a **Git repo** (revision history, clone, fork), can hold several files, can be embedded.

|                      | Public gist          | Secret gist             |
| -------------------- | -------------------- | ----------------------- |
| In Discover / search | Yes                  | No                      |
| Who can view         | Anyone               | **Anyone with the URL** |
| Visibility change    | Cannot become secret | Can become public       |

- **Secret ≠ private.** Credentials belong in a private repo; rotate any secret ever posted in a gist. Only the owner edits; others fork.
- **Wiki**: longer docs beside the code (README stays short). It's a Git repo you can clone. Public repos on every plan, private repos on paid plans.
  - Default editors: people with write access. Public repo + clear **Restrict editing to collaborators only** → any GitHub user can edit.
  - **Indexed by search engines only if the repo has 500+ stars AND editing is restricted to collaborators.** For findable docs GitHub recommends Pages.
- **GitHub Pages**: static site (HTML, CSS, JS) from a repo; no server-side code.
  - User/org site: repo named `<owner>.github.io` → `https://<owner>.github.io` (one per account). Project site: `https://<owner>.github.io/<repo>`. Custom domains supported.
  - Source: **Deploy from a branch** (root or `/docs`, optional Jekyll) or **GitHub Actions** (any generator, e.g. Hugo; no branch of built files).
  - **Public on the internet even from a private repo** (private-repo publishing needs a paid plan). Members-only (private publishing) needs an org on **Enterprise Cloud**.

| Need                                             | Use   |
| ------------------------------------------------ | ----- |
| Share one snippet by link, with history          | Gist  |
| Longer docs beside the code, editable in browser | Wiki  |
| Public website or search-indexed docs            | Pages |

- **Traps:**
  - PR into a non-default branch never auto-closes issues.
  - Ignore silences mentions too.
  - Save vs Done: Save keeps it; Done clears it.
  - A private repo does not make its Pages site private.

📖 Full lesson: [GitHub Collaboration Tools: Issues, Pull Requests, Discussions, Notifications and Pages (GH-900)](https://www.savemycert.com/revision/github-foundations/github-issues-pull-requests-discussions-collaboration/?utm_source=github&utm_medium=readme&utm_campaign=gh-900-study-guide)

[← Back to the study guide](../README.md)
