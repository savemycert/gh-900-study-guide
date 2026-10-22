# Domain 6: Understand privacy, security, and administration (14%)

How accounts are protected and who can do what: 2FA and passkeys, repository and organization roles, teams, visibility, branch protection and rulesets, and enterprise controls such as Enterprise Managed Users and Copilot policies. Questions usually carry a constraint (least access, no push, a non-member, hide from the public, keep someone's admin rights), and the options are near-twin roles or settings.

## 6.1 Security and access management

- **2FA** (Settings → Password and authentication) adds a second proof after the password. Second factors:
  - **Authenticator app (TOTP)**: the recommended starting method.
  - **SMS**: works but weakest; not available in every country.
  - **Security keys**: FIDO2/WebAuthn hardware or built-in authenticators.
  - **GitHub Mobile**: approve the sign-in in the app.
  - **Passkeys**: replace password and second factor together.
- **Not second factors**: an **SSH key** (Git operations) and a **personal access token** (Git over HTTPS, API). The emailed device-verification code is for accounts _without_ 2FA.
- **Recovery codes**: each used once when your factor is unavailable. Store them away from the device and register more than one method.
  - A password reset does **not** remove 2FA. **GitHub Support cannot turn off 2FA.**
  - Last resort: an **account recovery request** proving ownership with a verified device, SSH key or PAT, reviewed by Support (can take a few business days). With none of these, the account can be lost for good.
- **Passkey**: a key pair held by an authenticator, unlocked by fingerprint, face, PIN or device password. Satisfies **both** password and 2FA. **Phishing-resistant** because it's bound to GitHub's domain; codes from apps or SMS can be relayed from a fake page.

| Passkey type | Lives in                                                                     | Effect                                                                  |
| ------------ | ---------------------------------------------------------------------------- | ----------------------------------------------------------------------- |
| Synced       | Cloud service (iCloud Keychain, Google Password Manager, a password manager) | On every device signed in to that service; survives losing one device   |
| Device-bound | One authenticator, e.g. a FIDO2 hardware key                                 | Can't be copied or backed up; the key itself can move between computers |

- GitHub doesn't sync passkeys; the authenticator does. An eligible registered security key can be **upgraded** to a passkey.
- **Org requires 2FA:**

| Without 2FA               | Result                                                                                              |
| ------------------------- | --------------------------------------------------------------------------------------------------- |
| Members, billing managers | Stay (still use a seat) but **blocked** from org resources until they enable it                     |
| Outside collaborators     | **Removed** from org repos, including their forks of private ones; can be re-invited after enabling |

- **Only allow secure two-factor methods** blocks **SMS** (passkeys, security keys, apps and GitHub Mobile are fine). Enterprise owners can enforce 2FA across all orgs.

| Repo role (org) | For                              | Adds                                                                                                     |
| --------------- | -------------------------------- | -------------------------------------------------------------------------------------------------------- |
| Read            | Viewers, discussers              | View, clone, open/comment on issues and PRs                                                              |
| Triage          | Managing issues/PRs without code | Labels, assign, close/reopen, mark duplicates; **no push**                                               |
| Write           | Contributors                     | Push, merge PRs, manage releases                                                                         |
| Maintain        | Project managers                 | Description, topics, wikis, merge options, Pages, interaction limits; no sensitive/destructive actions   |
| Admin           | Full control                     | Access, **branch protection and rulesets**, visibility, webhooks, deploy keys; delete, archive, transfer |

- Pick the **lowest role** that covers the job. **Maintain cannot touch branch protection or rulesets**; that's Admin. Org owners have admin on every org repo. Enterprise Cloud orgs can define **custom repository roles**.
- **Personal-account repos** have only **owner** and **collaborators**. Collaborators can push and manage issues/PRs; only the owner invites, changes visibility or deletes. No Triage or read-only role → move the repo to an organization for finer roles.

| Org role             | Allows                                                                                |
| -------------------- | ------------------------------------------------------------------------------------- |
| Owner                | Full admin of the org. Keep at least two                                              |
| Member               | Default; gets the base permission on every repo; can create repos/projects if allowed |
| Moderator            | Block/unblock users, manage interaction limits and comments on public repos           |
| Billing manager      | Payment methods, plans, receipts; **no repo access**                                  |
| Security manager     | Security alerts and settings org-wide, read access to all repos                       |
| GitHub App manager   | Settings of some or all org-owned GitHub Apps                                         |
| Outside collaborator | Not a member; only specific repos; no teams; **no base permission**                   |

- Outside collaborators suit contractors needing one or two repos for a limited time. Enterprise Cloud orgs can create **custom organization roles**.
- **Base permission** (Settings → Member privileges): No permission, Read, Write or Admin on **all** org repos, including future ones. A **floor**: a higher direct or team grant wins. Never applies to outside collaborators. Team grants must be repeated for each new repo; base permission doesn't.
- **Teams** (members only, one org):
  - **Visible**: seen and @mentioned by all members. **Secret**: seen only by its members and org owners.
  - **Nested**: one parent, many children. Children **inherit the parent's repo access**; mentioning a parent notifies children's members.
  - **Secret teams can't be nested** (no parent, no children), so they get access only by direct grants.
  - **Team maintainers** manage name, description, visibility, membership (org members) and review settings without being owners.

| Visibility | Who can see                                                                                                                    |
| ---------- | ------------------------------------------------------------------------------------------------------------------------------ |
| Public     | Everyone on the internet                                                                                                       |
| Private    | Owner and people/teams granted access (plus members via base permission)                                                       |
| Internal   | Every member of the **enterprise**, across all its orgs; not the public, not outside collaborators. Enterprise-owned orgs only |

- **Internal enables InnerSource.** Private can't do it: base permission covers only its own org, and teams from other orgs can't be added.
- **Public → private**: stars and watchers erased; existing public forks stay public and are detached; explicit access and history unchanged; on GitHub Free a Pages site is unpublished. Only admins/owners change visibility, and owners can restrict that to owners.
- **Restrict repo creation** (Member privileges): owners choose whether members create repos and of which visibility (e.g. private only). Base permissions, branch protection and rulesets act on existing repos, so they don't control this.
- **Branch protection rule** (Admin, Settings → Branches, by name or pattern). Available on public repos on Free, and public + private on Pro, Team and Enterprise Cloud. Can require:
  - a PR with N **approving reviews** (optionally code owner review, dismiss stale approvals)
  - passing **status checks**
  - **conversation resolution**
  - **signed commits** or **linear history**
  - a **locked** branch or **push restrictions**
- **Defaults**: once a rule matches, **force pushes and deletion are blocked** unless allowed. Everything else is off until selected. **Admins bypass by default**; enable **Do not allow bypassing the above settings** to bind them. Only **one** protection rule applies per branch.

|            | Branch protection            | Ruleset                                                                                 |
| ---------- | ---------------------------- | --------------------------------------------------------------------------------------- |
| Per branch | One rule                     | Many rulesets + a protection rule can all apply                                         |
| Overlap    | n/a                          | Rules aggregate; **most restrictive** wins; no priority order                           |
| Pause      | Edit or delete               | Enforcement status **Disabled** keeps the config (Active; Evaluate on Enterprise plans) |
| Exemptions | Admins bypass unless blocked | **Bypass list** of roles, teams, GitHub Apps                                            |
| Visible to | Admin-only Settings          | Anyone with read access sees active rulesets                                            |
| Targets    | Branches                     | Branches or tags                                                                        |

- A looser second ruleset can't relax a stricter one. To exempt a release bot, add it to the **bypass list**; more permission doesn't exempt it. Creating rulesets needs Admin.
- **Enterprise Managed Users (EMU)**: an Enterprise Cloud enterprise type where the company **IdP owns every account**. Provisioning by **SCIM**; sign-in by **SAML or OIDC**; IdP controls usernames, profile, email, org and team membership. Deactivating in the IdP removes access.
  - Managed users create only private or internal content inside the enterprise.
  - Outside it they can view public repos but **can't push, open issues/PRs, comment, react, star, watch or fork**, can't create public repos, and can't create gists. Open-source work needs a separate personal account.
  - Alternative: **personal accounts + SAML SSO** (developers' own accounts authenticate through the IdP) when people use one account for work and open source.
- **Copilot policy management** (Business/Enterprise): **org owners** assign seats and set the org's Copilot policies (features, models, settings). Repo admins and billing managers don't. In an enterprise, **enterprise owners** set each policy first: enable or disable for all orgs, or **let organizations decide**. Seats from orgs with different settings → GitHub generally applies the **least restrictive** setting.
- **Traps:**
  - Maintain can't create branch protection.
  - Outside collaborators: removed when 2FA is required, no base permission, no teams.
  - "Hide the team" and "inherit parent access" are mutually exclusive.
  - Admins bypass protection unless told not to.

📖 Full lesson: [GitHub Security and Access Management: 2FA, Passkeys, Roles and Branch Protection (GH-900)](https://www.savemycert.com/revision/github-foundations/github-security-2fa-roles-permissions-branch-protection/?utm_source=github&utm_medium=readme&utm_campaign=gh-900-study-guide)

[← Back to the study guide](../README.md)
