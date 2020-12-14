<div align="center">

<h1>Задачи по Javascript: Регулярные выражения</h1>

<a href="https://github.com/dollaween/javascript-tasks">На главную</a> | <a href="https://github.com/dollaween/javascript-questions">Вопросы</a> | <a href="https://github.com/dollaween/javascript-tests">Тесты</a>

</div>

---

##### 1. Выберите только буквы (включая русские)

<details><summary><b>Ответ</b></summary>
<p>

```javascript
/[A-zА-я]+/g
```

</p>
</details>

---

##### 2. Выберите только цифры

<details><summary><b>Ответ</b></summary>
<p>

```javascript
/[0-9]+/g
```

</p>
</details>

---

##### 3. Выберите все, кроме цифр

<details><summary><b>Ответ</b></summary>
<p>

```javascript
/\D/g
```

</p>
</details>

---

##### 4. Выберите все, кроме букв (включая русские) и цифр

<details><summary><b>Ответ</b></summary>
<p>

```javascript
/[^\wа-яА-Я0-9+]/g
```

</p>
</details>

---

Ссылки:
* [Регулярные выражения](https://learn.javascript.ru/regular-expressions)
