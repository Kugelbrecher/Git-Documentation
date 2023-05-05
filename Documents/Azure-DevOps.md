# Azure DevOps

## 1. Azure Command-Line Interface (CLI)
Documentation [here](https://learn.microsoft.com/en-us/cli/azure/?view=azure-cli-latest)

```bash
# install
brew update && brew install azure-cli
# check installation
az --version

# sign in
# successful login will show a list of subscriptions
az login

```

Git clone repos from Azure DevOps to local machine
```bash
git clone https://COMPANY@dev.azure.com/organization/project/_git/repo
```
Then it will ask for your password. This is NOT your Azure DevOps password.
It is a credential token that you can get from `Clone Repository Page>Generate Git Credentials`.

## 2. React and C-sharp
Front-end: localhost:3000

Back-end: localhost:5001/swagger/index.html