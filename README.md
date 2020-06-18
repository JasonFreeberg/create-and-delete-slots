# GitHub Workflows to create and delete slots

App Service allows you to create [indpendent environments](https://docs.microsoft.com/en-us/azure/app-service/deploy-staging-slots) for test, QA, staging, etc. You can also route a percentage of production traffic to these environments to test your changes (known as testing in production). The [GitHub Flow](https://guides.github.com/introduction/flow/) branching strategy uses a single primary tracking branch.

This repository contains two workflow files. One will create a deployment slot on your App Service for each pull request, and deploy the PR branch to it. The second workflow will delete the slot when the PR is closed or merged. The workflows reference NPM and Node.js, but they can be used with any language/app framework.

## More resources

- GitHub Actions integration with App Service
- Actions to set up language SDK's
  - Node.js
  - Java
  - .NET
  - Ruby
  - Python
