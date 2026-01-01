# FIX COMMIT ISSUE 
```Fix last commit	git reset --soft HEAD~1	Staged and ready to commit again
Redo last commit	git reset HEAD~1	Keep files but must git add again
Delete last commit	git reset --hard HEAD~1	Deleted forever
Remove older commit	git rebase -i HEAD~N	Removed from history (requires drop)
```


# Fix changes with last commit
```
git add -A → stages all changes (including deletions)
git commit → saves a snapshot
git push → uploads it to GitHub (origin)
```
