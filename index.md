# git: Курс молодого бойца


!SLIDE 

# git
## Курс молодого бойца

!SLIDE 

## Создать
## Сохранить
## Изменить
# Сохранить снова

!SLIDE 

## Что
## Кем
## Когда

!SLIDE 

## Система контроля изменений (версий)

* Хранить информацию об изменениях
* Работать одновременно с несколькими клиентами
* Работать быстро
* Работать стабильно

!SLIDE 

# git

!SLIDE 

## Информация об изменениях

<img src="images/screen1.png" />

!SLIDE 

<img src="images/screen3.png" height="600px"/>

!SLIDE 

## Распрделённость

<img src="images/screen2.png" />

!SLIDE 

# Изнутри

!SLIDE

## blob
## tree 
## commit
## tag
 
!SLIDE

## blob
<img src="images/inside1.png" />

`$ git show 6ff87c4664`

```text
Note that the only valid version of the GPL as far as this project
is concerned is _this_ particular version of the license (ie v2, not
v2.2 or v3.x or whatever), unless explicitly otherwise stated.
...
```
 
!SLIDE

## tree
<img src="images/inside2.png" />

`$ git ls-tree fb3a8bdd0ce`

```text
100644 blob 63c918c667fa005ff12ad89437f2fdc80926e21c    .gitignore
100644 blob 289b046a443c0647624607d471289b2c7dcd470b    INSTALL
040000 tree 2fb783e477100ce076f6bf57e4a6f026013dc745    Documentation
...
```

!SLIDE

## commit
<img src="images/inside3.png" />

`$ git show -s --pretty=raw 2be7fcb476`

```text
commit 2be7fcb4764f2dbcee52635b91fedb1b3dcf7ab4
tree fb3a8bdd0ceddd019615af4d57a53f43d8cee2bf
parent 257a84d9d02e90447b149af58b271c19405edb6a
author Dave Watson  1187576872 -0400
committer Junio C Hamano  1187591163 -0700
...
```

!SLIDE

# Коммит =
## Дерево + Родитель + Автор + Коммитер + Комментарий

!SLIDE

```text
.
|-- README
`-- lib
|-- inc
|   `-- tricks.rb
`-- mylib.rb
```

<img src="images/inside4.png" />

!SLIDE

## Ссылки

`.git/refs`

`.git/refs/heads`

`.git/refs/tags`

!SLIDE

`git update-ref refs/heads/master 1a410efbd13591db07496601ebc7a059dd55cfe9`

!SLIDE 

## HEAD

```text
$ cat .git/HEAD 
ref: refs/heads/master
```

`git checkout test`

```text
$ cat .git/HEAD 
ref: refs/heads/test
```

!SLIDE

## Теги (метки)

* Почти как коммит, только тег
* Указатель который никогда не перемещяется
* Объект-паразит

!SLIDE

# Снаружи

!SLIDE
# no GUI
# only CLI

!SLIDE

<img src="images/outside1.png" />

!SLIDE

## Workflow

`git add FILENAME`

`git commit -m "My pretty commit"`

`git pull --rebase`

`git push`

!SLIDE

## Всегда коммитьте изменения
## Пока не сделан push можно делать что угодно
## Читайте что пишет git

!SLIDE

## Где?

`git status`

`git where [ХЕШ]`

!SLIDE

## Что?

`git log [ОТКУДА] [КУДА]`

`git diff [ОТКУДА] [КУДА]`

`git blame [ФАЙЛ]`

`git status -v`

!SLIDE

## Отдать/Плучить

`git fetch`

`git pull`

`git push`

`git push --all`

!SLIDE

## Ой, врените всё назад

`git reset [--hard|soft] [ХЕШ]`

`git checkout ИМЯ_ФАЙЛА`

`git revert ХЕШ_КОММИТА`

!SLIDE

## Жонглируем ветками

`git checkout -b new_branch`

`git branch -D new_branch`

`git push origin :new_branch`

!SLIDE

## Fast Forward Merge

!SLIDE

`git checkout develop`

`git merge feature`

<img src="images/mr1.png" />

!SLIDE

## No Fast Forward Merge

!SLIDE

`git checkout develop`

`git merge --no-ff feature`

<img src="images/mr2.png" />

!SLIDE

## Rebase & Fast Forward Merge

!SLIDE

`git checkout rebase develop`

`git checkout develop`

`git merge feature`

<img src="images/mr3.png" />

!SLIDE

## Конфликты

* both modified
* deleted by us
* deleted by them

!SLIDE

`git rebase --continue`

`git rebase --skip`

-----------------------------------

`git commit`

!SLIDE

## reflog

`git reflog`

```text
2e3e7c6 HEAD@{0}: commit: Link on issue tracker improved
6cda7f1 HEAD@{1}: commit: Migration added
728330f HEAD@{2}: commit: Issue tracker param added to projects
b8b65cb HEAD@{3}: commit: Enumerize gem added
9dbd5e3 HEAD@{4}: commit: Undev settings added
e131b42 HEAD@{5}: commit: Link to issues follows to redmine now
b96bfe5 HEAD@{6}: checkout: moving from develop to feature/issues-link-22282
b96bfe5 HEAD@{7}: checkout: moving from feature/edit-images-22339 to develop
b96bfe5 HEAD@{8}: checkout: moving from develop to feature/edit-images-22339
b96bfe5 HEAD@{9}: rebase finished: returning to refs/heads/develop

```

!SLIDE

## cherry-pick

`git cherry-pick [ХЕШ]`

!SLIDE 

## Бинарный поиск по коммитам

`git bisect start`

`git bisect bad`

`git bisect good v1.0`

!SLIDE

## remotes

`origin` - не всегда единственный и главный репозиторий

`git remote -v`

`git remote add [name] [url]`

`git remote rm [name]`

