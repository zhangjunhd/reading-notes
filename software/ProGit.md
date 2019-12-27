![cover](https://img1.doubanio.com/view/subject/l/public/s27715507.jpg)

    作者: Scott Chacon / Ben Straub
    出版社: Apress
    出版年: 2014-11-9
    页数: 350
    定价: USD 59.99
    装帧: Paperback
    ISBN: 9781484200773

[豆瓣链接](https://book.douban.com/subject/26208470/)

- [Git Basics](#git-basics)
  - [Snapshots, Not Differences](#snapshots-not-differences)
  - [Nearly Every Operation Is Local](#nearly-every-operation-is-local)
  - [Git Has Integrity](#git-has-integrity)
  - [Git Generally Only Adds Data](#git-generally-only-adds-data)
  - [The Three States](#the-three-states)
- [Getting a Git Repository](#getting-a-git-repository)
  - [Cloning an Existing Repository](#cloning-an-existing-repository)
- [Recording Changes to the Repository](#recording-changes-to-the-repository)
  - [Checking the Status of Your Files](#checking-the-status-of-your-files)
  - [Tracking New Files](#tracking-new-files)
  - [Staging Modified Files](#staging-modified-files)
  - [Short Status](#short-status)
  - [Ignoring Files](#ignoring-files)
  - [Viewing Your Staged and Unstaged Changes](#viewing-your-staged-and-unstaged-changes)
  - [Committing Your Changes](#committing-your-changes)
  - [Skipping the Staging Area](#skipping-the-staging-area)
  - [Removing Files](#removing-files)
  - [Moving Files](#moving-files)
- [Viewing the Commit History](#viewing-the-commit-history)
  - [Limiting Log Output](#limiting-log-output)
- [Undoing Things](#undoing-things)
  - [Unstaging a Staged File](#unstaging-a-staged-file)
  - [Unmodifying a Modified File](#unmodifying-a-modified-file)
- [Working with Remotes](#working-with-remotes)
  - [Showing Your Remotes](#showing-your-remotes)
  - [Adding Remote Repositories](#adding-remote-repositories)
  - [Fetching and Pulling from Your Remotes](#fetching-and-pulling-from-your-remotes)
  - [Pushing to Your Remotes](#pushing-to-your-remotes)
  - [Inspecting a Remote](#inspecting-a-remote)
  - [Removing and Renaming Remotes](#removing-and-renaming-remotes)
- [Tagging](#tagging)
  - [Creating Tags](#creating-tags)
  - [Annotated Tags](#annotated-tags)
  - [Lightweight Tags](#lightweight-tags)
  - [Tagging Later](#tagging-later)
  - [Sharing Tags](#sharing-tags)
- [Git Aliases](#git-aliases)
- [Branching in a Nutshell](#branching-in-a-nutshell)
  - [Creating a New Branch](#creating-a-new-branch)
  - [Switching Branches](#switching-branches)
- [Basic Branching and Merging](#basic-branching-and-merging)
  - [Basic Branching](#basic-branching)
  - [Basic Merging](#basic-merging)
  - [Basic Merge Conflicts](#basic-merge-conflicts)
- [Branch Management](#branch-management)
- [Branching Workflows](#branching-workflows)
  - [Long-Running Branches](#long-running-branches)
  - [Topic Branches](#topic-branches)
- [Remote Branches](#remote-branches)
  - [Pushing](#pushing)
  - [Tracking Branches](#tracking-branches)
  - [Pulling](#pulling)
  - [Deleting Remote Branches](#deleting-remote-branches)
- [Rebasing](#rebasing)
  - [The Basic Rebase](#the-basic-rebase)
  - [Rebase vs. Merge](#rebase-vs-merge)
- [Distributed Workflows](#distributed-workflows)
  - [Centralized Workflow](#centralized-workflow)
  - [Integration-Manager Workflow](#integration-manager-workflow)
  - [Dictator and Lieutenants Workflow](#dictator-and-lieutenants-workflow)
- [Contributing to a Project](#contributing-to-a-project)
  - [Commit Guidelines](#commit-guidelines)
  - [Private Small Team](#private-small-team)
  - [Private Managed Team](#private-managed-team)
  - [Tagging Your Releases](#tagging-your-releases)
  - [Generating a Build Number](#generating-a-build-number)

## Git Basics
### Snapshots, Not Differences
The major difference between Git and any other VCS (Subversion and friends included) is the way Git thinks about its data. Conceptually, most other systems store information as a list of file-based changes. These systems (CVS, Subversion, Perforce, Bazaar, and so on) think of the information they keep as a set of files and the changes made to each file over time.

![1-4](https://www.safaribooksonline.com/library/view/pro-git-second/9781484200766/images/9781484200773_Fig01-04.jpg)

Figure 1-4. Storing data as changes to a base version of each file

Git doesn’t think of or store its data this way. Instead, Git thinks of its data more like a set of snapshots of a miniature filesystem. Every time you commit, or save the state of your project in Git, it basically takes a picture of what all your files look like at that moment and stores a reference to that snapshot. To be efficient, if files have not changed, Git doesn’t store the file again, just a link to the previous identical file it has already stored. Git thinks about its data more like a **stream of snapshots**.

![1-5](https://www.safaribooksonline.com/library/view/pro-git-second/9781484200766/images/9781484200773_Fig01-05.jpg)

Figure 1-5. Storing data as snapshots of the project over time

### Nearly Every Operation Is Local
Most operations in Git only need local files and resources to operate—generally no information is needed from another computer on your network.

### Git Has Integrity
Everything in Git is check-summed before it is stored and is then referred to by that checksum. This means it’s impossible to change the contents of any file or directory without Git knowing about it.

The mechanism that Git uses for this checksumming is called a SHA-1 hash.

### Git Generally Only Adds Data
When you do actions in Git, nearly all of them only add data to the Git database. It is hard to get the system to do anything that is not undoable or to make it erase data in any way. As in any VCS, you can lose or mess up changes you haven’t committed yet; but after you commit a snapshot into Git, it is very difficult to lose, especially if you regularly push your database to another repository.

### The Three States
`Committed` means that the data is safely stored in your local database. `Modified` means that you have changed the file but have not committed it to your database yet. `Staged` means that you have marked a modified file in its current version to go into your next commit snapshot.

![1-6](https://www.safaribooksonline.com/library/view/pro-git-second/9781484200766/images/9781484200773_Fig01-06.jpg)

The Git directory is where Git stores the metadata and object database for your project.

The working directory is a single checkout of one version of the project.

The staging area is a file, generally contained in your Git directory, that stores information about what will go into your next commit.

The basic Git workflow goes something like this:

1. You modify files in your working directory.
2. You stage the files, adding snapshots of them to your staging area.
3. You do a commit, which takes the files as they are in the staging area and stores that snapshot permanently to your Git directory.

## Getting a Git Repository
```
$ git init

$ git add *.c
$ git add LICENSE
$ git commit -m 'initial project version'
```

### Cloning an Existing Repository
```
$ git clone https://github.com/libgit2/libgit2
```

If you want to clone the repository into a directory named something other than libgit2, you can specify that as the next command-line option:

```
$ git clone https://github.com/libgit2/libgit2 mylibgit
```

That command does the same thing as the previous one, but the target directory is called mylibgit.

## Recording Changes to the Repository
Remember that each file in your working directory can be in one of two states: tracked or untracked. `Tracked` files are files that were in the last snapshot; they can be unmodified, modified, or staged. `Untracked` files are everything else—any files in your working directory that were not in your last snapshot and are not in your staging area.

![2-1](https://www.safaribooksonline.com/library/view/pro-git-second/9781484200766/images/9781484200773_Fig02-01.jpg)

Figure 2-1. The lifecycle of the status of your files

### Checking the Status of Your Files
```
$ git status
On branch master
nothing to commit, working directory clean

$ echo 'My Project' > README
$ git status
On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)

    README

nothing added to commit but untracked files present (use "git add" to track)
```

### Tracking New Files
```
$ git add README

$ git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

    new file:   README
```

### Staging Modified Files
```
$ git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

    new file:   README

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

    modified: benchmarks.rb

$ git add benchmarks.rb
$ git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

    new file:   README
    modified:   benchmarks.rb

$ vim benchmarks.rb
$ git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

    new file:   README
    modified:   benchmarks.rb

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

    modified:   benchmarks.rb

$ git add benchmarks.rb
$ git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

    new file:   README
    modified:   benchmarks.rb
```

### Short Status
If you run git status -s or git status --short you get a far more simplified output from the command.

```
$ git status -s
 M README
MM Rakefile
A  lib/git.rb
M  lib/simplegit.rb
?? LICENSE.txt
```

There are two columns to the output—the **left hand column indicates that the file is staged and the right hand column indicates that it’s modified.** So for example in that output, the README file is modified in the working directory but not yet staged, while the lib/simplegit.rb file is modified and staged. The Rakefile was modified, staged and then modified again, so there are changes to it that are both staged and unstaged.

### Ignoring Files
The rules for the patterns you can put in the .gitignore file are as follows:

- Blank lines or lines starting with # are ignored.
- Standard glob patterns work.
- You can end patterns with a forward slash (/) to specify a directory.
- You can negate a pattern by starting it with an exclamation point (!).

Here is another example .gitignore file:

```
# a comment - this is ignored
*.a       # no .a files
!lib.a    # but do track lib.a, even though you're ignoring .a files above
/TODO     # only ignore the root TODO file, not subdir/TODO
build/    # ignore all files in the build/ directory
doc/*.txt # ignore doc/notes.txt, but not doc/server/arch.txt
```

### Viewing Your Staged and Unstaged Changes
```
$ git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

    new file:   README

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

    modified:   benchmarks.rb
```

To see what you’ve changed but not yet staged, type git diff with no other arguments:
```
$ git diff
diff --git a/benchmarks.rb b/benchmarks.rb
index 3cb747f..e445e28 100644
--- a/benchmarks.rb
+++ b/benchmarks.rb
@@ -36,6 +36,10 @@ def main
           @commit.parents[0].parents[0].parents[0]
         end

+        run_code(x, 'commits 1') do
+          git.commits.size
+        end
+
         run_code(x, 'commits 2') do
           log = git.commits('master', 15)
           log.size
```

If you want to see what you’ve staged that will go into your next commit, you can use git diff --staged.
```
$ git diff --staged
diff --git a/README b/README
new file mode 100644
index 0000000..03902a1
--- /dev/null
+++ b/README
@@ -0,0 +1,4 @@
+My Project
+
+ This is my project and it is amazing.
+
```

For another example, if you stage the benchmarks.rb file and then edit it, you can use git diff to see the changes in the file that are staged and the changes that are unstaged:
```
$ git add benchmarks.rb
$ echo '# test line' >> benchmarks.rb
$ git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

    modified: benchmarks.rb

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

    modified: benchmarks.rb
```

Now you can use git diff to see what is still unstaged:
```
$ git diff
diff --git a/benchmarks.rb b/benchmarks.rb
index e445e28..86b2f7c 100644
--- a/benchmarks.rb
+++ b/benchmarks.rb
@@ -127,3 +127,4 @@ end
 main()

 ##pp Grit::GitRuby.cache_client.stats
+# test line
```

and git diff --cached to see what you’ve staged so far:
```
$ git diff --cached
diff --git a/benchmarks.rb b/benchmarks.rb
index 3cb747f..e445e28 100644
--- a/benchmarks.rb
+++ b/benchmarks.rb
@@ -36,6 +36,10 @@ def main
          @commit.parents[0].parents[0].parents[0]
        end

+        run_code(x, 'commits 1') do
+          git.commits.size
+        end
+
        run_code(x, 'commits 2') do
          log = git.commits('master', 15)
          log.size
```

### Committing Your Changes
```
$ git commit
```

`git config --global core.editor` The editor displays the following text (this example is a Vim screen):
```
# Please enter the commit message for your changes. Lines starting
# with '#' will be ignored, and an empty message aborts the commit.
# On branch master
# Changes to be committed:
#       new file:   README
#       modified:   benchmarks.rb
#
~
~
~
".git/COMMIT_EDITMSG" 9L, 283C
```

Alternatively, you can type your commit message inline with the commit command by specifying it after a -m flag, like this:
```
$ git commit -m "Story 182: Fix benchmarks for speed"
[master 463dc4f] Story 182: Fix benchmarks for speed
 2 files changed, 2 insertions(+)
 create mode 100644 README
```

### Skipping the Staging Area
Adding the -a option to the git commit command makes Git automatically stage every file that is already tracked before doing the commit, letting you skip the git add part:

```
$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

    modified: benchmarks.rb

no changes added to commit (use "git add" and/or "git commit -a")
$ git commit -a -m 'added new benchmarks'
[master 83e38c7] added new benchmarks
 1 file changed, 5 insertions(+), 0 deletions(-)
```

### Removing Files
To remove a file from Git, you have to remove it from your tracked files (more accurately, remove it from your staging area) and then commit. The git rm command does that, and also removes the file from your working directory so you don’t see it as an untracked file the next time around.

If you simply remove the file from your working directory, it shows up under the “Changed but not updated” (that is, unstaged) area of your git status output:
```
$ rm grit.gemspec
$ git status
On branch master
Changes not staged for commit:
  (use "git add/rm <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

    deleted: grit.gemspec

no changes added to commit (use "git add" and/or "git commit -a")
```

Then, if you run git rm, it stages the file’s removal:
```
$ git rm grit.gemspec
rm 'grit.gemspec'
$ git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

    deleted: grit.gemspec
```

The next time you commit, the file will be gone and no longer tracked. If you modified the file and added it to the index already, you must force the removal with the -f option.

Another useful thing you may want to do is to keep the file in your working tree but remove it from your staging area. In other words, you may want to keep the file on your hard drive but not have Git track it anymore. This is particularly useful if you forgot to add something to your .gitignore file and accidentally added it, like a large log file or a bunch of .a compiled files. To do this, use the --cached option:
```
$ git rm --cached README
```

### Moving Files
```
$ git mv file_from file_to
```

In fact, if you run something like this and look at the status, you’ll see that Git considers it a renamed file:
```
$ git mv README.md README
$ git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

    renamed: README.md -> README
```

However, this is equivalent to running something like this:
```
$ mv README.md README
$ git rm README.md
$ git add README
```

## Viewing the Commit History
```
git clone https://github.com/schacon/simplegit-progit

$ git log
commit ca82a6dff817ec66f44342007202690a93763949
Author: Scott Chacon <schacon@gee-mail.com>
Date:   Mon Mar 17 21:52:11 2008 -0700

    changed the version number

commit 085bb3bcb608e1e8451d4b2432f8ecbe6306e7e7
Author: Scott Chacon <schacon@gee-mail.com>
Date:   Sat Mar 15 16:40:33 2008 -0700

    removed unnecessary test

commit a11bef06a3f659402fe7563abf99ad00de2209e6
Author: Scott Chacon <schacon@gee-mail.com>
Date:   Sat Mar 15 10:31:28 2008 -0700

    first commit
```

One of the more helpful options is -p, which shows the difference introduced in each commit. You can also use -2, which limits the output to only the last two entries:
```
$ git log -p -2
commit ca82a6dff817ec66f44342007202690a93763949
Author: Scott Chacon <schacon@gee-mail.com>
Date:   Mon Mar 17 21:52:11 2008 -0700

    changed the verison number

diff --git a/Rakefile b/Rakefile
index a874b73..8f94139 100644
--- a/Rakefile
+++ b/Rakefile
@@ -5,7 +5,7 @@ require 'rake/gempackagetask'
 spec = Gem::Specification.new do |s|
     s.platform  =   Gem::Platform::RUBY
     s.name      =   "simplegit"
-    s.version   =   "0.1.0"
+    s.version   =   "0.1.1"
     s.author    =   "Scott Chacon"
     s.email     =   "schacon@gee-mail.com"
     s.summary   =   "A simple gem for using Git in Ruby code."

commit 085bb3bcb608e1e8451d4b2432f8ecbe6306e7e7
Author: Scott Chacon <schacon@gee-mail.com>
Date:   Sat Mar 15 16:40:33 2008 -0700

    removed unnecessary test

diff --git a/lib/simplegit.rb b/lib/simplegit.rb
index a0a60ae..47c6340 100644
--- a/lib/simplegit.rb
+++ b/lib/simplegit.rb
@@ -18,8 +18,3 @@ class SimpleGit
     end

 end
-
-if $0 == __FILE__
-  git = SimpleGit.new
-  puts git.show
-end
\ No newline at end of file
```

For example, if you want to see some abbreviated stats for each commit, you can use the --stat option:
```
$ git log --stat
commit ca82a6dff817ec66f44342007202690a93763949
Author: Scott Chacon <schacon@gee-mail.com>
Date:   Mon Mar 17 21:52:11 2008 -0700

    changed the verison number

 Rakefile | 2 +-
 1 file changed, 1 insertion(+), 1 deletion(-)

commit 085bb3bcb608e1e8451d4b2432f8ecbe6306e7e7
Author: Scott Chacon <schacon@gee-mail.com>
Date:   Sat Mar 15 16:40:33 2008 -0700

    removed unnecessary test

 lib/simplegit.rb | 5 -----
 1 file changed, 5 deletions(-)

commit a11bef06a3f659402fe7563abf99ad00de2209e6
Author: Scott Chacon <schacon@gee-mail.com>
Date:   Sat Mar 15 10:31:28 2008 -0700

    first commit

 README           |  6 ++++++
 Rakefile         | 23 +++++++++++++++++++++++
 lib/simplegit.rb | 25 +++++++++++++++++++++++++
 3 files changed, 54 insertions(+)
```

As you can see, the --stat option prints below each commit entry a list of modified files, how many files were changed, and how many lines in those files were added and removed. It also puts a summary of the information at the end.

Another really useful option is --pretty. This option changes the log output to formats other than the default.
```
$ git log --pretty=oneline
ca82a6dff817ec66f44342007202690a93763949 changed the verison number
085bb3bcb608e1e8451d4b2432f8ecbe6306e7e7 removed unnecessary test
a11bef06a3f659402fe7563abf99ad00de2209e6 first commit

$ git log --pretty=format:"%h - %an, %ar : %s"
ca82a6d - Scott Chacon, 6 years ago : changed the version number
085bb3b - Scott Chacon, 6 years ago : removed unnecessary test
a11bef0 - Scott Chacon, 6 years ago : first commit
```

Table 2-1. Useful Options for git log --pretty=format

| Option | Description of Output |
| ------ | --------------------- |
| %H | Commit hash |
| %h | Abbreviated commit hash |
| %T | Tree hash |
| %t | Abbreviated tree hash |
| %P | Parent hash |
| %p | Abbreviated parent hash |
| %an | Author name |
| %ae | Author e-mail |
| %ad | Author date (format respects the –date= option |
| %ar | Author date, relative |
| %cn | Committer name |
| %ce | Committer e-mail |
| %cd | Committer date |
| %cr | Committer date, relative |
| %s | Subject |

The `author` is the person who originally wrote the work, whereas the `committer` is the person who last applied the work.

The oneline and format options are particularly useful with another log option called --graph. This option adds a nice little ASCII graph showing your branch and merge history:
```
$ git log --pretty=format:"%h %s" --graph
* 2d3acf9 ignore errors from SIGCHLD on trap
*  5e3ee11 Merge branch 'master' of git://github.com/dustin/grit
|\
| * 420eac9 Added a method for getting the current branch.
* | 30e367c timeout code and tests
* | 5a09431 add timeout protection to grit
* | e1193f8 support for heads with slashes in them
|/
* d6016bc require time for xmlschema
*  11d191e Merge branch 'defunkt' into local
```

Table 2-2. Common Options to git log

| Option | Description of Output |
| ------ | --------------------- |
| -p | Show the patch introduced with each commit. |
| --stat | Show statistics for files modified in each commit. |
| --shortstat | Display only the changed/insertions/deletions line from the --stat command. |
| --name-only | Show the list of files modified after the commit information. |
| --name-status | Show the list of files affected with added/modified/deleted information as well. |
| --abbrev-commit | Show only the first few characters of the SHA-1 checksum instead of all 40. |
| --relative-date | Display the date in a relative format (for example, “2 weeks ago”) instead of using the full date format. |
| --graph | Display an ASCII graph of the branch and merge history beside the log output. |
| --pretty | Show commits in an alternate format. Options include oneline, short, full, fuller, and format (where you specify your own format). |

### Limiting Log Output
In fact, you can do `-<n>`, where n is any integer to show the last n commits.

Table 2-3. Options to Limit the output of git log

| Option | Description of Output |
| ------ | --------------------- |
| -(n) | Show only the last n commits |
| --since, --after | Limit the commits to those made after the specified date |
| --until, --before | Limit the commits to those made before the specified date |
| --author | Only show commits in which the author entry matches the specified string |
| --committer | Only show commits in which the committer entry matches the specified string |
| --grep | Only show commits with a commit message containing the string |
| -S | Only show commits adding or removing code matching the string |

For example, if you want to see which commits modifying test files in the Git source code history were committed by Junio Hamano and were not merges in the month of October 2008, you can run something like this:

```
$ git log --pretty="%h - %s" --author=gitster --since="2008-10-01" \
   --before="2008-11-01" --no-merges -- t/
5610e3b - Fix testcase failure when extended attributes are in use
acd3b9e - Enhance hold_lock_file_for_{update,append}() API
f563754 - demonstrate breakage of detached checkout with symbolic link HEAD
d1a43f2 - reset --hard/read-tree --reset -u: remove unmerged new paths
51a94af - Fix "checkout --track -b newbranch" on detached HEAD
b0ad11e - pull: allow "git pull origin $something:$current_branch" into an unborn branch
```

## Undoing Things
One of the common undos takes place when you commit too early and possibly forget to add some files, or you mess up your commit message. If you want to try that commit again, you can run commit with the --amend option:

```
$ git commit –amend

$ git commit -m 'initial commit'
$ git add forgotten_file
$ git commit --amend
```

### Unstaging a Staged File
```
$ git add .
$ git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

    renamed:    README.md -> README
    modified:   benchmarks.rb

$ git reset HEAD benchmarks.rb
Unstaged changes after reset:
M       benchmarks.rb
$ git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

    renamed: README.md -> README

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

    modified: benchmarks.rb
```

### Unmodifying a Modified File
```
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

    modified: benchmarks.rb

$ git checkout -- benchmarks.rb
$ git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

    renamed: README.md -> README
```

## Working with Remotes
### Showing Your Remotes
```
$ git clone https://github.com/schacon/ticgit
Cloning into 'ticgit'...
remote: Reusing existing pack: 1857, done.
remote: Total 1857 (delta 0), reused 0 (delta 0)
Receiving objects: 100% (1857/1857), 374.35 KiB | 268.00 KiB/s, done.
Resolving deltas: 100% (772/772), done.
Checking connectivity... done.
$ cd ticgit
$ git remote
origin

$ git remote -v
Origin  https://github.com/schacon/ticgit (fetch)
Origin  https://github.com/schacon/ticgit (push)

$ cd grit
$ git remote -v
bakkdoor  https://github.com/bakkdoor/grit (fetch)
bakkdoor  https://github.com/bakkdoor/grit (push)
cho45     https://github.com/cho45/grit (fetch)
cho45     https://github.com/cho45/grit (push)
defunkt   https://github.com/defunkt/grit (fetch)
defunkt   https://github.com/defunkt/grit (push)
koke      git://github.com/koke/grit.git (fetch)
koke      git://github.com/koke/grit.git (push)
origin    git@github.com:mojombo/grit.git (fetch)
origin    git@github.com:mojombo/grit.git (push)
```

### Adding Remote Repositories
To add a new remote Git repository as a shortname you can reference easily, run `git remote add [shortname] [url]`:
```
$ git remote
origin
$ git remote add pb https://github.com/paulboone/ticgit
$ git remote -v
origin  https://github.com/schacon/ticgit (fetch)
origin  https://github.com/schacon/ticgit (push)
pb      https://github.com/paulboone/ticgit (fetch)
pb      https://github.com/paulboone/ticgit (push)

$ git fetch pb
remote: Counting objects: 43, done.
remote: Compressing objects: 100% (36/36), done.
remote: Total 43 (delta 10), reused 31 (delta 5)
Unpacking objects: 100% (43/43), done.
From https://github.com/paulboone/ticgit
 * [new branch]      master     -> pb/master
 * [new branch]      ticgit     -> pb/ticgit
```

### Fetching and Pulling from Your Remotes
```
$ git fetch [remote-name]
```

If you clone a repository, the command automatically adds that remote repository under the name “origin.”

### Pushing to Your Remotes
The command for this is simple: `git push [remote-name] [branch-name]`.

```
$ git push origin master
```

### Inspecting a Remote
If you want to see more information about a particular remote, you can use the `git remote show [remote-name] command`.

```
$ git remote show origin
* remote origin
  Fetch URL: https://github.com/schacon/ticgit
  Push  URL: https://github.com/schacon/ticgit
  HEAD branch: master
  Remote branches:
    master                               tracked
    dev-branch                           tracked
  Local branch configured for 'git pull':
    master merges with remote master
  Local ref configured for 'git push':
    master pushes to master (up to date)
```

### Removing and Renaming Remotes
```
$ git remote rename pb paul
$ git remote
origin
paul

$ git remote rm paul
$ git remote
origin
```

## Tagging
```
$ git tag
v0.1
v1.3
```

If you’re only interested in looking at the 1.8.5 series, you can run this:

```
$ git tag -l 'v1.8.5*'
v1.8.5
v1.8.5-rc0
v1.8.5-rc1
v1.8.5-rc2
v1.8.5-rc3
v1.8.5.1
v1.8.5.2
v1.8.5.3
v1.8.5.4
v1.8.5.5
```

### Creating Tags
Git uses two main types of tags: `lightweight` and `annotated`.

A lightweight tag is very much like a branch that doesn’t change—it’s just a pointer to a specific commit.

Annotated tags, however, are stored as full objects in the Git database. They’re checksummed; contain the tagger name, e-mail, and date; have a tagging message; and can be signed and verified with GNU Privacy Guard (GPG).

### Annotated Tags
```
$ git tag -a v1.4 -m 'my version 1.4'
$ git tag
v0.1
v1.3
v1.4

$ git show v1.4
tag v1.4
Tagger: Ben Straub <ben@straub.cc>
Date:   Sat May 3 20:19:12 2014 -0700

my version 1.4

commit ca82a6dff817ec66f44342007202690a93763949
Author: Scott Chacon <schacon@gee-mail.com>
Date:   Mon Mar 17 21:52:11 2008 -0700

    changed the verison number
```

### Lightweight Tags
To create a lightweight tag, don’t supply the -a, -s, or -m option:

```
$ git tag v1.4-lw
$ git tag
v0.1
v1.3
v1.4
v1.4-lw
v1.5

$ git show v1.4-lw
commit ca82a6dff817ec66f44342007202690a93763949
Author: Scott Chacon <schacon@gee-mail.com>
Date:   Mon Mar 17 21:52:11 2008 -0700

    changed the verison number
```

### Tagging Later
You can also tag commits after you’ve moved past them. Suppose your commit history looks like this:

```
$ git log --pretty=oneline
15027957951b64cf874c3557a0f3547bd83b3ff6 Merge branch 'experiment'
a6b4c97498bd301d84096da251c98a07c7723e65 beginning write support
0d52aaab4479697da7686c15f77a3d64d9165190 one more thing
6d52a271eda8725415634dd79daabbc4d9b6008e Merge branch 'experiment'
0b7434d86859cc7b8c3d5e1dddfed66ff742fcbc added a commit function
4682c3261057305bdd616e23b64b0857d832627b added a todo file
166ae0c4d3f420721acbb115cc33848dfcc2121a started write support
9fceb02d0ae598e95dc970b74767f19372d61af8 updated rakefile
964f16d36dfccde844893cac5b347e7b3d44abbc commit the todo
8a5cbc430f1a9c3d00faaeffd07798508422908a updated readme

$ git tag -a v1.2 9fceb02

$ git tag
v0.1
v1.2
v1.3
v1.4
v1.4-lw
v1.5

$ git show v1.2
tag v1.2
Tagger: Scott Chacon <schacon@gee-mail.com>
Date:   Mon Feb 9 15:32:16 2009 -0800

version 1.2
commit 9fceb02d0ae598e95dc970b74767f19372d61af8
Author: Magnus Chacon <mchacon@gee-mail.com>
Date:   Sun Apr 27 20:43:35 2008 -0700

    updated rakefile
...
```

### Sharing Tags
This process is just like sharing remote branches—you can run `git push origin [tagname]`.

```
$ git push origin v1.5
Counting objects: 14, done.
Delta compression using up to 8 threads.
Compressing objects: 100% (12/12), done.
Writing objects: 100% (14/14), 2.05 KiB | 0 bytes/s, done.
Total 14 (delta 3), reused 0 (delta 0)
To git@github.com:schacon/simplegit.git
 * [new tag]         v1.5 -> v1.5

$ git push origin --tags
Counting objects: 1, done.
Writing objects: 100% (1/1), 160 bytes | 0 bytes/s, done.
Total 1 (delta 0), reused 0 (delta 0)
To git@github.com:schacon/simplegit.git
* [new tag]         v1.4 -> v1.4
* [new tag]         v1.4-lw -> v1.4-lw
```

## Git Aliases
```
$ git config --global alias.co checkout
$ git config --global alias.br branch
$ git config --global alias.ci commit
$ git config --global alias.st status
$ git config --global alias.unstage 'reset HEAD --'
```

## Branching in a Nutshell
![3-1](https://www.safaribooksonline.com/library/view/pro-git-second/9781484200766/images/9781484200773_Fig03-01.jpg)

Figure 3-1. A commit and its tree

![3-2](https://www.safaribooksonline.com/library/view/pro-git-second/9781484200766/images/9781484200773_Fig03-02.jpg)

Figure 3-2. Commits and their parents

A branch in Git is simply a lightweight movable pointer to one of these commits. The default branch name in Git is `master`.

![3-3](https://www.safaribooksonline.com/library/view/pro-git-second/9781484200766/images/9781484200773_Fig03-03.jpg)

Figure 3-3. A branch and its commit history

### Creating a New Branch
```
$ git branch testing
```

![3-4](https://www.safaribooksonline.com/library/view/pro-git-second/9781484200766/images/9781484200773_Fig03-04.jpg)

Figure 3-4. Two branches pointing into the same series of commits

How does Git know what branch you’re currently on? It keeps a special pointer called `HEAD`.

![3-5](https://www.safaribooksonline.com/library/view/pro-git-second/9781484200766/images/9781484200773_Fig03-05.jpg)

Figure 3-5. HEAD pointing to a branch

You can easily see this by running a simple git log command that shows you where the branch pointers are pointing. This option is called --decorate.

```
$ git log --oneline --decorate
f30ab (HEAD, master, testing) add feature #32 - ability to add new
34ac2 fixed bug #1328 - stack overflow under certain conditions
98ca9 initial commit of my project
```

### Switching Branches
```
$ git checkout testing
```

![3-6](https://www.safaribooksonline.com/library/view/pro-git-second/9781484200766/images/9781484200773_Fig03-06.jpg)

Figure 3-6. HEAD points to the current branch

Well, let’s do another commit:

```
$ vim test.rb
$ git commit -a -m 'made a change'
```

![3-7](https://www.safaribooksonline.com/library/view/pro-git-second/9781484200766/images/9781484200773_Fig03-07.jpg)

Figure 3-7. The HEAD branch moves forward when a commit is made

```
$ git checkout master
```

![3-8](https://www.safaribooksonline.com/library/view/pro-git-second/9781484200766/images/9781484200773_Fig03-08.jpg)

Figure 3-8. HEAD moves when you checkout

That command did two things. It moved the HEAD pointer back to point to the master branch, and it reverted the files in your working directory to the snapshot that master points to.

    SWITCHING BRANCHES CHANGES FILES IN YOUR WORKING DIRECTORY

Let’s make a few changes and commit again:

```
$ vim test.rb
$ git commit -a -m 'made other changes'
```

![3-9](https://www.safaribooksonline.com/library/view/pro-git-second/9781484200766/images/9781484200773_Fig03-09.jpg)

Figure 3-9. Divergent history

```
$ git log --oneline --decorate --graph --all
* c2b9e (HEAD, master) made other changes
| * 87ab2 (testing) made a change
|/
* f30ab add feature #32 - ability to add new formats to the
* 34ac2 fixed bug #1328 - stack overflow under certain conditions
* 98ca9 initial commit of my project
```

## Basic Branching and Merging
### Basic Branching
![3-10](https://www.safaribooksonline.com/library/view/pro-git-second/9781484200766/images/9781484200773_Fig03-10.jpg)

Figure 3-10. A simple commit history

To create a branch and switch to it at the same time, you can run the git checkout command with the -b switch:

```
$ git checkout -b iss53
Switched to a new branch "iss53"
```

This is shorthand for:

```
$ git branch iss53
$ git checkout iss53
```

![3-11](https://www.safaribooksonline.com/library/view/pro-git-second/9781484200766/images/9781484200773_Fig03-11.jpg)

Figure 3-11. Creating a new branch pointer

```
$ vim index.html
$ git commit -a -m 'added a new footer [issue 53]'
```

![3-12](https://www.safaribooksonline.com/library/view/pro-git-second/9781484200766/images/9781484200773_Fig03-12.jpg)

Figure 3-12. The iss53 branch has moved forward with your work

```
$ git checkout master
Switched to branch 'master'

$ git checkout -b hotfix
Switched to a new branch 'hotfix'
$ vim index.html
$ git commit -a -m 'fixed the broken email address'
[hotfix 1fb7853] fixed the broken email address
 1 file changed, 2 insertions(+)
```

![3-13](https://www.safaribooksonline.com/library/view/pro-git-second/9781484200766/images/9781484200773_Fig03-13.jpg)

Figure 3-13. Hotfix branch based on master

```
$ git checkout master
$ git merge hotfix
Updating f42c576..3a0874c
Fast-forward
 index.html | 2 ++
 1 file changed, 2 insertions(+)
 ```

 Git simplifies things by moving the pointer forward because there is no divergent work to merge together—this is called a `fast-forward`.

![3-14](https://www.safaribooksonline.com/library/view/pro-git-second/9781484200766/images/9781484200773_Fig03-14.jpg)

First you’ll delete the hotfix branch, because you no longer need it—the master branch points at the same place. You can delete it with the -d option to git branch:

```
$ git branch -d hotfix
Deleted branch hotfix (3a0874c).
```

Now you can switch back to your work-in-progress branch on issue #53 and continue working on it.

```
$ git checkout iss53
Switched to branch "iss53"
$ vim index.html
$ git commit -a -m 'finished the new footer [issue 53]'
[iss53 ad82d7a] finished the new footer [issue 53]
1 file changed, 1 insertion(+)
```

![3-15](https://www.safaribooksonline.com/library/view/pro-git-second/9781484200766/images/9781484200773_Fig03-15.jpg)

Figure 3-15. Work continues on iss53

### Basic Merging
```
$ git checkout master
Switched to branch 'master'
$ git merge iss53
Merge made by the 'recursive' strategy.
README |    1 +
1 file changed, 1 insertion(+)
```

In this case, your development history has diverged from some older point. Because the commit on the branch you’re on isn’t a direct ancestor of the branch you’re merging in, Git has to do some work. In this case, Git does a simple `three-way merge`, using the two snapshots pointed to by the branch tips and the common ancestor of the two.

![3-16](https://www.safaribooksonline.com/library/view/pro-git-second/9781484200766/images/9781484200773_Fig03-16.jpg)

Figure 3-16. Three snapshots used in a typical merge

Instead of just moving the branch pointer forward, Git creates a new snapshot that results from this three-way merge and automatically creates a new commit that points to it. This is referred to as a merge commit, and is special in that it has more than one parent.

### Basic Merge Conflicts
```
$ git merge iss53
Auto-merging index.html
CONFLICT (content): Merge conflict in index.html
Automatic merge failed; fix conflicts and then commit the result.

$ git status
On branch master
You have unmerged paths.
  (fix conflicts and run "git commit")

Unmerged paths:
  (use "git add <file>..." to mark resolution)

    both modified: index.html

no changes added to commit (use "git add" and/or "git commit -a")
```

Your file contains a section that looks something like this:

```
<<<<<<< HEAD:index.html
<div id="footer">contact : email.support@github.com</div>
=======
<div id="footer">
 please contact us at support@github.com
</div>
>>>>>>>iss53:index.html
```

This resolution has a little of each section, and the <<<<<<<, =======, and >>>>>>>lines have been completely removed. After you’ve resolved each of these sections in each conflicted file, run git add on each file to mark it as resolved. Staging the file marks it as resolved in Git.

## Branch Management
The git branch command does more than just create and delete branches. If you run it with no arguments, you get a simple listing of your current branches:

```
$ git branch
   iss53
* master
   testing
```

Notice the * character that prefixes the master branch: it indicates the branch that you currently have checked out (i.e., the branch that HEAD points to).

To see the last commit on each branch, you can run git branch -v:

```
$ git branch -v
  iss53   93b412c fix javascript issue
* master  7a98805 Merge branch 'iss53'
  testing 782fd34 add scott to the author list in the readmes

$ git branch --merged
  iss53
* master
```

Because you already merged in iss53 earlier, you see it in your list. Branches on this list without the * in front of them are generally fine to delete with git branch -d.

To see all the branches that contain work you haven’t yet merged in, you can run git branch --no-merged:

```
$ git branch --no-merged
   testing
```

Because it contains work that isn’t merged in yet, trying to delete it with git branch –d will fail:

```
$ git branch -d testing
error: The branch 'testing' is not fully merged.
If you are sure you want to delete it, run 'git branch -D testing'.
```

## Branching Workflows
### Long-Running Branches
Many Git developers have a workflow that embraces this approach, such as having only code that is entirely stable in their master branch—possibly only code that has been or will be released. They have another parallel branch named develop or next that they work from or use to test stability—it isn’t necessarily always stable, but whenever it gets to a stable state, it can be merged into master.

![3-18](https://www.safaribooksonline.com/library/view/pro-git-second/9781484200766/images/9781484200773_Fig03-18.jpg)

Figure 3-18. A linear view of progressive-stability branching

![3-19](https://www.safaribooksonline.com/library/view/pro-git-second/9781484200766/images/9781484200773_Fig03-19.jpg)

Figure 3-19. A “silo” view of progressive-stability branching

Some larger projects also have a proposed or pu (proposed updates) branch that has integrated branches that may not be ready to go into the next or master branch.

### Topic Branches
Topic branches, however, are useful in projects of any size. A topic branch is a short-lived branch that you create and use for a single particular feature or related work.

![3-20](https://www.safaribooksonline.com/library/view/pro-git-second/9781484200766/images/9781484200773_Fig03-20.jpg)

Figure 3-20. Multiple topic branches

![3-21](https://www.safaribooksonline.com/library/view/pro-git-second/9781484200766/images/9781484200773_Fig03-21.jpg)

Figure 3-21. History after merging dumbidea and iss91v2

It’s important to remember when you’re doing all this that these branches are completely local. When you’re branching and merging, everything is being done only in your Git repository—no server communication is happening.

## Remote Branches
![3-22](https://www.safaribooksonline.com/library/view/pro-git-second/9781484200766/images/9781484200773_Fig03-22.jpg)

Figure 3-22. Server and local repositories after cloning

If you do some work on your local master branch, and, in the meantime, someone else pushes to git.ourcompany.com and updates its master branch, then your histories move forward differently. Also, as long as you stay out of contact with your origin server, your origin/master pointer doesn’t move.

![3-23](https://www.safaribooksonline.com/library/view/pro-git-second/9781484200766/images/9781484200773_Fig03-23.jpg)

Figure 3-23. Local and remote work can diverge

To synchronize your work, you run a git fetch origin command. This command looks up which server “origin” is (in this case, it’s git.ourcompany.com), fetches any data from it that you don’t yet have, and updates your local database, moving your origin/master pointer to its new, more up-to-date position.

![3-24](https://www.safaribooksonline.com/library/view/pro-git-second/9781484200766/images/9781484200773_Fig03-24.jpg)

Figure 3-24. git fetch updates your remote references

![3-25](https://www.safaribooksonline.com/library/view/pro-git-second/9781484200766/images/9781484200773_Fig03-25.jpg)

Figure 3-25. Adding another server as a remote

![3-26](https://www.safaribooksonline.com/library/view/pro-git-second/9781484200766/images/9781484200773_Fig03-26.jpg)

Figure 3-26. Remote tracking branch for teamone/master

### Pushing
If you have a branch named serverfix that you want to work on with others, you can push it up the same way you pushed your first branch. Run `git push (remote) (branch)`:

```
$ git push origin serverfix
Counting objects: 24, done.
Delta compression using up to 8 threads.
Compressing objects: 100% (15/15), done.
Writing objects: 100% (24/24), 1.91 KiB | 0 bytes/s, done.
Total 24 (delta 2), reused 0 (delta 0)
To https://github.com/schacon/simplegit
 * [new branch] serverfix -> serverfix
```

Git automatically expands the serverfix branchname out to refs/heads/serverfix:refs/heads/serverfix, which means, “Take my serverfix local branch and push it to update the remote’s serverfix branch.”

You can also do git push origin serverfix:serverfix, which does the same thing – it says, “Take my serverfix and make it the remote’s serverfix.” You can use this format to push a local branch into a remote branch that is named differently. If you didn’t want it to be called serverfix on the remote, you could instead run git push origin serverfix:awesomebranch to push your local serverfix branch to the awesomebranch branch on the remote project.

The next time one of your collaborators fetches from the server, they will get a reference to where the server’s version of serverfix is under the remote branch origin/serverfix:

```
$ git fetch origin
remote: Counting objects: 7, done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 0), reused 3 (delta 0)
Unpacking objects: 100% (3/3), done.
From https://github.com/schacon/simplegit
 * [new branch] serverfix -> origin/serverfix
```

It’s important to note that when you do a fetch that brings down new remote branches, you don’t automatically have local, editable copies of them. In other words, in this case, you don’t have a new serverfix branch—you only have an origin/serverfix pointer that you can’t modify.

To merge this work into your current working branch, you can run git merge origin/serverfix. If you want your own serverfix branch that you can work on, you can base it off your remote branch:

```
$ git checkout -b serverfix origin/serverfix
Branch serverfix set up to track remote branch serverfix from origin.
Switched to a new branch 'serverfix'
```

### Tracking Branches
Checking out a local branch from a remote branch automatically creates what is called a “tracking branch” (or sometimes an “upstream branch”). Tracking branches are local branches that have a direct relationship to a remote branch. If you’re on a tracking branch and type git push, Git automatically knows which server and branch to push to. Also, running git pull while on one of these branches fetches all the remote references and then automatically merges in the corresponding remote branch.

When you clone a repository, it generally automatically creates a master branch that tracks origin/master. That’s why git push and git pull work out of the box with no other arguments.

The simple case is the example you just saw, running `git checkout -b [branch] [remotename]/[branch]`. This is a common enough operation that git provides the --track shorthand:

```
$ git checkout --track origin/serverfix
Branch serverfix set up to track remote branch serverfix from origin.
Switched to a new branch 'serverfix'
```

To set up a local branch with a different name than the remote branch, you can easily use the first version with a different local branch name:

```
$ git checkout -b sf origin/serverfix
Branch sf set up to track remote branch serverfix from origin.
Switched to a new branch 'sf'
```

If you already have a local branch and want to set it to a remote branch you just pulled down, or want to change the upstream branch you’re tracking, you can use the -u or --set-upstream-to option to git branch to explicitly set it at any time.

```
$ git branch -u origin/serverfix
Branch serverfix set up to track remote branch serverfix from origin.
```

If you want to see what tracking branches you have set up, you can use the -vv option to git branch. This lists your local branches with more information, including what each branch is tracking and whether your local branch is ahead, behind or both.

```
$ git branch -vv
  iss53     7e424c3 [origin/iss53: ahead 2] forgot the brackets
  master    1ae2a45 [origin/master] deploying index fix
* serverfix f8674d9 [teamone/server-fix-good: ahead 3, behind 1] this should do it
  testing   5ea463a trying something new
```

It’s important to note that these numbers are only since the last time you fetched from each server. This command does not reach out to the servers, it’s telling you about what it has cached from these servers locally. If you want totally up to date ahead and behind numbers, you’ll need to fetch from all your remotes right before running this. You could do that like this: $ git fetch --all; git branch -vv.

### Pulling
While the git fetch command will fetch down all the changes on the server that you don’t have yet, it will not modify your working directory at all. It will simply get the data for you and let you merge it yourself. However, there is a command called git pull which is essentially a git fetch immediately followed by a git merge in most cases.

### Deleting Remote Branches
```
$ git push origin --delete serverfix
To https://github.com/schacon/simplegit
 - [deleted] serverfix
```

## Rebasing
### The Basic Rebase
![3-27](https://www.safaribooksonline.com/library/view/pro-git-second/9781484200766/images/9781484200773_Fig03-27.jpg)

Figure 3-27. Simple divergent history

![3-28](https://www.safaribooksonline.com/library/view/pro-git-second/9781484200766/images/9781484200773_Fig03-28.jpg)

Figure 3-28. Merging to integrate diverged work history

With the rebase command, you can take all the changes that were committed on one branch and replay them on another one.

```
$ git checkout experiment
$ git rebase master
First, rewinding head to replay your work on top of it...
Applying: added staged command
```

![3-29](https://www.safaribooksonline.com/library/view/pro-git-second/9781484200766/images/9781484200773_Fig03-29.jpg)

Figure 3-29. Rebasing the change introduced in C3 onto C4

![3-30](https://www.safaribooksonline.com/library/view/pro-git-second/9781484200766/images/9781484200773_Fig03-30.jpg)

Figure 3-30. Fast-forwarding the master branch

There is no difference in the end product of the integration, but rebasing makes for a cleaner history. If you examine the log of a rebased branch, it looks like a linear history: it appears that all the work happened in series, even when it originally happened in parallel.

Note that the snapshot pointed to by the final commit you end up with, whether it’s the last of the rebased commits for a rebase or the final merge commit after a merge, is the same snapshot—it’s only the history that is different.

### Rebase vs. Merge
One point of view on this is that your repository’s commit history is a record of what actually happened. It’s a historical document, valuable in its own right, and shouldn’t be tampered with. From this angle, changing the commit history is almost blasphemous; you’re lying about what actually transpired. So what if there was a messy series of merge commits? That’s how it happened, and the repository should preserve that for posterity.

The opposing point of view is that the commit history is the story of how your project was made. You wouldn’t publish the first draft of a book, and the manual for how to maintain your software deserves careful editing. This is the camp that uses tools like rebase and filter-branch to tell the story in the way that’s best for future readers.

## Distributed Workflows
### Centralized Workflow
![5-1](https://www.safaribooksonline.com/library/view/pro-git-second/9781484200766/images/9781484200773_Fig05-01.jpg)

Figure 5-1. Centralized workflow

### Integration-Manager Workflow
The process works as follows:

1. The project maintainer pushes to their public repository.
2. A contributor clones that repository and makes changes.
3. The contributor pushes to their own public copy.
4. The contributor sends the maintainer an e-mail asking them to pull changes.
5. The maintainer adds the contributor’s repo as a remote and merges locally.
6. The maintainer pushes merged changes to the main repository.

![5-2](https://www.safaribooksonline.com/library/view/pro-git-second/9781484200766/images/9781484200773_Fig05-02.jpg)

Figure 5-2. Integration-manager workflow

### Dictator and Lieutenants Workflow
Various integration managers are in charge of certain parts of the repository; they’re called `lieutenants`. All the lieutenants have one integration manager known as the benevolent `dictator`.

The process works like this:

1. Regular developers work on their topic branch and rebase their work on top of master. The master branch is that of the dictator.
2. Lieutenants merge the developers’ topic branches into their master branch.
3. The dictator merges the lieutenants’ master branches into the dictator’s master branch.
4. The dictator pushes their master to the reference repository so the other developers can rebase on it.

![5-3](https://www.safaribooksonline.com/library/view/pro-git-second/9781484200766/images/9781484200773_Fig05-03.jpg)

Figure 5-3. Benevolent dictator workflow

## Contributing to a Project
### Commit Guidelines
First, you don’t want to submit any whitespace errors. Git provides an easy way to check for this—before you commit, run git diff --check, which identifies possible whitespace errors and lists them for you.

![5-4](https://www.safaribooksonline.com/library/view/pro-git-second/9781484200766/images/9781484200773_Fig05-04.jpg)

Figure 5-4. Output of git diff -check

Next, try to make each commit a logically separate changeset.

The last thing to keep in mind is the commit message. Getting in the habit of creating quality commit messages makes using and collaborating with Git a lot easier.

### Private Small Team
![5-11](https://www.safaribooksonline.com/library/view/pro-git-second/9781484200766/images/9781484200773_Fig05-11.jpg)

Figure 5-11. General sequence of events for a simple multiple-developer Git workflow

### Private Managed Team
![5-12](https://www.safaribooksonline.com/library/view/pro-git-second/9781484200766/images/9781484200773_Fig05-15.jpg)

Figure 5-15. Basic sequence of this managed-team workflow

### Tagging Your Releases
When you’ve decided to cut a release, you’ll probably want to drop a tag so you can re-create that release at any point going forward.

```
$ git tag -s v1.5 -m 'my signed 1.5 tag'
You need a passphrase to unlock the secret key for
user: "Scott Chacon <schacon@gmail.com>"
1024-bit DSA key, ID F721C45A, created 2009-02-09
```

### Generating a Build Number
Git gives you the name of the nearest tag with the number of commits on top of that tag and a partial SHA-1 value of the commit you’re describing:

```
$ git describe master
v1.6.2-rc1-20-g8c5b85c
```
