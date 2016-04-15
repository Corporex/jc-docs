Git Cheat Sheet
=======================

### Some useful bash aliases
```bash
# Show uncommitted changes:
# Usage: git-changes
alias git-changes='git commit -a --verbose --dry-run'

# Remove files from the index (opposite of git add):
# Usage: git-remove <file.ext>
alias git-remove='git reset HEAD'

# Revert uncommitted changes in a file:
# Usage: git-revert <file.ext>
alias git-revert='git checkout'

# Revert ALL local changes to master. Can use git stash to save a copy.
# Usage: git-revert-everything
alias git-revert-everything='git fetch origin && git checkout master && git reset --hard origin/master'
```

### git commands
```bash
git add --update # stages only the files which are already tracked and not new
git commit --amend     # Change previous commit message and / or add staged files.
git show --name-status # Show diff of previous commit
git log --stat # Show latest changes committed
git remote set-url origin git@github.com:jonathancross/pics.jonathancross.com.git # Allow git push via ssh without password
```

### Configure git to sign all commits with my PGP key
```bash
git config --global user.email [EMAIL ADDRESS OF YOUR PGP IDENTITY]
git config --global user.signkey [YOUR KEY HERE]
git config --global commit.gpgsign true
```

NOTE: git and GitHub will show that code was signed with your signing **subkey** (rather than primary key) which users may not recognize.  See [example here](https://github.com/jonathancross/j-renamer/commit/e93093aa5d87a33b0758b1614c31d70aae7999ed).

### Show commit signature info ([more info](https://git-scm.com/book/en/v2/Git-Tools-Signing-Your-Work))
```bash
git log --show-signature -1               # Details of last commit sig.
git log --pretty="format:%h %G? %aN  %s"  # Log of last commits. The "G" means good signature, "N" means no sig.
```

### GitHub specific info
* To merge a branch back into master, use a pull request.  Will go from right (compare or "head" branch, what you did) to left ("base" where it should go)!
* To merge changes made in original to the fork, click on the green arrows, change the base, then create pull request, then merge the pull request.