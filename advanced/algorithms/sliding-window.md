<div align="center">

# Задачи по паттерну Sliding Window

[Вопросы](https://github.com/dollaween/javascript-questions)
|
[Тесты](https://github.com/dollaween/javascript-tests)
|
[Задачи](https://github.com/dollaween/javascript-tasks)

</div>

---

**Цель задач:** Практика применения паттерна Sliding Window.

---

##### 1. Решите задачу с помощью паттерна Sliding Window
Напишите функцию, которая принимает массив чисел `nums` и число `n`. Функция должна вычислить максимальную сумму `n`-подряд идущих элементов в массиве.

```javascript
function maxSubarraySum(nums, n) {}

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

---

##### 2. Решите задачу с помощью паттерна Sliding Window
Напишите функцию, которая принимает массив положительных чисел `arr` и число `num`. Функция должна вернуть минимальную длину непрерывного подмассива сумма которого больше или равна числу `num`.

```javascript
function minSubArrayLen(arr, num) {}

minSubArrayLen([2, 3, 1, 2, 4, 3], 7)
// 2, потому что [4, 3] — минимальный непрерывный подмассив, сумма чисел которого больше или равно 7

minSubArrayLen([2, 1, 6, 5, 4], 9)
// 2, потому что [5, 4] — минимальный непрерывный подмассив

minSubArrayLen([3, 1, 62, 19], 52)
// 1, потому что [62] — минимальный непрервный подмассив, который больше чем 52
```

<details><summary><b>Решение</b></summary>
<p>

```javascript
function minSubArrayLen(arr, num) {
  let a = 0   // start
  let b = 0   // end
  let sum = 0
  let min = Infinity

  while (a < arr.length) {
    if (sum < num && b < arr.length) {
      sum += arr[b]
      b++
    } else if (sum >= num) {
      min = Math.min(min, b - a)
      sum -= arr[a]
      a++
    } else {
      break
    }
  }

  return min === Infinity ? 0 : min
}
```

</p>
</details>

---

##### 3. Решите задачу с помощью паттерна Sliding Window
Напишите функцию, которая принимает строку `str` и возвращает длину самой длинной подстроки без повторяющихся символов.

```javascript
function lengthOfLongestSubstring(str) {}

lengthOfLongestSubstring('abracadabra')
// 4, самая длинная подстрока без повторяющихся символов — 'brac'

lengthOfLongestSubstring('aaaa')
// 1, самая длинная подстрока без повторяющихся символов — 'a'

lengthOfLongestSubstring('abbcdb')
// 3, самая длинная подстрока без повторяющихся символов — 'bcd'
```

<details><summary><b>Решение 1</b></summary>
<p>

```javascript
function lengthOfLongestSubstring(str) {
  const set = new Set()
  let a = 0   // start
  let b = 0   // end
  let max = 0

  while(b < str.length) {
    if(!set.has(str.charAt(b))) {
      set.add(str.charAt(b))
      b++
      max = Math.max(set.size, max)
    } else {
      set.delete(str.charAt(a))
      a++
    }
  }

  return max
};
```

</p>
</details>

<details><summary><b>Решение 2</b></summary>
<p>

```javascript
function lengthOfLongestSubstring(str) {
  let seen = {}
  let max = 0
  let a = 0   // start
  let b = 0   // end

  for (; b < str.length; b++) {
    let char = str[b]
    if (seen[char]) {
      a = Math.max(a, seen[char])
    }
    max = Math.max(max, b - a + 1)
    seen[char] = b + 1
  }

  return max
};
```

</p>
</details>
