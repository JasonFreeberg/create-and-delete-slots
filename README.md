# GitHub Workflows to deploy PR's

> For every Pull Request these workflows will create a slot, build and deploy the PR branch, then delete the slot when the PR closes.

App Service allows you to create [indpendent environments](https://docs.microsoft.com/en-us/azure/app-service/deploy-staging-slots) for test, QA, staging, etc. You can route a percentage of production traffic to these environments to test your changes with user traffic (known as [testing in production](https://medium.com/@copyconstruct/testing-in-production-the-safe-way-18ca102d0ef1)).

This repository contains two workflow files. One will create a deployment slot on your App Service for each pull request, and deploy the PR branch to it. The second workflow will delete the slot when the PR is closed or merged. The workflow that builds and deploys the app references Java and Maven, but you can easily replace those usages with your language's build tool and SDK.

## Creating a Service Principal

Both workflows will require you to create an Azure Service Principal and [save it as a secret](https://docs.github.com/en/actions/configuring-and-managing-workflows/creating-and-storing-encrypted-secrets) named `WEB_APP_SP`. To create the service principal, run the command below and copy the JSON output as the secret's value.

```bash
 az ad sp create-for-rbac --name "myApp" --role contributor \
                          --scopes /subscriptions/{subscription-id}/resourceGroups/{resource-group} \
                          --sdk-auth
```

## "setup" actions for common languages

Replace the `actions/setup-java` action with the action for your app's language.

  - [Node.js](https://github.com/actions/setup-node)
  - [Java](https://github.com/actions/setup-java)
  - [.NET](https://github.com/actions/setup-python)
  - [Ruby](https://github.com/actions/setup-ruby)
  - [Python](https://github.com/actions/setup-python)

> [More information on creating the service principal](https://github.com/Azure/login#configure-deployment-credentials).

## More resources

- [App Service integration with GitHub Actions](https://www.youtube.com/watch?v=b2oyxbSbLPA)
