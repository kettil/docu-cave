# Git

## Remove old branches

[source](https://bitspeicher.blog/veraltete-git-branches-loswerden/)

```bash
# remove old references
git fetch -p

# list only locale branches
git fetch -p && git branch -vv | grep ': gone]

# remove only locale branches
git fetch -p && for branch in `git branch -vv | grep ': gone]' | awk '{print $1}'`; do git branch -D $branch; done
```
