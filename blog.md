> In any SDLC task or Devops task, working with **version control is inevitable**.
>
> People often focus on DSA, database, networking and various other fundamentals which are important but ***learning version control tool like git is a skill which is as important as any other fundamentals***.
>
> This blog talks about the `everyday usecases with git` which every developer or devops engineer will certainly face during their projects and **the purpose of this blog is to help you learn from my experience** which I faced when  I started working. ( I learned it the hard way, hope it helps in your learning journey)
>
>

## Prequisites

- Understanding of why do we need a version control?
- Understanding of [git](https://git-scm.com) ( how to play around and commands ).


# UseCases

## When another developer push their changes to same branch on remote

- **Scenario**: You and your teammate is working on the same branch, however he/she pushed their commit changes to remote.
- You are still working on your local, and when you try to push your changes to remote; you simple can't!

- Here in the branch `rebase-demo` other developer commit their changes first and **as a result we wont be able to push our changes until we pull the changes of remote**.

picture

**A Bad Solution**: Running `git push -f` on your local would definitely solve the issue but it will surely **mess up your commit history** and overwrites other user's commit .


**The Better Solution**: Do a **rebase**. It pulls changes from remote and stack our local changes on top of that, **hence avoiding an extra commit and leading to cleaner commit history**.

```sh
git pull -r
```
picture

## There is a bug in the code, how to find the cause?

**Scenario**: We don't know which commit caused the bug, in order to find the cause and perform our testing to ensure the bug was caused by a particular commit, git allows us to go back in time; to go back to that specfic version of the project i.e to checkout the commit which is in question.

**Solution**:- Git allows us to view the history of commit using `git log` command and using the hash of the commit we can `checkout` to a speicfic time in code and verify/test the cause.


```sh
git log
```

picture

- Now suppose i think `added command by another developer` commit is the cause of the bug. I can copy its hash and go back in time to this commit.


```sh
git checkout 7e2931eb88588982b59283f55d742c8ff6b41fd1
```

picture

- We will be in detached `HEAD state` and the prompts will also change. Here we can see **line 10 which is the current state of remote is not in local**. From this state we can either create a new branch and replicate the bug and test it.
We can return back to the current state by `git checkout <branch name>`


```sh
git checkout rebase-demo
```

## Undo your commits

**Scenario**: There are so many ways to undo commit, google pulls lot of different posts on stackoverflow but which one to use for which case? Let's demystify this.

**Let's make some bad changes and try to fix them.**

- There is change on `line 12` change and i want to revert that.
- **HEAD** represents the pointer to last commit. In order to revert it we specify `HEAD~n` where **n stands for number of commits we want to revert**.

```sh
git reset --hard HEAD~1
```

- `reset --hard` not only delete the changes but removes the commit from the commit history. *line 13 will be deleted* previous commit will become the current (HEAD will point to this) , be very cautious with **--hard** option as you can loose all your changes depending on the value of `n`,

**Scenario**: Now i dont want to delete the changes, but instead fix them or change them, for such use case `--soft` will be used. Let's make some changes and fix them with **--soft** option

- Here on line 12 there is typo.

```sh
git reset --soft HEAD~1
```







### From DevOps Perspective

- AWS Resource Explorer is integrated with AWS CLI, AWS SDKs, and Query API which allows us to build automation for searching our service.

Till then, **Happy Learning!**