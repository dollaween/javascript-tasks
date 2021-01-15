<div align="center">

# Базовые задачи по массивам

[Вопросы](https://github.com/dollaween/javascript-questions)
|
[Тесты](https://github.com/dollaween/javascript-tests)
|
[Задачи](https://github.com/dollaween/javascript-tasks)

</div>

---

**Цель задач:** Знать о наличии и уметь применять встроенные методы массивов.

Найти все методы можно здесь:
* [MDN. Array](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array)

---

##### 1. Возведение чисел в квадрат
Напишите функцию, которая принимает массив чисел и возвращает массив этих чисел возведенных в квадрат. Решите задачу нескольким способами: с помощью цикла `for`, методов `forEach`, `map`, `reduce`.

```javascript
function square(numbers) {}

square([1, 2, 3, 4, 5])
// [1, 4, 9, 16, 25]
```

<details><summary><b>Решение 1: цикл for</b></summary>
<p>

```javascript
function square(numbers) {
  const result = []
  for (let i = 0; i < numbers.length; i++) {
    result.push(numbers[i] ** 2)
  }
  return result
}
```

</p>
</details>

<details><summary><b>Решение 2: метод forEach</b></summary>
<p>

```javascript
function square(numbers) {
  const result = []
  numbers.forEach((num) => result.push(num ** 2))
  return result
}
```

</p>
</details>

<details><summary><b>Решение 3: метод map</b></summary>
<p>

```javascript
function square(numbers) {
  return numbers.map((num) => num ** 2)
}
```

</p>
</details>

<details><summary><b>Решение 4: метод reduce</b></summary>
<p>

```javascript
function square(numbers) {
  return numbers.reduce((acc, num) => {
    acc.push(num ** 2)
    return acc
  }, [])
}
```

</p>
</details>

---

##### 2. Фильтрация элементов
Напишите функцию, которая принимает массив элементов и исключение. Функция должна возвращать отфильтрованный массив в котором не содержится исключение.

```javascript
function filter(arr, exception) {}

filter([1, 2, 3, 4, 5], 4)
// [1, 2, 3, 5]
```

<details><summary><b>Решение</b></summary>
<p>

```javascript
function filter(arr, exception) {
  return arr.filter((val) => val !== exception)
}
```

</p>
</details>

---


