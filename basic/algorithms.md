<div align="center">

# Базовые задачи по алгоритмам

[Вопросы](https://github.com/dollaween/javascript-questions)
|
[Тесты](https://github.com/dollaween/javascript-tests)
|
[Задачи](https://github.com/dollaween/javascript-tasks)

</div>

---

**Цель задач:** Знать о наличии и уметь применять алгоритмы.

---

##### 1. Алгоритм линейного поиска
Напишите функцию, которая принимает массив и искомое значение. Верните индекс искомого значения в массиве. Если значение не найден — верните `-1`.

```javascript
function linearSearch(arr, val) {}

linearSearch([1, 2, 3, 4, 5], 1)        // 0
linearSearch([1, 2, 3, 4, 5], 3)        // 2
linearSearch([1, 2, 3, 4, 5], 10)       // -1
```

<details><summary><b>Решение</b></summary>
<p>

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
