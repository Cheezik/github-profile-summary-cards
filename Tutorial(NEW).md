# Let's get started!
This tutorial will help you deploy Github-profile-summary-cards with ease.



### Table of Contents
1. [Generate token](#generate-token)
2. [Select a repo](#select-a-repo)

   - [Create a new repo](#new-repo)
    - [Add to existing repo (Recommended ⭐)](#existing-repo)
3. [Create a workflow](#create-a-workflow)
    - [Additional information](#additional-information)
4. [Edit workflow file](#edit-workflow-file)
5. [Run the workflow](#run-the-workflow)
6. [Final Step](#final-step)
7. [The end](#the-end)


# Generate token 

1. Navigate to your profile's Settings -> Developer setting -> Personal access tokens -> Generate new token


2. Name your token
(i'd recommend naming it something after `profile-summary-cards-token`) and ticking these boxes:
    
3. And copy your token (**and dont lose it! you'd have to generate a new token**)


<!--
repo
-  repo:status
-  repo_deployment
-  public_repo
user
-  read:user
-  user:email
-->

# Select a repo

- If you want to add to already EXISTING repository.  [Next Step](#existing-repo)
  - (E.g. If you already have a README that shows up on your profile) 
- If you want to create a brand NEW repository. [Next Step](#new-repo)


### New repo
To Create a new repo from template:
1. Go to [Template link](https://github.com/vn7n24fzkq/github-profile-summary-cards-example)
2. Click on "Use this template" button in the top right corner
3. Select "Create a new template" and Name the repo as your username<br>(E.g. `FunnyUsername/FunnyUsername`, this popup should appear if you done it correctly)
![this popup should appear if you done it correctly](/github-profile-summary-cards.wiki/assets_new/special_repo.png)
4. You are good to go. lets continue

### Existing repo

1. Add a README.md file **[if you dont have that file already]**
2. Rename your repo to your username (E.g. `FunnyUsername/FunnyUsername`) **[if you havent already]**
![this popup should appear if you done it correctly](/github-profile-summary-cards.wiki/assets_new/special_repo.png)
3. Thats pretty much all. lets continue


# Create a workflow

Now we will add a workflow to automatically update the summary cards.

1. Navigate to repo's Actions -> New workflow -> Set up workflow yourself 
2. Name your new workflow (i'd recommend naming it something after `profile-summary-cards`)
  * **Make sure you put `.yml` at the end!**
  
  Put this code snippet in:

  ```name: GitHub-Profile-Summary-Cards

on:
  create:
  schedule: # execute every 24 hours
    - cron: "* */24 * * *"
  workflow_dispatch:

jobs:
  build:
    runs-on: ubuntu-latest
    name: generate-github-cards
    permissions:
      contents: write

    steps:
      - uses: actions/checkout@v2
      - uses: vn7n24fzkq/github-profile-summary-cards@release
        env:
          GITHUB_TOKEN: ${{ secrets.[YOUR_SECRET_TOKEN_NAME] }}
        with:
          USERNAME: ${{ github.repository_owner }}
```
4. **Commit changes!**
## Additional information

>Please note that workflow in current configuration will run every 24h (it will update every 24h) if you want to change it here is a ``cron's job definition``

```# .---------------- minute (0 - 59)
# |  .------------- hour (0 - 23)
# |  |  .---------- day of month (1 - 31)
# |  |  |  .------- month (1 - 12) OR jan,feb,mar,apr ...
# |  |  |  |  .---- day of week (0 - 6) (Sunday=0 or 7) OR                            # |  |  |  |  |     sun,mon,tue,wed,thu,fri,sat
# |  |  |  |  |
# *  *  *  *  * 
```

So lets say you want it to run every 15 hours: <br>
`- cron: "* */15 * * *"`

Or for example you want it to run every friday at 12:35pm: <br>
`- cron: "35 12 * * fri"`

# Create Secret for Token

1. Navigate to repo's Settings -> Secrets and variables -> Actions -> Repository secrets -> New repository secret

2. Name your secret (again i'd suggest naming your secret as `summary_card_token` or simular) 

3. Past in your **Personal access token**. 
  - in case you've lost it. please go back to [Generate token](#generate-token) and get a new one

4. **Copy that New secret's name!**

# Edit workflow file
Now we obtained the Secret we can move to the last step before deployment 🎉

1. Navigate back to Code -> .github -> workflows -> `profile-summary-cards.yml` *(or customised name you gave to the .yml file)*

2. Hit the pencil icon at the right side of your screen

3. Edit the `[YOUR_SECRET_TOKEN_NAME]` inside the `GITHUB_TOKEN: ${{ secrets.[YOUR_SECRET_TOKEN_NAME] }}` with the Secret 

- (Resault should look something like this: `GITHUB_TOKEN: ${{ secrets.SUMMARY_CARD_TOKEN }}`)

4. Commit changes

# Run the workflow

1. Navigate to Actions -> on the left side `profile-summary-cards` -> hit the button `Run workflow` -> Run workflow

2. Wait till the workflow run appears (if not refresh the site)

    - its normal that the loading indicator "gets stuck" at a certant point, just refresh the page.

3. If the loading indicators turn blue with a check inside, Congratuation! 
    - if for some reason not, you've probably messed up somewhere (or this tutorial got outdated!) i recommand going from the begening again OR making a new repo and renaming it after you've succesfully managed to deploy this app.

# Final step    
You did you! now we are ready to chose the thme we want our cards to be in
1. Navigate to Code -> profile-summary-card-output -> Find the theme that suits you well -> README.md

you can get really creative with the layout you want your cards to be in, but for simpicity sake, i will pick bundle

2. Copy the desired markdown section.

3. Navigate to Code -> Hit the pencil button on the right side of your README.md file

4. Paste in the copied content and hit Commit changes!

# The end

Now if everything went right. The cards should appear on your profile!

Dont be afraid to experiment with themes! there are many that might suit you better.

---
Thats it guys, thank you for going trough this tutorial. i hope you found it somewhat helpfull. 

if you find any typos/erros please open an issue so i can get on them asap.

Have a pleasent rest of your day ^^