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
У нас есть история из четырех коммитов: A, B, C, D, E, где A — первый коммит, E — последний. Необходимо объединить все коммиты, при этом чтобы история состояла из двух коммитов.

```bash
# Из такой истории:
A <- B <- C <- D <- E

# Сделать такую:
A <- E
```

<details><summary><b>Решение</b></summary>
<p>

```bash
git reset --soft HEAD~n
# [принять изменения, сделать коммит]
# при отправке изменений на сервер, понадобится использовать флаг --force:
git push --force
```

</p>
</details>
---

##### 3. 

<details><summary><b>Решение</b></summary>
<p>

```bash
```

</p>
</details>

---

##### 3. 

<details><summary><b>Решение</b></summary>
<p>

```bash
```

</p>
</details>

---

##### 3. 

<details><summary><b>Решение</b></summary>
<p>

```bash
```

</p>
</details>
