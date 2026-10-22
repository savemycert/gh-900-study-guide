# GH-900 Commonly Confused Services and Concepts

Side-by-side comparisons of the GH-900 services and ideas that exam questions most often set against each other. Each table ends with the one thing to remember.

- [Domain 1: Understand Git and GitHub basics](#domain-1-understand-git-and-github-basics)
- [Domain 2: Work with GitHub repositories](#domain-2-work-with-github-repositories)
- [Domain 3: Collaborate using GitHub](#domain-3-collaborate-using-github)
- [Domain 4: Apply modern development practices](#domain-4-apply-modern-development-practices)
- [Domain 5: Manage projects with GitHub](#domain-5-manage-projects-with-github)
- [Domain 6: Understand privacy, security, and administration](#domain-6-understand-privacy-security-and-administration)
- [Domain 7: Explore the GitHub community](#domain-7-explore-the-github-community)

## Domain 1: Understand Git and GitHub basics

### Git vs GitHub

|            | Git                                                    | GitHub                                                    |
| ---------- | ------------------------------------------------------ | --------------------------------------------------------- |
| What it is | Distributed version control software                   | Hosting platform built around Git                         |
| Runs       | Locally, online or offline                             | GitHub's cloud, or self-hosted as Enterprise Server       |
| Account    | None needed                                            | Needed to contribute                                      |
| Owns       | Commits, staging, branches, merge, diff, log, blame    | Pull requests, reviews, issues, Actions, permissions      |
| Exam cue   | "on a laptop with no internet", "combine two branches" | "request a review", "track a bug", "control who can push" |

**Remember:** ask whether it works on a plain clone with only Git installed. Merging is Git even though a pull request ends in one.

### git fetch vs git pull

|                     | git fetch                                          | git pull                                         |
| ------------------- | -------------------------------------------------- | ------------------------------------------------ |
| Downloads commits?  | Yes, into remote-tracking branches (`origin/main`) | Yes                                              |
| Changes your branch | No                                                 | Yes, merges (or rebases) into the current branch |
| Use it when         | You want to inspect before integrating             | You want the latest work in your branch now      |
| Exam cue            | "review incoming changes first"                    | "update my local branch"                         |

**Remember:** pull = fetch + integrate. After a fetch, `git log main` still doesn't show the new commits.

### Branch vs Tag vs Fork

|          | Branch                               | Tag                           | Fork                                         |
| -------- | ------------------------------------ | ----------------------------- | -------------------------------------------- |
| What     | Movable pointer to a line of work    | Fixed label on one commit     | Copy of the whole repo under another account |
| Moves?   | Yes, with each new commit            | No                            | Separate repository                          |
| Use      | Parallel work in the same repo       | Mark a release such as `v1.0` | Contribute without write access              |
| Exam cue | "try an idea without affecting main" | "mark the shipped version"    | "no push access to the original"             |

**Remember:** branch moves, tag stays, fork is a new repository.

### Personal account vs Organization vs Enterprise account

|            | Personal account         | Organization                         | Enterprise account                         |
| ---------- | ------------------------ | ------------------------------------ | ------------------------------------------ |
| Represents | One person               | A group that shares ownership        | A company managing many organizations      |
| Sign in?   | Yes                      | No                                   | No                                         |
| Owns       | Own repos                | Group repos                          | Organizations                              |
| Exam cue   | "a developer's identity" | "work must not depend on one person" | "central policy and billing for many orgs" |

**Remember:** nobody signs in to an organization or enterprise. People act through their one personal account.

### GitHub Pro vs GitHub Team vs GitHub Enterprise

|          | GitHub Pro                                           | GitHub Team                                    | GitHub Enterprise                                          |
| -------- | ---------------------------------------------------- | ---------------------------------------------- | ---------------------------------------------------------- |
| For      | Personal accounts                                    | Organizations                                  | Organizations under an enterprise account                  |
| Adds     | Advanced tools on the person's private repos         | The same tools on the org's private repos      | Team + SAML SSO, SCIM, internal repos, enterprise policies |
| Exam cue | "my own private repository needs protected branches" | "lowest-cost org plan with required reviewers" | "SSO", "internal repositories", "many organizations"       |

**Remember:** features follow the plan of the account that owns the repository.

### Enterprise Cloud vs Enterprise Cloud with data residency vs Enterprise Server

|          | Enterprise Cloud       | With data residency                  | Enterprise Server                       |
| -------- | ---------------------- | ------------------------------------ | --------------------------------------- |
| Run by   | GitHub                 | GitHub                               | Customer's IT team                      |
| Data     | GitHub.com             | Chosen region, own GHE.com subdomain | Customer's data center or private cloud |
| Exam cue | "no servers to manage" | "data must stay in the EU"           | "must run on our own infrastructure"    |

**Remember:** residency answers _where data is stored_; Server answers _who runs the platform_.

### Draft pull request vs Ready pull request

|                     | Draft                                    | Ready for review                    |
| ------------------- | ---------------------------------------- | ----------------------------------- |
| Can be merged?      | No, GitHub blocks it                     | Yes, once approvals and checks pass |
| Code owner requests | Not sent                                 | Sent                                |
| Comments and checks | Yes                                      | Yes                                 |
| Exam cue            | "early feedback, must not be merged yet" | "finished, ready to review"         |

**Remember:** a draft is an enforced block, not a naming convention.

### GitHub Desktop vs GitHub Mobile vs GitHub CLI

|          | GitHub Desktop                     | GitHub Mobile                                       | GitHub CLI               |
| -------- | ---------------------------------- | --------------------------------------------------- | ------------------------ |
| Runs on  | Windows, macOS                     | Android, iOS                                        | Terminals, scripts, CI   |
| For      | Local Git through a GUI            | Notifications, reviews, sign-in approvals on the go | Scripting and automation |
| Exam cue | "prefers not to type Git commands" | "away from the computer", "approve a sign-in"       | "automate in a script"   |

**Remember:** Desktop works with local repositories, Mobile works with GitHub itself, and scripts need the CLI.

### Collapsed section vs HTML comment vs Alert

|        | Collapsed section (`<details>`) | HTML comment (`<!-- -->`)             | Alert (`> [!WARNING]`)            |
| ------ | ------------------------------- | ------------------------------------- | --------------------------------- |
| Shown? | Hidden until clicked            | Never rendered                        | Always, highlighted               |
| Use    | Long logs, optional detail      | Guidance for whoever edits a template | Callouts such as breaking changes |

**Remember:** hidden-until-clicked is still visible content; a comment never reaches readers.

## Domain 2: Work with GitHub repositories

### README vs CONTRIBUTING vs CODE_OF_CONDUCT vs SUPPORT vs SECURITY

|          | README                         | CONTRIBUTING                | CODE_OF_CONDUCT             | SUPPORT               | SECURITY                                                       |
| -------- | ------------------------------ | --------------------------- | --------------------------- | --------------------- | -------------------------------------------------------------- |
| Answers  | What is this, how do I use it? | How do I submit a change?   | How must I behave?          | Where do I get help?  | Which versions are supported, how do I report a vulnerability? |
| Surfaced | Repo main page                 | When opening issues and PRs | Overview, community profile | When opening an issue | The repo's Security area                                       |

**Remember:** each file answers one question. SECURITY.md is a policy document, not a scanner.

### CODEOWNERS vs Require review from Code Owners

|          | CODEOWNERS file                         | "Require review from Code Owners"           |
| -------- | --------------------------------------- | ------------------------------------------- |
| What     | Maps paths to owners                    | A branch protection or ruleset setting      |
| Effect   | Owners are **requested** automatically  | Owner approval is **required** before merge |
| Exam cue | "automatically ask the right reviewers" | "cannot merge without the owner's approval" |

**Remember:** the file requests; only a protection rule enforces.

### Template repository vs Fork vs Clone

|           | Generate from template                    | Fork                                   | Clone                      |
| --------- | ----------------------------------------- | -------------------------------------- | -------------------------- |
| History   | One fresh commit                          | Full parent history                    | Full history               |
| Link back | None                                      | Linked; can open PRs to the parent     | Remote only, local copy    |
| Branches  | Default only unless Include all branches  | Default by default                     | All                        |
| Exam cue  | "new independent project from a skeleton" | "contribute back without write access" | "work on it on my machine" |

**Remember:** templates start fresh and never sync; forks keep history and a route back.

### Browser upload vs Git push vs Git LFS

|                | Browser upload                 | Git push                     | Git LFS          |
| -------------- | ------------------------------ | ---------------------------- | ---------------- |
| Per-file limit | 25 MiB                         | 100 MiB (warns above 50 MiB) | Larger files     |
| Exam cue       | "small file, no Git installed" | "a 60 MiB file"              | "a 300 MiB file" |

**Remember:** choose the simplest method the file size allows.

### Pulse vs Contributors vs Traffic vs Dependency graph

|          | Pulse                         | Contributors                 | Traffic                                      | Dependency graph                  |
| -------- | ----------------------------- | ---------------------------- | -------------------------------------------- | --------------------------------- |
| Shows    | Activity summary for a period | Commits per person over time | Views, visitors, clones, referrers (14 days) | Packages used and dependents      |
| Who sees | Per repo permission and plan  | Per repo permission and plan | **Push access only**                         | Per repo permission and plan      |
| Exam cue | "what happened this week"     | "who commits most"           | "where visitors come from"                   | "which packages, exportable SBOM" |

**Remember:** on GitHub Free, repository graphs exist only for public repositories.

### Star vs Watch

|               | Star                                          | Watch                     |
| ------------- | --------------------------------------------- | ------------------------- |
| Does          | Bookmarks, shows appreciation, feeds rankings | Controls notifications    |
| Notifications | None                                          | At the level you choose   |
| Exam cue      | "save it for later"                           | "hear about new releases" |

**Remember:** starring subscribes you to nothing.

### Archive vs Make private vs Delete

|                 | Archive                          | Make private                                        | Delete                 |
| --------------- | -------------------------------- | --------------------------------------------------- | ---------------------- |
| Public can read | Yes, read-only                   | No                                                  | No                     |
| Reversible      | Yes, unarchive                   | Partly; stars and watchers are lost, forks detached | Usually within 90 days |
| Exam cue        | "finished but keep it available" | "hide from the public"                              | "remove completely"    |

**Remember:** archive is the standard way to retire a project that people still use.

## Domain 3: Collaborate using GitHub

### Issue vs Pull request vs Discussion

|            | Issue                                        | Pull request                     | Discussion                             |
| ---------- | -------------------------------------------- | -------------------------------- | -------------------------------------- |
| For        | Actionable work with an owner                | Proposing and reviewing a change | Questions, ideas, announcements, polls |
| Assignees  | Yes, up to ten                               | Yes, plus reviewers              | No                                     |
| Closes via | Merged PR with a closing keyword, or by hand | Merge or close                   | Never by a PR; Q&A can mark an answer  |
| Exam cue   | "bug that someone must fix"                  | "review this code change"        | "how do I…?", "should we…?"            |

**Remember:** concrete work with an end is an issue; open conversation is a discussion.

### Closing keyword in PR description vs in commit message vs plain #mention

|                     | PR description keyword          | Commit message keyword                          | Plain `#42`                 |
| ------------------- | ------------------------------- | ----------------------------------------------- | --------------------------- |
| Closes the issue    | Yes, on merge to default branch | Yes, when the commit reaches the default branch | No                          |
| Listed as linked PR | Yes                             | No                                              | No, timeline reference only |

**Remember:** put "Fixes #42" in the PR description to get both the link and the close, and only merges into the default branch count.

### Comment vs Approve vs Request changes

|          | Comment                    | Approve                 | Request changes                |
| -------- | -------------------------- | ----------------------- | ------------------------------ |
| Signals  | Feedback, no verdict       | OK to merge             | Must be addressed before merge |
| Exam cue | "a question, not blocking" | "the change looks good" | "this must be fixed first"     |

**Remember:** the review state, not the comment text, tells the author and protection rules where the PR stands.

### review-requested: vs reviewed-by: vs assignee:

|          | `review-requested:USER`            | `reviewed-by:USER`        | `assignee:USER`            |
| -------- | ---------------------------------- | ------------------------- | -------------------------- |
| Finds    | PRs still waiting on that reviewer | PRs they already reviewed | Items they own             |
| Exam cue | "my review queue"                  | "what I've reviewed"      | "work I'm responsible for" |

**Remember:** requested = pending, reviewed-by = done, assignee = ownership.

### Participating and @mentions vs Custom vs Ignore

|          | Participating and @mentions       | Custom                                  | Ignore                      |
| -------- | --------------------------------- | --------------------------------------- | --------------------------- |
| Notifies | Threads you're in or mentioned in | That, plus chosen types (e.g. Releases) | Nothing, not even mentions  |
| Exam cue | "quiet, but keep my mentions"     | "only tell me about new releases"       | "never hear from this repo" |

**Remember:** Ignore goes further than people expect: it drops @mentions too.

### Save vs Done vs Unsubscribe (notifications inbox)

|          | Save                           | Done                   | Unsubscribe                                         |
| -------- | ------------------------------ | ---------------------- | --------------------------------------------------- |
| Effect   | Kept indefinitely (`is:saved`) | Cleared from the inbox | Cleared and no future notifications from the thread |
| Exam cue | "come back to this later"      | "dealt with"           | "stop hearing about this thread"                    |

**Remember:** unsaved notifications are kept for five months.

### Secret gist vs Private repository

|                   | Secret gist               | Private repository         |
| ----------------- | ------------------------- | -------------------------- |
| Who can view      | Anyone with the URL       | Only people granted access |
| Listed/searchable | No                        | No                         |
| Exam cue          | "share a snippet by link" | "must stay confidential"   |

**Remember:** secret means unlisted, not private.

### Gist vs Wiki vs GitHub Pages

|             | Gist                            | Wiki                                                | GitHub Pages                        |
| ----------- | ------------------------------- | --------------------------------------------------- | ----------------------------------- |
| For         | Snippets and small files        | Longer docs beside the code                         | A published static website          |
| Findability | Public gists listed in Discover | Indexed only with 500+ stars and restricted editing | Recommended for search-indexed docs |
| Exam cue    | "share one script"              | "usage guides next to the code"                     | "public site or documentation site" |

**Remember:** a Pages site is public even from a private repo, unless privately published from an Enterprise Cloud organization.

## Domain 4: Apply modern development practices

### GitHub Actions vs Copilot vs Codespaces vs github.dev

|          | GitHub Actions            | GitHub Copilot                          | GitHub Codespaces                   | github.dev                      |
| -------- | ------------------------- | --------------------------------------- | ----------------------------------- | ------------------------------- |
| Does     | Runs automation on events | Suggests code, answers, completes tasks | Cloud dev environment with compute  | Free browser editor, no compute |
| Exam cue | "test every pull request" | "suggest the rest of this function"     | "build and debug from a Chromebook" | "fix a typo quickly"            |

**Remember:** runs automation, writes code, gives a machine, or just edits text.

### Job vs Step vs Action

|          | Job                                   | Step                           | Action                                  |
| -------- | ------------------------------------- | ------------------------------ | --------------------------------------- |
| What     | A set of steps on one runner          | One command or action in a job | Reusable unit a step calls with `uses:` |
| Order    | Parallel by default; `needs:` to wait | Sequential within the job      | n/a                                     |
| Exam cue | "run lint and build at the same time" | "run tests after installing"   | "reuse checkout from Marketplace"       |

**Remember:** jobs are parallel unless `needs:` says otherwise; steps are always in order.

### GitHub-hosted runner vs Self-hosted runner vs Larger runner

|               | GitHub-hosted (standard)               | Self-hosted                            | Larger runner                      |
| ------------- | -------------------------------------- | -------------------------------------- | ---------------------------------- |
| Machine       | GitHub's fresh VM per job              | Yours                                  | GitHub's, with more CPU and memory |
| Maintained by | GitHub                                 | You                                    | GitHub                             |
| Minutes       | Free in public repos; quota in private | Use no minutes                         | Always billed                      |
| Exam cue      | "no infrastructure to manage"          | "special hardware", "internal network" | "more power on GitHub's machines"  |

**Remember:** self-hosted means your hardware; larger still means GitHub's hardware.

### Ask mode vs Agent mode vs Copilot cloud agent

|            | Ask mode             | Agent mode                           | Copilot cloud agent                          |
| ---------- | -------------------- | ------------------------------------ | -------------------------------------------- |
| Does       | Answers and suggests | Edits files, runs commands, iterates | Researches, implements, opens a pull request |
| Where      | Your IDE             | Your IDE, while your session is open | Ephemeral cloud environment on GitHub        |
| Started by | A chat question      | A task in chat                       | Assigning an issue to Copilot, agents panel  |
| Exam cue   | "explain this code"  | "fix the failing tests in my editor" | "work on it while nobody has an editor open" |

**Remember:** agent mode acts in your IDE; the cloud agent works in the background and delivers a PR it never merges.

### Copilot individual plans vs Copilot Business vs Copilot Enterprise

|                | Individual (Free, Pro, Pro+, Max) | Copilot Business                             | Copilot Enterprise                            |
| -------------- | --------------------------------- | -------------------------------------------- | --------------------------------------------- |
| Bought by      | The person                        | An organization, per seat                    | An enterprise on GitHub Enterprise Cloud      |
| Central policy | No                                | Yes, plus content exclusion and audit logs   | Everything in Business                        |
| Exam cue       | "freelancer paying for herself"   | "company without GHEC wants central control" | "GHEC enterprise wants the largest allowance" |

**Remember:** Copilot Pro is an individual Copilot plan; GitHub Pro is an account plan that doesn't include Copilot.

### devcontainer.json vs Dotfiles vs Settings Sync vs Prebuilds

|          | devcontainer.json                  | Dotfiles                          | Settings Sync                         | Prebuilds                           |
| -------- | ---------------------------------- | --------------------------------- | ------------------------------------- | ----------------------------------- |
| Scope    | Everyone using the repo            | Every codespace I create          | My VS Code everywhere                 | A repo, branch and config           |
| Holds    | Image, features, extensions, ports | Shell aliases, prompt, Git config | Themes, keybindings, VS Code settings | A ready-built snapshot              |
| Exam cue | "same tools for the whole team"    | "my aliases in every codespace"   | "my editor theme follows me"          | "codespaces take too long to start" |

**Remember:** team config lives in the repo; personal config follows the user; prebuilds are about speed.

### Codespace stopped vs Codespace deleted

|                | Stopped                          | Deleted                                                    |
| -------------- | -------------------------------- | ---------------------------------------------------------- |
| Compute billed | No                               | No                                                         |
| Storage billed | Yes                              | No                                                         |
| Files          | Kept                             | Gone                                                       |
| Happens        | After 30 idle minutes by default | Automatically after 30 days inactive by default, or by you |

**Remember:** stopping saves compute, only deleting stops storage charges.

### github.dev vs Codespaces

|                 | github.dev                     | Codespaces                                        |
| --------------- | ------------------------------ | ------------------------------------------------- |
| Cost            | Free                           | Compute and storage billed (personal free quota)  |
| Terminal        | None                           | Yes                                               |
| Build/run/debug | No                             | Yes                                               |
| Opened by       | Press `.` on a repo or PR      | Browser, VS Code desktop or `gh codespace create` |
| Exam cue        | "edit docs in the browser now" | "run the test suite in the cloud"                 |

**Remember:** when the work needs to run something, continue in a codespace.

## Domain 5: Manage projects with GitHub

### Label vs Milestone vs Project

|          | Label                       | Milestone                          | Project                                      |
| -------- | --------------------------- | ---------------------------------- | -------------------------------------------- |
| Scope    | One repository              | One repository                     | Many repositories, user or org owned         |
| Per item | Many                        | At most one                        | Item can be in several                       |
| Dates    | None                        | Optional due date and % complete   | Date and iteration fields, roadmap, insights |
| Exam cue | "categorize as bug or docs" | "everything for v2.0 in this repo" | "track work across five repositories"        |

**Remember:** labels and milestones stop at the repository boundary; projects cross it.

### Table vs Board vs Roadmap

|           | Table                      | Board                              | Roadmap                                   |
| --------- | -------------------------- | ---------------------------------- | ----------------------------------------- |
| Best for  | Detail, triage, bulk edits | Flow between stages                | Work over time                            |
| Driven by | Any fields                 | A single select or iteration field | Start and target date or iteration fields |
| Exam cue  | "see many fields at once"  | "drag cards from Todo to Done"     | "spot overlapping dates this quarter"     |

**Remember:** detail, flow, time. Only the roadmap draws dates as bars.

### Iteration field vs Single select of sprint names

|                      | Iteration field                      | Single select              |
| -------------------- | ------------------------------------ | -------------------------- |
| Dates behind it      | Yes, start date and duration         | No                         |
| Breaks (holidays)    | Yes                                  | No                         |
| `@current` / `@next` | Yes                                  | No                         |
| Exam cue             | "views that always show this sprint" | "fixed list of priorities" |

**Remember:** anything time-based and repeating is an iteration field.

### Saved reply vs Issue template

|          | Saved reply                         | Issue or pull request template        |
| -------- | ----------------------------------- | ------------------------------------- |
| Who      | You, when commenting                | Anyone opening a new issue or PR      |
| Stored   | Your personal account settings      | Files in the repository               |
| Shared?  | No, private to you                  | Yes, for everyone                     |
| Exam cue | "reuse my standard reply to triage" | "make every bug report include steps" |

**Remember:** saved replies fill comment boxes; templates fill new issues and PRs.

### Current chart vs Historical chart

|          | Current                         | Historical                          |
| -------- | ------------------------------- | ----------------------------------- |
| Shows    | A snapshot now                  | A trend over time                   |
| X-axis   | A field such as Status          | Time                                |
| Exam cue | "points per status this sprint" | "burn up since the project started" |

**Remember:** the default insights chart is a historical burn up.

### Milestone vs Release

|          | Milestone                            | Release                                 |
| -------- | ------------------------------------ | --------------------------------------- |
| Is       | Planned work toward a due date       | Packaged, shipped software at a Git tag |
| Exam cue | "track progress toward the deadline" | "publish v1.2 with release notes"       |

**Remember:** milestones plan the work, releases ship it.

## Domain 6: Understand privacy, security, and administration

### Triage vs Write vs Maintain vs Admin

|          | Triage                              | Write                    | Maintain                                             | Admin                                                            |
| -------- | ----------------------------------- | ------------------------ | ---------------------------------------------------- | ---------------------------------------------------------------- |
| Push     | No                                  | Yes                      | Yes                                                  | Yes                                                              |
| Adds     | Labels, assign, close, duplicates   | Push, merge, releases    | Settings such as topics, wikis, merge options, Pages | Access, branch protection, rulesets, visibility, delete/transfer |
| Exam cue | "manage issues without code access" | "contributor who merges" | "project manager, nothing destructive"               | "set up branch protection"                                       |

**Remember:** branch protection and rulesets need Admin. Maintain is one step short.

### Member vs Outside collaborator

|                            | Member             | Outside collaborator           |
| -------------------------- | ------------------ | ------------------------------ |
| Base permission            | Yes                | No                             |
| Can join teams             | Yes                | No                             |
| Org requires 2FA, has none | Stays, but blocked | Removed from repos             |
| Exam cue                   | "employee"         | "contractor on one repository" |

**Remember:** outside collaborators only ever get the specific repositories they're added to.

### Base permission vs Team access

|            | Base permission                               | Team access                                    |
| ---------- | --------------------------------------------- | ---------------------------------------------- |
| Applies to | Every member, every repo (including new ones) | Team members, repos granted to the team        |
| Acts as    | A floor; higher grants win                    | A grant per repository                         |
| Exam cue   | "all members can read every repo"             | "only the web team can write to the site repo" |

**Remember:** base permissions never reach outside collaborators.

### Visible team vs Secret team

|          | Visible team                      | Secret team                        |
| -------- | --------------------------------- | ---------------------------------- |
| Seen by  | All org members                   | Its members and org owners         |
| Can nest | Yes                               | No parent, no children             |
| Exam cue | "mention the whole platform team" | "confidential acquisition project" |

**Remember:** hiding a team rules out inherited access.

### Public vs Private vs Internal

|          | Public        | Private                         | Internal                                     |
| -------- | ------------- | ------------------------------- | -------------------------------------------- |
| Who sees | Everyone      | People and teams granted access | Every enterprise member, across all its orgs |
| Needs    | Any plan      | Any plan                        | An enterprise-owned organization             |
| Exam cue | "open source" | "only this team"                | "whole company, never the public"            |

**Remember:** internal is the InnerSource visibility.

### Synced passkey vs Device-bound passkey

|               | Synced                             | Device-bound                             |
| ------------- | ---------------------------------- | ---------------------------------------- |
| Stored        | Cloud service or password manager  | One authenticator such as a hardware key |
| Lose a device | Still available elsewhere          | Gone with that authenticator             |
| Exam cue      | "available on my phone and laptop" | "cannot be copied"                       |

**Remember:** GitHub doesn't sync passkeys; the authenticator does.

### Branch protection rule vs Ruleset

|            | Branch protection rule          | Ruleset                                                    |
| ---------- | ------------------------------- | ---------------------------------------------------------- |
| Per branch | Only one applies                | Many can layer, most restrictive wins                      |
| Exemptions | Admins bypass unless blocked    | Named bypass list                                          |
| Pausing    | Edit or delete                  | Set enforcement to Disabled                                |
| Targets    | Branches                        | Branches or tags                                           |
| Exam cue   | "require two approvals on main" | "several policies on one branch", "exempt the release bot" |

**Remember:** a looser ruleset can never relax a stricter one.

### Enterprise Managed Users vs Personal accounts with SAML SSO

|              | Enterprise Managed Users                    | Personal accounts + SAML SSO                          |
| ------------ | ------------------------------------------- | ----------------------------------------------------- |
| Accounts     | Created and owned by the company IdP (SCIM) | Developers' own accounts                              |
| Outside work | Read public repos only; no contributing     | Full open source participation                        |
| Exam cue     | "company must control every identity"       | "developers use one account for work and open source" |

**Remember:** EMU trades open source participation for full identity control.

## Domain 7: Explore the GitHub community

### Follow vs Watch vs Star

|          | Follow                                  | Watch                        | Star                       |
| -------- | --------------------------------------- | ---------------------------- | -------------------------- |
| Target   | A user or organization                  | A repository                 | A repository               |
| You get  | Their public activity on your dashboard | Notifications                | A bookmark, appreciation   |
| Exam cue | "see what this developer is doing"      | "tell me about new releases" | "save this repo for later" |

**Remember:** follow people, watch repositories for notifications, star to bookmark.

### GitHub Sponsors vs GitHub Marketplace

|             | GitHub Sponsors                       | GitHub Marketplace                          |
| ----------- | ------------------------------------- | ------------------------------------------- |
| Purpose     | Fund developers and organizations     | Find and add actions and apps               |
| Money flows | From sponsor to maintainer            | From customer to app publisher (paid plans) |
| Exam cue    | "support the maintainer of a library" | "add a code quality check to workflows"     |

**Remember:** Sponsors pays people; Marketplace extends GitHub.

### Personal-account sponsorship vs Organization sponsorship

|            | From a personal account               | From an organization account   |
| ---------- | ------------------------------------- | ------------------------------ |
| GitHub fee | None                                  | Can carry a fee                |
| Exam cue   | "maintainer receives the full amount" | "company sponsors the project" |

**Remember:** the fee depends on who pays, not who receives.

### Open source vs InnerSource

|            | Open source                 | InnerSource                                                    |
| ---------- | --------------------------- | -------------------------------------------------------------- |
| Who sees   | Everyone                    | Only people inside the company                                 |
| Visibility | Public                      | Usually internal                                               |
| Practices  | Forks, PRs, open discussion | The same practices, plus trusted committers inside the company |
| Exam cue   | "anyone can reuse it"       | "other teams can contribute, nobody outside sees it"           |

**Remember:** InnerSource is a set of practices, not a branching model or a visibility setting on its own.

### Fork vs Template

|           | Fork                                     | Template                                 |
| --------- | ---------------------------------------- | ---------------------------------------- |
| History   | Full                                     | One fresh commit                         |
| Link back | Yes, PRs to upstream                     | None                                     |
| Exam cue  | "fix a bug in a project I can't push to" | "start a new service from a starter kit" |

**Remember:** fork to contribute back, template to start fresh.

### Topics vs Labels

|          | Topics                                 | Labels                             |
| -------- | -------------------------------------- | ---------------------------------- |
| Classify | The repository itself                  | Issues, PRs, discussions inside it |
| Effect   | Repo appears on GitHub's subject pages | Filtering and triage               |
| Exam cue | "help people find the repo by subject" | "mark issues as bugs"              |

**Remember:** only topics make a repository discoverable by subject.

### Standard hosted runner vs Self-hosted runner vs Larger runner (public repos)

|                      | Standard GitHub-hosted      | Self-hosted                    | Larger runner               |
| -------------------- | --------------------------- | ------------------------------ | --------------------------- |
| Cost on public repos | Free                        | Free (you pay for the machine) | Always billed               |
| Exam cue             | "no budget, public project" | "use our own hardware"         | "more power, GitHub-hosted" |

**Remember:** larger runners are never free, even for open source.

[← Back to the study guide](README.md)
