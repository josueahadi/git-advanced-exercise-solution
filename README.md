# Git Advanced Exercise Solution

This comprehensive exercise combines essential Git skills, from manipulating history to advanced branching strategies.

### [Link to exercise](https://github.com/HIRWA13/Git-exercise?tab=readme-ov-file)


## Challenges:
#### Part 1: Refining Git History (10 Challenges)
1. #### Missing File Fix

    ```bash
    $ touch test{1..4}.md
        git add test1.md && git commit -m "chore: Create initial file"
        git add test2.md && git commit -m "chore: Create another file"
        git add test3.md && git commit -m "chore: Create third and fourth files"

    thegym@DESKTOP-TOARFF1 MINGW64 ~/Desktop/git-advanced (main)
    1 file changed, 0 insertions(+), 0 deletions(-)
    create mode 100644 test1.md
    [main b96795b] chore: Create another file
    1 file changed, 0 insertions(+), 0 deletions(-)
    create mode 100644 test2.md
    [main 97102e4] chore: Create third and fourth files
    1 file changed, 0 insertions(+), 0 deletions(-)
    create mode 100644 test3.md

    thegym@DESKTOP-TOARFF1 MINGW64 ~/Desktop/git-advanced (main)
    $ git status
    On branch main
    Your branch is based on 'origin/main', but the upstream is gone.
    (use "git branch --unset-upstream" to fixup)

    Untracked files:
    (use "git add <file>..." to include in what will be committed)
            test4.md

    nothing added to commit but untracked files present (use "git add" to track)

    thegym@DESKTOP-TOARFF1 MINGW64 ~/Desktop/git-advanced (main)
    $ git add test4.md && git commit -m "chore: create fourth file"
    [main f04d718] chore: create fourth file
    1 file changed, 0 insertions(+), 0 deletions(-)
    create mode 100644 test4.md

    thegym@DESKTOP-TOARFF1 MINGW64 ~/Desktop/git-advanced (main)
    $ git log
    commit f04d718901b9a5d043bb8b9f0a4124d55db7386f (HEAD -> main)
    Author: josueahadi <ahadihjosue@gmail.com>
    Date:   Mon May 20 15:15:36 2024 +0200

        chore: create fourth file

    commit 97102e4223991ebe079ae56ead750ad39ec6f4a7
    Author: josueahadi <ahadihjosue@gmail.com>
    Date:   Mon May 20 15:12:01 2024 +0200

        chore: Create third and fourth files

    commit b96795b74d99fbea7b4a6a3a59b12d753ae07254
    Author: josueahadi <ahadihjosue@gmail.com>
    Date:   Mon May 20 15:12:00 2024 +0200

        chore: Create another file

    commit 0e1110c607e1c421c99bd80acbac7010aa21cf89
    Author: josueahadi <ahadihjosue@gmail.com>
    Date:   Mon May 20 15:12:00 2024 +0200

        chore: Create initial file

    ```

2. #### Editing Commit History

    ```bash
    $ git log
    commit f04d718901b9a5d043bb8b9f0a4124d55db7386f (HEAD -> main)
    Author: josueahadi <ahadihjosue@gmail.com>
    Date:   Mon May 20 15:15:36 2024 +0200

        chore: create fourth file

    commit 97102e4223991ebe079ae56ead750ad39ec6f4a7
    Author: josueahadi <ahadihjosue@gmail.com>
    Date:   Mon May 20 15:12:01 2024 +0200

        chore: Create third and fourth files

    commit b96795b74d99fbea7b4a6a3a59b12d753ae07254
    Author: josueahadi <ahadihjosue@gmail.com>
    Date:   Mon May 20 15:12:00 2024 +0200

        chore: Create another file

    commit 0e1110c607e1c421c99bd80acbac7010aa21cf89
    Author: josueahadi <ahadihjosue@gmail.com>
    Date:   Mon May 20 15:12:00 2024 +0200

        chore: Create initial file

    thegym@DESKTOP-TOARFF1 MINGW64 ~/Desktop/git-advanced (main)
    chore: Create second file
    $ git rebase -i HEAD~3
    Stopped at b96795b...  chore: Create another file
    You can amend the commit now, with

    git commit --amend

    Once you are satisfied with your changes, run

    git rebase --continue

    thegym@DESKTOP-TOARFF1 MINGW64 ~/Desktop/git-advanced (main|REBASE 1/3)
    $ git status
    interactive rebase in progress; onto 0e1110c
    Last command done (1 command done):
    edit b96795b chore: Create another file
    Next commands to do (2 remaining commands):
    pick 97102e4 chore: Create third and fourth files
    pick f04d718 chore: create fourth file
    (use "git rebase --edit-todo" to view and edit)
    You are currently editing a commit while rebasing branch 'main' on '0e1110c'.
    (use "git commit --amend" to amend the current commit)
    (use "git rebase --continue" once you are satisfied with your changes)

    nothing to commit, working tree clean

    thegym@DESKTOP-TOARFF1 MINGW64 ~/Desktop/git-advanced (main|REBASE 1/3)
    $ git commit --amend
    [detached HEAD d7e6dca] chore: Create second file
    Date: Mon May 20 15:12:00 2024 +0200
    1 file changed, 0 insertions(+), 0 deletions(-)
    create mode 100644 test2.md

    thegym@DESKTOP-TOARFF1 MINGW64 ~/Desktop/git-advanced (main|REBASE 1/3)
    $ git status
    interactive rebase in progress; onto 0e1110c
    Last command done (1 command done):
    edit b96795b chore: Create another file
    Next commands to do (2 remaining commands):
    pick 97102e4 chore: Create third and fourth files
    pick f04d718 chore: create fourth file
    (use "git rebase --edit-todo" to view and edit)
    You are currently editing a commit while rebasing branch 'main' on '0e1110c'.
    (use "git commit --amend" to amend the current commit)
    (use "git rebase --continue" once you are satisfied with your changes)

    nothing to commit, working tree clean

    thegym@DESKTOP-TOARFF1 MINGW64 ~/Desktop/git-advanced (main|REBASE 1/3)
    $ git rebase --continue
    Successfully rebased and updated refs/heads/main.

    thegym@DESKTOP-TOARFF1 MINGW64 ~/Desktop/git-advanced (main)
    $ git log
    commit 9a8fa63c65dc4ae7c920484df2742ed49e721da4 (HEAD -> main)
    Author: josueahadi <ahadihjosue@gmail.com>
    Date:   Mon May 20 15:15:36 2024 +0200

        chore: create fourth file

    commit a753549068dabc6393957f6c17c5d7f0c78e734b
    Author: josueahadi <ahadihjosue@gmail.com>
    Date:   Mon May 20 15:12:01 2024 +0200

        chore: Create third and fourth files

    commit d7e6dcaf9fe142c51367cb43a96e8052d8c4d27b
    Author: josueahadi <ahadihjosue@gmail.com>
    Date:   Mon May 20 15:12:00 2024 +0200

        chore: Create second file

    commit 0e1110c607e1c421c99bd80acbac7010aa21cf89
    Author: josueahadi <ahadihjosue@gmail.com>
    Date:   Mon May 20 15:12:00 2024 +0200

        chore: Create initial file

    thegym@DESKTOP-TOARFF1 MINGW64 ~/Desktop/git-advanced (main)
    $
    ```

3. #### Keeping History Tidy - Squashing Commits

    ```bash
    thegym@DESKTOP-TOARFF1 MINGW64 ~/Desktop/git-advanced (main)
    $ git rebase -i root
    fatal: invalid upstream 'root'

    thegym@DESKTOP-TOARFF1 MINGW64 ~/Desktop/git-advanced (main)
    $ git rebase -i --root
    [detached HEAD b97890a] chore: Create initial file
    Date: Mon May 20 15:12:00 2024 +0200
    2 files changed, 0 insertions(+), 0 deletions(-)
    create mode 100644 test1.md
    create mode 100644 test2.md
    Successfully rebased and updated refs/heads/main.

    thegym@DESKTOP-TOARFF1 MINGW64 ~/Desktop/git-advanced (main)
    $ git log
    commit 9069ba6b3d554c9fb7fd6542a95d9300e32ea2d0 (HEAD -> main)
    Author: josueahadi <ahadihjosue@gmail.com>
    Date:   Mon May 20 15:15:36 2024 +0200

        chore: create fourth file

    commit 6f58f811f17f4fbba17a90151a447ea28134e603
    Author: josueahadi <ahadihjosue@gmail.com>
    Date:   Mon May 20 15:12:01 2024 +0200

        chore: Create third and fourth files

    commit b97890a7255baa27d5ae86c32fa1c70b16a4a9d6
    Author: josueahadi <ahadihjosue@gmail.com>
    Date:   Mon May 20 15:12:00 2024 +0200

        chore: Create initial file

        chore: Create second file

    thegym@DESKTOP-TOARFF1 MINGW64 ~/Desktop/git-advanced (main)
    $
    ```


4. #### Splitting a Commit

    ```bash
    $ git log
    commit 9069ba6b3d554c9fb7fd6542a95d9300e32ea2d0 (HEAD -> main)
    Author: josueahadi <ahadihjosue@gmail.com>
    Date:   Mon May 20 15:15:36 2024 +0200

        chore: create fourth file

    commit 6f58f811f17f4fbba17a90151a447ea28134e603
    Author: josueahadi <ahadihjosue@gmail.com>
    Date:   Mon May 20 15:12:01 2024 +0200

        chore: Create third and fourth files

    commit b97890a7255baa27d5ae86c32fa1c70b16a4a9d6
    Author: josueahadi <ahadihjosue@gmail.com>
    Date:   Mon May 20 15:12:00 2024 +0200

        chore: Create initial file

        chore: Create second file

    thegym@DESKTOP-TOARFF1 MINGW64 ~/Desktop/git-advanced (main)
    $ git rebase -i b97890a7255baa27d5ae86c32fa1c70b16a4a9d6
    Stopped at 6f58f81...  chore: Create third and fourth files
    You can amend the commit now, with

    git commit --amend

    Once you are satisfied with your changes, run

    git rebase --continue

    thegym@DESKTOP-TOARFF1 MINGW64 ~/Desktop/git-advanced (main|REBASE 1/2)
    $ git reset HEAD~

    thegym@DESKTOP-TOARFF1 MINGW64 ~/Desktop/git-advanced (main|REBASE 1/2)
    $ git commit -m "Create Third File"
    interactive rebase in progress; onto b97890a
    Last command done (1 command done):
    edit 6f58f81 chore: Create third and fourth files
    Next command to do (1 remaining command):
    pick 9069ba6 chore: create fourth file
    (use "git rebase --edit-todo" to view and edit)
    You are currently editing a commit while rebasing branch 'main' on 'b97890a'.
    (use "git commit --amend" to amend the current commit)
    (use "git rebase --continue" once you are satisfied with your changes)

    Untracked files:
    (use "git add <file>..." to include in what will be committed)
            test3.md

    nothing added to commit but untracked files present (use "git add" to track)

    thegym@DESKTOP-TOARFF1 MINGW64 ~/Desktop/git-advanced (main|REBASE 1/2)
    $ git add test3.md

    thegym@DESKTOP-TOARFF1 MINGW64 ~/Desktop/git-advanced (main|REBASE 1/2)
    $ git commit -m "Create Third File"
    [detached HEAD a0cf2c6] Create Third File
    1 file changed, 0 insertions(+), 0 deletions(-)
    create mode 100644 test3.md

    thegym@DESKTOP-TOARFF1 MINGW64 ~/Desktop/git-advanced (main|REBASE 1/2)
    $ git status
    interactive rebase in progress; onto b97890a
    Last command done (1 command done):
    edit 6f58f81 chore: Create third and fourth files
    Next command to do (1 remaining command):
    pick 9069ba6 chore: create fourth file
    (use "git rebase --edit-todo" to view and edit)
    You are currently editing a commit while rebasing branch 'main' on 'b97890a'.
    (use "git commit --amend" to amend the current commit)
    (use "git rebase --continue" once you are satisfied with your changes)

    nothing to commit, working tree clean

    thegym@DESKTOP-TOARFF1 MINGW64 ~/Desktop/git-advanced (main|REBASE 1/2)
    $ git add test4.md

    thegym@DESKTOP-TOARFF1 MINGW64 ~/Desktop/git-advanced (main|REBASE 1/2)
    $

    thegym@DESKTOP-TOARFF1 MINGW64 ~/Desktop/git-advanced (main|REBASE 1/2)
    $

    thegym@DESKTOP-TOARFF1 MINGW64 ~/Desktop/git-advanced (main|REBASE 1/2)
    $

    thegym@DESKTOP-TOARFF1 MINGW64 ~/Desktop/git-advanced (main|REBASE 1/2)
    $

    thegym@DESKTOP-TOARFF1 MINGW64 ~/Desktop/git-advanced (main|REBASE 1/2)
    $ git commit -m "Create Fourth File"
    interactive rebase in progress; onto b97890a
    Last command done (1 command done):
    edit 6f58f81 chore: Create third and fourth files
    Next command to do (1 remaining command):
    pick 9069ba6 chore: create fourth file
    (use "git rebase --edit-todo" to view and edit)
    You are currently editing a commit while rebasing branch 'main' on 'b97890a'.
    pick 9069ba6 chore: create fourth file
    (use "git commit --amend" to amend the current commit)
    (use "git rebase --continue" once you are satisfied with your changes)

    Untracked files:
    (use "git add <file>..." to include in what will be committed)
            test4.md

    nothing added to commit but untracked files present (use "git add" to track)

    thegym@DESKTOP-TOARFF1 MINGW64 ~/Desktop/git-advanced (main|REBASE 1/2)
    $ git rebase --continue
    error: The following untracked working tree files would be overwritten by merge:
            test4.md
    Please move or remove them before you merge.
    Aborting
    hint: Could not execute the todo command
    hint:
    hint:     pick 9069ba6b3d554c9fb7fd6542a95d9300e32ea2d0 chore: create fourth file
    hint:
    pick 9069ba6 chore: create fourth file
    #
    drop 9069ba6 chore: create fourth file
    thegym@DESKTOP-TOARFF1 MINGW64 ~/Desktop/git-advanced (main|REBASE 2/2)
    $ git rebase --edit-todo

    thegym@DESKTOP-TOARFF1 MINGW64 ~/Desktop/git-advanced (main|REBASE 2/2)
    $ git rebase --continue
    error: The following untracked working tree files would be overwritten by merge:
            test4.md
    Please move or remove them before you merge.
    Aborting
    hint: Could not execute the todo command
    hint:
    hint:     pick 9069ba6b3d554c9fb7fd6542a95d9300e32ea2d0 chore: create fourth file
    hint:
    hint: It has been rescheduled; To edit the command before continuing, please
    hint: edit the todo list first:
    hint:
    hint:     git rebase --edit-todo
    hint:     git rebase --continue

    thegym@DESKTOP-TOARFF1 MINGW64 ~/Desktop/git-advanced (main|REBASE 3/3)
    $ git rebase --edit-todo
    hint: Waiting for your editor to close the file...

    thegym@DESKTOP-TOARFF1 MINGW64 ~/Desktop/git-advanced (main|REBASE 3/3)
    $ git rebase --continue
    Successfully rebased and updated refs/heads/main.

    thegym@DESKTOP-TOARFF1 MINGW64 ~/Desktop/git-advanced (main)
    $ git log
    commit a0cf2c6bdc72592d2831e4cb2ca7c0856dd492a6 (HEAD -> main)
    Author: josueahadi <ahadihjosue@gmail.com>
    Date:   Tue May 21 11:37:55 2024 +0200

        Create Third File

    commit b97890a7255baa27d5ae86c32fa1c70b16a4a9d6
    Author: josueahadi <ahadihjosue@gmail.com>
    Date:   Mon May 20 15:12:00 2024 +0200

        chore: Create initial file

        chore: Create second file

    thegym@DESKTOP-TOARFF1 MINGW64 ~/Desktop/git-advanced (main)
    $ git commit -m "Create Fourth File"
    On branch main
    Your branch is based on 'origin/main', but the upstream is gone.
    (use "git branch --unset-upstream" to fixup)

    Untracked files:
    (use "git add <file>..." to include in what will be committed)
            test4.md

    nothing added to commit but untracked files present (use "git add" to track)

    thegym@DESKTOP-TOARFF1 MINGW64 ~/Desktop/git-advanced (main)
    $ git add test4.md 

    thegym@DESKTOP-TOARFF1 MINGW64 ~/Desktop/git-advanced (main)
    $ git commit -m "Create Fourth File"
    [main 96513cd] Create Fourth File
    1 file changed, 0 insertions(+), 0 deletions(-)
    create mode 100644 test4.md

    thegym@DESKTOP-TOARFF1 MINGW64 ~/Desktop/git-advanced (main)
    $
    ```

5. #### Advanced Squashing

    ```bash
    $ git log
    commit 96513cd753511831c9d2f67eeecec5e1249be7f0 (HEAD -> main)
    Author: josueahadi <ahadihjosue@gmail.com>
    Date:   Tue May 21 11:43:59 2024 +0200

        Create Fourth File

    commit a0cf2c6bdc72592d2831e4cb2ca7c0856dd492a6
    Author: josueahadi <ahadihjosue@gmail.com>
    Date:   Tue May 21 11:37:55 2024 +0200

        Create Third File

    commit b97890a7255baa27d5ae86c32fa1c70b16a4a9d6
    Author: josueahadi <ahadihjosue@gmail.com>
    Date:   Mon May 20 15:12:00 2024 +0200

        chore: Create initial file

        chore: Create second file

    thegym@DESKTOP-TOARFF1 MINGW64 ~/Desktop/git-advanced (main)
    $ git rebase -i HEAD~3
    fatal: invalid upstream 'HEAD~3'

    thegym@DESKTOP-TOARFF1 MINGW64 ~/Desktop/git-advanced (main)
    $ git rebase -i HEAD~2
    [detached HEAD 077a9a5] Create third and fourth files
    Date: Tue May 21 11:37:55 2024 +0200
    2 files changed, 0 insertions(+), 0 deletions(-)
    create mode 100644 test3.md
    create mode 100644 test4.md
    Successfully rebased and updated refs/heads/main.

    thegym@DESKTOP-TOARFF1 MINGW64 ~/Desktop/git-advanced (main)
    $ git status
    On branch main
    Your branch is based on 'origin/main', but the upstream is gone.
    (use "git branch --unset-upstream" to fixup)

    nothing to commit, working tree clean

    thegym@DESKTOP-TOARFF1 MINGW64 ~/Desktop/git-advanced (main)
    $ git log
    commit 077a9a5503ddcbd0a49f21ba4263d91143aff3f1 (HEAD -> main)
    Author: josueahadi <ahadihjosue@gmail.com>
    Date:   Tue May 21 11:37:55 2024 +0200

        Create third and fourth files

        Create Third File

        Create Fourth File

    commit b97890a7255baa27d5ae86c32fa1c70b16a4a9d6
    Author: josueahadi <ahadihjosue@gmail.com>
    Date:   Mon May 20 15:12:00 2024 +0200

        chore: Create initial file

        chore: Create second file

    thegym@DESKTOP-TOARFF1 MINGW64 ~/Desktop/git-advanced (main)
    ```

6. #### Dropping a Commit

    ```bash

    thegym@DESKTOP-TOARFF1 MINGW64 ~/Desktop/git-advanced (main)
    $ git add .

    thegym@DESKTOP-TOARFF1 MINGW64 ~/Desktop/git-advanced (main)
    $ git commit -m "Unwanted commit"
    [main cc81ac0] Unwanted commit
    1 file changed, 1 insertion(+)
    create mode 100644 unwanted.txt

    thegym@DESKTOP-TOARFF1 MINGW64 ~/Desktop/git-advanced (main)
    pick 077a9a5 Create third and fourth files
    $ git log
    commit cc81ac0413679818bace4c2c9e9df4aeac98e0ee (HEAD -> main)
    Author: josueahadi <ahadihjosue@gmail.com>
    Date:   Tue May 21 11:56:03 2024 +0200

        Unwanted commit

    commit 077a9a5503ddcbd0a49f21ba4263d91143aff3f1
    Author: josueahadi <ahadihjosue@gmail.com>
    Date:   Tue May 21 11:37:55 2024 +0200

        Create third and fourth files

        Create Third File

        Create Fourth File

    commit b97890a7255baa27d5ae86c32fa1c70b16a4a9d6
    Author: josueahadi <ahadihjosue@gmail.com>
    Date:   Mon May 20 15:12:00 2024 +0200

        chore: Create initial file

        chore: Create second file

    thegym@DESKTOP-TOARFF1 MINGW64 ~/Desktop/git-advanced (main)
    $ git rebase -i HEAD~2
    Successfully rebased and updated refs/heads/main.
    ```

7. #### Reordering Commits

    ```bash
    thegym@DESKTOP-TOARFF1 MINGW64 ~/Desktop/git-advanced (main)
    $ git log
    commit 077a9a5503ddcbd0a49f21ba4263d91143aff3f1 (HEAD -> main)
    Author: josueahadi <ahadihjosue@gmail.com>
    Date:   Tue May 21 11:37:55 2024 +0200

        Create third and fourth files

        Create Third File

        Create Fourth File

    commit b97890a7255baa27d5ae86c32fa1c70b16a4a9d6
    Author: josueahadi <ahadihjosue@gmail.com>
    Date:   Mon May 20 15:12:00 2024 +0200

        chore: Create initial file

        chore: Create second file

    thegym@DESKTOP-TOARFF1 MINGW64 ~/Desktop/git-advanced (main)
    $ git rebase -i --root
    Successfully rebased and updated refs/heads/main.

    thegym@DESKTOP-TOARFF1 MINGW64 ~/Desktop/git-advanced (main)
    $ git log
    commit 8bf34abf46d9310e54fe23cf83852d0fc73edbf1 (HEAD -> main)
    Author: josueahadi <ahadihjosue@gmail.com>
    Date:   Mon May 20 15:12:00 2024 +0200

        chore: Create initial file

        chore: Create second file

    commit b5c1ed811e3d6793a4e607ccf6cf299218aeb05d
    Author: josueahadi <ahadihjosue@gmail.com>
    Date:   Tue May 21 11:37:55 2024 +0200

        Create third and fourth files

        Create Third File

        Create Fourth File
    ```

8. #### Cherry-Picking Commits

    ```bash
    thegym@DESKTOP-TOARFF1 MINGW64 ~/Desktop/git-advanced (main)
    $ git checkout -b ft/branch
    Switched to a new branch 'ft/branch'

    thegym@DESKTOP-TOARFF1 MINGW64 ~/Desktop/git-advanced (ft/branch)
    $ touch test5.md

    thegym@DESKTOP-TOARFF1 MINGW64 ~/Desktop/git-advanced (ft/branch)
    $ git add test5.md && git commit -m "Implemented test 5"
    [ft/branch f83933b] Implemented test 5
    1 file changed, 1 insertion(+)
    create mode 100644 test5.md

    thegym@DESKTOP-TOARFF1 MINGW64 ~/Desktop/git-advanced (ft/branch)
    $ git status
    On branch ft/branch
    Changes not staged for commit:
    (use "git add <file>..." to update what will be committed)
    (use "git restore <file>..." to discard changes in working directory)
            modified:   test5.md

    no changes added to commit (use "git add" and/or "git commit -a")

    thegym@DESKTOP-TOARFF1 MINGW64 ~/Desktop/git-advanced (ft/branch)
    $ git add test5.md 

    thegym@DESKTOP-TOARFF1 MINGW64 ~/Desktop/git-advanced (ft/branch)
    $ git commit -m "new line"
    [ft/branch 8a37834] new line
    1 file changed, 5 insertions(+), 1 deletion(-)

    thegym@DESKTOP-TOARFF1 MINGW64 ~/Desktop/git-advanced (ft/branch)
    $ git status
    On branch ft/branch
    nothing to commit, working tree clean

    thegym@DESKTOP-TOARFF1 MINGW64 ~/Desktop/git-advanced (ft/branch)
    $ git checkout main
    Switched to branch 'main'
    Your branch is based on 'origin/main', but the upstream is gone.
    (use "git branch --unset-upstream" to fixup)

    thegym@DESKTOP-TOARFF1 MINGW64 ~/Desktop/git-advanced (main)
    $ git status
    On branch main
    Your branch is based on 'origin/main', but the upstream is gone.
    (use "git branch --unset-upstream" to fixup)

    nothing to commit, working tree clean

    thegym@DESKTOP-TOARFF1 MINGW64 ~/Desktop/git-advanced (main)
    $ git lo
    git: 'lo' is not a git command. See 'git --help'.

    The most similar commands are
            log
            flow

    thegym@DESKTOP-TOARFF1 MINGW64 ~/Desktop/git-advanced (main)
    $ git log
    commit 8bf34abf46d9310e54fe23cf83852d0fc73edbf1 (HEAD -> main)
    Author: josueahadi <ahadihjosue@gmail.com>
    Date:   Mon May 20 15:12:00 2024 +0200

        chore: Create initial file

        chore: Create second file

    commit b5c1ed811e3d6793a4e607ccf6cf299218aeb05d
    Author: josueahadi <ahadihjosue@gmail.com>
    Date:   Tue May 21 11:37:55 2024 +0200

        Create third and fourth files

        Create Third File

        Create Fourth File

    thegym@DESKTOP-TOARFF1 MINGW64 ~/Desktop/git-advanced (main)
    $ git checkout ft/branch 
    Switched to branch 'ft/branch'

    thegym@DESKTOP-TOARFF1 MINGW64 ~/Desktop/git-advanced (ft/branch)
    $ git log
    commit 8a37834218fd47c33115021013985d554ad99748 (HEAD -> ft/branch)
    Author: josueahadi <ahadihjosue@gmail.com>
    Date:   Tue May 21 12:55:51 2024 +0200

        new line

    commit f83933b7835a78f71fa02fa25453cbf453835853
    Author: josueahadi <ahadihjosue@gmail.com>
    Date:   Tue May 21 12:36:11 2024 +0200

        Implemented test 5

    commit 8bf34abf46d9310e54fe23cf83852d0fc73edbf1 (main)
    Author: josueahadi <ahadihjosue@gmail.com>
    Date:   Mon May 20 15:12:00 2024 +0200

        chore: Create initial file

        chore: Create second file

    commit b5c1ed811e3d6793a4e607ccf6cf299218aeb05d
    Author: josueahadi <ahadihjosue@gmail.com>
    Date:   Tue May 21 11:37:55 2024 +0200

        Create third and fourth files

        Create Third File

    thegym@DESKTOP-TOARFF1 MINGW64 ~/Desktop/git-advanced (ft/branch)
    $ git checkout main 
    Switched to branch 'main'
    Your branch is based on 'origin/main', but the upstream is gone.
    (use "git branch --unset-upstream" to fixup)
    CONFLICT (modify/delete): test5.md deleted in HEAD and modified in 8a37834 (new line).  Version 8a37834 (new line) of test5.md left in tree.
    error: could not apply 8a37834... new line
    hint: After resolving the conflicts, mark them with
    hint: "git add/rm <pathspec>", then run
    hint: "git cherry-pick --continue".
    hint: You can instead skip this commit with "git cherry-pick --skip".      
    hint: To abort and get back to the state before "git cherry-pick",
    hint: run "git cherry-pick --abort".
    hint: Disable this message with "git config advice.mergeConflict false"    

    thegym@DESKTOP-TOARFF1 MINGW64 ~/Desktop/git-advanced (main|CHERRY-PICKING)

    $ git diff
    * Unmerged path test5.md

    thegym@DESKTOP-TOARFF1 MINGW64 ~/Desktop/git-advanced (main|CHERRY-PICKING)

    $ git cherry-pick --continue
    U       test5.md
    error: Committing is not possible because you have unmerged files.
    hint: Fix them up in the work tree, and then use 'git add/rm <file>'       
    hint: as appropriate to mark resolution and make a commit.
    fatal: Exiting because of an unresolved conflict.

    thegym@DESKTOP-TOARFF1 MINGW64 ~/Desktop/git-advanced (main|CHERRY-PICKING)

    $ git status
    On branch main
    Your branch is based on 'origin/main', but the upstream is gone.
    (use "git branch --unset-upstream" to fixup)

    You are currently cherry-picking commit 8a37834.
    (all conflicts fixed: run "git cherry-pick --continue")
    (use "git cherry-pick --skip" to skip this patch)
    (use "git cherry-pick --abort" to cancel the cherry-pick operation)      

    Changes to be committed:
            new file:   test5.md


    thegym@DESKTOP-TOARFF1 MINGW64 ~/Desktop/git-advanced (main|CHERRY-PICKING)
    $ git commit -m "chore: cherry-pick commands"
    [main a04e7b4] chore: cherry-pick commands
    Date: Tue May 21 12:55:51 2024 +0200
    1 file changed, 5 insertions(+)
    create mode 100644 test5.md

    ```

9. #### Visualizing Commit History

    ```bash
    $ git log --graph
    * commit a04e7b43ff4a31049f66d718f3e66057fea9e7f4 (HEAD -> main)
    | Author: josueahadi <ahadihjosue@gmail.com>
    | Date:   Tue May 21 12:55:51 2024 +0200
    | 
    |     chore: cherry-pick commands
    | 
    * commit 8bf34abf46d9310e54fe23cf83852d0fc73edbf1
    | Author: josueahadi <ahadihjosue@gmail.com>
    | Date:   Mon May 20 15:12:00 2024 +0200
    | 
    |     chore: Create initial file
    |     
    |     chore: Create second file
    | 
    * commit b5c1ed811e3d6793a4e607ccf6cf299218aeb05d
    Author: josueahadi <ahadihjosue@gmail.com>
    Date:   Tue May 21 11:37:55 2024 +0200
    
        Create third and fourth files
        
        Create Third File
        
        Create Fourth File
    ```

10. #### Understanding Reflogs

    ```bash
    $ git reflog
    a04e7b4 (HEAD -> main) HEAD@{0}: commit (cherry-pick): chore: cherry-pick commands
    8bf34ab HEAD@{1}: checkout: moving from ft/branch to main
    8a37834 (ft/branch) HEAD@{2}: checkout: moving from main to ft/branch
    8bf34ab HEAD@{3}: checkout: moving from ft/branch to main
    8a37834 (ft/branch) HEAD@{4}: commit: new line
    f83933b HEAD@{5}: commit: Implemented test 5
    8bf34ab HEAD@{6}: checkout: moving from main to ft/branch
    8bf34ab HEAD@{7}: rebase (finish): returning to refs/heads/main
    8bf34ab HEAD@{8}: rebase (pick): chore: Create initial file
    b5c1ed8 HEAD@{9}: rebase (pick): Create third and fourth files
    28739b4 HEAD@{10}: rebase (start): checkout 28739b44dd80429a6562edb1c73525eeb7fb47e4
    077a9a5 HEAD@{11}: rebase (finish): returning to refs/heads/main
    077a9a5 HEAD@{12}: rebase (start): checkout HEAD~2
    cc81ac0 HEAD@{13}: commit: Unwanted commit
    077a9a5 HEAD@{14}: rebase (finish): returning to refs/heads/main
    077a9a5 HEAD@{15}: rebase (squash): Create third and fourth files
    a0cf2c6 HEAD@{16}: rebase (start): checkout HEAD~2
    96513cd HEAD@{17}: commit: Create Fourth File
    a0cf2c6 HEAD@{18}: rebase (finish): returning to refs/heads/main
    a0cf2c6 HEAD@{19}: commit: Create Third File
    b97890a HEAD@{20}: reset: moving to HEAD~
    6f58f81 HEAD@{21}: rebase: fast-forward
    b97890a HEAD@{22}: rebase (start): checkout b97890a7255baa27d5ae86c32fa1c70b16a4a9d6
    9069ba6 HEAD@{23}: rebase (finish): returning to refs/heads/main
    9069ba6 HEAD@{24}: rebase (start): checkout 6f58f811f17f4fbba17a90151a447ea28134e603
    9069ba6 HEAD@{25}: rebase (finish): returning to refs/heads/main
    9069ba6 HEAD@{26}: rebase (pick): chore: create fourth file
    6f58f81 HEAD@{27}: rebase (pick): chore: Create third and fourth files     
    b97890a HEAD@{28}: rebase (squash): chore: Create initial file
    0e1110c HEAD@{29}: rebase: fast-forward
    3c0974e HEAD@{30}: rebase (start): checkout 3c0974eb95c5058a95adbf50b59f54c52fae4948
    9a8fa63 HEAD@{31}: rebase (abort): returning to refs/heads/main
    0e1110c HEAD@{32}: rebase (start): checkout HEAD~3
    9a8fa63 HEAD@{33}: rebase (abort): returning to refs/heads/main
    0e1110c HEAD@{34}: rebase (start): checkout HEAD~3
    9a8fa63 HEAD@{35}: rebase (finish): returning to refs/heads/main
    9a8fa63 HEAD@{36}: rebase (start): checkout HEAD~0
    9a8fa63 HEAD@{37}: rebase (finish): returning to refs/heads/main
    9a8fa63 HEAD@{38}: rebase: fast-forward
    a753549 HEAD@{39}: rebase: fast-forward
    d7e6dca HEAD@{40}: rebase: fast-forward
    0e1110c HEAD@{41}: rebase (start): checkout HEAD~3
    9a8fa63 HEAD@{42}: rebase (finish): returning to refs/heads/main
    9a8fa63 HEAD@{43}: rebase (pick): chore: create fourth file
    a753549 HEAD@{44}: rebase (pick): chore: Create third and fourth files     
    d7e6dca HEAD@{45}: commit (amend): chore: Create second file
    b96795b HEAD@{46}: rebase: fast-forward
    0e1110c HEAD@{47}: rebase (start): checkout HEAD~3
    f04d718 HEAD@{48}: rebase (finish): returning to refs/heads/main
    f04d718 HEAD@{49}: rebase (start): checkout b96795b74d99fbea7b4a6a3a59b12d753ae07254
    f04d718 HEAD@{50}: rebase (finish): returning to refs/heads/main
    f04d718 HEAD@{51}: rebase (start): checkout b96795b74d99fbea7b4a6a3a59b12d753ae07254
    f04d718 HEAD@{52}: rebase (finish): returning to refs/heads/main
    f04d718 HEAD@{53}: rebase (start): checkout HEAD~2
    f04d718 HEAD@{54}: commit: chore: create fourth file
    97102e4 HEAD@{55}: commit: chore: Create third and fourth files
    b96795b HEAD@{56}: commit: chore: Create another file
    0e1110c HEAD@{57}: commit (initial): chore: Create initial file
    (END)
    ```