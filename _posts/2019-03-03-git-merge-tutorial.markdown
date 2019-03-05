---
layout: post
title: "Git Merge Tutorial"
description: Git merge is used to join two or more development histories together. In this article, we are going to talk about different cases of merging the branches with example.
date: 2019-03-03 08:44:46
author: sarad
categories:
- blog
- Git
tags: Git tutorial, git merge, git merge example, git merge tutorial, git merge explained
generes: Git
img: 2019-03-03-git-merge-tutorial.png
imagealt: git merge tutorial
thumb: 2019-03-03-git-merge-tutorial.png
redirect_from:
  - /blog/git/git-merge-tutorial
---

Git merge is used to join two or more development histories together. In this article, we are going to talk about different cases of merging the branches with example. <!--more--> Let's get started.

>**Contents**
1. [Parameters and Details](#parameter-detail)
2. [Automatic Merging](#automatic-merge)
3. [Finding all branches with no merged changes](#find-branches-with-no-merged-changes)
4. [Aborting a merge](#aborting-merge)
5. [Merge with a commit](#merge-with-commit)
6. [Keep changes from only one side of a merge](#keep-changes-from-one-side)
7. [Merge one branch into another](#merge-into-another-branch)

### <a class="anchor" name="parameter-detail"></a>Parameters and their detail

The *git merge* command takes following parameters. Let's have a look at the table along with thier short detail.

| Parameter | Details |
| --- | --- |
| `-m` | Message to be included in the merge commit |
| `-v` | Show verbose output |
| `--abort` | Attempt to revert all files back to their state |
| `--ff-only` | Aborts instantly when a merge-commit would be required |
| `--no-ff` | Forces creation of a merge-commit, even if it wasn't mandatory |
| `--no-commit` | Pretends the merge failed to allow inspection and tweaking of the result |
| `--stat` | Show a diffstat after merge completion |
| `-n / --no-stat` | Don't show the diffstat |
| `--squash` | Allows for a single commit on the current branch with the merged changes |

### <a class="anchor" name="automatic-merge"></a>Automatic Merging

When the commits on two branches don't conflict, Git can automatically merge them:

```
~/Stack Overflow(branch:master) » git merge another_branch
Auto-merging file_a
Merge made by the 'recursive' strategy.
 file_a | 2 +-
 1 file changed, 1 insertion(+), 1 deletion(-)
```

### <a class="anchor" name="find-branches-with-no-merged-changes"></a>Finding all branches with no merged changes

Sometimes you might have branches lying around that have already had their changes merged into master. This finds all branches that are not master that have no unique commits as compared to master. This is very useful for finding branches that were not deleted after the PR was merged into master.

```
for branch in $(git branch -r) ; do
 [ "${branch}" != "origin/master" ] && [ $(git diff master...${branch} | wc -l) -eq 0 ] && echo -
e `git show --pretty=format:"%ci %cr" $branch | head -n 1`\\t$branch
 done | sort -r
```

### <a class="anchor" name="aborting-merge"></a>Aborting a merge

After starting a merge, you might want to stop the merge and return everything to its pre-merge state. Use *--abort*:

```
git merge --abort
```

### <a class="anchor" name="merge-with-commit"></a>Merge with a commit

Default behaviour is when the merge resolves as a fast-forward, only update the branch pointer, without creating a merge commit. Use *--no-ff* to resolve.

```
git merge <branch_name> --no-ff -m "<commit message>"
```

### <a class="anchor" name="keep-changes-from-one-side"></a>Keep changes from only one side of a merge

During a merge, you can pass *--ours* or *--theirs* to *git checkout* to take all changes for a file from one side or the other of a merge.

```
$ git checkout --ours -- file1.txt # Use our version of file1, delete all their changes
$ git checkout --theirs -- file2.txt # Use their version of file2, delete all our changes
```

### <a class="anchor" name="merge-into-another-branch"></a>Merge one branch into another


```
git merge incomingBranch
```
This merges the branch incomingBranch into the branch you are currently in. For example, if you are currently in master, then incomingBranch will be merged into master.

Merging can create conflicts in some cases. If this happens, you will see the message *Automatic merge failed*; fix conflicts and then commit the result. You will need to manually edit the conflicted files, or to undo your merge attempt, run:

```
git merge --abort
```

>*This article is compiled from the original Stack Overflow Documentation released under 
[CC BY-SA 3.0](https://creativecommons.org/licenses/by-sa/3.0/){:target="_blank"}
and created by these contributors: 
[Liam Ferris](https://stackoverflow.com/users/5363885/){:target="_blank"},
[Vogel612](https://stackoverflow.com/users/1803692/){:target="_blank"},
This website is not affiliated with
[Stack Overflow](https://stackoverflow.com/){:target="_blank"}.
For corrections or feedback comment below or email to
<a href="mailto:ictsimplified@gmail.com?Subject=Feedback on Git Merge" target="_top">ictsimplified@gmail.com</a>*

