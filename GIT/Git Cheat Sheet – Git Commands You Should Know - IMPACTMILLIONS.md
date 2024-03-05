---
created: 2024-03-05T08:05:05 (UTC +01:00)
tags: [git command,git commands,commit in git,git commit,git commits,how to commit in git,how to git commit,what is git commit,git tutorial,github tutorial,tutorial git,git push command,git commit command,git push,how to git push,git cheat sheet,git command list,git commands list,github command,github commands]
source: https://impactmillions.org/git-cheat-sheet-git-commands-you-should-know/
author: scritto da                                      Anup Maurya
---

# Git Cheat Sheet – Git Commands You Should Know - IMPACTMILLIONS

> ## Excerpt
> Git Cheat Sheet – Git Commands You Should Know. Git and GitHub are essential tools for developers to efficiently manage their code, collaborate with others ...

---
-   [[#What is a Distributed Version Control System?]]
-   [[#Git Cheat Sheet – Git Commands You Should Know - IMPACTMILLIONS]]
-   [[#How to check your Git configuration]]
-   [Come impostare il tuo nome utente Git](https://impactmillions.org/git-cheat-sheet-git-commands-you-should-know/#penci-How-to-setup-your-Git-username "Come impostare il tuo nome utente Git")
-   [Come configurare l'e-mail dell'utente Git](https://impactmillions.org/git-cheat-sheet-git-commands-you-should-know/#penci-How-to-setup-your-Git-user-email "Come configurare l'e-mail dell'utente Git")
-   [Come memorizzare nella cache le credenziali di accesso in Git](https://impactmillions.org/git-cheat-sheet-git-commands-you-should-know/#penci-How-to-cache-your-login-credentials-in-Git "Come memorizzare nella cache le credenziali di accesso in Git")
-   [Come inizializzare un repository Git](https://impactmillions.org/git-cheat-sheet-git-commands-you-should-know/#penci-How-to-initialize-a-Git-repo "Come inizializzare un repository Git")
-   [Come aggiungere un file all'area di staging in Git](https://impactmillions.org/git-cheat-sheet-git-commands-you-should-know/#penci-How-to-add-a-file-to-the-staging-area-in-Git "Come aggiungere un file all'area di staging in Git")
-   [Come aggiungere tutti i file nell'area di staging in Git](https://impactmillions.org/git-cheat-sheet-git-commands-you-should-know/#penci-How-to-add-all-files-in-the-staging-area-in-Git "Come aggiungere tutti i file nell'area di staging in Git")
-   [Come aggiungere solo determinati file all'area di staging in Git](https://impactmillions.org/git-cheat-sheet-git-commands-you-should-know/#penci-How-to-add-only-certain-files-to-the-staging-area-in-Git "Come aggiungere solo determinati file all'area di staging in Git")
-   [Come verificare lo stato di un repository in Git](https://impactmillions.org/git-cheat-sheet-git-commands-you-should-know/#penci-How-to-check-a-repositorys-status-in-Git "Come verificare lo stato di un repository in Git")
-   [Come eseguire il commit delle modifiche nell'editor in Git](https://impactmillions.org/git-cheat-sheet-git-commands-you-should-know/#penci-How-to-commit-changes-in-the-editor-in-Git "Come eseguire il commit delle modifiche nell'editor in Git")
-   [Come confermare le modifiche con un messaggio in Git](https://impactmillions.org/git-cheat-sheet-git-commands-you-should-know/#penci-How-to-commit-changes-with-a-message-in-Git "Come confermare le modifiche con un messaggio in Git")
-   [Come eseguire il commit delle modifiche (e saltare l'area di staging) in Git](https://impactmillions.org/git-cheat-sheet-git-commands-you-should-know/#penci-How-to-commit-changes-and-skip-the-staging-area-in-Git "Come eseguire il commit delle modifiche (e saltare l'area di staging) in Git")
-   [Come vedere la cronologia dei commit in Git](https://impactmillions.org/git-cheat-sheet-git-commands-you-should-know/#penci-How-to-see-your-commit-history-in-Git "Come vedere la cronologia dei commit in Git")
-   [Come vedere la cronologia dei commit, comprese le modifiche in Git](https://impactmillions.org/git-cheat-sheet-git-commands-you-should-know/#penci-How-to-see-your-commit-history-including-changes-in-Git "Come vedere la cronologia dei commit, comprese le modifiche in Git")
-   [Come vedere un commit specifico in Git](https://impactmillions.org/git-cheat-sheet-git-commands-you-should-know/#penci-How-to-see-a-specific-commit-in-Git "Come vedere un commit specifico in Git")
-   [Come visualizzare le statistiche di registro in Git](https://impactmillions.org/git-cheat-sheet-git-commands-you-should-know/#penci-How-to-see-log-stats-in-Git "Come visualizzare le statistiche di registro in Git")
-   [Come vedere le modifiche apportate prima di confermarle utilizzando "diff" in Git](https://impactmillions.org/git-cheat-sheet-git-commands-you-should-know/#penci-How-to-see-changes-made-before-committing-them-using-diff-in-Git "Come vedere le modifiche apportate prima di confermarle utilizzando "diff" in Git")
-   [Come visualizzare le modifiche utilizzando "git add -p"](https://impactmillions.org/git-cheat-sheet-git-commands-you-should-know/#penci-How-to-see-changes-using-git-add-p "Come visualizzare le modifiche utilizzando "git add -p"")
-   [Come rimuovere i file tracciati dall'albero di lavoro corrente in Git](https://impactmillions.org/git-cheat-sheet-git-commands-you-should-know/#penci-How-to-remove-tracked-files-from-the-current-working-tree-in-Git "Come rimuovere i file tracciati dall'albero di lavoro corrente in Git")
-   [Come rinominare i file in Git](https://impactmillions.org/git-cheat-sheet-git-commands-you-should-know/#penci-How-to-rename-files-in-Git "Come rinominare i file in Git")
-   [Come ignorare i file in Git](https://impactmillions.org/git-cheat-sheet-git-commands-you-should-know/#penci-How-to-ignore-files-in-Git "Come ignorare i file in Git")
-   [Come ripristinare le modifiche non organizzate in Git](https://impactmillions.org/git-cheat-sheet-git-commands-you-should-know/#penci-How-to-revert-unstaged-changes-in-Git "Come ripristinare le modifiche non organizzate in Git")
-   [Come ripristinare le modifiche graduali in Git](https://impactmillions.org/git-cheat-sheet-git-commands-you-should-know/#penci-How-to-revert-staged-changes-in-Git "Come ripristinare le modifiche graduali in Git")
-   [Come modificare il commit più recente in Git](https://impactmillions.org/git-cheat-sheet-git-commands-you-should-know/#penci-How-to-amend-the-most-recent-commit-in-Git "Come modificare il commit più recente in Git")
-   [Come eseguire il rollback dell'ultimo commit in Git](https://impactmillions.org/git-cheat-sheet-git-commands-you-should-know/#penci-How-to-rollback-the-last-commit-in-Git "Come eseguire il rollback dell'ultimo commit in Git")
-   [Come ripristinare un vecchio commit in Git](https://impactmillions.org/git-cheat-sheet-git-commands-you-should-know/#penci-How-to-rollback-an-old-commit-in-Git "Come ripristinare un vecchio commit in Git")
-   [Come creare un nuovo ramo in Git](https://impactmillions.org/git-cheat-sheet-git-commands-you-should-know/#penci-How-to-create-a-new-branch-in-Git "Come creare un nuovo ramo in Git")
-   [Come passare a un ramo appena creato in Git](https://impactmillions.org/git-cheat-sheet-git-commands-you-should-know/#penci-How-to-switch-to-a-newly-created-branch-in-Git "Come passare a un ramo appena creato in Git")
-   [Come elencare i rami in Git](https://impactmillions.org/git-cheat-sheet-git-commands-you-should-know/#penci-How-to-list-branches-in-Git "Come elencare i rami in Git")
-   [Come creare un ramo in Git e passare ad esso immediatamente](https://impactmillions.org/git-cheat-sheet-git-commands-you-should-know/#penci-How-to-create-a-branch-in-Git-and-switch-to-it-immediately "Come creare un ramo in Git e passare ad esso immediatamente")
-   [Come eliminare un ramo in Git](https://impactmillions.org/git-cheat-sheet-git-commands-you-should-know/#penci-How-to-delete-a-branch-in-Git "Come eliminare un ramo in Git")
-   [Come unire due rami in Git](https://impactmillions.org/git-cheat-sheet-git-commands-you-should-know/#penci-How-to-merge-two-branches-in-Git "Come unire due rami in Git")
-   [Come mostrare il registro dei commit come grafico in Git](https://impactmillions.org/git-cheat-sheet-git-commands-you-should-know/#penci-How-to-show-the-commit-log-as-a-graph-in-Git "Come mostrare il registro dei commit come grafico in Git")
-   [Come mostrare il registro dei commit come grafico di tutti i rami in Git](https://impactmillions.org/git-cheat-sheet-git-commands-you-should-know/#penci-How-to-show-the-commit-log-as-a-graph-of-all-branches-in-Git "Come mostrare il registro dei commit come grafico di tutti i rami in Git")
-   [Come interrompere un'unione in conflitto in Git](https://impactmillions.org/git-cheat-sheet-git-commands-you-should-know/#penci-How-to-abort-a-conflicting-merge-in-Git "Come interrompere un'unione in conflitto in Git")
-   [Come aggiungere un repository remoto in Git](https://impactmillions.org/git-cheat-sheet-git-commands-you-should-know/#penci-How-to-add-a-remote-repository-in-Git "Come aggiungere un repository remoto in Git")
-   [Come vedere gli URL remoti in Git](https://impactmillions.org/git-cheat-sheet-git-commands-you-should-know/#penci-How-to-see-remote-URLs-in-Git "Come vedere gli URL remoti in Git")
-   [Come ottenere maggiori informazioni su un repository remoto in Git](https://impactmillions.org/git-cheat-sheet-git-commands-you-should-know/#penci-How-to-get-more-info-about-a-remote-repo-in-Git "Come ottenere maggiori informazioni su un repository remoto in Git")
-   [Come inviare le modifiche a un repository remoto in Git](https://impactmillions.org/git-cheat-sheet-git-commands-you-should-know/#penci-How-to-push-changes-to-a-remote-repo-in-Git "Come inviare le modifiche a un repository remoto in Git")
-   [Come estrarre le modifiche da un repository remoto in Git](https://impactmillions.org/git-cheat-sheet-git-commands-you-should-know/#penci-How-to-pull-changes-from-a-remote-repo-in-Git "Come estrarre le modifiche da un repository remoto in Git")
-   [Come controllare i rami remoti che Git sta monitorando](https://impactmillions.org/git-cheat-sheet-git-commands-you-should-know/#penci-How-to-check-remote-branches-that-Git-is-tracking "Come controllare i rami remoti che Git sta monitorando")
-   [Come recuperare le modifiche del repository remoto in Git](https://impactmillions.org/git-cheat-sheet-git-commands-you-should-know/#penci-How-to-fetch-remote-repo-changes-in-Git "Come recuperare le modifiche del repository remoto in Git")
-   [Come controllare il registro dei commit corrente di un repository remoto in Git](https://impactmillions.org/git-cheat-sheet-git-commands-you-should-know/#penci-How-to-check-the-current-commits-log-of-a-remote-repo-in-Git "Come controllare il registro dei commit corrente di un repository remoto in Git")
-   [Come unire un repository remoto con il repository locale in Git](https://impactmillions.org/git-cheat-sheet-git-commands-you-should-know/#penci-How-to-merge-a-remote-repo-with-your-local-repo-in-Git "Come unire un repository remoto con il repository locale in Git")
-   [Come ottenere il contenuto dei rami remoti in Git senza unirli automaticamente](https://impactmillions.org/git-cheat-sheet-git-commands-you-should-know/#penci-How-to-get-the-contents-of-remote-branches-in-Git-without-automatically-merging "Come ottenere il contenuto dei rami remoti in Git senza unirli automaticamente")
-   [Come inviare un nuovo ramo a un repository remoto in Git](https://impactmillions.org/git-cheat-sheet-git-commands-you-should-know/#penci-How-to-push-a-new-branch-to-a-remote-repo-in-Git "Come inviare un nuovo ramo a un repository remoto in Git")
-   [Come rimuovere un ramo remoto in Git](https://impactmillions.org/git-cheat-sheet-git-commands-you-should-know/#penci-How-to-remove-a-remote-branch-in-Git "Come rimuovere un ramo remoto in Git")
-   [Come utilizzare il rebase Git](https://impactmillions.org/git-cheat-sheet-git-commands-you-should-know/#penci-How-to-use-Git-rebase "Come utilizzare il rebase Git")
-   [Come eseguire rebase in modo interattivo in Git](https://impactmillions.org/git-cheat-sheet-git-commands-you-should-know/#penci-How-to-run-rebase-interactively-in-Git "Come eseguire rebase in modo interattivo in Git")
-   [Come forzare una richiesta push in Git](https://impactmillions.org/git-cheat-sheet-git-commands-you-should-know/#penci-How-to-force-a-push-request-in-Git "Come forzare una richiesta push in Git")
-   [Conclusione](https://impactmillions.org/git-cheat-sheet-git-commands-you-should-know/#penci-Conclusion "Conclusione")

Git and GitHub are essential tools for [developers](https://impactmillions.org/what-is-git-and-github-git-vs-github/) to efficiently manage their code, collaborate with others, and to contribute in open-source projects. Git is a distributed version control system that helps developers collaborate on projects of any scale.

Linus Torvalds, the developer of the Linux kernel, created Git in 2005 to help control the Linux kernel’s development.

## What is a Distributed Version Control System?

A distributed version control system is a system that helps you keep track of changes you’ve made to files in your project.

[Git](https://github.com/) has many different commands you can use. And I’ve found that these some of the command, I use the most often (and are therefore the most helpful to remember).

You Might Be Interested In

So I have written them down and thought it’d be nice to share them with the community. I hope you find them useful – Enjoy.

## How to check your Git configuration

The command below returns a list of information about your git configuration including user name and email:
```sh
git config -l

```
## How to setup your Git username
With the command below you can configure your user name:

```sh
git config --global user.name "Anup-maurya"

```

## How to setup your Git user email

This command lets you setup the user email address you’ll use in your commits.

```sh
git config --global user.email "anupmaurya@gmail.com"

```

## How to cache your login credentials in Git

You can store login credentials in the cache so you don’t have to type them in each time. Just use this command:

```sh
git config --global credential.helper cache

```

## How to initialize a Git repo

Everything starts from here. The first step is to initialize a new Git repo locally in your project root. You can do so with the command below:

*git init*
## How to add a file to the staging area in Git

The command below will add a file to the staging area. Just replace `filename_here` with the name of the file you want to add to the staging area.

```
git add filename_here
```

## Come aggiungere tutti i file nell'area di staging in Git

Se desideri aggiungere tutti i file del tuo progetto all'area di staging, puoi utilizzare un carattere jolly  `.` e ogni file verrà aggiunto per te.

```
git add .
```

## Come aggiungere solo determinati file all'area di staging in Git

Con l'asterisco nel comando seguente, puoi aggiungere tutti i file che iniziano con "fil" nell'area di staging.

```
git add fil*
```

## Come verificare lo stato di un repository in Git

Questo comando mostrerà lo stato del repository corrente inclusi i file in stage, non in stage e non tracciati.

```
git status
```

## Come eseguire il commit delle modifiche nell'editor in Git

Questo comando aprirà un editor di testo nel terminale in cui potrai scrivere un messaggio di commit completo.

Un messaggio di commit è costituito da un breve riepilogo delle modifiche, una riga vuota e una descrizione completa delle modifiche successive.

```
git commit
```

## Come confermare le modifiche con un messaggio in Git

Puoi aggiungere un messaggio di commit senza aprire l'editor. Questo comando ti consente di specificare solo un breve riepilogo per il tuo messaggio di commit.

```
git commit -m "your commit message here"
```

## How to commit changes (and skip the staging area) in Git

You can add and commit tracked files with a single command by using the -a and -m options.

```
git commit -a -m"your commit message here"

```

## How to see your commit history in Git

This command shows the commit history for the current repository:
  

```
git log
```
## How to see your commit history including changes in Git

This command shows the commit’s history including all files and their changes:
git log -p
## How to see a specific commit in Git

This command shows a specific commit.

Replace commit-id with the id of the commit that you find in the commit log after the word commit.
  

```
git show commit-id
```

## How to see log stats in Git

This command will cause the Git log to show some statistics about the changes in each commit, including line(s) changed and file names.
  

```
git log --stat
```
## How to see changes made before committing them using “diff” in Git

You can pass a file as a parameter to only see changes on a specific file.  
`git diff` shows only unstaged changes by default.

We can call diff with the `--staged` flag to see any staged changes.

```
git diff
git diff all_checks.py
git diff --staged

```

## How to see changes using “git add -p”

This command opens a prompt and asks if you want to stage changes or not, and includes other options.
  

```
git add -p
```
## How to remove tracked files from the current working tree in Git

This command expects a commit message to explain why the file was deleted.
  

```
git rm filename
```
## How to rename files in Git

This command stages the changes, then it expects a commit message.
  

```
git mv oldfile newfile
```
## How to ignore files in Git

Create a `.gitignore` file and commit it.

## How to revert unstaged changes in Git
    

```
git checkout filename
```


## How to revert staged changes in Git

You can use the -p option flag to specify the changes you want to reset.

```
git reset HEAD filename
git reset HEAD -p

```

## How to amend the most recent commit in Git

`git commit --amend` allows you to modify and add changes to the most recent commit.
  

```
git commit --amend
```
!!Note!!: fixing up a local commit with amend is great and you can push it to a shared repository after you’ve fixed it. But you should avoid amending commits that have already been made public.

## How to rollback the last commit in Git

`git revert` will create a new commit that is the opposite of everything in the given commit.  
We can revert the latest commit by using the head alias like this:
  

```
git revert HEAD
```
## How to rollback an old commit in Git

You can revert an old commit using its commit id. This opens the editor so you can add a commit message.
  

```
git revert comit_id_here
```
## How to create a new branch in Git

By default, you have one branch, the main branch. With this command, you can create a new branch. Git won’t switch to it automatically – you will need to do it manually with the next command.
  

```sh
git branch branch_name
```
## How to switch to a newly created branch in Git

When you want to use a different or a newly created branch you can use this command:
  

```sh 
git checkout branch_name
```
## How to list branches in Git

You can view all created branches using the `git branch` command. It will show a list of all branches and mark the current branch with an asterisk and highlight it in green.
  

```sh
git branch
```
## Come creare un ramo in Git e passare ad esso immediatamente
In a single command, you can create and switch to a new branch right away.

```sh 
git checkout -b branch_name

```


## Come eliminare un ramo in Git

When you are done working with a branch and have merged it, you can delete it using the command below:

```sh
git branch -d branch_name

```

## How to merge two branches in Git

To merge the history of the branch you are currently in with the `branch_name`, you will need to use the command below:
  

```sh
git merge branch_name
```
## How to show the commit log as a graph in Git

We can use `--graph` to get the commit log to show as a graph. Also,  
`--oneline` will limit commit messages to a single line.

```sh
git log --graph --oneline

```

## How to show the commit log as a graph of all branches in Git

Does the same as the command above, but for all branches.

```sh
git log --graph --oneline --all

```

## How to abort a conflicting merge in Git

If you want to throw a merge away and start over, you can run the following command:
```sh
git merge --abort
```
## How to add a remote repository in Git

This command adds a remote repository to your local repository (just replace `https://repo_here` with your remote repo URL).

```sh
git add remote https://repo_here

```

## How to see remote URLs in Git

You can see all remote repositories for your local repository with this command:
```sh
git remote -v
```
## How to get more info about a remote repo in Git

Just replace `origin` with the name of the remote obtained by  
running the git remote -v command.
```sh
git remote show origin 
```
## How to push changes to a remote repo in Git

When all your work is ready to be saved on a remote repository, you can push all changes using the command below:
```sh
git push 
```
## How to pull changes from a remote repo in Git

If other team members are working on your repository, you can retrieve the latest changes made to the remote repository with the command below:
```sh
git pull 
```
## How to check remote branches that Git is tracking

This command shows the name of all remote branches that Git is tracking for the current repository:
```sh
git branch -r
```
## How to fetch remote repo changes in Git

This command will download the changes from a remote repo but will not perform a merge on your local branch (as git pull does that instead).
```sh
git fetch
```
## How to check the current commits log of a remote repo in Git

Commit after commit, Git builds up a log. You can find out the remote repository log by using this command:
```sh
git log origin/main
```
## How to merge a remote repo with your local repo in Git

If the remote repository has changes you want to merge with your local, then this command will do that for you:
```sh
git merge origin/main
```
## How to get the contents of remote branches in Git without automatically merging

This lets you update the remote without merging any content into the  
local branches. You can call git merge or git checkout to do the merge.
  

```sh
git remote update
```
## How to push a new branch to a remote repo in Git

If you want to push a branch to a remote repository you can use the command below. Just remember to add -u to create the branch upstream:

```sh
git push -u origin branch_name


```

## How to remove a remote branch in Git

If you no longer need a remote branch you can remove it using the command below:

```sh
git push --delete origin branch_name_here

```

## How to use Git rebase

You can transfer completed work from one branch to another using `git rebase`.

```sh
git rebase branch_name_here

```

Git Rebase può diventare davvero complicato se non lo fai correttamente. Prima di utilizzare questo comando ti suggerisco di rileggere la documentazione ufficiale  [qui](https://git-scm.com/book/it/v2/Git-Branching-Rebasing)

## Come eseguire rebase in modo interattivo in Git

Puoi eseguire git rebase in modo interattivo utilizzando il flag -i.  
Si aprirà l'editor e presenterà una serie di comandi che puoi utilizzare.

```sh
git rebase -i master
# p, pick = use commit
# r, reword = use commit, but edit the commit message
# e, edit = use commit, but stop for amending
# s, squash = use commit, but meld into previous commit
# f, fixup = like "squash", but discard this commit's log message
# x, exec = run command (the rest of the line) using shell
# d, drop = remove commit

```

## Come forzare una richiesta push in Git

Questo comando forzerà una richiesta push. Questo di solito va bene per i rami delle richieste pull perché nessun altro avrebbe dovuto clonarli.  
Ma questo non è qualcosa che vuoi fare con i repository pubblici.
  

```sh
git push -f
```

## Conclusione

Questi comandi possono migliorare notevolmente la tua produttività in Git. Non è necessario ricordarli tutti: ecco perché ho scritto questo foglietto illustrativo. Aggiungi questa pagina ai segnalibri per riferimento futuro o stampala se preferisci.
