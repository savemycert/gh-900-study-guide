# Domain 2: Work with GitHub repositories (14%)

One topic covering everything about a repository itself: the conventional files GitHub recognizes, templates and the default branch, adding files, the Insights tab, stars and feature previews, and how to maintain or retire a project. Most questions describe a maintainer's need and ask which file, setting or view meets it. The hard ones turn on exact rules: which README wins, which CODEOWNERS line applies, what a template copies.

## 2.1 Repository management

- **A GitHub repository** = a Git repository (files, history, branches) plus GitHub features around it (issues, PRs, settings, Insights).

| File                 | Answers                                                              | Where GitHub looks             |
| -------------------- | -------------------------------------------------------------------- | ------------------------------ |
| `README.md`          | What is this, how do I install and use it? Rendered on the main page | `.github`, root, `docs`        |
| `LICENSE`            | What may others legally do with the code?                            | Root                           |
| `CONTRIBUTING.md`    | How do I submit a change here?                                       | `.github`, root, `docs`        |
| `CODE_OF_CONDUCT.md` | How must I behave?                                                   | `.github`, root, `docs`        |
| `SUPPORT.md`         | Where do I get help?                                                 | `.github`, root, `docs`        |
| `SECURITY.md`        | Which versions get fixes, how do I report a vulnerability privately? | `.github`, root, `docs`        |
| `CODEOWNERS`         | Who owns which paths (auto review requests)?                         | `.github`, root, `docs`        |
| `.gitignore`         | What should Git never track?                                         | Usually root (also per folder) |

- **Community health files**: CONTRIBUTING, CODE_OF_CONDUCT, SUPPORT, SECURITY, issue/PR templates, `FUNDING.yml`. Pick the file whose question matches the need.
- **README:**
  - Rendered on the repo's main page. GitHub builds an outline from its headings. Very large READMEs are truncated.
  - Several READMEs → GitHub shows the first found in this order: **`.github/README.md` → root `README.md` → `docs/README.md`**. "I edited the root README and nothing changed" usually means a `.github` copy exists.
  - **Profile README**: a **public** repo named exactly your username with a non-empty `README.md` in its root. Organization profile: `profile/README.md` in the org's public `.github` repo.
- **LICENSE:**
  - No license → **default copyright**: the author keeps all rights. Nobody may reproduce, distribute or build on the code.
  - GitHub's Terms of Service still let users **view and fork** a public repo on GitHub, but that is not permission to reuse the code.
  - GitHub applies no default license. Choose one at creation or add `LICENSE` to the root later (shown in the About sidebar).
- **CONTRIBUTING.md** is linked when someone opens an issue or PR. **SUPPORT.md** is linked when someone opens an issue. **SECURITY.md** appears in the repo's Security area.
- **SECURITY.md is documentation only.** It does not turn on Dependabot, code scanning or anything else.
- **CODEOWNERS:**
  - Maps path patterns to users or teams; GitHub **automatically requests reviews** from them on PRs that touch matching files.
  - Location: `.github/`, root, `docs/`. The first one found (in that order) is used.
  - **Last matching pattern wins.** Owners are not merged across lines. To give a path several owners, list them on one line.
  - Uses the CODEOWNERS on the PR's **base branch**. A CODEOWNERS file sitting on an unmerged feature branch has no effect on PRs into `main`.
  - Owners need **write** access. Teams must be visible with write access.
  - **Draft PRs get no owner requests** until marked ready.
  - **Requesting ≠ requiring.** Mandatory owner approval is a separate branch protection/ruleset setting: "Require review from Code Owners".
- **Default community health files** come from a **public** repo named **`.github`** in the account or org:
  - Supported defaults: CODE_OF_CONDUCT, CONTRIBUTING, SUPPORT, SECURITY, GOVERNANCE, FUNDING.yml, issue and PR templates (including `ISSUE_TEMPLATE` and `config.yml`).
  - Used only where a repo lacks its own file of that type. Defaults never merge with a repo's own files.
  - Issue templates: if the repo's own `.github/ISSUE_TEMPLATE` has any valid template or a `config.yml`, **none** of the default set is used.
  - **No default LICENSE.** A private `.github` repo supplies nothing.
  - A template repository is not a substitute: it seeds new repos once and does nothing for existing ones.
- **Community standards** (Insights → Community standards, public repos): checklist of description, README, code of conduct, contributing, license, security policy, issue/PR templates. Maintainers click **Add**; contributors without write access click **Propose**. It is informational and never blocks merging.
- **Creating a repo**: owner (you or an org), name unique within that owner, description, visibility (public, private, or internal for enterprise orgs), optional README, `.gitignore` template and license, or pick a template.

|          | Generate from template                              | Fork                           | Clone and push    |
| -------- | --------------------------------------------------- | ------------------------------ | ----------------- |
| History  | One new commit, no template history                 | Full parent history            | Full history      |
| Link     | None: no sync, no PRs back                          | Linked; can open PRs to parent | None on GitHub    |
| Branches | Default branch only unless **Include all branches** | Default branch by default      | Whatever you push |

- **Template details:** with Include all branches, each branch arrives with its own unrelated history, so PRs between template and new repo are impossible. Templates **cannot include Git LFS files**. It is a one-time copy; later template commits don't flow through.
- **Default branch**: what visitors see and the default PR base. New repos use `main` unless the account/org sets another name. Admins can switch or rename it.
- **Renaming a branch on GitHub** retargets open PRs, moves branch protection and redirects file links. It **cannot** update local clones (GitHub shows the commands), and hard-coded names in workflows or raw URLs need editing.
- **Adding files in the browser** (every change is a commit):
  - Add file → Create new file. Type `folder/` in the name to create folders.
  - Add file → Upload files, or drag and drop (up to 100 files at a time).
  - **Move/rename**: edit the file and type `folder/` before the name. Shown as a rename, unlike delete + re-upload. (Git infers renames from identical content.)
  - Issue attachments, release assets and wiki content are stored on GitHub but are **not** tracked repo files.
- **Commit options in the browser**: commit directly, or **create a new branch and start a pull request** (keeps the default branch untouched until review). Needs write access; others edit a fork.

| How added      | Size limit                              |
| -------------- | --------------------------------------- |
| Browser upload | 25 MiB per file                         |
| Git push       | 100 MiB per file (warning above 50 MiB) |
| Bigger         | Git LFS                                 |

- Pick the simplest method the size allows: 25–100 MiB needs Git, only over 100 MiB needs LFS.

| Insights view            | Shows                                                                                         |
| ------------------------ | --------------------------------------------------------------------------------------------- |
| Pulse                    | Summary of a period (default a week): PRs opened/merged, issues opened/closed, top committers |
| Contributors             | Commits per contributor over time                                                             |
| Traffic                  | Views, unique visitors, clones, referrers, popular content for 14 days. **Push access only**  |
| Commits / Code frequency | Commit activity over a year; additions and deletions per week                                 |
| Network / Forks          | Branch history across the repo and forks; list of forks                                       |
| Community standards      | The checklist above (public repos)                                                            |
| Dependency graph         | Dependencies and dependents                                                                   |

- **Plan limits:** on GitHub Free (personal and org), repository graphs are **public repos only**. Pro, Team and Enterprise Cloud show them for private repos. A missing graph is either a permission issue or a plan issue.
- **Dependency graph** is built from manifest and lock files. _Dependencies_: packages used, with versions, licenses and known vulnerabilities; exportable as an **SBOM**. _Dependents_ (public repos): who uses this repo. About packages, not people.
- **Organization dependency insights** (Enterprise Cloud orgs, org Insights tab): one view of open security advisories and licenses across the org's dependencies. Relies on the dependency graph. In maintenance mode.

| Action            | Does                                                                                     |
| ----------------- | ---------------------------------------------------------------------------------------- |
| Star              | Bookmark in _Your stars_, appreciation, feeds rankings/recommendations. No notifications |
| Watch             | Controls notifications about the repo                                                    |
| Fork              | Copy into your account to change it                                                      |
| Follow (a person) | Their activity on your dashboard                                                         |

- **Star lists** group stars (e.g. "Rust tools"). Lists are public; a private repo in a list is visible only to people who can already read it. **Topics** are set by maintainers to describe their own repo.
- **Release stages**: private preview (selected customers) → public preview (anyone, may change, no full support/SLAs) → general availability (GA). Many public-preview UI features toggle per user from **profile picture menu → Feature preview**, with a feedback link. It's a personal setting, not a repo setting.
- **Maintenance best practices:**
  - Description and **topics** in About for discovery.
  - `.gitignore` for build output, dependencies and local secrets.
  - Key files and templates. Use the community checklist to find gaps and `.github` defaults to cover many repos.
  - CODEOWNERS for routing, and protect the default branch.
  - Retire by **archiving**, not deleting. Before archiving, close open issues/PRs and update the README.

| Option       | Public can still read/fork?                       | Reversible?                                              |
| ------------ | ------------------------------------------------- | -------------------------------------------------------- |
| Archive      | Yes, read-only (no issues, PRs, comments, pushes) | Yes, unarchive                                           |
| Make private | No                                                | Partly: stars and watchers lost, public forks detached   |
| Delete       | No                                                | Usually within 90 days (not for some fork-network repos) |

- **Traps:**
  - "Make code owners' approval mandatory" → branch protection setting, not CODEOWNERS alone.
  - "Default LICENSE for every repo" → not possible.
  - "Who can see Traffic?" → push access, and private only on paid plans.
  - Starring does not subscribe you to anything.

📖 Full lesson: [GitHub Repository Management: README, CODEOWNERS, Templates and Insights (GH-900)](https://www.savemycert.com/revision/github-foundations/github-repository-management-readme-codeowners-templates/?utm_source=github&utm_medium=readme&utm_campaign=gh-900-study-guide)

[← Back to the study guide](../README.md)
