# 2. Monorepo

> The monorepo approach uses a single repository to host all the code for the multiple libraries or services composing a company’s projects. At its most extreme, the whole codebase from a company — spanning various projects and coded in different languages — is hosted in a single repository.

Benefits :

1. Lowers Barriers of Entry and streamlines the initial setup
2. Centrally Located Code Management
3. Managing all the different pull requests if there are multiple repositories for each project/library can be difficult so a monorepo makes it easy to perform all modifications to all code for all libraries and submit it under a single pull request.

Issues :

1. When the code for a library contains breaking changes, which make the tests for dependent libraries fail, the code must also be fixed before merging the changes.
2. Requires Download of Entire Codebase
3. Unmodified Libraries May Be Newly Versioned
4. Forking Is More Difficult and hence contributors can face problems navigating to their project of interest in the monorepo.

---
