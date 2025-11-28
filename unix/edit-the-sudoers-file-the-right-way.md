# Use visudo to safely edit the /etc/sudoers file 

The /etc/sudoers file is a way for unix systems to administer various levels of permissions for different users. It is important to make sure you "know what you're doing" when editing this file. Especially so because if you mangle the syntax of the file, you could lock yourself, or even the root user, out of all kinds of access. Even from being able to reverse and fix your mistake.

## visudo
Fortunately, there is a command, `visudo`, that opens the sudoers file in an editor that will perform pre-save checks to ensure the file has valid syntax. These include basic sanity checks and checks for parse errors. 

```zsh
visudo /etc/sudoers
```

`visudo` locks the sudoers file against concurrent edits - that is, it ensures that the edits will be one atomic operation. This locking is important because it ensures that no one can mess up your carefully consdiered config changes. It is akin to state locking the .tfstate file. 

During this lock, `visudo` will wait for those edits to finish, then validate the new file before committing to the real location. It will not let you save a malformed sudoers file. Finding other footguns is an exercise for the reader. 

## sudoedit
If you like this behaviour in general, you can replicate this for other edits by using the generic `sudoedit` cmd. This floes through the same lock/copy/edit/copy/unlock cycle. 

## Editor
Though the default on macOS is `vim`, the `visudo` cmd is not locked to opening files in `vi` (or `vim`),  it can run with whatever your favourite editor is by setting the `SUDO_EDITOR` env var. 

[source](https://manpages.ubuntu.com/manpages/impish/en/man8/visudo.8.html#environment)