# Use A Space To Exclude Command From History

Shells keep track of your cmd history, which means you get the benefit of in-built history search cmds such as `ctrl+r`. This means you can quickly traverse pack to a previous command that you want to run again. It also means [a tool like `fzf` can hook into your history file](https://github.com/junegunn/fzf?tab=readme-ov-file#key-bindings-for-command-line) so that you can fuzzy-search for a command you may have executed weeks ago.

Your history stores these old cmds on your machine in a plaintext file. Not every command should be stored in a plaintext file. For instance, you don't want `zsh` to persist a command that includes a password. 

With the `histignorespace` option enabled, we can put a leading space in front cmds to exclude that cmd itself from the history file:

```zsh
$ echo 'this command will be remembered'
this command will be remembered

$  echo 'this command will be forgotten'
this command will be forgotten
```

Notice the leading space in the second command. Trying pressing your _up_ arrow and notice only that first `echo` is remembered.

Make sure `histignorespace` is included in the list when you run `setopt`. If it isn't, then add it:

```zsh
$ setopt histignorespace
```

[source](https://stackoverflow.com/questions/8473121/execute-a-command-without-keeping-it-in-history/49643320#49643320)
