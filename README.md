# Git Courseware

## Introduction

This repository is part of a introduction course to Git and GitHub, working mostly with YAML files. The purpose is to be a point of reference more readily available than a presentation. Feel free to fork or clone this repository and make it personal, if you like.

## Prerequisites

Git must be installed locally, if you are not only using *Codespaces*. For *Codespaces*, Git is already installed.

- For Windows, the latest version of Git can be downloaded from [this location][git-win].
- Linux, BSD and Mac users may already have it installed. If not, follow your distro guidelines for installing it.
- For Mac, you can also use this [guide][xcode] for installing using Xcode.
  - Homebrew is also an option

## Integrated Development Environment (IDE)

An IDE like Visual Studio Code (VSCode) is not strictly necessary, and your own preference of Notepad, GNOME Text Editor, TextEdit, Notepad++ and nano will take you far. Provided you have Git installed, and know your Git commands from the terminal of your preference.

Where an IDE like VSCode, VIM and Emacs help you, are with the Language Servers available for your development language of choice: allowing for auto-completion, error checking, jump-to-defintion and all that good stuff. IDEs also provide extensions you can use to tailor your own development flow, adding linters, prettifiers, helpers, code analysis and [pets](https://marketplace.visualstudio.com/items?itemName=tonybaloney.vscode-pets).

In this course we will have a look at Visual Studio Code, as that is one of the most distributed IDEs currently around.

### Setting up Visual Studio Code

VS Code can be installed by downloading it from [code.visualstudio.com](https://code.visualstudio.com/). If you cannot download due to restrictions by your corporate entity, they might have a developer image where this is pre-installed, or it may be available using a Software Center.

If you are using GitHub, you can also opt to using Visual Studio Code as the IDE in GitHub Codespaces, by defining "Visual Studio Code for the Web" as Editor preference in your [GitHub Settings][codespace-settings].

#### Connecting your GitHub user to Visual Studio Code

When running a GitHub Codespace, your GitHub user will be set up. All you have to do is press the *Person* icon in the lower left corner, and enable *Settings sync*. Provided you have enabled the setting in the [GitHub Settings][codespace-settings] under *Settings Sync*.

For VSCode installed, just click the *Person* icon in the lower left corner, and log in using your GitHub account.

Doing this gives you the opportunity to auto install, and setup VSCode using the same extensions and settings across different environments: like at work, at home and in, and across, GitHub Codespaces.

Once logged in, ensure that "Settings Sync is On" using the *Person* icon.

#### Add your extensions

When working with YAML files, or indeed this repository, there are a few extensions I would highly recommend:

| Extension | Short description | Link |
| - | - | - |
| EditorConfig | Helps to maintain consistent coding styles cross developers. Github has native support for it, and it can be added as an extension for VS Code. Requires a `.editorconfig` file repositories in order to work. | [extension][editorconf] |
| YAML | The YAML linter from Red Hat, includes support for Kubernetes syntax | [extension][yaml] |
| Linter | Supports many linters, including [*yamllint*][yamllint]. Requires a `.yamllint` file in your repository to override default settings globally. | [extension][linter] |

### Closing off the IDE setup

This is just to get you started. There are maaaany more extensions that may serve you well in the future, but I'll leave it up to you to find [them][vscode-pets].

At the root of this repository, you will find examples for both `.editorconfig` and `.yamllint` overrides. These files only work within the context they are loaded, so for files outside of this repository, they will have no effect. You should, therefore, consider adding these files to all repositories, to ensure that the developer experience will be same, cross the repositories you connect with.

Please note that these files can be expanded and changed, fitting to your needs.

By following the steps above, you should be off to a good start towards dominating the world of YAML files, and beyond....

### Installing Pre-Commit hooks

If you are able to work locally, and have Python installed, enabling pre-commit hooks are a superb way to ensure that the quality of your code is as good as it can be. Introducing pre-commit hooks into a repository means that much of the code issue will be fixed before it is ever commited. This is part of a shift-left strategy, where you try to fix issues as soon as possible before any lenghty process (like a pull request can be) occurs. You can read more about pre-commit [here][pre-commit].

Pre-Commit hooks can be installed on GitHub codespaces, or in computers where Python is installed. You can do this in the following manner:

Open a terminal in VSCode, and enter the following command:

```sh
pip install pre-commit
```

This install is only required once per computer/codespace.

To set up the pre-commit hooks in your current repository, issue the command:

```sh
pre-commit install
```

This installs the pre-commit hooks into the current repository. It it now required that you add a file named `.pre-commit-config.yaml` to the root of your repository, and add that file to the source control. The `.per-commit-config.yaml` file is where you specify what should be executed as part of a pre-commit check. In this repository, you will find a `.pre-commit-config.yaml` file suited for validating repositories of YAML files.

Once that is done, you can issue the command:

```sh
pre-commit run -a
```

This will run the pre-commit hooks without having to commit anything. It will run through the hooks described in the `.pre-commit-config.yaml` file. Any errors that appear should be sorted out before continuing.

Once all issues are sorted out, the pre-commit checks will run on each and every commit - validating that everything is according to the specifications in the cheks. If not, the commit will fail, and you need to sort out the issues before trying to commit again.

## Working with Git/GitHub

### Creating a new repository

The easiest way to create a new repository at GitHub, is to make use of the [GitHub Dashboard][github-dashboard]. At the top left corner, you are presented with a green *New* button, right next to "Top Repositories". Press that button.

Select a repository template if applicable. Note that a selecting a template automatically switches the *Owner* to the origin of that template.

Use the drop down button for *Owner* to select which user or organization the repository should be created in, and provide a fitting name for the repository. The repository name needs to be unique within the *Owner* you have selected.

A description for the repository can be provided now, however - it is optional, and you can add one later.

Make a selection of whether the repository should be public or private. Follow your organization guidelines, if you are allowed to create new repositories. For a repository you own yourself, you are allowed to define it as you wish. The main difference is that there are limitations to which additional GitHub benefits you can make use of, when on a Free account. For public repositories, there are limits - but most additional benefits can be made use of.

You can add a README file to get you going, add a `.gitignore` file to help you avoid adding helper files to your repository, and you can choose to add a license.

By pressing the *Create repository* button, the repository is created.

From this point, you should really go to the *Settings* button of your repository, and define what you might be allowed - or not allowed to do.

### Cloning your repository

In case you work on your local computer, you need to clone your repository locally, before you can start working on it. Open your favorite terminal (be it Powershell, CMD or a unix terminal).

Navigate to a repository you will work with in GitHub, and select the *<> Code* button. Select HTTPS, SSH or GitHub CLI under *Clone* and copy the path.

Open your terminal, and navigate to where you want to store your repository locally. Replace `url-copied-from-button` with the clone path copied from the *<> Code* button.

```sh
cd /navigate/to/your/desired/folder/src

git clone url-copied-from-button
```

> ***DO NOT*** use a folder inside Onedrive, Google Drive, iCloud, Dropbox or something to that effect, to store repositories. They ***will*** eventually break the local repository.

### Branches

Branches in Git are cheap. They reference the repository branch you branched off of (usually main or master) at a specific point in time, referenced by a commit SHA.

When you want to make a change to a repository, it is best practice to start the process by creating a new branch from the branch you want your changes to be merged to. Usually, this is the main branch.

There are several ways to create a branch.

#### Branching in GitHub

The easiest way to branch in GitHub is to go to the main page of the repository, and click the *branch* shortcut right next to the branch selector. You are now placed in a url like so: `https://github.com/<organization>/<repository>/branches`. You can also press the drop down button for branches, and select *View all branches*. This takes you to the same place.

Select the "New branch" button, and provid a name.

> Tip: name the branch something that resembles what you want to achieve. Like `feat/add_more_pizzas`, or `bug/eliminate_rats_in_the_cheese`. Naming branches *may* be part of a naming standard in your organization. In such cases, refer to these standards for naming.

Once the branch name has been set, use the drop down button for *Source* to select what you are branching off of. Usually, this should be **main**.

By clicking on your newly created branch, your are taken to that branch code space.

Use the drop down button for branches to switch between active branches.

> Tip: By pressing the *<> Code* button and selecting *Codespaces*, you can create a new codespace with your current branch active.

#### Branching locally using VSCode

Open VSCode, select *File* and *Open folder*. Navigate to where the repository has been cloned locally. Select the repository folder, and press *Open*. In its Explorer activity section, you should now see all files associated with that repository only.

Go to the *Source Control* activity and press the *View and More Actions...* button, and make sure *Branches* is ticked. You should see it as a collapsed section of the SOURCE CONTROL section. Expand it.

When hovering the BRANCHES section, you will see a +-symbol. Press that symbol, which will provide a popup dialogue at the top of your VSCode window.

Enter the branch name. Follow your organization guidelines for naming it that exists, else provide a good name that describes what you want to achieve. Press *Enter* when done.

You can now select "Create Branch" or "Create Branch and Switch". You should select the "Create Branch and Switch" in order to be able to start working right away.

Use the "Switch to Another Branch..." button right next to the +-symbol in BRANCHES to switch between branches.

> Please note that this will create a branch from your current active branch. If that is not main, you need to switch branches first by using the "Switch to Another Branch..." shortcut in the same BRANCHES section.

##### Alternative way to branch in VSCode

An alternative way to create a branch is to use the shortcuts Shift+Ctrl+P in order to active the *Command palette*. Start typing "git create", and select "Git: Create branch..." or "Git: Create branch from...".

- "Git: Create branch..." creates a branch from your current active branch. If the active branch is not main, you might have to switch branches first.
- "Git: Create branch from..." provides an ability to select which branch to branch from.

> Tip: If selecting "Create branch from ..." you get a list of possible branches to choose from.
> *main* will be your local main. *origin/main* represents the remote repository in GitHub.

#### Branching locally using Git commands

In your terminal (can be the terminal in VSCode), make sure you are navigated into the correct repository.

First of all, make sure you are in the branch you want to branch off of, like *main*. Also ensure that your local *main* is up to date with the remote *origin/main*. You can do this by issuing the following commands

```sh
git checkout main # This ensures that your active branch is *main*
git fetch # This fetches all remote changes, but does not pull them
git pull # This pulls all changes from the remote repository
```

##### Create new branch without switching

Create a new branch from updated *main*, but do not switch to it:

```sh
git branch newbranchname
```

You can also create a new branch from a different branch than your currently active one, issuing the following command:

```sh
git branch newbranchname -t origin/main
```

This tells git to create a new branch named *newbranchname* from the branch available remotely at *origin/main*.

##### Switch to a different branch

Issue this command to switch to the new branch:

```sh
git checkout newbranchname
```

> Tip: You can switch between your two latest checkouts (*main* and your current *newbranchname*) by issuing the following command:
>
> ```sh
> git checkout -
> ```
>
> The `-` represents the previous branch name you used. Much the same way `cd` works.

##### Create and switch to a new branch

In order to create a new branch, and switch to it automatically, you can instead issue the following command:

```sh
git checkout -b newbranchname
```

The `-b` option is used to create a branch with the name that follows immediately after the `-b`.

You can also create a branch from a different branch than your currently active branch the same way, by issuing the following command:

```sh
git checkout -b newbranchname -t origin/main
```

This tells git to create a new branch named *newbranchname* from the branch available remotely at *origin/main*.

#### Deleting a branch in GitHub

Branches can be deleted in the branches section. This will only delete the branch in GitHub, not any local branches downstream branches.

#### Deleting a branch in VSCode

Go to the *BRANCES* section, use the "Refresh" symbol, and then switch to the *main* branch. Using the "Switch to Another Branch..." button, or the "Switch to Branch..." button directly on the branch.

Right click on the you want to delete, and then select the "Delete Branch...".

> Note that you *cannot* delete a branch that is currently active.

#### Deleting a branch using the terminal

First, checkout the main branch issuing the following command:

```sh
git checkout main
```

Then, fetch and pull all changes made remotely:

```sh
git fetch && git pull
```

Finally, delete the branch you want to delete by issuing the command:

```sh
git branch -d newbranchname
```

> Note that if you now receive a warning that the local branch cannot be deleted, you need to use this command instead
>
> ```sh
> git branch -D newbranchname
> ```
>
> This will detach the local branch from upstream, and delete the local branch.

### Git Add

No changes made to a branch is part of the local branch before the changes has been added to the "tracker". You will see that files are modified (`M`) from what the branch knows, or that a file is not yet part of the branch tracker yet (`U`), but these changes are not yet part of the source control. In order to add any changes made, you need to put any new files and/or any changes to existing files into a staging area. This is performed by providing the `git add` command.

You can see the status of individual files in a terminal by issuing the command:

```sh
git status
```

#### Add changes in GitHub

Changes made directly in GitHub are added and commited at the moment you press "Commit changes...".

#### Add changes in VSCode

In VSCode, use the +-symbol next to files under *Changes* in *SOURCE CONTROL*. This will move them into the staging area.

#### Add changes using terminal

In a terminal, never use the `git add .` command. It will add all changes, in all files, also files that have not been previously tracked. This is the most common way of introducing items in your repository that your REALLY do not want to be there. Examples include passwords, secrets, or files containing things you are just trying out.

##### Add new files using terminal

New files can be added in a chain, separated by a space in your add command. You can do one file, or many files at the same time. The command is:

```sh
git add file1.ext file2.ext Examples/file3.ext
```

##### Add changes to tracked files using terminal

You can add changes to already tracked files using the command above, but you also have a nice way of reviewing the changes you have made by issuing the following command:

```sh
git add -p
```

Now you can go through the changes, review them in and press `y` to include them, `n` to not include, `a` to include all changes in that file or `q` to stop. Plus a ton more options.

### Git Stash

It may very well be that you have made changes that you do not want to be part of a commit, or you need to change branches and have to either commit or stash your current changes in order to do so.

The `git stash` command stashes all your changes temporarily, until you either `clear` the stash, or `pop` the stash.

- `git stash clear` will remove what has been stashed, and it will not be recoverable.
- `git stash pop` will reapply the changes you previously stashed to the current active branch, and then clear the same changes from the stash.

#### Stash changes in GitHub

As far as I know, this is not possible. You have already commited your changes.

#### Stash changes in VSCode

First add all files that should be commited. Commit those changes. Then right click the "Changes" area, and select select "Stash All Changes". Change the stash message, or press *Enter* to use the one suggested.

> You can also stash individual files, it is just more cumbersome.

To pop the stash, you will find the current stash under *STASHES*. Select the *Apply Stash* button, and choose to *Pop* the stash.

#### Stash changes using the terminal

The easiest way is to add and commit the changes you need first. Then you can simply issue the command:

```sh
git stash
```

To stash all changes to tracked files, or:

```sh
git stash --include-untracked
```

to also include files that have not yet been added to the source control tracker.

You can, as well stash files indivdually by using

```sh
git stash file1.ext file2.ext Example/file3.ext
```

To recover the changes using terminal on your current active branch, you can issue the command:

```sh
git stash pop
```

This will reapply all the changes you previously stashed.

> Issuing the command below, will instead clear the stash. You will not be able to recover these changes again.
>
> ```sh
> git stash clear
> ```

### Remove files from branch

Files that are part of the source control tracker can also be removed. You can just delete the file outright, but then you need to add and commit that to the staging area by using Add afterwards. If you are prepared to use the terminal, there is a much more efficient way of removing individual files - or entire folders with content.

#### Remove files using GitHub

Select the file you want to delete, and press the *...*-button on the top row. Select *Delete file*.

#### Remove files using VSCode

First, delete the file from the *Explorer* activity. Then go to the *SOURCE CONTROL* activity and select the +-symbol next to the file (should be represented with strikethrough and `D`), and press the +-symbol to stage the file deletion.

#### Remove files and folders using the terminal

In the terminal, you can issue the `git rm` command. This removes and stages the removal immediately.

For individual files:

```sh
git rm file1.ext file2.ext Example/file3.ext
```

If you need to remove an entire folder, you can do this by:

```sh
git rm foldername -rf
```

The `-r` option makes it recursive, deleting everything in the folder you have stated. The `-f` option forces it to remove files, even recursively.

### Commit changes

All changes in staging will be part of the same commit. If you want to avoid certain changes inside a commit, you should not add those changes to the staging area yet. Either stash the remaining changes, or leave them alone for now.

> Tip: You should provide a commit message that is relevant to what will change by this commit.
> When writing the message, write in present tense, not in past tense.
> The commit message is a window into what happens now, not what has happened.

Please note that you can continue making new changes after you have made a commit. The changes you make after commit has completed, will be diffed against the commit SHA, and no longer the branch off SHA.

Keep making changes and commits until you are satisifed. You may publish the commited changes to the remote GitHub repository at any time.

#### Commit in GitHub

Commit is made at the same time any file is changed and saved, as you need to "Commit changes..." to save them. Remember to add a proper commit message.

#### Commit in VSCode

All changes listed in "Staged Changes" will be part of the commit. Add a proper commit message, and press the *v Commit* button. The button should now change to show you the *Publish Branch" button - if no more changes remain.

Pressing the *Publish Branch* button, pushes the branch to the remote GitHub repository. The branch name in GitHub will be the same as your current branch name.

#### Commit using the terminal

When you have added all the changes you want for the commit, you can either issue `git commit`, which initiates an interactive commit dialogue. You can also omit that dialogue by adding the `-m ` option followed by your commit message in quotes. It may look something like this:

```sh
git commit -m "Add mozarella pizza topping to the list"
```

### Push commited changes to the GitHub repository

When you make a commit, the commit is local to your repository - until you decide to publish the commited changes to the remote repository. You can publish commited changes as often as you want to, or never.

#### Push commited changes using GitHub

All commited changes on GitHub, is already in GitHub. You do not need to publish these.

#### Push commited changes using VSCode

Once all changes are commited, and no more changes are listed, the *v Commit* button changes to *Publish Branch*. Press this button to push your changes to the remote GitHub repository. It will create a branch in the GitHub repository with the same name as your current branch, and setting the remote (GitHub) branch as upstream for your current active branch.

#### Push commited changes using terminal

If the current branch has never been pushed to remote (GitHub) before, you need to create the remote branch as upstream for your current branch. You can do this by issuing the following command:

```sh
git push --set-upstream origin active_branch_name
```

This will create a branch upstream for your branch in origin (GitHub), and give the branch the same name as what you have replaced `active_branch_name` with. Usually, this should be the same name as you have used for your current active branch locally.

Following the initial push, you can continue updating the remote branch with more commits using the command:

```sh
git push
```

### Pull request

Creating a Pull Request means that you create a request for the owner(s) or maintainer(s) of a repository to review and pull any changes you have made in your branch, into the sacred *main* branch. In order to do so, the changes you have made must be published to a branch in GitHub first.

All the Pull Request administrative work: create, review, comment, approve/decline are performed in GitHub. The exception being if you have the [GitHub Pull Request and Issues][github-pr-issues] extension in VSCode, or if you are using the [GitHub CLI][github-cli]. I will not be covering those two in this course.

All the while the pull request is not yet approved and merged, you can continue pushing changes to the branch. Including fixing any issues that might arise.

#### Create pull request in GitHub

Once you navigate to the repository in GitHub, you should be presented with a yellow banner on the *<> Code* page that "your repository had recent pushes x minutes ago". If you cannot see the yellow banner, navigate to the *Branches* section of the repository. You can find this right next to the "Select branch" drop down button on the *<> Code* page.

Select "Compare & pull request" from the yellow banner, or "New pull request" button from Branches in order to create a new pull request.

Fill in the pull request details, according to the template used for your repository. If you do not have a template, request for one to be made available, or fill in according to what seems to be most likely.

Once finshed, either press the "Create pull request" button, or press the arrow button to create a draft first.

A draft pull request can later be promoted to a proper pull request, in case there are changes still to be made.

#### Review pull requests

If it is your job to review pull requests, you should do this diligently by following any organizational protocol created for reviewing pull requests. This may include reading the title, reading the description and checking that the changes made matches what is in the title and description.

Depending on the potential severity of the changes, you may need to clone the pull request, and rerun any tests that have been performed, verifying that everything is as it should be.

Follow up on any GitHub actions that have ran, and see that they go through OK.

In the "Files changed" tab, review every file changed, added or removed. Make comments where you are unsure, things are unclear, or possibly in error. Use the "Viewed" checkbox when you have finished reviewing a file.

Finally, press the "Review changes" button, write a comment and either just *Comment*, *Approve* or *Request changes*.

> Tip: Keep in mind that noone wants to do break stuff, or write bad code. In order to keep a civil conversation, be supportive and suggest changes or improvements in a voice that gains everyone. Show off your good manners :)

#### Merge a pull request

Once the pull request has been approved by the number of reviewers needed, the pull request can be merged.

Use the merge button in order to merge the pull request to *main*. Usually, you should select the "Squash and merge" option, in order to squash all the possible commits made in the current pull request into one. That one commit will have all the changes, and will be named by the title provided in the pull request.

If the option of deleting the branch should appear afterwards, you should proceed to do so. This choice may also be automated for you.

Lastly, follow the procedure for deleting a branch as described in the branches section of this README.

### Revert a merge

Reverting a merge is easier the closer to the merge you are. Keep in mind that unless a branch has completed a pull request, there is no need for a revert. The branch can simply be deleted, or you can revert the changes locally and pick up from where everything was working.

#### Revert in GitHub

To revert the changes merged, go to the *Pull request* pane in the GitHub repository.. Select *Closed* and open the pull request that failed. Scroll down until you see the `user merged commit .... into main` message. Press the *Revert* button available.

This will create a new pull request, reverting the changes made in the original pull request. This pull request needs to go through the same steps as creating the original pull request, in that the fields need to be filled in.

Once the reverting pull request has been approved, merge it to the *main* branch. Everything should be back to normal.

#### Revert in VSCode

Reverting changes in VSCode should only happen if you need to revert changes you have made locally. In such a case, go to the *COMMITS* section of the *Source Control* activity. Find the commit you want to revert, right click the same commit and select "Revert Commit...". Select the "Revert and no edit" option.

#### Revert using terminal

In the terminal, you revert using the commit SHA. First, find the commit that needs to be reverted by issuing the command:

```sh
git log --oneline
```

Press `q` to exit the dialogue, after noting the SHA id of the commit that must be reverted. Issue the following command to revert the commit, if the SHA was `f4sd49`:

```sh
git revert f4sd49
```

<!-- Resource links -->
[git-win]: https://git-scm.com/download/win
[xcode]: https://developer.apple.com/xcode/resources/
[codespace-settings]: https://github.com/settings/codespaces
[editorconf]: https://marketplace.visualstudio.com/items?itemName=EditorConfig.EditorConfig
[yaml]: https://marketplace.visualstudio.com/items?itemName=redhat.vscode-yaml
[yamllint]: https://github.com/adrienverge/yamllint
[linter]: https://marketplace.visualstudio.com/items?itemName=fnando.linter
[vscode-pets]: https://marketplace.visualstudio.com/items?itemName=tonybaloney.vscode-pets
[pre-commit]: https://pre-commit.com/
[github-dashboard]: https://github.com/dashboard
[github-pr-issues]: https://marketplace.visualstudio.com/items?itemName=GitHub.vscode-pull-request-github
[github-cli]: https://cli.github.com/
