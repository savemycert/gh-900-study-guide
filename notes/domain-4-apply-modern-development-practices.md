# Domain 4: Apply modern development practices (14%)

One topic, four products: GitHub Actions runs automation, GitHub Copilot suggests code and completes tasks, GitHub Codespaces gives you a cloud development environment, and github.dev is a free browser editor. Questions describe a need and ask which tool, workflow term, Copilot mode or plan, or Codespaces setting fits. Read for who pays, where the work runs, and whose settings may change.

## 4.1 Automation and AI tools

- **Tell the four apart by purpose:** Actions _runs_ automation, Copilot _suggests and writes_ code, Codespaces is a _full environment with compute_, github.dev is a _quick editor with no compute_. None of them tracks work (that's Projects).
- **GitHub Actions** runs a workflow of jobs whenever a chosen event happens. Uses:
  - **CI/CD**: test every push or PR (result shows as a check on the PR), then deploy.
  - **Publish on release**: build a package or image when a release is published.
  - **Repository automation**: label or comment on new issues, add them to a project.
  - **Scheduled**: `schedule` trigger with cron syntax (e.g. nightly link check).
  - **Manual**: `workflow_dispatch` adds a Run workflow button.

| Term     | Meaning                                                                                           |
| -------- | ------------------------------------------------------------------------------------------------- |
| Event    | Activity (push, PR, issue opened, release), a schedule or a manual trigger that starts a workflow |
| Workflow | YAML file in **`.github/workflows`**; says which events trigger it and which jobs run             |
| Job      | Set of steps on **one runner**                                                                    |
| Step     | One shell command or action; steps run **in order** and share the runner                          |
| Action   | Reusable unit a step calls with `uses:` (many in Marketplace)                                     |
| Runner   | Machine that executes a job: GitHub-hosted or self-hosted                                         |

- **Only `.github/workflows` runs.** `.github/ISSUE_TEMPLATE` holds issue templates; `.devcontainer` configures codespaces.
- **Jobs run in parallel by default**, each on its own runner. Use `needs:` to make one wait. File order doesn't set job order. Steps within a job are always sequential.

|             | GitHub-hosted                                                             | Self-hosted                                                   |
| ----------- | ------------------------------------------------------------------------- | ------------------------------------------------------------- |
| Provided by | GitHub (Ubuntu, Windows, macOS VMs)                                       | You: physical, VM or container, your data center or cloud     |
| Lifecycle   | Fresh VM per job, then discarded                                          | Persists between jobs unless you set it up otherwise          |
| Maintenance | GitHub patches images                                                     | You install, patch, secure                                    |
| Fits        | Standard builds, no infrastructure                                        | Special hardware, custom OS/software, internal network access |
| Minutes     | Free (standard runners) in public repos; private repos use the plan quota | Use no minutes (you pay for your machine)                     |

- **Larger runners** are GitHub-hosted machines with more CPU/RAM. Still GitHub's machines.
- **Billing**: standard hosted runners are free in **public** repos. **Private** repos use the plan's monthly minutes and storage (GitHub Free included); overage is billed within spending limits. Public repos don't consume the quota.
- **Copilot inline suggestions**: ghost text from context. Prompt by **typing code** or **writing a comment describing the logic**. In VS Code: **Tab** accepts, **Esc** rejects, **Alt+] / Alt+[** (Option on macOS) cycles alternatives. Cycling inserts nothing.
- Not inline suggestions: Copilot Chat (e.g. `/explain`), Copilot code review (request Copilot as a reviewer), assigning an issue to Copilot (cloud agent).
- **Public code policy** (individual, or org/enterprise for members): **block** suggestions matching public code, or **allow** them with **references** to where the code appears so the developer can check its license. Compared against public repos on GitHub.com only.

| Surface             | Does                                                                        | Runs                                                       |
| ------------------- | --------------------------------------------------------------------------- | ---------------------------------------------------------- |
| Ask mode            | Answers and suggests; files unchanged unless you apply                      | Your IDE                                                   |
| Plan mode           | Writes a step-by-step plan to review before coding                          | Your IDE                                                   |
| Agent mode          | Autonomously edits files, runs commands (builds, tests), iterates on errors | Your IDE, while your session is open                       |
| Inline chat         | Changes or explains the selected code                                       | Your editor                                                |
| Copilot cloud agent | Researches, plans, implements in the background; opens a PR                 | Ephemeral cloud environment on GitHub (powered by Actions) |

- **Agent vs ask**: should Copilot change files and run commands (agent) or only answer (ask)?
- **Agent mode vs cloud agent**: agent mode needs your open IDE; the cloud agent works on GitHub with no editor open. The cloud agent may also be called the Copilot coding agent.
- **Cloud agent details:**
  - Start it by assigning an issue to Copilot, from the agents panel or a Chat conversation, or `@copilot` in a comment on a PR it's working on.
  - It creates a branch, commits and opens a **pull request**. It **never merges** itself; normal review, required checks and protection apply.
  - `copilot-setup-steps.yml` preinstalls tools for its environment.
  - Suits well-scoped backlog work: bug fixes, small features, tests, docs.
- **Multi-model support**: choose a model per conversation in the **model picker**. Models trade speed against reasoning depth, and some use more of the plan's monthly AI allowance (GitHub AI Credits).
  - **Auto** lets Copilot pick based on availability, which helps reduce rate limiting.
  - Changing the chat model does **not** change the model behind inline suggestions.
  - Business/Enterprise admins control available models by policy. A Business member with an empty picker → the org hasn't allowed model switching.

|            | Individual (Free, Pro, Pro+, Max)   | Copilot Business                                         | Copilot Enterprise                                          |
| ---------- | ----------------------------------- | -------------------------------------------------------- | ----------------------------------------------------------- |
| Bought by  | The person, personal account        | An org (or enterprise), per seat                         | An enterprise on **GitHub Enterprise Cloud**, per seat      |
| Management | User's own settings                 | Org-wide policy, **content exclusion**, audit logs       | Everything in Business                                      |
| Allowance  | Free is limited; paid tiers step up | Org plan allowance                                       | Larger monthly AI allowance + extra enterprise capabilities |
| Fits       | Freelancer or hobbyist              | Company managing Copilot centrally, with or without GHEC | GHEC enterprise wanting the most                            |

- The exam's "Copilot for Individuals" = today's individual plans. Free needs no payment; verified students can get free access.
- **Copilot Pro is not GitHub Pro.** GitHub Pro is an account plan and doesn't buy Copilot.
- Individual plans have no org policies or content exclusion.
- Without GHEC, a company needing central management chooses **Business**. On GHEC, the **enterprise owner chooses the plan per org**, so orgs can differ.
- **Codespace** = a Docker container on a GitHub-hosted VM, with the repo cloned, a terminal and compute. Open it in the **browser**, **VS Code desktop**, or **GitHub CLI** (`gh codespace create`, `gh codespace ssh`); JetBrains IDEs supported.
- **Lifecycle and billing:**
  - **Compute** billed only while **active**. **Storage** billed while it **exists**, stopped or not.
  - **Idle timeout** defaults to **30 minutes** → the codespace **stops** (files kept). Changeable; orgs can set a shorter maximum.
  - **Maximum running lifetime: 12 hours** (separate from idle timeout).
  - Stopped, inactive codespaces are **auto-deleted after 30 days** by default.
  - Personal accounts get a monthly free quota. To stop storage use now, **delete** unneeded codespaces.
- **Dev container**: `.devcontainer/devcontainer.json` (or `.devcontainer.json` in the root); several configs can live in `.devcontainer` subfolders. Sets:
  - base **image**, or a **Dockerfile** / Docker Compose file
  - **features** (packaged tools/runtimes)
  - VS Code **extensions and settings**
  - **ports** to forward, lifecycle commands such as `postCreateCommand`
- **No config** → a default Linux image with popular runtimes (Python, Node.js, Java…) plus Git and GitHub CLI.
- **Applying a config change**: existing codespaces don't pick it up. Run **Codespaces: Rebuild Container** (or `gh codespace rebuild`). A rebuild **keeps `/workspaces`** and clears changes elsewhere (e.g. your home directory). New codespaces don't include files from your other codespaces.

| Need                                            | Use                                                  | Scope                    |
| ----------------------------------------------- | ---------------------------------------------------- | ------------------------ |
| Same runtimes, extensions, ports for the team   | `devcontainer.json` in the repo                      | Everyone using the repo  |
| My shell aliases, prompt, Git config everywhere | **Dotfiles** repo, enabled in my Codespaces settings | Every codespace I create |
| My VS Code themes, keybindings, settings        | VS Code **Settings Sync**                            | My VS Code everywhere    |
| Faster creation for a big repo                  | **Prebuilds**                                        | Repo + branch + config   |

- **Dotfiles** repo can be private; GitHub clones it into each new codespace. Dotfiles don't personalise user-scoped VS Code settings; that's Settings Sync.
- **Prebuilds** run a **GitHub Actions workflow** that builds the codespace and saves a snapshot; new codespaces start from it. They use Actions minutes and storage.
- **github.dev**: press **`.`** on a repo or PR (or **`>`** for a new tab), or change `github.com` to `github.dev`. Free, instant, browser-only VS Code.

|                                | github.dev                                     | Codespaces                                    |
| ------------------------------ | ---------------------------------------------- | --------------------------------------------- |
| Starts                         | Instantly                                      | Seconds to minutes                            |
| Cost                           | Free                                           | Compute while active, storage while it exists |
| Terminal / build / run / debug | None                                           | Yes, dedicated VM                             |
| Extensions                     | Web-compatible only                            | Most Marketplace extensions                   |
| Config                         | No dev container                               | `devcontainer.json` or default image          |
| Best for                       | Typos, docs, small multi-file edits, reviewing | Building, running, testing, debugging         |

- **Rule:** start in github.dev; once you need to _run_ something, **Continue Working On** a codespace.
- **Traps:**
  - Workflow file in the wrong folder → never runs.
  - "Jobs run top to bottom" → false without `needs:`.
  - Self-hosted runner ≠ larger runner.
  - A stopped codespace still costs storage; a shorter idle timeout doesn't help.
  - Personal preferences don't belong in the team's `devcontainer.json`.

📖 Full lesson: [GitHub Actions, Copilot, Codespaces and github.dev: Automation and AI Tools (GH-900)](https://www.savemycert.com/revision/github-foundations/github-actions-copilot-codespaces-github-dev/?utm_source=github&utm_medium=readme&utm_campaign=gh-900-study-guide)

[← Back to the study guide](../README.md)
