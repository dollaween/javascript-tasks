<div align="center">

<h1>Задачи по Javascript: Браузер</h1>

<a href="https://github.com/dollaween/javascript-tasks">На главную</a> | <a href="https://github.com/dollaween/javascript-questions">Вопросы</a> | <a href="https://github.com/dollaween/javascript-tests">Тесты</a>

</div>

---

##### 1. Выведите в консоль все пары "ключ": "значение" из `localStorage`
```javascript
localStorage.setItem('login', 'Alfred')
localStorage.setItem('age', '60')
localStorage.setItem('password', 'Bruce Wayne')

/** ВАШ КОД */
```
Результат:
```bash
age: 60
login: Alfred
password: Bruce Wayne
```

<details><summary><b>Решение 1</b></summary>
<p>

```javascript
for (let key of Object.keys(localStorage)) {
  console.log(`${key}: ${localStorage.getItem(key)}`);
}
```

</p>
</details>

<details><summary><b>Решение 2</b></summary>
<p>

```javascript
for(let key in localStorage) {
  if (!localStorage.hasOwnProperty(key)) {
    continue;
  }
  console.log(`${key}: ${localStorage.getItem(key)}`);
}
```

</p>
</details>

---
