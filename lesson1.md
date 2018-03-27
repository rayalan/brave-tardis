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

1. Run `git config user.name "{your first name} {your favorite animal}"` For example, `git config user.name "Alan Wolf"` (Note that the double quotes do matter since there is a space in the line.)
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

Exercise 3: Commit Details
--------------------------

1. `35868d5b8ccbcddb63d08b7c7f5f2d0ed7a4ecbb` is a sha1 hash, and uniquely identifies a repository commit and the resulting repository state.
2. Let's look at at one commit. Run `git show 35868d5b8ccbcddb63d08b7c7f5f2d0ed7a4ecbb`. What information is available? What did you expect to see that was not available?
3. Git hashes can be abbreviated to the first few characters. Try `git show 35868d5b`. How short can you go?
4. (Optional) Git commits are stored on disk. Let's look at this one by decompressing the raw information stored on the disk. Run `python -c "import zlib; print(zlib.decompress(open('.git/objects/35/868d5b8ccbcddb63d08b7c7f5f2d0ed7a4ecbb','rb').read()))"`.

Exercise 4: Changing Workspace State
------------------------------------

Let's learn about changing the workspace state. The current state of the repository is `HEAD`.

1. Let's figure out what `HEAD` currently is. Run `git log -n 1` and take note of the sha1hash -- that is the sha1 hash of HEAD. And run `ls -l` and take note of the current files.
2. Let's change the workspace state. Run `git checkout 35868d5b`. Now where is `HEAD` at? What files exist? What does source tree look like?
3. Run `git log -n 3`. How does the git history compare to other times we've run the `git log` command?
4. Pick another commit by hash. Run `git checkout {hash}`. Is `HEAD` where you predicted? What about the file state?
5. Let's reset our state back to where it was at the beginning. Run `git checkout --detach origin/master`  (Note that is not a universal reset command, but is correct for this tutorial.)

Exercise 5: Making Commits
--------------------------

Let's learn about making commits.

1. First, we need some file changes. Edit this file (`lesson1.md`) with same changes that you think it should have. Change at least two separate sections of the file.
2. Run `git status`. This should show you what files have changes that are not part of the current repository state.
3. Run 'git diff`. This shows what changes exist between the working directory and the current repository state.
4. Run `git diff --cached`. (Hint: It shouldn't show much)
3. Run `git add -p`. It will ask if you want to `stage a hunk`. Answer at least one question with `y` and one question with `n`. If you don't get both questions, make some more changes. If you answer `y` (yes), the lines will be added to the index. If you answer `n` (no), the lines will be skipped. If you answer `s`, it will split the lines into smaller chunks. We'll find out what adding to the index does in a couple steps.
4. Run `git status` again. What does it show?
5. Run `git diff` again. What does it show?
6. Run `git diff --cached` again. What does it show now?
7. Run `git add -p` again. Answer yes to all questions.
8. Run `git status`, `git diff`, and `git diff --cached` yet again. What do these show now? What is `git diff` showing? What about `git diff --cached`?
9. Make one more change to `lesson1.md`. Now `git status` should show staged files for indexing and unstaged changes.
9. Let's make the commit. Run `git commit -m "This is my first commit"`
10. Run `git show HEAD` to see the most recent commit. (`git show` also works -- as does the `git log -n 1` and `git show {hash}` on the resulting hash.)
11. What does `git log -n 3` show now?
12. Let's make another commit. Run `git commit --allow-empty -m "{message of your choice}"`. What is the the sha1 hash of your commit? What are the contents of your hash?

Exercise 6: Extra tricks with commits (Bonus)
---------------------------------------------

1. Make changes to a file in at least two different sections.
2. Run `git status` and `git diff`
3. Run `git checkout -p`. Select `y` for at least one section, and `n` for another.
2. Run `git status` and `git diff`. What did `git checkout -p` do?

Wrap-up
-------

1. Run `git log -n 1` and record the sha1 hash. We will need it later.
2. Run `get reset`

Recap
-----

What do the following commands do:

    git add -p
    git checkout -p
    git checkout {hash}
    git commit -m "message"
    git diff
    git diff --cached
    git log -n 4
    git status
