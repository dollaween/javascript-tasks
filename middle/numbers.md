<div align="center">

# Задачи среднего уровня по числам

[Вопросы](https://github.com/dollaween/javascript-questions)
|
[Тесты](https://github.com/dollaween/javascript-tests)
|
[Задачи](https://github.com/dollaween/javascript-tasks)

</div>

---

##### 1. Реверсивное число
Напишите функцию, которая принимает число `x` и возвращает число с перевернутыми цифрами. Если полученное число выходит за диапазон 32-битных чисел, то верните `0`.

```javascript
function reverse(x) {}

reverse(123)            // 321
reverse(320)            // 21
reverse(1534236469)     // 0
```

<details><summary><b>Решение</b></summary>
<p>

```javascript
function reverse(n) {
  const sign = n < 0
  let reversed = 0
  n = Math.abs(n)

  while (n) {
    reversed = reversed * 10 + (n % 10)
    n = Math.floor(n/10)
  }

  return reversed > 0x7FFFFFFF ? 0 : sign ? -reversed : reversed
}
```

</p>
</details>
