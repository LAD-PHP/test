# SOME project with my data

# HEAD
git head показывает последний коммит

# log
git log показывает историю коммитов

git log --oneline - показывает урезанную историю коммитов, хеш может быть разной длины. гит сам выбирает длину чтобы хеши были уникальными

# commit
`git commit --amend --no-edit` - забыли добавить файл или дописать текст, не хотите делать новый коммит, а просто добавить к последнему.

## изменить сообщение коммита
`git commit --amend -m "Новое сообщение"`


# ОТКАТ

### откат файла из staged в untrack

```
daler@bash:~/dev/first-project$ touch unstage
daler@bash:~/dev/first-project$ git add .
daler@bash:~/dev/first-project$ git status
On branch main
Your branch and 'origin/main' have diverged,
and have 1 and 1 different commits each, respectively.
  (use "git pull" to merge the remote branch into yours)

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   readme.md
        new file:   unstage

daler@bash:~/dev/first-project$ git restore --staged unstage
daler@bash:~/dev/first-project$ git status
On branch main
Your branch and 'origin/main' have diverged,
and have 1 and 1 different commits each, respectively.
  (use "git pull" to merge the remote branch into yours)

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   readme.md

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        unstage
```

### Откатить commit
```
$ git log --oneline # хеш можно найти в истории
7b972f5 (HEAD -> master) style: добавить комментарии, расставить отступы
b576d89 feat: добавить массив Expenses и цикл для добавления трат # вот сюда и вернёмся
4b58962 refactor: разделить analyzeExpenses() на countSum() и saveExpenses()

$ git reset --hard b576d89
# теперь мы на этом коммите
HEAD is now at b576d89 feat: добавить массив Expenses и цикл для добавления трат
```