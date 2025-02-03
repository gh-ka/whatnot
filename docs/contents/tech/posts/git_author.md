---
title: Howto change git commit author retroactively
# authors:
#     - Kathy
date: 2024-08-27
categories:
  - git
tags:
  - git
some_url: https://stackoverflow.com/questions/3042437/how-can-i-change-the-commit-author-for-a-single-commit
---

# Changing Git commit author

When you work on a repo where you should be commiting as `author1` while git is configured with credentials of `author2 `, you might need to retroactively replace the author on some commits to the correct value. This can happen, for example, when you contribute to a private repository while working in your organization's setup or vice versa. 

```bash
# first, configure the correct values locally, this modifies .git/config
git config --local user.name <name>
git config --local user.email <email>

# now you can reset author to the configured value in the last commit
commit --amend --reset-author --no-edit

# or on two last commits
git rebase --onto HEAD~2 --exec "git commit --amend --reset-author --no-edit" HEAD~2
# or on 'n' commits by replacing '2' with 'n' in the command above

# observe git log locally and, if the change is ok, push to the default remote
git push --force-with-lease
```