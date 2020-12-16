<div align="center">

<h1>Задачи по Javascript: Функции</h1>

<a href="https://github.com/dollaween/javascript-tasks">На главную</a> | <a href="https://github.com/dollaween/javascript-questions">Вопросы</a> | <a href="https://github.com/dollaween/javascript-tests">Тесты</a>

</div>

---

##### 1. Напишите функцию, которая возвращает n-ую запись в последовательности Фибоначчи

Последовательность Фибоначчи — это ряд чисел, где каждое последующее является суммой двух предыдущих. Первые десять чисел: `[0, 1, 1, 2, 3, 5, 8, 13, 21, 34]`.

```javascript
fibonacci(3)    // 2
fibonacci(9)    // 34
```

<details><summary><b>Подсказка</b></summary>
<p>

Создайте массив состоящий из первых двух чисел последовательности Фибоначчи. При помощи цикла от 2 до N (нужное значение) в каждой итерации добавляйте в конец массива число, равное сумме двух последних чисел массива.

</p>
</details>

<details><summary><b>Решение 1</b></summary>
<p>

```javascript
function fibonacci(num) {
  const result = [0, 1]

  for (let i = 2; i <= num; i++) {
    result.push(result[i - 1] + result[i - 2])
  }

  return result[num]
}
```

</p>
</details>

<details><summary><b>Решение 2</b></summary>
<p>

Работает очень медленно:

```javascript
function fibonacci(num) {
  if (num < 2) {
    return num
  }
  return fibonacci(num - 1) + fibonacci(num - 2)
}
```

</p>
</details>

---
