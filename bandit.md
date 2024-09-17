Assignment 1 - Over the Wire's "Bandit" - Noah Lee - September 17th 2024

* Level 0: Sucessfully SSH'd into the bandit server
* Level 0->1: `cat readme` - found password ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If -> using cat command (seeing whats in files)
* Level 1->2:  cat ./- -> 263JGJPfgU6LtdEvgfWU1XP5yac29mFx -> what to do when there are weird filenames
* Level 2->3: cat "spaces in this filename" MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx -> how to handle spaces in filenames
* Level 3->4: cat inhere/...Hiding-From-You 2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ -> using ls -a to see hidden files
* Level 4->5: file ./* -> ./-file07: ASCII text -> 4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw -> `*` wildcard to apply a command on all files in a directory
* Level 5->6: file */{.,}* | grep "ASCII text" | du -b -a | grep 1033 -> 1033	./maybehere07/.file2 -> cat ./maybehere07/.file2 HWasnPhtq9AVKe0dmk45nxy20cvUa6EG -> using the pipe operator to chain commands.
* Level 6->7: find / -type f -user bandit7 -group bandit6 -size 33c 2>/dev/null (2>dev>null is redirecting stderror away from the cli) -> cat /var/lib/dpkg/info/bandit7.password -> morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj -> Use the find command to find files with certain parameters or permissions.
* Level 7->8: 

