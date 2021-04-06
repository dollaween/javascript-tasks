<div align="center">

# Задачи по Git

[Вопросы](https://github.com/dollaween/javascript-questions)
|
[Тесты](https://github.com/dollaween/javascript-tests)
|
[Задачи](https://github.com/dollaween/javascript-tasks)

</div>

---

**Цель задач:** Практика по Git.

---

##### 1.Как отменить последний коммит?

<details><summary><b>Решение</b></summary>
<p>

```bash
git commit -m 'Commit with mistake'   # допустим, мы сделали такой коммит с ошибкой
git reset HEAD~
# [отредактировать файлы, по необходимости]
git add .
git commit -c ORIG_HEAD               # используем предыдущее сообщение коммита
```

</p>
</details>

---

##### 2. Как исправить сообщение последнего коммита?

<details><summary><b>Решение</b></summary>
<p>

```bash
git commit --amend
```

</p>
</details>

---

##### 3. Как внести правки в последний коммит?

<details><summary><b>Решение</b></summary>
<p>

```bash
# [сделать правки]
git commit --amend

# если сообщение коммита менять не нужно, то:
git commit --amend --no-edit
```

</p>
</details>

---

##### 4. Как исправить историю коммитов?
У нас есть история из пяти коммитов: A, B, C, D, E, где A — первый коммит, E — последний. Необходимо объединить все коммиты, при этом чтобы история состояла из двух коммитов.

```bash
# Из такой истории:
A <- B <- C <- D <- E

# Сделать такую:
A <- E
```

<details><summary><b>Решение 1</b></summary>
<p>

```bash
git reset --soft HEAD~n
# [принять изменения, сделать коммит]
# при отправке изменений на сервер понадобится использовать флаг --force:
git push --force
```

</p>
</details>

<details><summary><b>Решение 2</b></summary>
<p>

```bash
git reset $(git merge-base branchFrom currentBranch)
# [принять изменения, сделать коммит]
# при отправке изменений на сервер понадобится использовать флаг --force:
git push --force
```

</p>
</details>

---


##### 5. Как слить вместе две ветки?

```bash
# Из такой истории:
[master] C1 <- C2 <- C3 <- C4
[feat1]     <- C5 <- C6

# Должно получится так:
[master] C1 <- C2 <- C3 <- C4 <- C5 <- C6
```

<details><summary><b>Решение 1</b></summary>
<p>

```bash
git checkout master
git merge feat1
# [решаем конфликты]
```

</p>
</details>

<details><summary><b>Решение 2</b></summary>
<p>

```bash
git rebase master feat1
# [решаем конфликты]
# после успешного слияния переходим на master
git checkout master
# и методом перемотки передвигаем указатель на последний коммит
git merge feat1
```

</p>
</details>

---

##### 6. Как влить в master только определенную ветку?
Допустим, у нас есть такая структура:

```bash
[master] C1 <- C2
[feat1]     <- C3 <- C4 <- C5
[feat2]           <- C6 <- C7
```
Как влить в `C2 (master)` только ветку с коммитами `C6` и `C7` `(feat2)`, игнорируя при этом `C3`?

<details><summary><b>Решение</b></summary>
<p>

```bash
git rebase --onto master feat2
# после переключаемся на master
git checkout master
# и делаем перемотку указателя
git merge feat2
```

</p>
</details>

---

##### 7. Как удалить ветку?

<details><summary><b>Решение</b></summary>
<p>

```bash
git branch -d <branch>
git branch -d feat1
```

</p>
</details>

---

##### 8. Как удалить ветку на сервере?

<details><summary><b>Решение</b></summary>
<p>

```bash
git push <remote> --delete <branch>
git push origin --delete feat1
```

</p>
</details>
