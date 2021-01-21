<div align="center">

# Задачи по алгоритму Sliding Window

[Вопросы](https://github.com/dollaween/javascript-questions)
|
[Тесты](https://github.com/dollaween/javascript-tests)
|
[Задачи](https://github.com/dollaween/javascript-tasks)

</div>

---

**Цель задач:** Практика применения алгоритма Sliding Window.

---

##### 1. Решите задачу с помощью алгоритма Sliding Window
Напишите функцию, которая принимает массив чисел `nums` и число `n`. Функция должна вычислить максимальную сумму `n`-подряд идущих элементов в массиве.

```javascript
maxSubarraySum([1, 2, 5, 2, 8, 1, 5], 2); // 10, так как максимальная сумма из двух подряд идущих элементов = 2 + 8
maxSubarraySum([1, 2, 5, 2, 8, 1, 5], 4); // 17, так как максимальная сумма из четырех подряд идущих элементов = 2 + 5 + 2 + 8
maxSubarraySum([4, 2, 1, 6], 1); // 6
maxSubarraySum([], 4); // null
```

<details><summary><b>Неоптимальное решение</b></summary>
<p>

```javascript
function maxSubarraySum(nums, n) {
  if (n > nums.length) {
    return null
  }

  let max = -Infinity

  for (let i = 0; i < nums.length - n + 1; i++) {
    let temp = 0
    for (let j = 0; j < n; j++) {
      temp += nums[i + j]
    }

    max = Math.max(max, temp)
  }

  return max
}
```

</p>
</details>


<details><summary><b>Решение</b></summary>
<p>

* **Сложность:** O(N)

```javascript
function maxSubarraySum(nums, n) {
  if (nums.length < n) {
    return null
  }

  let max = 0
  let temp = 0

  for (let i = 0; i < n; i++) {
    max += nums[i]
  }

  temp = max;
  for (let i = n; i < nums.length; i++) {
    temp = temp - nums[i - n] + nums[i]
    max = Math.max(max, temp)
  }

  return max
}
```

</p>
</details>

