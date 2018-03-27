Lesson 3
========

So far we have learned about manipulating the working tree, commits, and a couple ways of sharing them with others. However, Git also makes it easy to share commits between repositories. Other repositories are known as "remote repositories" or "remotes" (regardless of where they are located). We are going to create two local repositories which talk to each other.

Additionally, we are going to start using branches. Think of branches as names or labels that we can assign to a sha1hash instead of having to remember the sha1 hash.

Exercise 1: Our first remote
----------------------------

We are going to create a second repository, which talks to the `brave-tardis` repo we have.

1. Run `cd ..`
2. Run `git clone brave-tardis local-tardis`
3. Run `cd local-tardis`
4. Configure a new user name and e-mail. Let's use your favorite gemstone this time.
5. Run `git config --global push.default simple`  (This basically configures how `git push` works in a more sane fashion than the default.)
6. What is the repository status? Use `git log` and `git status` to find out. (You can also add this repository to SourceTree if you want to visualize the state.)
7. Run `git branch -a` This will show local branch names such as `master` and remote names such as `remotes/origin/master`. (The default remote name is `origin`, but we can name remotes almost anything.)
8. Run `git remote` to see a list of remotes.
9. Run `git remote show origin` to see details about the origin.

Demo: Is it really a copy?
--------------------------

You can run through earlier exercises to convince yourself that local-tardis is really a fully functional repository. Run `git reset --hard` and `git checkout master` when you are done to get back to the starting conditions.

Exercise 2: Switching repositories
----------------------------------

Now we have two repositories saved on our disk, one named `brave-tardis` and another named `local-tardis`. The `local-tardis` repository has `brave-tardis` as a remote repostiory (and `brave-tardis` has its own remote on github, but let's not worry about that.)

1. To switch `brave-tardis`, do `cd ../brave-tardis`
2. To switch `local-tardis`, do `cd ../local-tardis`
3. It may be useful to open a second terminal or bash window and do `cd Documents/local-tardis` so that you have one terminal in each repository.

Exercise 3: My first branch
---------------------------

(If you have SourceTree visualizing `local-tardis`, close it for a moment before running this exercise; it will try to auto-update periodically which can ruin the demonstration.)

1. Go back to `brave-tardis`
2. Run `git checkout -b {favorite-animal}-branch1 {recordedSha1Hash}`
3. Run `git branch`
4. Go to `local-tardis`
5. Run `git branch -a`. Which branches does it show you?
6. Run `git fetch`.
7. Run `git branch -a`. Which branches does it show you?

As you may have surmised, the local repository view of remote branches is not live or dynamic; it is cached and only updated when `git fetch` is run.

Exercise 4: My first push
-------------------------

Let's create a new branch in our local repository, and then tell the remote (`brave-tardis`) about it.

1. Go to `local-tardis`
2. Run `git checkout -b {favorite-gemstone}-branch2 origin/master`
3. Create a new file named `excerise4.md`. Edit it with three lessons you have learned so far.
4. Run `git status`, `git diff`, and `git diff --cached`. What is the state of the working directory and the index?
5. Run `git add exercise4.md`
6. Run `git status`, `git diff`, and `git diff --cached`. What did `git add` do?`
7. Run `git commit -m "{some message}"`
8. Run `git status`, `git diff`, `git diff --cached`, and `git log -n 1`. Is the state what you expected?
9. Run `git branch -a`. What branches exist locally? What about remotely?
10. Go to `brave-tardis`
11. Run `git branch`. What branches exist locally?
12. Go back to `local-tardis`
13. Run `git push`
14. Run `git branch -a` What branches exist remotely?
15. Go back to `brave-tardis`.
16. Run `git branch`. What branches exist locally?

Exercise 5: A repository chain (bonus)
--------------------------------------

1. Run `cd ..`.
2. Create two more repositories, `git clone local-tardis city-tardis` and `git clone city-tardis street-tardis`
3. Give yourself a unique identity in `city-tardis` and `street-tardis`
4. Go to `street-tardis` and make a new branch with a new commit with new file. Can you push the branch so that it appears in `brave-tardis`? (Hint, once a repository has a branch, you can make it the current branch by running `git checkout {branchName}`.)
5. Go to `brave-tardis` and create a new branch with a new commit with a new file. Can you make that branch locally visible in `street-tardis`? (Hint: You want to `fetch`)

Recap
-----

What do the following commands do:

    git add
    git branch
    git branch -a
    git clone
    git fetch
    git push
    git remote
    git remote show origin
