# Grep Over Commit Messages

The `git log` command supports a `--grep` flag that allows you to search (via grep, obviously) through all the historic commit messages for that repo. This can be done through the console as well. 

In our case, the more descriptive commit messages will therefore allow for easier tracking and faster problem-resolution. Sadly, we don't include ticket numbers as standard process in the commit message. 

For example, finding ticket `#99770` could be accomplished with:

```zsh
git log --grep="#99770"
```

See `man git-log` for more details.
