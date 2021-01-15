<div align="center">

# Задачи по нотации О большое

[Вопросы](https://github.com/dollaween/javascript-questions)
|
[Тесты](https://github.com/dollaween/javascript-tests)
|
[Задачи](https://github.com/dollaween/javascript-tasks)

</div>

---

**Цель задач:** 

Узнать о нотации О большое можно здесь:
* [Youtube. Оценка сложности алгоритма. Сложность алгоритмов. Big O, Большое О](https://www.youtube.com/watch?v=ZRdOb4yR0kk)

---

##### 1. Напишите пример функции равной сложности `O(N)`

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

##### 2. Напишите пример функции равной сложности `O(N^2)`

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

---

##### 3. Напишите пример функции равной сложности `O(log N)`

<details><summary><b>Решение</b></summary>
<p>

```javascript
function example(n) {
  for (let i = 2; i <= n; i *= 2) {
    console.log(i)
  }
}
```

</p>
</details>

---

##### 4. Напишите пример функции равной сложности `O(N log N)`

<details><summary><b>Решение</b></summary>
<p>

```javascript
function example(n) {
  for (let i = 0; i <= n; i++) {
    for (let k = 2; k <= n; k *= 2) {
      console.log(i, k)
    }
  }
}
```

</p>
</details>
