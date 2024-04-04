# Parallel code scanning on monorepo

This is a sample demonstration of how to run parallel code scanning a monorepo using GitHub CodeQL.

There are many considerations and tactics in [Monorepo Book](https://monorepo-book.github.io/) on how to gain efficiency from monorepo. This demonstration primarily focuses on CodeQL code scanning.

### :grey_question: Problem to solve

When you have a large monorepo with multiple projects, it can consume unnecessary compute resources to scan projects with no new changes. This may lead to longer scanning duration, increase feedback lead time, and disrupt the developer's flow - which will further discourage developers to commit frequently and increase commit sizes.

### :bulb: Proposed solution

Scan only the projects that have new commits.

### :hammer_and_wrench: Implementation

At a high level,

1. Use `git diff` to get the list of files that have changed
2. Evaluate the path of the changed files with `.github/scripts/list-changed` to determine which projects to scan
3. Configure the advanced setup of CodeQL scan (i.e. `codeql.yml`) with `codeql-config.yml` to scan only the identified project folders

## Credits

This demonstration built on top of the idea and scripts from [thedave42/parallel-code-scanning](https://github.com/thedave42/parallel-code-scanning).

Sample projects to build this sample monorepo are:

- [WebGoat/WebGoat](https://github.com/WebGoat/WebGoat)
- [adeyosemanputra/pygoat](https://github.com/adeyosemanputra/pygoat)
- [microsoft/TailwindTraders-Website](https://github.com/microsoft/TailwindTraders-Website)
- [juice-shop/juice-shop](https://github.com/juice-shop/juice-shop)
