<div align="center">

# Задачи по алгоритмам поиска

[Вопросы](https://github.com/dollaween/javascript-questions)
|
[Тесты](https://github.com/dollaween/javascript-tests)
|
[Задачи](https://github.com/dollaween/javascript-tasks)

</div>

---

**Цель задач:** Знать о наличии и уметь применять алгоритмы поиска.

---

##### 1. Напишите пример алгоритма линейного поиска

```javascript
function linearSearch(arr, val) {}

linearSearch([1, 2, 3, 4, 5], 1)        // 0
linearSearch([1, 2, 3, 4, 5], 3)        // 2
linearSearch([1, 2, 3, 4, 5], 10)       // -1
```

<details><summary><b>Решение</b></summary>
<p>

* **Сложность:** O(N)

```javascript
function linearSearch(arr, val) {
  for (let i = 0; i < arr.length; i++) {
    if (arr[i] === val) return i
  }
  return -1
}
```

</p>
</details>

---

##### 2. Напишите пример алгоритма бинарного поиска

```javascript

```

<details><summary><b>Решение</b></summary>
<p>

* **Сложность:** O(log N)

```javascript

```

</p>
</details>

---

##### 3. Напишите пример алгоритма Jump search

```javascript
jumpSearch([1, 2, 3, 4, 5, 6, 7, 8, 9, 10], 6)   // 5
jumpSearch([1, 2, 3, 4, 5, 6, 7, 8, 9, 10], 15)  // -1
```

<details><summary><b>Решение</b></summary>
<p>

* **Сложность:** O(√n)

```javascript
function jumpSearch(arr, target) {
  const length = arr.length
  const step = Math.floor(Math.sqrt(length))
  let blockStart = 0
  let currentStep = step

  while (arr[Math.min(currentStep, length) - 1] < target) {
    blockStart = currentStep
    currentStep += step

    if (blockStart >= length)
      return -1
  }

  while (arr[blockStart] < target) {
    blockStart++
    if (blockStart === Math.min(currentStep, length))
      return -1
  }

  return arr[blockStart] === target
    ? blockStart
    : -1
}
```

</p>
</details>
