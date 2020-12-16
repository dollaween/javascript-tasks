<div align="center">

<h1>Задачи по Javascript: Массивы</h1>

<a href="https://github.com/dollaween/javascript-tasks">На главную</a> | <a href="https://github.com/dollaween/javascript-questions">Вопросы</a> | <a href="https://github.com/dollaween/javascript-tests">Тесты</a>

</div>

---

##### 1. Извлеките из массива только уникальные значения

```javascript
uniqueValues([1, 1, 2, 3, 4, 2, 3, 7, 5, 5, 7, 8])
// => [1, 2, 3, 4, 7, 5, 8]
```

<details><summary><b>Подсказка</b></summary>
<p>

Попробуйте использовать `new Set()`.

</p>
</details>

<details><summary><b>Решение</b></summary>
<p>

```javascript
function uniqueValues(arr) {
  return [...new Set(arr)]
}
```

</p>
</details>

---

##### 2. Перемешайте элементы в массиве

```javascript
shuffle([1, 2, 3, 4, 5, 6, 7])
// => [6, 4, 1, 7, 5, 2, 3]
```

<details><summary><b>Подсказка</b></summary>
<p>

Попробуйте использовать метод `Array.sort()` и `Math.random()`.

</p>
</details>

<details><summary><b>Решение</b></summary>
<p>

```javascript
function shuffle(arr) {
  return arr.sort(() => Math.random() - 0.5)
}
```

</p>
</details>
