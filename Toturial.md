## Let's start

---

### First step

|      We create a Personal access token with permissions we need      |
| :------------------------------------------------------------------: |
|                          1. Find `Settings`                          |
|                    ![](./assets/find-setting.png)                    |
|                     2. Find `Developer Settings`                     |
|              ![](./assets/find-developer-settings.png)               |
|                   3. Find `Personal access tokens`                   |
|            ![](./assets/find-personal-access-tokens.png)             |
|                 4. Press `Generate new token` button                 |
|                 ![](./assets/generate-new-token.png)                 |
|           5. Type access token name and check permissions            |
|                    ![](./assets/create-token.png)                    |
|        6. Scroll to bottom and press `Generate token` button         |
|               ![](./assets/generate-token-button.png)                |
| 7. Then we get the token, copy the token value, we will use it later |
|                  ![](./assets/copy-token-value.png)                  |

---

### Add to repo

- If you want create a Profile README or create a new repository. [Next Step](#use-template)

- If you want add to a exist repository. [Next Step](#add-personal-access-token-to-repo)

---

### Use template

|                   Open template page [github-profile-summary-cards-example](https://github.com/vn7n24fzkq/github-profile-summary-cards-example)                   |
| :---------------------------------------------------------------------------------------------------------------------------------------------------------------: |
|                                                             Find and press `Use this template` button                                                             |
|                                                               ![](./assets/press-use-template.png)                                                                |
| Type repository name then press `Create repository from template` button (If you want to create a Profile README repository then the name should be you username) |
|                                                                 ![](./assets/type-repo-name.png)                                                                  |
|                                                                   Now we have a new repository                                                                    |
|                                                                    ![](./assets/new-repo.png)                                                                     |

[Next Step](#add-personal-access-token-to-repo)

---

### Add Github Action to repo

|           We are gonna use the personal token we early copy            |
| :--------------------------------------------------------------------: |
|                    Find and click `Add file` button                    |
|                  ![](./assets/where-is-add-file.png)                   |
| Type file name with path `.github/workflows/profile-summary-cards.yml` |
|                    ![](./assets/type-file-name.png)                    |
|                       Copy and paste to the file                       |

```yml
name: GitHub-Profile-Summary-Cards

on:
  schedule: # execute every 24 hours
    - cron: "* */24 * * *"
  workflow_dispatch:

jobs:
  build:
    runs-on: ubuntu-latest
    name: generate

    steps:
      - uses: actions/checkout@v2
      - uses: vn7n24fzkq/github-profile-summary-cards@release
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
        with:
          USERNAME: ${{ github.repository_owner }}
```

| It should looks likt this one |
| :---------------------------: |
|  ![](./assets/new-file.png)   |
|      Then we commit file      |
| ![](./assets/commit-file.png) |

[Next Step](#add-personal-access-token-to-repo)

---

### Add Personal access token to repo

|                                   We are gonna use the personal token we early copy                                   |
| :-------------------------------------------------------------------------------------------------------------------: |
|                                             Find `Settings` in repository                                             |
|                                         ![](./assets/find-repo-settings.png)                                          |
|                                          Find secrets in repository settings                                          |
|                                            ![](./assets/find-secrets.png)                                             |
| Now, we type secret name you want and paste the personal access token as secret Value, then press `Add secret` button |
|                                     ![](./assets/type-token-and-token-value.png)                                      |
|                                              It should has a secret here                                              |
|                                           ![](./assets/secret-preview.png)                                            |

[Next Step](#change-github-action-token)

---

### Change Github Action token

|                   We are almost done!                    |
| :------------------------------------------------------: |
|          Find the github action file just added          |
|           ![](./assets/find-workflow-file.png)           |
|                And we do some modify this                |
|             ![](./assets/edit-workflow.png)              |
| Replace default GITHUB_TOKEN with the secret we jsut add |
|               ![](./assets/old-secret.png)               |
|                     With new secret                      |
|              ![](./assets/new-secrect.png)               |
|                    Commit this change                    |
|             ![](./assets/commit-secret.png)              |

[Next Step](#trigger-action)

### Trigger action

|               Now the action should automatically start                |
| :--------------------------------------------------------------------: |
|                       We can check workflow runs                       |
|                   ![](./assets/where-is-action.png)                    |
|                         Run workflow manually                          |
|                     ![](./assets/run-workflow.png)                     |
| Wait workflow finish (You need to refresh page to see latest workflow) |
|                     ![](./assets/run-workflow.png)                     |

[Next Step](#everything-are-finished!)

---

### Everything are finished!

|        We can see all cards of each themes 🎉         |
| :---------------------------------------------------: |
| Check profile-summary-card-output folder in your repo |
|               ![](./assets/output.png)                |
|                 :star: Finish :star:                  |
|               ![](./assets/finish.png)                |
