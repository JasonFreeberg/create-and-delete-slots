# GitHub Workflows to deploy PR's

> For every Pull Request these workflows will create a slot, build and deploy the PR branch, then delete the slot when the PR closes.

App Service allows you to create [indpendent environments](https://docs.microsoft.com/en-us/azure/app-service/deploy-staging-slots) for test, QA, staging, etc. You can route a percentage of production traffic to these environments to test your changes with real-world user traffioc (known as [testing in production](https://medium.com/@copyconstruct/testing-in-production-the-safe-way-18ca102d0ef1)). The [GitHub Flow](https://guides.github.com/introduction/flow/) branching strategy uses a single primary tracking branch.

This repository contains two workflow files. One will create a deployment slot on your App Service for each pull request, and deploy the PR branch to it. The second workflow will delete the slot when the PR is closed or merged. The workflow that builds and deploys the app references NPM and Node.js, but you can easily replace those usages with your framework's build tool and SDK.

  - [Node.js](https://github.com/actions/setup-node)
  - [Java](https://github.com/actions/setup-java)
  - [.NET](https://github.com/actions/setup-python)
  - [Ruby](https://github.com/actions/setup-ruby)
  - [Python](https://github.com/actions/setup-python)

## More resources

- GitHub Actions integration with App Service
