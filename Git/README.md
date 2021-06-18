# Git

## Scenario 1: Change username and email

Your GitHub's username and email have been updated, but they have not been updated in your local Git.

1. Update your username and email
```git
git config user.name 'your-username'
git config user.email 'your-email'
```

2. Create `email.sh` in your project directory and replace `OLD_EMAIL`, `CORRECT_NAME` and `CORRECT_EMAIL` with your own ones.
```sbtshell
#!/bin/sh

git filter-branch --env-filter '

OLD_EMAIL="your-old-email"
CORRECT_NAME="your-new-username"
CORRECT_EMAIL="your-new-email"

if [ "$GIT_COMMITTER_EMAIL" = "$OLD_EMAIL" ]
then
    export GIT_COMMITTER_NAME="$CORRECT_NAME"
    export GIT_COMMITTER_EMAIL="$CORRECT_EMAIL"
fi
if [ "$GIT_AUTHOR_EMAIL" = "$OLD_EMAIL" ]
then
    export GIT_AUTHOR_NAME="$CORRECT_NAME"
    export GIT_AUTHOR_EMAIL="$CORRECT_EMAIL"
fi
' --tag-name-filter cat -- --branches --tags
```

3. Run this shell script in CMD.
```
./email.sh
```

4. Push commits to remote.
```git
git push origin --force --all
```

P.S. If the following error shows after step 3,
```
Cannot create a new backup.
A previous backup already exists in refs/original/
Force overwriting the backup with -f
``` 
please execute the following git command:
```git
git update-ref -d refs/original/refs/heads/master
```