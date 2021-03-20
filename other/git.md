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
git commit -c ORIG_HEAD               # такой записью используем предыдущее сообщение коммита
```

</p>
</details>
