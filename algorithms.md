<div align="center">

<h1>Задачи по Javascript: Алгоритмы</h1>

<a href="https://github.com/dollaween/javascript-tasks">На главную</a> | <a href="https://github.com/dollaween/javascript-questions">Вопросы</a> | <a href="https://github.com/dollaween/javascript-tests">Тесты</a>

</div>

---

##### 1. Напишите пример функции, удовлетворяющий сложности `O(N)`

<details><summary><b>Решение</b></summary>
<p>

```javascript
function example(n) {
  if (n === 1) return 1
  return n + example(n - 1)
}
```

</p>
</details>

---

##### 2. Напишите пример функции, удовлетворяющий сложности `O(N^2)`

<details><summary><b>Решение</b></summary>
<p>

```javascript
function example(n) {
  for (let i = 0; i <= n; i++) {
    for (let k = 0; k <= n; k++) {
      console.log(i, k)
    }
  }
}
```

</p>
</details>
