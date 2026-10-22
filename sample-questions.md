# GH-900 Sample Questions with Answers

20 worked practice questions for the **GitHub Foundations (GH-900)** exam. Try each one before you open the answer.

For many more, with the same explanation on every option, use the [GH-900 practice questions](https://www.savemycert.com/practice/github-foundations/?utm_source=github&utm_medium=readme&utm_campaign=gh-900-study-guide) on SaveMyCert.

## Question 1

*Understand Git and GitHub basics*

**A team keeps its scripts in a shared network folder. Files are regularly overwritten, and nobody can tell who changed a file or for what reason. Which capability of a version control system addresses this most directly?** Choose one.

- **a.** Compressing the stored files so that the shared folder uses much less disk space
- **b.** Scanning each saved file for passwords or keys before the change is accepted
- **c.** Running the scripts on a schedule or each time a file in the shared folder is saved
- **d.** Recording each change together with its author, its time and a descriptive message

<details>
<summary>Show answer and explanation</summary>

**Answer: d**

- **a** ❌ Git does compress what it stores, but saving disk space does not tell anyone who changed a file or why.
- **b** ❌ Secret scanning is a real GitHub security feature, but it detects leaked credentials; it does not record authorship or the reason for a change.
- **c** ❌ Running code on events or schedules is automation (for example GitHub Actions), not version control. It leaves the who-and-why question unanswered.
- **d** ✅ Version control stores every change as a recorded entry with who made it, when, and a message saying why. That answers exactly the question the team cannot answer today.

**The concept.** Version control keeps a history of changes in which every change records its author, its timestamp and a message describing it.

**Why this is correct.** The team's problem is missing accountability: overwritten files and no record of who changed what. A version control system such as Git records each change as a commit with an author, a date and a message, so the history answers who, what, when and why. Compression, secret scanning and scheduled automation are all real capabilities, but none of them creates a record of changes.

**How to reason it out**

1. Identify the gap: no record of who changed a file or why.
2. Recall what version control stores for every change: author, time, message and the change itself.
3. Reject capabilities that solve a different problem (storage, security, automation).
4. Choose the recorded history with authorship and messages.

> **Exam tip:** Version control answers who changed what, when and why: every change carries an author, a time and a message.

</details>

📖 Learn this topic: [Git vs GitHub: Version Control Fundamentals for GitHub Foundations (GH-900)](https://www.savemycert.com/revision/github-foundations/git-vs-github-version-control-fundamentals/?utm_source=github&utm_medium=readme&utm_campaign=gh-900-study-guide)

---

## Question 2

*Understand Git and GitHub basics*

**A configuration file is tracked in a Git repository. A change committed last week broke the website, and the team wants the file exactly as it was before that change. What does version control make possible?** Choose one.

- **a.** Recovering the version from before last week's change from a backup outside Git
- **b.** Restoring the file's contents from a commit made before last week's change
- **c.** Restoring the version from before last week's change from GitHub, not a clone
- **d.** Rebuilding the version from before last week's change from the commit messages

<details>
<summary>Show answer and explanation</summary>

**Answer: b**

- **a** ❌ No separate backup is needed: Git keeps every committed version of the file, not just the newest one, so the earlier version is already in the repository.
- **b** ✅ Every commit is a stored snapshot, so the file can be brought back from any commit made before the faulty change, and the history of what happened is kept.
- **c** ❌ A local clone holds the full history too; the earlier version can be restored on any clone without GitHub.
- **d** ❌ Commit messages describe changes, but Git also stores the full contents of every committed version, so nothing has to be rebuilt by hand.

**The concept.** Version control lets you return a file or a whole project to any earlier committed state.

**Why this is correct.** Each Git commit stores a snapshot of the tracked files, so the version from before last week's change is still in the repository and can be restored (for example by reverting the faulty commit or checking out the old file). The distractors assume the earlier contents are missing, recoverable only from messages, or held only on GitHub; in Git every clone holds every committed version.

**How to reason it out**

1. Note that the file is tracked and the faulty change was committed.
2. Recall that every commit is a full snapshot kept in the history.
3. Recall that the local repository holds that history, not just GitHub.
4. Choose restoring the file from an earlier commit.

> **Exam tip:** Committed means recoverable: any earlier commit can be brought back.

</details>

📖 Learn this topic: [Git vs GitHub: Version Control Fundamentals for GitHub Foundations (GH-900)](https://www.savemycert.com/revision/github-foundations/git-vs-github-version-control-fundamentals/?utm_source=github&utm_medium=readme&utm_campaign=gh-900-study-guide)

---

## Question 3

*Understand Git and GitHub basics*

**A volunteer group wants a shared place on GitHub for its repositories. Ownership must not depend on any single volunteer, and access should be managed in teams while each person keeps their own login. Which account setup fits?** Choose one.

- **a.** A personal account owned by the group's leader, with the others added as collaborators
- **b.** An enterprise account that each volunteer signs in to directly with shared credentials
- **c.** A machine user account that the volunteers share to push commits and manage access
- **d.** An organization account that the volunteers join with their own personal accounts

<details>
<summary>Show answer and explanation</summary>

**Answer: d**

- **a** ❌ Repositories would belong to one person's account, so ownership depends on that volunteer, and personal accounts have no teams.
- **b** ❌ Enterprise accounts manage policy and billing for several organizations; nobody signs in to them as a shared login, and they are a paid GitHub Enterprise feature.
- **c** ❌ Machine users are user accounts meant for automation such as CI. Sharing one would remove individual logins and attribution.
- **d** ✅ Correct. Organizations are shared accounts that own repositories; members sign in with their own user accounts and are grouped into teams for access.

**The concept.** GitHub has three account types: user (personal) accounts, organization accounts and enterprise accounts.

**Why this is correct.** An organization is a shared account where people collaborate across many projects at once. It owns the repositories, so nothing depends on one member, and owners organize members into teams to grant access. Each member keeps signing in with their own personal account. A leader's personal account ties ownership to one person; an enterprise account sits above organizations for central policy and billing; a machine user is for automation.

**How to reason it out**

1. Spot the requirements: shared ownership, team-based access, individual logins.
2. Personal accounts are owned by one person, so they fail the ownership requirement.
3. Enterprise accounts govern several organizations; they are not the place a small group collaborates.
4. Choose an organization joined through members' own personal accounts.

> **Exam tip:** Shared ownership plus teams = an organization; people still sign in as themselves.

</details>

📖 Learn this topic: [Working with GitHub: Accounts, Plans, the GitHub Flow, Markdown, Desktop and Mobile (GitHub Foundations GH-900)](https://www.savemycert.com/revision/github-foundations/github-accounts-flow-markdown-desktop-mobile/?utm_source=github&utm_medium=readme&utm_campaign=gh-900-study-guide)

---

## Question 4

*Understand Git and GitHub basics*

**Four developers need to change the same codebase during the same week without overwriting each other's work. Which benefit of version control helps them most?** Choose one.

- **a.** Each file can be edited by just one person at a time until that person saves and closes it
- **b.** Each change is tested by a build server before anybody else can save a file
- **c.** Each person's changes are recorded separately and can later be merged into one version
- **d.** Each person's edits are synced live into one shared copy while they are typing

<details>
<summary>Show answer and explanation</summary>

**Answer: c**

- **a** ❌ File locking is how some older centralised systems avoided conflicts. It serialises the work instead of letting four people change the codebase at once, and Git does not work this way.
- **b** ❌ Automated testing is continuous integration, a separate practice. It does not keep developers from overwriting each other's changes.
- **c** ✅ Version control lets each developer work on their own line of changes and then combines those changes, so nobody's work is overwritten.
- **d** ❌ Live co-editing of a single copy is how online document editors work. Version control instead keeps separate, recorded changes and merges them.

**The concept.** Version control supports parallel work: people change the same project at the same time and their changes are merged.

**Why this is correct.** The team needs parallel work without lost changes. In Git, each developer commits changes on their own branch or clone, and the changes are merged; Git flags the rare case where two people changed the same lines. Locking files serialises work, automated testing checks quality rather than protecting changes, and live co-editing of one shared copy is a different model with no separate recorded changes to combine.

**How to reason it out**

1. Identify the need: several people, same codebase, same time, nothing overwritten.
2. Recall that version control records each person's changes separately.
3. Recall that separate changes are combined by merging.
4. Choose separate recorded changes that are merged.

> **Exam tip:** Version control lets many people change one project at once: work separately, then merge.

</details>

📖 Learn this topic: [Git vs GitHub: Version Control Fundamentals for GitHub Foundations (GH-900)](https://www.savemycert.com/revision/github-foundations/git-vs-github-version-control-fundamentals/?utm_source=github&utm_medium=readme&utm_campaign=gh-900-study-guide)

---

## Question 5

*Understand Git and GitHub basics*

**Which two statements about GitHub account types are accurate? (Select TWO.)** Choose 2.

- **a.** An organization owns public repositories, while private ones belong to its members
- **b.** A personal account can own repositories, packages and projects
- **c.** You cannot sign in to an organization; members use their own user accounts
- **d.** Enterprise accounts are included with GitHub Team to group several organizations
- **e.** Each person needs a separate personal account for work and for open source projects

<details>
<summary>Show answer and explanation</summary>

**Answer: b, c**

- **a** ❌ Organizations can own both public and private repositories; private work does not have to live in members' personal accounts.
- **b** ✅ Correct. User accounts own resources such as repositories, packages and projects, just as organizations can.
- **c** ✅ Correct. Organizations have no login of their own. Members sign in as themselves and their actions on organization resources are attributed to their user accounts.
- **d** ❌ Enterprise accounts come with GitHub Enterprise Cloud and GitHub Enterprise Server, not with GitHub Team.
- **e** ❌ GitHub recommends a single personal account for both; access to employer resources comes from organization membership.

**The concept.** Personal accounts, organizations and enterprise accounts play different roles.

**Why this is correct.** Every person on GitHub.com signs in with a user account, which can own repositories, packages and projects. Organizations also own resources, public and private, but cannot be signed in to: members act through their own accounts. Enterprise accounts, available with GitHub Enterprise Cloud and Server, centrally manage policy and billing for multiple organizations.

**How to reason it out**

1. Recall what each account type can own.
2. Remember that only user accounts sign in.
3. Match enterprise accounts to the GitHub Enterprise plans, not GitHub Team.
4. Reject the claims that split public and private ownership or require two personal accounts.

> **Exam tip:** Users sign in and own things; organizations own things but nobody signs in to them.

</details>

📖 Learn this topic: [Working with GitHub: Accounts, Plans, the GitHub Flow, Markdown, Desktop and Mobile (GitHub Foundations GH-900)](https://www.savemycert.com/revision/github-foundations/github-accounts-flow-markdown-desktop-mobile/?utm_source=github&utm_medium=readme&utm_campaign=gh-900-study-guide)

---

## Question 6

*Understand Git and GitHub basics*

**A small team keeps a project in a cloud drive that already saves an automatic version history for each file. The team now wants to build two alternative versions of the whole project at the same time and later combine the best parts. Which benefit of Git is the strongest reason to move?** Choose one.

- **a.** Shared access that lets the whole team open the same project files online
- **b.** A version history that keeps each earlier copy of a file so it can be restored
- **c.** An off-site copy of the project files that is kept if a laptop is ever lost
- **d.** Branches that let separate lines of work develop side by side and be merged

<details>
<summary>Show answer and explanation</summary>

**Answer: d**

- **a** ❌ The cloud drive already gives the team shared access. Sharing files is not the gap described in the scenario.
- **b** ❌ Git does keep full history, but the cloud drive already provides per-file version history, so this is not a reason to move.
- **c** ❌ The cloud drive already keeps the files off the laptops. Protecting against a lost device is not the new requirement.
- **d** ✅ This is the requirement the cloud drive cannot meet: Git branches let two versions of the entire project evolve side by side, and merging combines them later.

**The concept.** Branching and merging: separate lines of work for a whole project that can be developed in parallel and combined.

**Why this is correct.** Several benefits of version control are real here, but the stem says the drive already gives per-file history, shared access and an off-site copy. The new requirement is two alternative versions of the whole project developed in parallel and combined later. That is exactly what Git branches and merges provide: each branch is an independent line of work across all files, and a merge brings the changes together while keeping the history of both.

**How to reason it out**

1. List what the current tool already does: per-file history, sharing, off-site storage.
2. Isolate the new requirement: parallel versions of the whole project, combined later.
3. Match it to the Git concept: branches for parallel lines of work, merge to combine.
4. Discard benefits the team already has, however true they are of Git.

> **Exam tip:** Per-file history is common; project-wide branching and merging is what version control like Git adds.

</details>

📖 Learn this topic: [Git vs GitHub: Version Control Fundamentals for GitHub Foundations (GH-900)](https://www.savemycert.com/revision/github-foundations/git-vs-github-version-control-fundamentals/?utm_source=github&utm_medium=readme&utm_campaign=gh-900-study-guide)

---

## Question 7

*Work with GitHub repositories*

**A maintainer wants people who open a repository's main page to see straight away what the project does, how to install it and how to start using it. Which file should hold this information?** Choose one.

- **a.** A SUPPORT.md file in the repository root
- **b.** A CONTRIBUTING.md file in the repository root
- **c.** A CODEOWNERS file in the .github folder
- **d.** A README.md file in the repository root

<details>
<summary>Show answer and explanation</summary>

**Answer: d**

- **a** ❌ SUPPORT.md points people to help resources (forums, chat, paid support). It is not rendered as the project's introduction on the main page.
- **b** ❌ CONTRIBUTING.md tells people how to contribute (coding style, tests, pull request process). GitHub links it when someone opens an issue or pull request; it is not the project's front page.
- **c** ❌ CODEOWNERS maps file paths to the people or teams responsible for reviewing them. It is never shown as a project description.
- **d** ✅ Correct. GitHub renders the README automatically on the repository's main page, so it is where you explain what the project does, how to install it and how to use it.

**The concept.** The README is the repository's front page.

**Why this is correct.** GitHub automatically displays a README found in the .github folder, the root or the docs folder on the repository's main page. That makes it the place for the project's purpose, installation and usage. CONTRIBUTING.md covers how to contribute, SUPPORT.md where to get help, and CODEOWNERS who reviews which paths.

**How to reason it out**

1. Identify what the visitor needs: an overview on the main page.
2. Recall which file GitHub renders automatically on the main page.
3. Separate it from files that serve contributors, support seekers or reviewers.
4. Choose the README.

> **Exam tip:** README = what the project is and how to use it, shown on the main page.

</details>

📖 Learn this topic: [GitHub Repository Management: README, CODEOWNERS, Templates and Insights (GH-900)](https://www.savemycert.com/revision/github-foundations/github-repository-management-readme-codeowners-templates/?utm_source=github&utm_medium=readme&utm_campaign=gh-900-study-guide)

---

## Question 8

*Work with GitHub repositories*

**A repository contains a README.md in its root, a second one in its docs folder and a third in its hidden .github folder. Each has different text. Which one does GitHub display on the repository's main page?** Choose one.

- **a.** The copy in the docs folder, because GitHub checks docs first
- **b.** The copy in the .github folder, because .github is checked first
- **c.** The copy in the root, because GitHub checks the root first
- **d.** The copy committed most recently, since GitHub ignores folder order

<details>
<summary>Show answer and explanation</summary>

**Answer: b**

- **a** ❌ The docs folder is checked last, after .github and the root.
- **b** ✅ Correct. When several READMEs exist, GitHub uses the one in .github first, then the root, then docs.
- **c** ❌ The root is the second place GitHub looks. A README in the .github folder takes precedence over it.
- **d** ❌ GitHub chooses by location order, not by commit date.

**The concept.** GitHub looks for a README in three locations, in a fixed order.

**Why this is correct.** A README is displayed automatically when it sits in the repository's .github folder, its root or its docs folder. If more than one exists, GitHub picks the .github copy first, then the root, then docs. That surprises people who expect the root file to win, and is a common reason a README edit seems to have no effect on the main page.

**How to reason it out**

1. List the three supported locations: .github, root, docs.
2. Recall the precedence order: .github, then root, then docs.
3. Ignore commit dates; only location matters.
4. The .github copy is displayed.

> **Exam tip:** README precedence: .github, then root, then docs.

</details>

📖 Learn this topic: [GitHub Repository Management: README, CODEOWNERS, Templates and Insights (GH-900)](https://www.savemycert.com/revision/github-foundations/github-repository-management-readme-codeowners-templates/?utm_source=github&utm_medium=readme&utm_campaign=gh-900-study-guide)

---

## Question 9

*Work with GitHub repositories*

**A developer publishes code in a public repository but never adds a license. Another company wants to copy the code into its own product. What does the missing license mean for them?** Choose one.

- **a.** They may use it under the MIT license that GitHub applies by default
- **b.** They may view it, but forking is blocked until a license is added
- **c.** They can view and fork it on GitHub, but have no right to reuse it
- **d.** They may reuse it if they credit the author, as with public code

<details>
<summary>Show answer and explanation</summary>

**Answer: c**

- **a** ❌ GitHub does not apply a default license. A repository without a license has none.
- **b** ❌ Public repositories can be viewed and forked under GitHub's Terms of Service whether or not they have a license.
- **c** ✅ Correct. Default copyright applies: the author keeps all rights. GitHub's Terms of Service let users view and fork public repositories, but that grants no right to reproduce, distribute or build on the code.
- **d** ❌ Attribution is a condition of some open source licenses. Without any license there is no grant at all, so crediting the author does not give permission.

**The concept.** No license means default copyright: all rights reserved by the author.

**Why this is correct.** Without a LICENSE file, default copyright law applies and nobody else may reproduce, distribute or create derivative works from the code. GitHub's Terms of Service still allow other users to view and fork a public repository on GitHub, but that is not permission to use the code elsewhere. GitHub applies no default license; a maintainer who wants reuse adds one, for example with the license picker when creating the repository.

**How to reason it out**

1. Notice there is no license file at all.
2. Recall that copyright applies by default and grants others nothing.
3. Recall what GitHub's Terms of Service do allow: viewing and forking on GitHub.
4. Conclude that reuse in another product is not permitted.

> **Exam tip:** Public is not the same as open source: without a LICENSE, the code is all rights reserved.

</details>

📖 Learn this topic: [GitHub Repository Management: README, CODEOWNERS, Templates and Insights (GH-900)](https://www.savemycert.com/revision/github-foundations/github-repository-management-readme-codeowners-templates/?utm_source=github&utm_medium=readme&utm_campaign=gh-900-study-guide)

---

## Question 10

*Collaborate using GitHub*

**An open-source maintainer receives many "how do I configure this?" questions filed as issues, and they bury real bug reports. The maintainer wants a place where helpers can answer and the best reply can be marked for future readers. What should the maintainer set up?** Choose one.

- **a.** An issue label named question plus a saved filter that hides it
- **b.** A repository wiki page where users append questions and answers
- **c.** A discussions category that uses the question and answer format
- **d.** A public gist that collects the questions for helpers to answer

<details>
<summary>Show answer and explanation</summary>

**Answer: c**

- **a** ❌ Labelled issues still sit in the issue tracker beside bugs, and issues have no way to mark one comment as the accepted answer.
- **b** ❌ A wiki is for maintained documentation. A shared page of appended questions has no threading, notifications per question, or marked answers.
- **c** ✅ Correct. Discussions are for open-ended conversation, and a question-and-answer category lets a comment be marked as the answer so later readers find it quickly.
- **d** ❌ Gists share snippets or files. They have a flat comment stream and nothing that marks an answer or organises questions by topic.

**The concept.** GitHub Discussions holds open-ended conversation such as questions, ideas and announcements, separately from the issue tracker.

**Why this is correct.** Questions about usage are not actionable work items, so they belong in Discussions rather than Issues. A category in the question-and-answer format adds the ability to mark a comment as the answer, which is exactly the 'best reply for future readers' requirement. A label keeps the questions in the tracker; a wiki page or gist has no answer-marking or per-question threads.

**How to reason it out**

1. Separate actionable work (bugs) from open-ended questions.
2. Questions go to Discussions, not Issues.
3. Pick the category format that can mark an answer: question and answer.
4. Reject options that keep questions in the tracker or lack threads.

> **Exam tip:** Bugs and tasks are issues; questions are discussions, and Q&A categories let you mark the answer.

</details>

📖 Learn this topic: [GitHub Collaboration Tools: Issues, Pull Requests, Discussions, Notifications and Pages (GH-900)](https://www.savemycert.com/revision/github-foundations/github-issues-pull-requests-discussions-collaboration/?utm_source=github&utm_medium=readme&utm_campaign=gh-900-study-guide)

---

## Question 11

*Collaborate using GitHub*

**A team finds a defect in its checkout page. It needs to give the defect an owner, follow it through to a code change, and see it closed automatically when the fix is merged. Which GitHub feature should the team use to record the defect?** Choose one.

- **a.** An issue in the repository that the fix will be merged into
- **b.** A discussion in the repository's General discussions category
- **c.** A comment on the commit that introduced the checkout defect
- **d.** A page in the repository wiki that lists the known defects

<details>
<summary>Show answer and explanation</summary>

**Answer: a**

- **a** ✅ Correct. Issues track actionable work: they take assignees and labels and can be closed automatically by a linked pull request.
- **b** ❌ Discussions suit open-ended conversation. They cannot be closed by merging a pull request, so they fail the automatic-closure requirement.
- **c** ❌ A commit comment records feedback on that commit, but it cannot be assigned, tracked to closure or closed by a pull request.
- **d** ❌ A wiki page is documentation. Entries on it have no owner field, state, or link to the pull request that fixes them.

**The concept.** Issues are GitHub's unit of trackable work; discussions are for conversation.

**Why this is correct.** An issue can be assigned, labelled, added to projects and linked to the pull request that fixes it, and a closing keyword in that pull request closes it on merge into the default branch. A discussion, a commit comment or a wiki entry can hold text about the defect but none of them has an owner, an open/closed state tied to the fix, or automatic closure.

**How to reason it out**

1. Note the needs: an owner, tracking to a code change, automatic closure.
2. Only issues combine assignees, state and pull request linking.
3. Discussions, commit comments and wiki pages lack those.

> **Exam tip:** If work needs an owner and a 'done' state, open an issue.

</details>

📖 Learn this topic: [GitHub Collaboration Tools: Issues, Pull Requests, Discussions, Notifications and Pages (GH-900)](https://www.savemycert.com/revision/github-foundations/github-issues-pull-requests-discussions-collaboration/?utm_source=github&utm_medium=readme&utm_campaign=gh-900-study-guide)

---

## Question 12

*Collaborate using GitHub*

**An issue proposes a broad redesign of a project's plugin system. Dozens of people are debating ideas, but nobody has agreed on any concrete work. A member with triage access wants to keep the whole conversation and its comments but take it out of the backlog of actionable work. What should they do?** Choose one.

- **a.** Transfer the issue into another repository of the same owner
- **b.** Close the issue as not planned and lock its conversation
- **c.** Convert the issue into a discussion in an ideas category
- **d.** Pin the issue so it shows at the top of the issue list

<details>
<summary>Show answer and explanation</summary>

**Answer: c**

- **a** ❌ Transferring keeps it as an issue, so it is still in a backlog of actionable work, only in a different repository.
- **b** ❌ That stops the conversation instead of keeping it open for ideas, and the redesign may still become planned work later.
- **c** ✅ Correct. Open-ended issues can be converted into discussions, which keeps the conversation and moves it out of the issue backlog. Triage permission is enough.
- **d** ❌ Pinning gives the issue more visibility in the tracker, which is the opposite of taking it out of the backlog.

**The concept.** Issues that are really open-ended conversation can be converted into discussions.

**Why this is correct.** GitHub lets people with triage access convert an issue into a discussion when an idea is still at an early stage. The comments move with it, and the backlog keeps only actionable work. Transferring leaves it as an issue elsewhere; closing and locking ends the conversation; pinning makes it more prominent in the tracker.

**How to reason it out**

1. Is there agreed, actionable work? No: it is still an idea.
2. The conversation must be kept, not ended.
3. Converting to a discussion keeps comments and leaves the backlog.
4. Transfer, close-and-lock and pin all fail one requirement.

> **Exam tip:** Open-ended idea in the issue tracker? Convert it to a discussion.

</details>

📖 Learn this topic: [GitHub Collaboration Tools: Issues, Pull Requests, Discussions, Notifications and Pages (GH-900)](https://www.savemycert.com/revision/github-foundations/github-issues-pull-requests-discussions-collaboration/?utm_source=github&utm_medium=readme&utm_campaign=gh-900-study-guide)

---

## Question 13

*Apply modern development practices*

**A team wants its test suite to run automatically whenever someone opens a pull request, with the result shown on the pull request before anyone merges it. Which GitHub feature provides this?** Choose one.

- **a.** GitHub Actions
- **b.** GitHub Projects
- **c.** GitHub Pages
- **d.** GitHub Codespaces

<details>
<summary>Show answer and explanation</summary>

**Answer: a**

- **a** ✅ Correct. An Actions workflow can be triggered by pull request events, run the tests on a runner and report the result as a check on the pull request.
- **b** ❌ Projects plans and tracks issues and pull requests on boards and tables. It does not execute any code.
- **c** ❌ Pages publishes a static website from a repository. It does not run test suites against pull requests.
- **d** ❌ Codespaces gives a developer a cloud development environment to work in. It does not run tests on its own when a pull request opens.

**The concept.** GitHub Actions runs automated workflows in response to repository events such as a pull request being opened.

**Why this is correct.** The requirement is automation triggered by an event (a pull request) that runs code (the tests) and reports back. That is exactly what an Actions workflow does: the pull request event triggers it, a runner executes the tests, and the result appears on the pull request. Pages publishes sites, Codespaces is an interactive environment for a person, and Projects only tracks work.

**How to reason it out**

1. Spot the trigger: a pull request is opened.
2. Spot the action: run code (tests) without a person starting it.
3. Event-driven automation that runs code is GitHub Actions.
4. Reject features that host sites, environments or plans.

> **Exam tip:** Something should run automatically when something happens in the repository: that is GitHub Actions.

</details>

📖 Learn this topic: [GitHub Actions, Copilot, Codespaces and github.dev: Automation and AI Tools (GH-900)](https://www.savemycert.com/revision/github-foundations/github-actions-copilot-codespaces-github-dev/?utm_source=github&utm_medium=readme&utm_campaign=gh-900-study-guide)

---

## Question 14

*Apply modern development practices*

**Which TWO tasks can a GitHub Actions workflow carry out in a repository? (Select TWO.)** Choose 2.

- **a.** Add a label to each new issue as soon as it is opened
- **b.** Collect a user's notifications into one filtered inbox for triage
- **c.** Build and publish a package when a release is published
- **d.** Host a running development environment that a developer edits in
- **e.** Suggest the next lines of code as a developer types in the editor

<details>
<summary>Show answer and explanation</summary>

**Answer: a, c**

- **a** ✅ Correct. Workflows can be triggered by issue events and call the GitHub API, so labelling new issues is a standard use beyond CI/CD.
- **b** ❌ The notifications inbox is a GitHub.com feature for each user. A workflow does not build or manage someone's inbox.
- **c** ✅ Correct. Building, packaging and publishing on a release event is a classic continuous delivery use of Actions.
- **d** ❌ An interactive, cloud-hosted development environment is GitHub Codespaces, not an Actions workflow. A workflow run ends when its jobs finish.
- **e** ❌ Suggesting code while someone types is GitHub Copilot in the editor. Workflows run on events, not inside a developer's editor.

**The concept.** GitHub Actions automates any repository task that an event can trigger, from CI/CD to issue and release housekeeping.

**Why this is correct.** Actions is not only CI: a workflow can react to issue, pull request, release, schedule and many other events and run any script or reusable action on a runner. Labelling new issues and building and publishing a package on release are both event-triggered automation. A live editing environment is Codespaces, code completion is Copilot, and the notification inbox is a per-user GitHub.com feature.

**How to reason it out**

1. Ask whether each task is triggered by an event and can run unattended.
2. Issue labelling on 'issue opened' and publishing on 'release published' both qualify.
3. An environment a person edits in is Codespaces.
4. Typing-time suggestions are Copilot; inbox triage is notifications.

> **Exam tip:** Actions automates CI/CD and everyday repository chores, anything an event can trigger.

</details>

📖 Learn this topic: [GitHub Actions, Copilot, Codespaces and github.dev: Automation and AI Tools (GH-900)](https://www.savemycert.com/revision/github-foundations/github-actions-copilot-codespaces-github-dev/?utm_source=github&utm_medium=readme&utm_campaign=gh-900-study-guide)

---

## Question 15

*Apply modern development practices*

**A developer is adding the first automated workflow to a repository. In which directory must the workflow's YAML file be committed for GitHub to run it?** Choose one.

- **a.** .devcontainer/workflows
- **b.** .github/actions
- **c.** .github/workflows
- **d.** .github/ISSUE_TEMPLATE

<details>
<summary>Show answer and explanation</summary>

**Answer: c**

- **a** ❌ The .devcontainer directory holds dev container configuration for Codespaces, not Actions workflows.
- **b** ❌ Custom actions are often kept in a folder like this, but GitHub only discovers workflow files in .github/workflows.
- **c** ✅ Correct. Workflows are YAML files in the .github/workflows directory of the repository; a repository can hold several of them.
- **d** ❌ This directory holds issue templates and their config file. Workflow files placed here are never run.

**The concept.** GitHub Actions workflows are YAML files stored in the repository's .github/workflows directory.

**Why this is correct.** GitHub looks for workflow definitions only in .github/workflows. Each YAML file there is a separate workflow with its own triggers and jobs. Folders such as .github/actions (a common home for custom actions), .devcontainer (Codespaces configuration) and .github/ISSUE_TEMPLATE (issue templates) have other purposes.

**How to reason it out**

1. Workflows are YAML files.
2. They live under the .github folder.
3. The exact subfolder is workflows.
4. Other .github or .devcontainer folders serve other features.

> **Exam tip:** One workflow per YAML file, all in .github/workflows.

</details>

📖 Learn this topic: [GitHub Actions, Copilot, Codespaces and github.dev: Automation and AI Tools (GH-900)](https://www.savemycert.com/revision/github-foundations/github-actions-copilot-codespaces-github-dev/?utm_source=github&utm_medium=readme&utm_campaign=gh-900-study-guide)

---

## Question 16

*Manage projects with GitHub*

**A product manager needs one place to plan work drawn from issues and pull requests in four repositories, and to switch between a spreadsheet-style list, a kanban board and a timeline. What should the manager create?** Choose one.

- **a.** A shared label added in each of the four repositories
- **b.** An organization project with items from each repo
- **c.** An organization discussion with a pinned planning post
- **d.** A milestone in the busiest of the four repositories

<details>
<summary>Show answer and explanation</summary>

**Answer: b**

- **a** ❌ Labels are created per repository and only tag items; they give no single planning surface and no table, board or timeline views.
- **b** ✅ Correct. A project is an adaptable table, board and roadmap that can hold issues and pull requests from many repositories, owned at the user or organization level.
- **c** ❌ Discussions hold conversation. They do not track issues and pull requests as items with fields, layouts or status.
- **d** ❌ A milestone belongs to one repository, so it cannot hold the other three repositories' work, and it has no board or timeline views.

**The concept.** GitHub Projects is a planning tool built from issues, pull requests and draft issues, viewed as a table, board or roadmap.

**Why this is correct.** The requirement combines two things: work from several repositories in one place, and three ways of looking at it. A project, owned by a user or an organization, can contain issues and pull requests from many repositories and offers table, board and roadmap layouts. Milestones and labels are both scoped to a single repository, and a discussion is a conversation, not a tracker.

**How to reason it out**

1. Note that the work spans several repositories.
2. Note the three views: list, kanban board and timeline.
3. Recall that projects offer table, board and roadmap layouts across repositories.
4. Reject tools scoped to one repository or meant for conversation.

> **Exam tip:** Cross-repository planning with table, board and roadmap views is what GitHub Projects is for.

</details>

📖 Learn this topic: [GitHub Projects, Labels, Milestones and Insights: Project Tracking (GH-900)](https://www.savemycert.com/revision/github-foundations/github-projects-labels-milestones-insights/?utm_source=github&utm_medium=readme&utm_campaign=gh-900-study-guide)

---

## Question 17

*Manage projects with GitHub*

**In a project's table view, a team lead changes an issue's Assignees cell from Ana to Raj. What happens to the issue itself in its repository?** Choose one.

- **a.** The issue is now assigned to Raj in the repository too
- **b.** The issue keeps Ana; the project row alone shows Raj
- **c.** The issue adds Raj and keeps Ana as a second assignee
- **d.** The issue gets a comment from the lead that mentions Raj

<details>
<summary>Show answer and explanation</summary>

**Answer: a**

- **a** ✅ Correct. Built-in fields such as Assignees, Labels and Milestone are the issue's own data, so editing them in the project updates the issue.
- **b** ❌ Projects do not keep a private copy of built-in metadata. The assignee shown in the project is the issue's real assignee, so it changes in both places.
- **c** ❌ The lead replaced Ana with Raj. The edit sets the assignee list exactly as the cell shows it, so Ana is removed.
- **d** ❌ Changing the field changes the assignment. It does not post a comment or a mention on the issue.

**The concept.** Projects stay in sync with the issues and pull requests they contain.

**Why this is correct.** A project item is a live view of the issue, not a copy. Built-in metadata (assignees, labels, milestone) is read from and written to the issue, so a change in the project shows up on the issue and vice versa. Custom fields are different: they exist only in the project. The tempting answer that only the project row changes describes custom fields, not built-in ones.

**How to reason it out**

1. Identify the field edited: Assignees, a built-in field.
2. Recall that built-in fields are the issue's own metadata.
3. Conclude that the change syncs back to the issue.
4. Remember that only custom fields live solely in the project.

> **Exam tip:** Editing assignees, labels or milestone in a project edits the issue itself.

</details>

📖 Learn this topic: [GitHub Projects, Labels, Milestones and Insights: Project Tracking (GH-900)](https://www.savemycert.com/revision/github-foundations/github-projects-labels-milestones-insights/?utm_source=github&utm_medium=readme&utm_campaign=gh-900-study-guide)

---

## Question 18

*Understand privacy, security, and administration*

**A developer turned on 2FA for her GitHub account using an authenticator app on her phone. The phone is lost, and she still knows her password. What should she use to sign in?** Choose one.

- **a.** One of the recovery codes she saved during setup
- **b.** A password reset link sent to her primary email
- **c.** A request to GitHub Support to switch off her 2FA
- **d.** A new personal access token created by a teammate

<details>
<summary>Show answer and explanation</summary>

**Answer: a**

- **a** ✅ Correct. Recovery codes are generated when 2FA is configured and let you sign in when the second factor is unavailable.
- **b** ❌ Resetting the password does not remove the second-factor step, so she would still be asked for a 2FA code.
- **c** ❌ GitHub Support cannot restore access to a 2FA account when the credentials and recovery methods are lost.
- **d** ❌ Tokens are created by the account owner for API and Git access; a teammate cannot create one for her, and it does not sign in to the website.

**The concept.** Recovery codes are the planned way back into a 2FA account when the second factor is lost.

**Why this is correct.** GitHub asks you to download and store recovery codes when you configure 2FA, and to set up additional recovery methods. Each code lets you complete sign-in without the lost device. A password reset still leaves the 2FA step in place, and GitHub Support cannot bypass 2FA for you, so an account with no codes or other recovery method can be lost for good.

**How to reason it out**

1. Note that the password is known but the second factor is gone.
2. Recall what GitHub gives you at 2FA setup for exactly this case.
3. Reject options that only reset the password or rely on someone else.
4. Sign in with a saved recovery code, then set up a new factor.

> **Exam tip:** Save your 2FA recovery codes somewhere safe: GitHub Support cannot bypass 2FA for you.

</details>

📖 Learn this topic: [GitHub Security and Access Management: 2FA, Passkeys, Roles and Branch Protection (GH-900)](https://www.savemycert.com/revision/github-foundations/github-security-2fa-roles-permissions-branch-protection/?utm_source=github&utm_medium=readme&utm_campaign=gh-900-study-guide)

---

## Question 19

*Understand privacy, security, and administration*

**A new contributor is enabling two-factor authentication on a personal GitHub account. Which two of the following can serve as a second factor for that account? (Select TWO.)** Choose 2.

- **a.** Codes from a TOTP authenticator app
- **b.** A FIDO2 hardware security key
- **c.** A fine-grained personal access token
- **d.** An SSH key added to the account
- **e.** A code sent to a secondary email

<details>
<summary>Show answer and explanation</summary>

**Answer: a, b**

- **a** ✅ Correct. Time-based one-time passwords from an authenticator app are a standard GitHub 2FA method.
- **b** ✅ Correct. Security keys (WebAuthn), such as FIDO2 hardware keys, can be registered as a second factor.
- **c** ❌ A personal access token authenticates API and Git requests in place of a password; it is not a 2FA method.
- **d** ❌ SSH keys authenticate Git operations over SSH; they are not a second factor for signing in.
- **e** ❌ Email codes are used for device verification when 2FA is off, not as a configured second factor.

**The concept.** GitHub 2FA methods are authenticator apps (TOTP), SMS, security keys, GitHub Mobile and passkeys.

**Why this is correct.** A second factor proves you hold something besides your password. GitHub accepts TOTP codes from an authenticator app or SMS as the base method, then lets you add security keys, GitHub Mobile and passkeys. SSH keys and personal access tokens are credentials for Git and API access, and email verification codes are what GitHub uses for unrecognised devices when 2FA is not enabled.

**How to reason it out**

1. Separate sign-in second factors from Git and API credentials.
2. Recall the supported methods: TOTP app, SMS, security key, GitHub Mobile, passkey.
3. Pick the authenticator app and the hardware key.

> **Exam tip:** Second factors: authenticator app, SMS, security key, GitHub Mobile, passkey. SSH keys and tokens are not 2FA.

</details>

📖 Learn this topic: [GitHub Security and Access Management: 2FA, Passkeys, Roles and Branch Protection (GH-900)](https://www.savemycert.com/revision/github-foundations/github-security-2fa-roles-permissions-branch-protection/?utm_source=github&utm_medium=readme&utm_campaign=gh-900-study-guide)

---

## Question 20

*Explore the GitHub community*

**A company is deciding whether to publish its internal date-parsing library as a public open source repository on GitHub. Which TWO benefits does making the project open source typically bring? (Select TWO.)** Choose 2.

- **a.** Outside developers can review the code and report or fix defects
- **b.** The project's code is protected from being copied by competitors
- **c.** Other projects can reuse the code under the terms of its license
- **d.** GitHub takes over maintenance and support of the public project
- **e.** Contributors receive write access to the repository by default

<details>
<summary>Show answer and explanation</summary>

**Answer: a, c**

- **a** ✅ Correct. Public code can be read by anyone, so more people find bugs and propose fixes through issues and pull requests.
- **b** ❌ The opposite: public code under an open source license is meant to be read, copied and reused within the license terms.
- **c** ✅ Correct. Reuse under a published license is a core benefit: others build on the code instead of rewriting it.
- **d** ❌ GitHub hosts the repository, but the project's maintainers stay responsible for it. Going public does not hand maintenance to GitHub.
- **e** ❌ Open source does not grant write access. Outside contributors fork the repository and open pull requests that maintainers review.

**The concept.** Open source makes code publicly available under a license so others can use, study, change and share it.

**Why this is correct.** The two real benefits are transparency (anyone can inspect the code, so more eyes find and fix problems) and reuse (others can build on it under its license). Open source does not give contributors write access; they contribute through forks and pull requests that maintainers review. GitHub does not maintain the project for its owners, and publishing code openly is the opposite of hiding it from competitors.

**How to reason it out**

1. Think about what changes when code becomes publicly readable.
2. Link public visibility to review and defect fixing by others.
3. Link the license to reuse in other projects.
4. Reject options about write access, GitHub-run maintenance or protection from copying.

> **Exam tip:** Open source trades secrecy for transparency, community review and reuse under a license.

</details>

📖 Learn this topic: [Open Source on GitHub: Sponsors, Marketplace, InnerSource, Forks and Discovery (GH-900)](https://www.savemycert.com/revision/github-foundations/github-open-source-sponsors-marketplace-innersource/?utm_source=github&utm_medium=readme&utm_campaign=gh-900-study-guide)

---

[← Back to the GH-900 study guide](README.md)
