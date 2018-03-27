Lesson 1
========

All about commits. In this lesson, we are going to learn to:

- Configuring Git
- View commits
- View commit history
- Change the repository state to the a particular commit
- Adding files to the index
- Making commits from files added to the index

I highly recommend taking notes (perhaps in a text editor) although you can also scroll back in the terminal to see older content.

Exercise 1: Configuring Git
---------------------------

Let's configure this Git repository. These settings will not affect any other repository.

1. Run `git config user.name "{your first name} {your favorite animal"` For example, `git config user.name "Alan Wolf"` (Note that the double quotes do matter since there is a space in the line.)
2. Run `git config user.email {your first name}.{your favorite animal}@{place your animal lives}.com` For example, `git configure user.email alan.wolf@den.com`

Exercise 2: View History
------------------------

Let's look at some recent commits, and then examine some commits in more detail.

1. Run `git log -n 3`  (`3` is the maximum number of commits to show; it show history back to the beginning of time if you do `git log`)

You should see something like this.

```
commit e06f1c68d000dff67d17e0b38b742805769bc2cb (HEAD)
Merge: 7ee93ac 35868d5
Author: Alan Ray <rayalan@users.noreply.github.com>
Date:   Tue Mar 27 15:00:24 2018 -0400

    Merge initial instructions

commit 35868d5b8ccbcddb63d08b7c7f5f2d0ed7a4ecbb
Author: Alan Ray <rayalan@users.noreply.github.com>
Date:   Tue Mar 27 14:59:38 2018 -0400

    Add recovery instructions

commit 3d8dcd18510f1818407ec2d338986895a7a91497
Author: Alan Ray <rayalan@users.noreply.github.com>
Date:   Tue Mar 27 14:59:17 2018 -0400

    Add initial getting started instructions
```

2. Go to SourceTree and select Workspace/History or possibly branches/master. This should show the commit and state history, with similar information. You can refer back to this view throughout the lessons to visualize the current repository state. Use `Cmd-R` (macOS) or `F5` (Windows) to refresh.
3. Let's look a particular view on history. When you ran `git log` in step 1, you saw different commits because your current workspace state was on a different commit than mine. Run `git log e06f1c6 -n`. How does that view compare the example in step 1?


Exercise 3: Changing Workspace State
------------------------------------

Let's learn about changing the workspace state. The current state of the repository is `HEAD`.

1. Let's figure out what `HEAD` currently is. Run `git log -n 1` and take note of the sha1hash -- that is the sha1 hash of HEAD. And run `ls -l` and take note of the current files.
2. Let's change the workspace state. Run `git checkout 35868d5b`. Now where is `HEAD` at? What files exist? What does source tree look like?
3. Run `git log -n 3`. How does the git history compare to other times we've run the `git log` command?
4. Pick another commit by hash. Run `git checkout {hash}`. Is `HEAD` where you predicted? What about the file state?
5. Let's reset our state back to where it was at the beginning. Run `git checkout --detach origin/master`  (Note that is not a universal reset command, but is correct for this tutorial.)
