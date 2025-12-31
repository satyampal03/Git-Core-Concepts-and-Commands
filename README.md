# FIX COMMIT ISSUE 
```Fix last commit	git reset --soft HEAD~1	Staged and ready to commit again
Redo last commit	git reset HEAD~1	Keep files but must git add again
Delete last commit	git reset --hard HEAD~1	Deleted forever
Remove older commit	git rebase -i HEAD~N	Removed from history (requires drop)
