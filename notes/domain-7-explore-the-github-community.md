# Domain 7: Explore the GitHub community (8%)

A light domain (official range 5–10%) about how people share, fund, find and build on code: open source, GitHub Sponsors, what GitHub gives open source projects, following people, the Marketplace, InnerSource, and choosing forks, templates and topics. The options are close neighbours, so match each one to its single job.

## 7.1 Open-source engagement

- **Open source** = code under a license that lets anyone read, use, modify and share it within its terms. On GitHub: a public repo with a `LICENSE`, README and contribution guidelines.
- **Benefits**: transparency and review (more eyes on defects and security), reuse instead of rewriting, shared improvement from varied users, a visible record for learning and hiring.
- **Open source is about who may use the code, not who may change the original.** Outsiders **fork and open pull requests**; they don't get write access. Maintainers decide what merges and stay responsible for upkeep. The **license** grants reuse rights.
- **GitHub Sponsors** pays developers and organizations that build open source:
  - The sponsored account sets up a profile and **tiers**: **monthly** (recurring) or **one-time**, each with an amount and optional rewards.
  - Sponsors pay from a personal or organization account.

| Sponsor              | GitHub fee                                                                  | Maintainer gets     |
| -------------------- | --------------------------------------------------------------------------- | ------------------- |
| Personal account     | None                                                                        | Full amount         |
| Organization account | Can carry a fee (card processing + service; see GitHub's docs for the rate) | Amount less the fee |

- Sponsors funds **people**. It isn't where you buy software (Marketplace), and stars or watching transfer no money.
- **FUNDING.yml** in **`.github/` on the default branch** shows a **Sponsor** button (Sponsorships also enabled under Settings → Features).
  - Keys: `github` (Sponsors usernames), external platforms (Open Collective, Patreon, Ko-fi, Liberapay, Tidelift…), `custom` URLs.
  - An org's `.github` repo can supply a default FUNDING.yml for repos without one.
  - It only **displays** links and moves no money. Nothing else in the repo creates the button.
- **How GitHub supports open source:**
  - Free public repos with issues, PRs, Discussions, Projects, wikis, and security features (Dependabot alerts, code scanning, secret scanning) for public repos.
  - **Free Actions on standard GitHub-hosted runners** for public repos. **Self-hosted runners** are free with Actions anywhere (you pay for the machine). **Larger runners are always billed**, even on public repos, and you can't register your own hardware as one.
  - **Free Copilot Pro for maintainers of popular open source repos** (eligibility reviewed regularly). Students and teachers have a separate offer.
  - Sponsors with no fee on personal-account sponsorships.
  - **Discovery**: Explore, trending, topics, `good first issue`.
  - These lower the cost of a public project. They don't change ownership or other products' pricing.

| Action | On                     | You get                                                                               |
| ------ | ---------------------- | ------------------------------------------------------------------------------------- |
| Follow | A user or organization | Their public activity on your **personal dashboard**. No notifications, no membership |
| Watch  | A repository           | **Notifications** at the level you choose                                             |
| Star   | A repository           | A **bookmark** (stars and star lists) and public appreciation. No notifications       |

- **Watch levels**: Participating and @mentions (default), All Activity, Custom (e.g. only **Releases**), Ignore (mutes; saves nothing).
- Following an org isn't joining it. Following organizations is labelled public preview in GitHub's docs. Watching every repo a person owns ≠ following them: it floods notifications and still misses what they star or create elsewhere.
- **GitHub Marketplace** catalogs **Actions** and **apps** (GitHub Apps, OAuth apps) from GitHub and third parties. Reference an action in a workflow; install an app on an account or org.
  - Anyone can publish an action; developers can list free apps.
  - **Paid plans: apps only** (not actions), app owned by an **organization**, which must pass **publisher verification**. Source needn't be public. GitHub handles billing.
  - Neighbours: **Sponsors** funds people, **Packages** hosts packages (npm, container images), **Explore** finds repos and topics.
- **InnerSource** = open source practices (transparency, PR contributions, open discussion, shared docs) for code that stays **inside one company**. Not open source; not a branching model.

| Visibility | Who sees                                     | InnerSource fit                           |
| ---------- | -------------------------------------------- | ----------------------------------------- |
| Public     | Everyone                                     | No, code leaves the company               |
| Internal   | Every member of the **enterprise**, all orgs | Yes, company-wide without per-team grants |
| Private    | Only granted people/teams                    | Workable but every team must be added     |

- Internal is available to enterprise-owned orgs (Enterprise Cloud or Server). The practices that make InnerSource work: README + **CONTRIBUTING.md**, **trusted committers** who review and mentor other teams' PRs, PRs with owner review (CODEOWNERS, branch protection) instead of blanket write access, and changes flowing **back** to the shared repo.

|                     | Fork                                       | Repo from a template                   |
| ------------------- | ------------------------------------------ | -------------------------------------- |
| Link to original    | Stays connected to upstream                | None, independent                      |
| History             | Full commit history                        | One fresh commit                       |
| Send changes back   | Yes, PR to upstream                        | No straightforward route               |
| Needs write access? | No                                         | No                                     |
| Use                 | Fix or improve a project you can't push to | Start a new project from a starter kit |

- **Open source contribution path**: fork → commit in the fork → PR to upstream. A repo becomes a template via **Template repository** in its settings; users choose **Use this template**.
- **Discoverable repositories** need three things:
  - **Visibility**: who can see it at all.
  - **Topics**: short lowercase subject tags in About (e.g. `terraform`). A topic links to GitHub's page for that subject. Set by maintainers.
  - A clear **description, README and community files**.
- Topics classify the **repository**. Labels sort issues and PRs inside it; tags mark versions. Only topics put the repo on subject pages.
- **Stacked requirements**: visibility decides _who_, fork vs template decides _history and link back_, topics decide _findability by subject_. Settle each one separately.
- **Traps:**
  - "Fund a maintainer" → Sponsors, not Marketplace or stars.
  - "Free runner for a public repo" → standard hosted or self-hosted, never larger.
  - "See what a person does" → follow; "notifications for a repo" → watch.
  - "Share across the company, not the public" → internal.

📖 Full lesson: [Open Source on GitHub: Sponsors, Marketplace, InnerSource, Forks and Discovery (GH-900)](https://www.savemycert.com/revision/github-foundations/github-open-source-sponsors-marketplace-innersource/?utm_source=github&utm_medium=readme&utm_campaign=gh-900-study-guide)

[← Back to the study guide](../README.md)
