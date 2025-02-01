## Using Conventional Commits for Git

### Commit Message Structure

| **Element**       | **Description**                                                      |
|-------------------|----------------------------------------------------------------------|
| `<type>`          | The type of change (e.g., `feat`, `fix`, `docs`).                    |
| `[scope]`         | An optional part that describes what part of the project is affected (e.g., `auth`, `parser`). |
| `<description>`   | A brief description of the change (e.g., `add login feature`).        |
| `[body]`          | Optional details or explanations of the change.                       |
| `[footer]`        | Optional extra info like `BREAKING CHANGE` or issue references.       |

### Commit Types

| **Type**          | **What It Means**                                                    |
|-------------------|----------------------------------------------------------------------|
| `feat`            | A new feature added to the project.                                   |
| `fix`             | A bug fix.                                                           |
| `BREAKING CHANGE` | A change that breaks backward compatibility.                          |
| `chore`           | Miscellaneous tasks like updates or maintenance.                     |
| `docs`            | Documentation updates.                                                |
| `style`           | Changes in formatting or code style (no logic change).                |
| `refactor`        | Code changes that improve structure but don’t add features or fix bugs. |
| `perf`            | Performance improvements.                                             |
| `test`            | Changes related to tests (new or fixed tests).                        |

### Examples of Commit Messages

| **Commit Type**        | **Example**                                              |
|------------------------|----------------------------------------------------------|
| Simple Commit          | `feat: add user authentication endpoint`                 |
| Commit with Scope      | `fix(auth): fix token expiry issue`                      |
| Breaking Change (Footer) | `feat: update login flow`<br>`BREAKING CHANGE: The login flow now requires a username.` |
| Breaking Change (`!`)  | `feat!: refactor login to use JWT authentication`        |
| Commit with Multiple Footers | `fix: resolve user registration bug`<br>`Reviewed-by: Alice`<br>`Refs: #123` |

---

### Pull Request (PR) Guidelines

| **Step**                | **Description**                                                              |
|-------------------------|------------------------------------------------------------------------------|
| **Branch Naming**        | Name branches like `feature/<feature-name>`, `fix/<bug-name>`, `chore/<task-name>`. |
| **PR Description**       | Briefly explain the changes. Link any related issues or PRs.                 |
| **PR Title**             | Follow the commit format: `feat(auth): add OAuth2 support`.                  |
| **Request for Review**   | Assign reviewers. Make sure code works and tests are passed.                  |
| **Squash Commits**       | Combine multiple commits into one if necessary for clarity.                 |

---

### Why Use Conventional Commits?

| **Benefit**               | **Explanation**                                                        |
|---------------------------|------------------------------------------------------------------------|
| **Automatic Changelog**    | Automatically generate changelogs based on commit types.                |
| **Semantic Versioning**    | Version updates are automated: `fix` = PATCH, `feat` = MINOR, `BREAKING CHANGE` = MAJOR. |
| **Better Collaboration**   | Clear commit history makes it easier for teams to collaborate.          |

---

### Commit Examples

| **Commit Type**         | **Example**                                                       | **Explanation**                                                       |
|-------------------------|-------------------------------------------------------------------|-----------------------------------------------------------------------|
| **feat**                | `feat: add user authentication endpoint`                          | Adds a new feature to the project (user authentication).             |
| **fix**                 | `fix: resolve token expiry issue`                                 | Fixes a bug related to token expiration.                             |
| **BREAKING CHANGE**     | `feat: update login flow`<br>`BREAKING CHANGE: The login flow now requires a username field.` | Introduces a breaking change (requires a username field now).       |
| **chore**               | `chore: update dependencies`                                      | Miscellaneous task, like updating project dependencies.              |
| **docs**                | `docs: update API documentation for login feature`                | Updates the documentation for the login feature.                     |
| **style**               | `style: format login form to match design guidelines`             | Only formatting changes with no logic changes.                       |
| **refactor**            | `refactor: improve login form structure for better readability`    | Code improvements without adding new features or fixing bugs.        |
| **perf**                | `perf: optimize login response time`                               | Improves the performance of the login process.                        |
| **test**                | `test: add unit test for user authentication`                     | Adds or fixes tests related to user authentication.                  |
| **revert**              | `revert: undo user authentication changes`<br>`Refs: #456`        | Reverts previous changes related to user authentication.             |

---
[Source](https://www.conventionalcommits.org/en/v1.0.0/#summary)