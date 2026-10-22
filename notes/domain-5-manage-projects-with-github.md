# Domain 5: Manage projects with GitHub (8%)

A lighter domain (official range 5–10%) about planning and following work: GitHub Projects with its layouts, fields and workflows, the repository-level labels and milestones, saved replies and assignees, and insights charts and status updates. The recurring distinction is scope: labels and milestones belong to one repository, a project spans many.

## 5.1 Project Tracking and organization

- **GitHub Projects** holds issues, PRs and **draft issues** as items in a table, board or roadmap, with custom fields and saved views. Owned by a **user or organization**, not a repository, so one project spans many repos. (This is the current Projects, not "Projects (classic)".)
- **Two-way sync**: built-in fields (Title, Assignees, Labels, Milestone, Repository, Reviewers, Linked pull requests) are the issue's own data. Change them in the project and the issue changes, and vice versa. **Custom fields** (Status, Priority, Points) live only in the project.
- **Views** are saved tabs: layout + filter + sort + group-by + slice-by + visible fields. Unsaved changes are flagged on the tab.
- Projects can be public or private, with read/write/admin access granted separately from repo access. Orgs can save projects as **templates**; a project can be **linked** to repos so it shows in their Projects tab.

| Layout  | Shows                                   | Driven by                                          | Use                              |
| ------- | --------------------------------------- | -------------------------------------------------- | -------------------------------- |
| Table   | Spreadsheet grid, one row per item      | Any fields                                         | Triage, bulk edits               |
| Board   | Kanban cards in columns                 | **Single select or iteration** field (e.g. Status) | Flow between stages              |
| Roadmap | Bars on a timeline (month/quarter/year) | **Start** and **target** date or iteration fields  | Dates, overlaps across a release |

- Only roadmap draws dates as bars. Text, number and date fields can't be board columns (no fixed set of values). Board columns can show a field sum and an item limit.

| Field type    | Choose when                                                  |
| ------------- | ------------------------------------------------------------ |
| Text          | Free notes                                                   |
| Number        | Estimates/points to sort, sum or chart                       |
| Date          | Due/start dates, roadmap bars                                |
| Single select | Fixed choices (status, priority, size); can be board columns |
| Iteration     | Repeating sprints/cycles                                     |

- **Iteration field**: start date + duration (days or weeks), generates consecutive blocks, supports **breaks** (e.g. holidays). Filters `iteration:@current`, `@next`, `@previous` keep views current without editing each sprint. A single select of sprint names can't do breaks or "current".
- **Draft issue**: lives only in the project (title, Markdown body, assignees, custom fields). **No labels or milestone** until converted to an issue in a chosen repo. Converting keeps it in the project.
- **Adding items**: paste a URL or type `#` to search; **bulk add from a repository** with a filter (e.g. `label:bug`); from the issue's Projects sidebar; or the auto-add workflow.

|                | Label                   | Milestone                      | Project                                  |
| -------------- | ----------------------- | ------------------------------ | ---------------------------------------- |
| Scope          | One repo                | One repo                       | Many repos (user/org owned)              |
| Per item       | Many                    | At most one                    | Item can be in several                   |
| Dates/progress | None                    | Optional due date + % complete | Date/iteration fields, roadmap, insights |
| Best for       | Categorising, filtering | A release or goal in one repo  | Planning across repos and teams          |

- **Default labels**: `bug`, `documentation`, `duplicate`, `enhancement`, `good first issue`, `help wanted`, `invalid`, `question`, `wontfix`.
  - `good first issue` marks beginner work and feeds the repo's **contribute page**. `help wanted` only signals that help is welcome.
  - Org owners can customise default labels for new repos; each copy is still a normal repo label.
- **Permissions**: **triage** can apply/dismiss labels (no push). **Write** is needed to create/edit/delete labels and to manage milestones.
- **Milestone ≠ release.** A milestone tracks planned work toward a due date; a release packages shipped software at a Git tag.
- **Built-in workflows** (no code). **On by default**: item **closed** → Status Done; PR **merged** → Status Done. Others can be enabled (on add, reopen, review approved/changes requested).
  - **Auto-add to project**: adds items matching a filter, but **only items created or updated after it's enabled**. Bring the existing backlog in once with bulk add.
  - **Auto-archive items**: archives items matching criteria (e.g. closed and stale). Archived items can be restored.
  - Anything beyond that → **GitHub Actions + GraphQL API**.

|         | Saved reply                    | Issue/PR template             |
| ------- | ------------------------------ | ----------------------------- |
| Used by | You, writing a comment         | Anyone opening a new issue/PR |
| Stored  | Your personal account settings | Repo files (e.g. `.github`)   |
| Fills   | A comment box                  | The body of a new issue/PR    |

- **Saved replies** work in issues, PRs and discussions in any repo or org where you can comment. Private to you; org members don't share them.
- **Assignee filters**:
  - `assignee:@me`: `@me` resolves to the viewer, so one shared view shows everyone their own items.
  - `-assignee:@me`: everything not assigned to you (leading hyphen negates).
  - `no:assignee`: unowned items, a good triage view.
  - `reviewers:@me`: PRs where you're a requested reviewer (not the same as assigned).
  - Group or slice by Assignees to see each person's workload.

|         | Current chart                          | Historical chart                               |
| ------- | -------------------------------------- | ---------------------------------------------- |
| Shows   | Items as they are now                  | Change over time                               |
| X-axis  | A field (Status, Assignees, Iteration) | Time                                           |
| Example | Points per status this sprint          | Default **burn up** chart (completed vs total) |

- **Chart settings**: layout (bar, column, line, stacked area…), X-axis, Y-axis = **count of items** or **sum/average/min/max of a number field**. Current charts can group bars by a second field. Filters use view syntax (`iteration:@current`, a Release field value).
- Sum of Points weights big tasks more; count treats all items equally.
- A chart filtered to one release can show progress across several repos, which a single milestone can't.
- **Status update**: status (**On track, At risk, Off track, Inactive, Complete**), optional start/target dates, Markdown message. Posted by people with **write** access to the project. Latest shows in the side panel, header and project lists; history is kept.
- **Traps:**
  - "Track across several repos" → project, not milestone.
  - "Labels on a draft issue" → convert first.
  - "Auto-add didn't pick up old issues" → expected; bulk add.
  - Triage applies labels; write creates them.

📖 Full lesson: [GitHub Projects, Labels, Milestones and Insights: Project Tracking (GH-900)](https://www.savemycert.com/revision/github-foundations/github-projects-labels-milestones-insights/?utm_source=github&utm_medium=readme&utm_campaign=gh-900-study-guide)

[← Back to the study guide](../README.md)
