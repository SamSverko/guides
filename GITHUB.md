# GitHub

## How to merge a PR that has no conflicts with master branch

1. Update `origin/master` reference, run `git fetch --prune`.
2. Rebase branch, run `git rebase origin/master`.
3. Push rebase changes to `origin/master`, run `git push --force`.
4. Merge the PR into `origin/master`.

---

## How to perform a version release

1. Checkout to a new release branch (e.g. `git checkout -b release/1.8.0`).
2. Update the version property of the `package.json` to your version (e.g. `"version": "1.8.0"`).
3. Have your PR reviewed and approved by another developer.
4. Merge the PR into `origin/master`.
5. Once all the GitHub checks have passed, navigate to the `/releases` page of the repository and select "Draft a new release".
6. Set the "Tag version" to `v1.8.0` (or whatever version number you are using, just make sure to start with `v`).
7. Set the "Target" to `master`.
8. Set the "Release title" to the same value as your "Tag version" (in this case, it would be `v1.8.0`).
9. Select "Publish release".
10. [Skip if you have `@eqworks/release` already installed globally] Install the [EQ Works Release CLI](https://github.com/EQWorks/release) package globally, run `sudo npm i -g @eqworks/release`.
11. Inside the repository, checkout back to `origin/master` and update its reference, run `git fetch --prune && git pull`.
12. Generate the release notes as a markdown file, run `release notes`.
13. Copy all the release notes contents from the newly created markdown file in the repository's root directory (it will be named something like `release-notes-v1.7.2-1.8.0md`.
14. Navigate back the to the `/releases` page of the repository, select your recently published release, select "Edit release", paste in the release notes contents into the "Write" section, and select "Update release".

---

## How to add an existing local project to a GitHub repository

1. On GitHub, create a new repository with the name of your project (in this scenario, the project will be called `alpha`).
2. In `alpha`, initialize the local directory as a Git repository.
3. Add the files to the new local repository, run `git add .`.
4. Commit the staged files, run `git commit -m "Initial commit"`.
5. On GitHub, copy the remote repository URL (e.g. `git@github.com:username/repository.git`).
6. In `alpha`, set the remote repository URL, run `git remote add origin [remote repository URL]`.
7. Verify that the remote repository URL was correctly added, run `git remote -v`.
8. Push the changes from the local repository to GitHub, run `git push -u origin master`.
