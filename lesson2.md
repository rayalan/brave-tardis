Lesson 2
========

So we've learned about how to make commits, how to examine the repository state, and how to change the repository and working directory state. If you are following the directions from last time, you have a recorded sha1 hash that indicates your last change, and `git log -n 2 {recordedSha1Hash1}` shows two commits, one with the message "This is my first commit" and one with a message of your choice.

Exercise 1: Commit Reuse
------------------------

Let's learn about reusing a commit that someone else has already made. Let's start by pretending to be someone else and reusing our own commits.

1. Make sure you have the recorded sha1Hash writted down somewhere. We're about to tell Git to set the repository state and working directory somewhere else, and it won't show us that commit anymore, although it will remember it if we use that hash.
2. Run `git reset --hard origin/master`
3. Run `git log -n 3` and make sure we are back to where we were at the start of exercise 1.
4. Let's change our name and e-mail address. (Remember lesson 1.1?) Run Run `git config user.name "{your first name} {a fearsome animal}"` and `git config user.email {your first name}.{a fearsome animal}@{place your animal hunts}.com`
5. Run `git cherry-pick {recordedSha1Hash}~` (Yes, the `~` is important. It roughly means "Use the parent commit of the one specified".)
6. Run `git show` and `git log -n 1`. What did cherry-pick do?
7. Run `git cherry-pick {recordedSha1Hash}`.
8. Run `git show` and `git log -n 1`. What did cherry-pick do?
9. Compare `git show` and `git show {recordedSha1Hash`. How do the commits differ?
10. Run `git cherry-pick {recordedSha1Hash}` again. What happens?

Exercise 2: Commit Reuse (via Diff+Apply)
-----------------------------------------

Let's learn another way to reuse the commits that we've made.

1. Run `git reset --hard origin/master` to reset back to our starting state.
2. Run `git diff {recordedSha1Hash}~ > patch1.diff`.
3. Run `git diff {recordedSha1Hash} > patch2.diff`.
4. Run `git apply patch1.diff`.
5. What has changed? (Hint: See `git status` and `git diff` and `git log`)
6. Run `git apply patch2.diff`. Now what has changed?
7. Add the changes with `git add -p`.
8. Commit them with `git commit -m {message}`
9. Is the commit what you expected?

Exercise 3: Commit Sharing -- Publishing
----------------------------------------

Let's publish our commits to the world -- or at least the `#git-training` Slack channel.

1. Run `git reset --hard origin/master` to reset back to our starting state.
2. Run `git format-patch -1 {recordedSha1Hash}~`
3. Run `git format-patch -1 {recordedSha1Hash}`
4. What files did it generate? What are the contents of those files?
5. Cut-n-paste the file contents to the Slack channel `#git-training`. (We should have everyone in the meeting added by now; if not, poke a virtual neighbor.)

Exercise 4: Commit Sharing -- Receiving
---------------------------------------

Let's apply someone else's commit.

1. Go to the Slack channel and find someone else's patch post. (That's what the contents of these files is called -- a `patch`. In Git, a patch is the difference of two repository states, plus some metadata.)
2. Copy their patch into a file, and save the file, say, as, myFirstPatch.patch.
3. Run `git apply myFirstPatch.patch`.
4. What has changed? (Hint: See `git status` and `git diff` and `git log`)
5. Repeat for a couple more patches. You may need to reset to the initial working state again if the patches collide; we haven't covered conflict resolution yet.

Exercise 5: Commits, The Dark Side (Bonus)
------------------------------------------

1. Let's reset one more time.
2. And grab a patch and save it to a file.
3. Let's edit the file and change the user name to `Scott Hammersley` and the year to 2008.
4. Apply the patch.
5. What happened?

Recap
-----

What do the following commands do?

    git format-patch -1
    git apply
    git cherry-pick

What do you think `git reset` does?
