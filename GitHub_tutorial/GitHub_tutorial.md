# Quick Guide: Using Git and GitHub

# 1. Create a new project directory
~/Documents/Projects ❯ mkdir NewProj                                                    11:58:16

# 2. Enter the new project directory
~/Documents/Projects ❯ cd NewProj

# 3. Create new files for your project
~/Documents/Projects/NewProj ❯ touch test.txt test2.py                                  11:58:31

# 4. Confirm files are in the project directory
~/Documents/Projects/NewProj ❯ ls                                                       11:59:32
test.txt test2.py

# 5. Initialize a new git repository
~/Documents/Projects/NewProj ❯ git init                                                 11:59:33
# (Git provides hints about branch naming)

# 6. Rename the branch to 'main' (recommended by GitHub)
~/Doc/Projects/NewProj main ❯ git branch -M main   

# 7. Show all files, including hidden ones (note .git directory)
~/Doc/Projects/NewProj main ?2 ❯ ls -al                                                 12:05:47
total 0
drwxr-xr-x   5 rpr23sxu  UEA\Domain Users   160 Jul  9 11:59 .
drwx------  37 rpr23sxu  UEA\Domain Users  1184 Jul  9 11:59 ..
drwxr-xr-x@  9 rpr23sxu  UEA\Domain Users   288 Jul  9 12:00 .git
-rw-r--r--   1 rpr23sxu  UEA\Domain Users     0 Jul  9 11:59 test.txt
-rw-r--r--   1 rpr23sxu  UEA\Domain Users     0 Jul  9 11:59 test2.py

# 8. Explore the .git directory (optional, for advanced users)
~/Doc/Projects/NewProj main ?2 ❯ cd .git                                                12:05:52
~/Doc/Proj/NewProj/.git main ?2 ❯ ls -al                                                12:06:13
total 24
drwxr-xr-x@  9 rpr23sxu  UEA\Domain Users  288 Jul  9 12:00 .
drwxr-xr-x   5 rpr23sxu  UEA\Domain Users  160 Jul  9 11:59 ..
-rw-r--r--@  1 rpr23sxu  UEA\Domain Users  137 Jul  9 11:59 config
-rw-r--r--@  1 rpr23sxu  UEA\Domain Users   73 Jul  9 11:59 description
-rw-r--r--@  1 rpr23sxu  UEA\Domain Users   23 Jul  9 11:59 HEAD
drwxr-xr-x@ 16 rpr23sxu  UEA\Domain Users  512 Jul  9 12:00 hooks
drwxr-xr-x@  3 rpr23sxu  UEA\Domain Users   96 Jul  9 12:00 info
drwxr-xr-x@  4 rpr23sxu  UEA\Domain Users  128 Jul  9 12:00 objects
drwxr-xr-x@  4 rpr23sxu  UEA\Domain Users  128 Jul  9 12:00 refs

# 9. Go back to project root and stage all files for commit
~/Doc/Proj/NewProj/.git main ?2 ❯ cd .. 
~/Doc/Projects/NewProj main ?2 ❯ git add --all                                          12:06:30

# 10. Commit your changes with a message
~/Doc/Projects/NewProj main +2 ❯ git commit -m "added test.txt and test2.py"            12:06:42
[main (root-commit) cf6f389] added test.txt and test2.py
 2 files changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test.txt
 create mode 100644 test2.py

# 11. Remove a file (demonstrating file deletion)
~/Documents/Projects/NewProj main ❯ rm test.txt                                         12:08:47

# 12. Add a new file (demonstrating file addition)
~/Doc/Projects/NewProj main !1 ❯ touch test3.r                                          12:09:16

# 13. List files to confirm changes
~/Doc/Projects/NewProj main !1 ?1 ❯ ls                                                  12:09:35
test2.py test3.r

# 14. Stage all changes (additions/deletions)
~/Doc/Projects/NewProj main !1 ?1 ❯ git add --all                                       12:09:38

# 15. Commit the changes with a message
~/Doc/Projects/NewProj main +2 ❯ git commit -m "deleted txt file added r file"          12:09:51

# 16. View commit history
~/Documents/Projects/NewProj main ❯ git log                                             12:10:27

# 17. Reset to a previous commit (undo changes)
~/Doc/Projects/NewProj main ❯ git reset --hard <the commit hash you want to reset to>
HEAD is now at cf6f389 added test.txt and test2.py

# 18. List files to confirm state after reset
~/Documents/Projects/NewProj main ❯ ls                                                  12:14:45
test.txt test2.py

# 19. Add a remote repository (link to GitHub)
~/Documents/Projects/NewProj main ❯ git remote add origin git@github.com:karlgrieshop/NewProj.git

# 20. Push your local commits to GitHub
~/Documents/Projects/NewProj main ❯ git push origin main                                12:22:56
# (If rejected, remote has changes you don't have)

# 21. Force push (overwrites remote history; use with caution)
~/Documents/Projects/NewProj main ❯ git push --force origin main                        12:24:01
Enumerating objects: 3, done.
Counting objects: 100% (3/3), done.
Delta compression using up to 12 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 248 bytes | 248.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
To github.com:karlgrieshop/NewProj.git
 + 5b2e5c5...cf6f389 main -> main (forced update)

# 22. View commit history
~/Documents/Projects/NewProj main ❯ git log                                             12:25:29

# 23. Add another file
~/Doc/Projects/NewProj main ❯ touch test4.sh                                            12:26:36

# 24. Stage and commit the new file
~/Documents/Projects/NewProj main ?1 ❯ git add --all                                    12:27:48
~/Documents/Projects/NewProj main +1 ❯ git commit -m "added test4.sh"                   12:30:27
[main c156f9a] added test4.sh
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test4.sh

# 25. Try to push again (may be rejected if remote has new commits)
~/Documents/Projects/NewProj main ❯ git push origin main                                12:30:52
# (If rejected, remote has new commits)

# 26. Pull remote changes (merge or rebase as needed)
~/Documents/Projects/NewProj main ❯ git pull origin main                                12:33:17
# (If prompted, specify merge/rebase/ff-only)

# 27. List files (notice it didn't work)
~/Documents/Projects/NewProj main ❯ ls                                                  12:35:00
test.txt test2.py test4.sh

# 28. Pull with rebase to resolve divergent branches
~/Documents/Projects/NewProj main ❯ git pull --rebase origin main                       12:35:32

# 29. List files to confirm all is up to date
~/Documents/Projects/NewProj main ❯ ls                                                  12:36:04
README.md test.txt  test2.py  test4.sh

# 30. View commit history (note changes made on remote are rolled into commit history)
~/Documents/Projects/NewProj main ❯ git log                                             12:37:36

# 31. Final push to GitHub (now that branches are synchronized)
~/Documents/Projects/NewProj main ❯ git push origin main                                12:38:47

# Done! Your local and remote repositories are now synchronized.
