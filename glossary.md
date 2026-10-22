# GH-900 Glossary

223 GH-900 terms and services, each in one plain-English sentence.

[#](#) · [A](#a) · [B](#b) · [C](#c) · [D](#d) · [E](#e) · [F](#f) · [G](#g) · [H](#h) · [I](#i) · [J](#j) · [L](#l) · [M](#m) · [N](#n) · [O](#o) · [P](#p) · [Q](#q) · [R](#r) · [S](#s) · [T](#t) · [U](#u) · [V](#v) · [W](#w)

## #

- **.git directory**: The hidden folder that holds a repository's commits, branches, remotes and configuration.
- **.gitignore**: A file listing paths Git should never track.
- **@current**: A filter value that always resolves to the iteration in progress.
- **@mention**: A reference to `@user` or `@org/team` that notifies people who can read the repository.

## A

- **Account recovery request**: A last-resort review by GitHub Support that needs a verified device, SSH key or personal access token.
- **Action**: A reusable unit of automation that a step calls with `uses:`.
- **Admin role**: The repository role with full control, including access, branch protection, rulesets and deletion.
- **Agent mode**: A Copilot Chat mode that autonomously edits files and runs commands in your IDE.
- **Alert (Markdown)**: A highlighted callout written as a blockquote starting `[!NOTE]`, `[!TIP]`, `[!IMPORTANT]`, `[!WARNING]` or `[!CAUTION]`.
- **Amend**: Rewriting the most recent commit with `git commit --amend`, which creates a new commit with a new ID.
- **Announcement category**: A discussion format in which only maintain or admin users can start threads.
- **Archive**: Making a repository read-only for everyone while keeping it viewable, forkable and reversible.
- **Ask mode**: A Copilot Chat mode that answers and suggests without changing files.
- **Assignee**: A person who owns an issue or pull request; up to ten per item.
- **assignee:@me**: A filter that shows each viewer the items assigned to them.
- **Auto (model selection)**: A model picker option in which Copilot chooses the model based on availability.
- **Auto-add workflow**: A project workflow that adds newly created or updated items matching a filter.
- **Auto-archive workflow**: A project workflow that archives items matching set criteria.

## B

- **Base permission**: The default access every organization member has to all of its repositories.
- **Billing manager**: An organization role that manages payment and plans without repository access.
- **Board layout**: A kanban project view whose columns come from a single select or iteration field.
- **Branch**: A lightweight, movable pointer to a commit that advances with each new commit on it.
- **Branch protection rule**: A rule that enforces requirements such as reviews and status checks before changes reach a branch.
- **Bulk add**: Adding many matching issues and pull requests from a repository to a project in one step.
- **Burn up chart**: The default historical chart comparing completed work with total work over time.
- **Bypass list**: The roles, teams or apps allowed to skip a ruleset's rules.

## C

- **CI/CD**: Continuous integration and delivery: automatically building and testing changes, then deploying or publishing them.
- **Clone**: Copying an existing repository, with its full history, to create a new local repository.
- **Closing keyword**: A word such as fixes, closes or resolves that, followed by an issue reference in a pull request description, closes that issue on merge into the default branch.
- **CODE_OF_CONDUCT.md**: The expected behaviour in a project's community and how it is enforced.
- **CODEOWNERS**: A file mapping paths to users or teams whose review GitHub requests automatically on matching pull requests.
- **Commit**: A snapshot of all tracked files plus author, committer, dates, message and parent commit IDs.
- **Commit ID (hash)**: An identifier computed from a commit's data, including its parent's ID, so it vouches for the whole history behind it.
- **Community health files**: Files such as CONTRIBUTING, CODE_OF_CONDUCT, SUPPORT, SECURITY, templates and FUNDING.yml that support contributors.
- **Community standards**: The Insights checklist that shows which recommended community files a public repository has.
- **config.yml (issue templates)**: A file that sets `blank_issues_enabled` and `contact_links` for the issue template chooser.
- **Content exclusion**: A Business and Enterprise setting that keeps chosen files out of Copilot.
- **CONTRIBUTING.md**: Guidelines on how to contribute, linked when people open issues and pull requests.
- **Contributors graph**: An Insights graph of commits per contributor over time.
- **Copilot Business**: The organization Copilot plan with central policy, content exclusion and audit logs.
- **Copilot Chat**: The chat interface for asking Copilot questions and giving it tasks.
- **Copilot cloud agent**: The Copilot agent that works in an ephemeral environment on GitHub and delivers its work as a pull request.
- **Copilot Enterprise**: The Copilot plan for enterprises on GitHub Enterprise Cloud, with a larger allowance than Business.
- **Copilot individual plans**: Copilot Free, Pro, Pro+ and Max, bought by a person for their own account.
- **Copilot policy**: An organization or enterprise setting that controls which Copilot features and models are allowed.
- **copilot-setup-steps.yml**: A workflow file that preinstalls tools for the Copilot cloud agent's environment.
- **Current chart**: An insights chart that shows items as they are now, split by a field.
- **Custom field**: A project-only field such as Status, Priority or Points.
- **Custom routing**: Sending email notifications for a specific organization's repositories to a chosen verified address.

## D

- **Default branch**: The branch GitHub shows first and targets with new pull requests, usually `main`.
- **Default community health files**: Health files supplied from a public `.github` repository to every repository in the account that lacks its own.
- **Default copyright**: The legal position when no license exists, in which the author keeps all rights to the code.
- **Dependency graph**: A view built from manifest and lock files that lists a repository's dependencies and dependents.
- **Dependency insights**: An organization-level view, on Enterprise Cloud, of security advisories and licenses across the organization's dependencies.
- **Dev container**: The configuration, usually `.devcontainer/devcontainer.json`, that defines how a codespace is built.
- **Dev container feature**: A packaged tool or runtime added to a dev container.
- **Development sidebar**: The section of an issue or pull request that lists linked work and allows manual linking.
- **Device-bound passkey**: A passkey held on one authenticator that cannot be copied or backed up.
- **Discoverable repository**: A repository that the right people can see and find by subject.
- **Discussion**: A forum thread attached to a repository or organization for questions, ideas, announcements and polls.
- **Discussion category**: A grouping of discussions whose format controls how threads behave.
- **Distributed version control**: A model in which every clone holds the complete repository and its full history.
- **Dotfiles repository**: A repository of personal configuration that GitHub applies to every new codespace you create.
- **Draft issue**: A project-only item that has no repository until it is converted to an issue.
- **Draft pull request**: A pull request that gets comments and checks but cannot be merged until marked ready for review.

## E

- **Enforcement status**: A ruleset's Active, Evaluate or Disabled state.
- **Enterprise account**: An account above organizations that manages policy and billing for many of them together.
- **Enterprise Managed Users (EMU)**: An Enterprise Cloud model in which the company identity provider creates and controls every account.
- **Event**: An activity, schedule or manual trigger that starts a workflow.
- **Explore**: GitHub's pages for discovering repositories, topics and trending projects.

## F

- **Feature preview**: A per-user menu for switching public-preview interface features on or off.
- **Fetch**: Downloading new commits from a remote into remote-tracking branches without changing your own branches.
- **Follow**: Subscribing to a user's or organization's public activity on your personal dashboard.
- **Fork**: A copy of a repository under another account that keeps its history and can send pull requests back.
- **FUNDING.yml**: A file in `.github` on the default branch that lists funding links and shows a Sponsor button.

## G

- **General availability (GA)**: The release stage in which a feature is fully released and supported.
- **Gist**: A Git repository for sharing snippets or small files by URL, with revision history.
- **Git**: Free, open-source, distributed version control software that runs on your own computer.
- **Git LFS (Large File Storage)**: A Git extension for tracking files too large for a normal push.
- **GitHub**: A cloud platform that hosts Git repositories and adds pull requests, issues, Actions and access control.
- **GitHub Actions**: GitHub's automation platform that runs workflows when events happen in a repository.
- **GitHub App**: An integration installed on an account or organization to extend GitHub.
- **GitHub CLI (gh)**: A command-line tool that exposes GitHub features such as pull requests and issues for scripts and terminals.
- **GitHub Codespaces**: Cloud-hosted development environments running in containers on GitHub-hosted virtual machines.
- **GitHub Connect**: A link between Enterprise Server and Enterprise Cloud that shares selected features and data.
- **GitHub Copilot**: GitHub's AI assistant that suggests code, answers questions and can complete tasks.
- **GitHub Desktop**: A free graphical app for Windows and macOS that performs local Git work without commands.
- **GitHub Enterprise Cloud**: GitHub-hosted enterprise offering, optionally with data residency on a GHE.com subdomain.
- **GitHub Enterprise Server**: The self-hosted enterprise offering that a customer runs on its own infrastructure.
- **GitHub Flavored Markdown**: The Markdown dialect GitHub renders in issues, pull requests, comments, wikis and `.md` files.
- **GitHub flow**: GitHub's branch-based workflow: branch, commit and push, open a pull request, address review, merge, delete the branch.
- **GitHub Marketplace**: GitHub's catalog of actions and apps from GitHub and third parties.
- **GitHub Mobile**: The Android and iOS app for notifications, reviews and sign-in approvals.
- **GitHub Packages**: GitHub's service for hosting software packages such as npm packages and container images.
- **GitHub Pages**: Static website hosting served directly from a repository.
- **GitHub Pro**: The paid plan for personal accounts that adds advanced tools for their private repositories.
- **GitHub Projects**: A planning tool owned by a user or organization that tracks issues, pull requests and draft issues from many repositories.
- **GitHub Sponsors**: GitHub's program for funding developers and organizations who build open source.
- **GitHub Team**: The paid organization plan that adds protected branches, required reviewers and code owners to private repositories.
- **GitHub-hosted runner**: A fresh, GitHub-maintained Ubuntu, Windows or macOS virtual machine created for each job.
- **github.dev**: A free, browser-based VS Code editor with no compute, opened by pressing the period key on a repository.
- **good first issue**: A default label marking beginner-friendly work that feeds the repository's contribute page.

## H

- **help wanted**: A default label signalling that maintainers would welcome help.
- **Historical chart**: An insights chart that shows how items changed over time.

## I

- **Idle timeout**: The period of inactivity, 30 minutes by default, after which a codespace stops.
- **Ignore**: The watch level that turns off all notifications from a repository, including @mentions.
- **Include all branches**: A template option that copies every branch's files, each with its own unrelated history.
- **Inline suggestion**: Copilot's ghost-text completion offered as you type or after a descriptive comment.
- **InnerSource**: Applying open source practices to code that stays inside one organization.
- **Insights tab**: A repository's built-in metrics dashboard of activity, people, traffic and dependency views.
- **Internal repository**: A repository visible to every member of an enterprise but not to the public.
- **Issue**: A record of actionable work, such as a bug, task or feature request, that can be assigned and closed.
- **Issue form**: A YAML issue template with typed input fields.
- **Issue template**: A Markdown or YAML file in `.github/ISSUE_TEMPLATE` that pre-fills new issues through a template chooser.
- **Item**: An issue, pull request or draft issue inside a project.
- **Iteration field**: A field that splits time into repeating blocks such as sprints, with optional breaks.

## J

- **Job**: A set of steps that runs on one runner; jobs run in parallel by default.

## L

- **Label**: A repository-scoped tag that categorizes issues, pull requests and discussions.
- **Larger runner**: A GitHub-hosted runner with more CPU and memory, always billed.
- **Least privilege**: Granting the lowest role that covers a task.
- **LICENSE**: The file stating what others may legally do with the code; without one, default copyright applies.

## M

- **Maintain role**: A repository role for managing settings without sensitive or destructive actions.
- **Maintainer**: A person responsible for reviewing, merging and looking after a project.
- **Merge**: Combining the changes of one branch into another relative to their common ancestor.
- **Merge conflict**: A stop in a merge when both branches changed the same lines, which a person must resolve and commit.
- **Mermaid diagram**: A diagram GitHub draws from a fenced code block whose language is `mermaid`.
- **Milestone**: A repository-scoped group of issues and pull requests working toward a goal, with an optional due date and progress percentage.
- **Model picker**: The Copilot Chat control for choosing which AI model answers a conversation.
- **Moderator**: An organization role that can block users and manage interaction limits and comments.

## N

- **needs**: The workflow keyword that makes one job wait for another.
- **Nested team**: A child team that inherits its parent team's repository access.
- **Network graph**: An Insights view of branch history across a repository and its forks.
- **Notifications inbox**: The page at github.com/notifications where notifications are triaged with Done, Save and filters.

## O

- **Open source**: Software published under a license that lets anyone read, use, modify and share it.
- **Organization**: A shared account that owns repositories for a group and manages access through teams; nobody signs in to it.
- **Organization owner**: A member with complete administrative access to an organization.
- **Outside collaborator**: A non-member with access only to specific repositories.

## P

- **Participating and @mentions**: The default watch level, notifying only about threads you take part in or are mentioned in.
- **Passkey**: A phishing-resistant, passwordless credential that satisfies both the password and 2FA steps.
- **Personal access token (PAT)**: A credential for Git over HTTPS and API calls, not a second factor.
- **Personal account**: An individual's identity on GitHub, which every action and commit attribution comes from.
- **Personal dashboard**: Your GitHub home page feed of activity from people and organizations you follow.
- **Pinned discussion**: A discussion shown at the top of the Discussions page for extra visibility.
- **Plan mode**: A Copilot Chat mode that writes an implementation plan for review before coding.
- **Prebuild**: A snapshot of a configured codespace built by an Actions workflow so new codespaces start faster.
- **Private publishing**: Restricting a Pages site to organization members, available to organizations on Enterprise Cloud.
- **Profile README**: A README in a public repository named after your username, shown at the top of your profile.
- **Project insights**: Configurable charts built from a project's items.
- **Project site**: A Pages site published from any other repository, served under `<owner>.github.io/<repository>`.
- **Project status update**: A report recording a project's health, dates and a message, shown in project lists.
- **Project workflow**: A built-in, no-code automation that updates project items when events happen.
- **Public code policy**: A setting that blocks Copilot suggestions matching public code or allows them with references.
- **Public preview**: A release stage in which anyone can try a feature that may still change and lacks full support.
- **Publisher verification**: The check an organization must pass before it can sell paid app plans in Marketplace.
- **Pull**: A fetch followed by integrating the downloaded commits into the current branch.
- **Pull request**: A proposal to merge changes from one branch into another, with discussion, review and checks.
- **Pull request review**: A set of comments submitted with the state Comment, Approve or Request changes.
- **Pull request template**: A `pull_request_template.md` file that pre-fills the body of new pull requests.
- **Pulse**: An Insights summary of pull requests, issues and top committers for a chosen period.
- **Push**: Sending local commits for a branch to a remote.

## Q

- **Q&A category**: A discussion format in which a comment can be marked as the answer.

## R

- **Read role**: A repository role for viewing, cloning and discussing.
- **README**: The file GitHub renders on a repository's main page to explain what the project is and how to use it.
- **Rebuild Container**: The command that applies configuration changes to an existing codespace, keeping `/workspaces`.
- **Recovery codes**: Single-use codes for finishing sign-in when your second factor is unavailable.
- **Relative link**: A link to a repository file by path, resolved against the branch or fork being viewed.
- **Remote**: A named link to another copy of the repository, by default called `origin`.
- **Remote-tracking branch**: A local reference such as `origin/main` that records where a remote's branch was at the last fetch.
- **Repository**: A project's files together with the full history of changes to them.
- **Request changes**: A review state saying the feedback must be addressed before the pull request is merged.
- **Revert**: Undoing a merged pull request by creating a new pull request that adds a reversing commit.
- **Roadmap layout**: A timeline project view that draws items as bars between start and target fields.
- **Ruleset**: A named collection of rules for branches or tags that layers with other rulesets.
- **Runner**: The machine that executes a workflow job.

## S

- **SAML single sign-on**: Signing in through the company identity provider to reach organization resources.
- **Saved notification**: A notification kept indefinitely until you remove it.
- **Saved reply**: A reusable comment text stored privately in your personal account settings.
- **SBOM (software bill of materials)**: An export of a repository's dependencies from the dependency graph.
- **schedule trigger**: A trigger that runs a workflow at fixed times using cron syntax.
- **SCIM**: The provisioning standard an identity provider uses to create and manage accounts.
- **Search qualifier**: A filter term such as `is:open` or `label:bug` used to narrow issues and pull requests.
- **Secret gist**: An unlisted gist that anyone with the URL can view.
- **Secret team**: A team visible only to its members and organization owners, which cannot be nested.
- **Security key**: A FIDO2/WebAuthn hardware or built-in authenticator used as a second factor.
- **Security manager**: An organization role that manages security alerts and settings across all repositories.
- **SECURITY.md**: A security policy listing supported versions and how to report a vulnerability privately.
- **Self-hosted runner**: A machine you provide and maintain to run Actions jobs, using no Actions minutes.
- **Settings Sync**: The VS Code feature that carries your editor settings, themes and keybindings into codespaces.
- **Single select field**: A field holding one value from a fixed list of options.
- **Sponsor button**: The repository button that opens the funding links in FUNDING.yml.
- **Sponsorship tier**: A monthly or one-time amount, with optional rewards, set by a sponsored account.
- **SSH key**: A key pair that authenticates Git operations, not web sign-in.
- **Staging area (index)**: The place where `git add` puts a snapshot of changes chosen for the next commit.
- **Star**: A bookmark on a repository that also shows appreciation and feeds GitHub's recommendations.
- **Star list**: A public, named group of starred repositories.
- **Status check**: An external result, such as a CI build, that a branch rule can require to pass.
- **Step**: A single command or action inside a job; steps run in order.
- **Suggested change**: A line comment proposing exact replacement text that the author can commit from the pull request page.
- **SUPPORT.md**: Where users can get help with the project.
- **Synced passkey**: A passkey backed up by a cloud service and available on all devices signed in to it.

## T

- **Table layout**: A spreadsheet-style project view with one row per item.
- **Tag**: A fixed label on one commit, typically used to mark a release.
- **Task list**: Markdown checkboxes written `- [ ]` and `- [x]` that render as clickable items.
- **Team**: A group of organization members granted access, mentioned and asked for reviews as a unit.
- **Team maintainer**: A member who manages a team's details and membership without being an owner.
- **Template repository**: A repository that others can generate new, independent repositories from, starting with one fresh commit.
- **Topic**: A subject tag on a repository that helps people find it by subject.
- **TOTP authenticator app**: An app that generates time-based one-time codes for 2FA.
- **Traffic graph**: An Insights view of views, visitors, clones, referrers and popular content for 14 days, visible with push access.
- **Triage role**: A repository role for managing issues and pull requests without push access.
- **Trusted committer**: A named maintainer who reviews and mentors contributions from other teams in InnerSource.
- **Two-factor authentication (2FA)**: Requiring a second proof of identity after the password at sign-in.

## U

- **Upstream**: The original repository that a fork was created from.
- **User or organization site**: A Pages site published from a repository named `<owner>.github.io`.

## V

- **Version control**: A system that records every change to a set of files, with who made it, when and why, so any committed version can be restored or compared.
- **View**: A saved tab combining a layout with filters, sorting, grouping and visible fields.

## W

- **Watch**: A repository setting that controls which notifications you receive about it.
- **Watch level**: The repository notification setting: Participating and @mentions, All Activity, Ignore or Custom.
- **Wiki**: A Git-backed set of documentation pages attached to a repository.
- **Workflow**: A YAML file in `.github/workflows` that defines triggers and jobs.
- **workflow_dispatch**: A trigger that adds a manual Run workflow button.
- **Working directory**: The project files you see and edit on disk.
- **Write role**: A repository role that adds pushing, merging and managing releases.

[← Back to the study guide](README.md)
