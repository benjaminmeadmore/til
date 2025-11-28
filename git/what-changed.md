# What Changed?

If you want to know what has changed at each commit in your Git history,
then just ask `git whatchanged`.

```zsh
git whatchanged

commit 52022a7a07b2473339074df741ecf5b7de613b39 (origin/addbucket_tsharp_sagacity-data-sw-dmm)
Author: Daniel McWhir <dmcwhir@sagacitysolutions.co.uk>
Date:   Thu Oct 31 12:27:29 2024 +0000

    addbucket_tsharp_sagacity-data-sw-dmm

:100644 100644 1a2b315 1226c4e M        main.tf

commit 111dfbae9fc12616bd98813547ab6dd0ecda4d22 (origin/strategyseven_user_remove_add, strategyseven_user_remove_add)
Author: Ben Meadmore <bmeadmore@sagacitysolutions.co.uk>
Date:   Thu Oct 31 10:26:57 2024 +0000

    re-adding lucy, adding team blue user

:100644 100644 789e5d2 37b2d61 M        sync-client.tf
:100644 100644 7cbd278 b2c1129 M        sync-prod.tf

...
```

This is an old command that is mostly equivalent to `git-log`. In fact, the man page for `git-whatchanged` says:

> New users are encouraged to use git-log(1) instead.

The difference is that `git-whatchanged` shows you the changed files in their raw format which can be useful if you know what you are looking for.

See `man git-whatchanged` for more details.
