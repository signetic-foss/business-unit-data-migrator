# Contributing to this project

First off, thank you for considering contributing to this project! Your support and involvement are greatly appreciated.

## Table of Contents

- [Code of Conduct](#code-of-conduct)
- [How Can I Contribute?](#how-can-i-contribute)
  - [Reporting Bugs](#reporting-bugs)
  - [Suggesting Enhancements](#suggesting-enhancements)
  - [Submitting Changes](#submitting-changes)
- [Development Setup](#development-setup)
- [Style Guidelines](#style-guidelines)
- [Branch Naming Convention](#branch-naming-convention)
- [Commit Messages](#commit-messages)
- [Using Commitizen for Commit Messages](#using-commitizen-for-commit-messages)
- [Pull Request Process](#pull-request-process)
- [Community](#community)
- [License](#license)

---

## Code of Conduct

This project and everyone participating in it is governed by the [this project Code of Conduct](./CODE_OF_CONDUCT.md). By participating, you are expected to uphold this code. Please report unacceptable behavior to [maintainer@example.com](mailto:maintainer@example.com).

## How Can I Contribute?

### Reporting Bugs

If you encounter any bugs or issues, please:

- **Ensure the issue hasn't been reported yet** by searching the [issue tracker](https://github.com/signetic-foss/this project/issues).
- **Open a new issue** if it hasn't been reported.
  - Use a clear and descriptive title.
  - Provide as much relevant information as possible.
  - Include steps to reproduce the issue.

### Suggesting Enhancements

We welcome suggestions to improve this project! To suggest an enhancement:

- **Check the roadmap** in [ROADMAP.md](./ROADMAP.md) and existing [issues](https://github.com/signetic-foss/this project/issues) to see if your idea is already being discussed.
- **Open a new issue** with the `enhancement` label.
  - Describe the feature you'd like to see.
  - Explain why it would be beneficial.
  - Include any examples or mockups if applicable.

### Submitting Changes

- **Fork the repository** and create your branch from `main`.
- **Work on an open issue**: If there's an existing issue that matches your contribution, comment on it to let others know you're working on it.
- **Write clear code**: Ensure your code follows the project's style guidelines.
- **Include tests**: For new features or bug fixes, include appropriate tests.
- **Document your changes**: Update the documentation in the `docs/` folder and the `README.md` if necessary.

## Development Setup

### Prerequisites

- **Node.js** (v18+ recommended)
- **pnpm** (package manager)
  ```bash
  npm install -g pnpm
  ```

### Steps

1. **Fork and Clone the Repository**

   ```bash
   git clone https://github.com/your-username/this project.git
   cd this project
   ```

2. **Install Dependencies**

   ```bash
   pnpm install
   ```

3. **Run the Application**

   ```bash
   pnpm start
   ```

4. **Run Tests**

   ```bash
   pnpm test
   ```

## Style Guidelines

- **Language**: All code should be written in **TypeScript**.
- **Formatting**: Use the provided `.editorconfig` and respect existing code style.
- **Linting**: Ensure your code passes linting checks.

## Branch Naming Convention

To maintain consistency and clarity, we use a branch naming convention that aligns with Conventional Commits. Please follow the structure below when creating branches for your contributions:

### Format:

```
<type>/<issue-or-ticket-id>-<short-description>
```

### Branch Types:

- **feat/**: For new features (aligns with the `feat` commit type).
- **fix/**: For bug fixes (aligns with the `fix` commit type).
- **chore/**: For maintenance tasks such as dependency updates or build process changes.
- **docs/**: For documentation-related updates.
- **refactor/**: For refactoring code without changing its behavior.
- **test/**: For adding or improving tests.
- **hotfix/**: For urgent fixes to be applied directly to production branches.

### Example Branch Names:

- `feat/123-add-authentication-feature`
- `fix/456-correct-login-error`
- `docs/update-api-readme`
- `chore/789-upgrade-dependencies`

By using this format, your branch names will be descriptive, and it will be easier for maintainers and other contributors to understand the purpose of the branch.

## Commit Messages

- **Format**: Use the [Conventional Commits](https://www.conventionalcommits.org/) style.
  - Example: `feat: add authentication middleware`
- **Structure**:
  - **feat**: A new feature
  - **fix**: A bug fix
  - **docs**: Documentation only changes
  - **style**: Changes that do not affect the meaning of the code (white-space, formatting, etc.)
  - **refactor**: A code change that neither fixes a bug nor adds a feature
  - **test**: Adding missing tests or correcting existing tests
  - **chore**: Changes to the build process or auxiliary tools

## Using Commitizen for Commit Messages

We use [Commitizen](https://commitizen.github.io/cz-cli/) to help structure commit messages according to the Conventional Commits standard. This makes it easier to write consistent and meaningful commit messages.

### To use Commitizen:

1. Ensure you have the dependencies installed:

   ```bash
   pnpm install
   ```

2. To make a commit using Commitizen, run:

   ```bash
   pnpm cz
   ```

   This will launch an interactive prompt that will guide you through the process of writing a properly formatted commit message.

By using `pnpm cz`, your commit messages will adhere to the Conventional Commits format automatically, helping to ensure consistency and clarity across all contributions.

## Pull Request Process

1. **Ensure your work is up-to-date** with the main repository.

   ```bash
   git checkout main
   git pull upstream main
   ```

2. **Push your feature branch** to your fork.

   ```bash
   git push origin feature/your-feature
   ```

3. **Open a Pull Request**:

   - Go to the original repository on GitHub.
   - Click on **New pull request**.
   - Select your feature branch.
   - Provide a clear and descriptive title.
   - In the description, explain the changes and reference any related issues.

4. **Wait for Review**:

   - Be responsive to feedback.
   - Make changes if requested.
   - Ensure all checks pass before merging.

## Community

- **Questions and Discussions**: Use the [Discussions](https://github.com/signetic-foss/this project/discussions) tab for general questions or to start a conversation.
- **Chat**: Join our community chat on [Discord](#) (if available) for real-time discussions.
- **Stay Updated**: Watch the repository to stay informed about new releases and updates.

## License

By contributing to this project, you agree that your contributions will be licensed under the [MIT License](./LICENSE).

---

Thank you for your contributions!
