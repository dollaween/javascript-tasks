<div align="center">

# Задачи по паттерну Multiple Pointers

[Вопросы](https://github.com/dollaween/javascript-questions)
|
[Тесты](https://github.com/dollaween/javascript-tests)
|
[Задачи](https://github.com/dollaween/javascript-tasks)

</div>

---

**Цель задач:** Практика применения паттерна Multiple Pointers.

---

##### 1. Решите задачу с помощью паттерна Multiple Pointers
Напишите функцию, которая принимает неограниченное количество аргументов и возвращает `false`, если среди аргументов нет повторяющихся.

```javascript
function areThereDuplicates(...args) {}

areThereDuplicates(1, 2, 3)             // false
areThereDuplicates(56, 'some', 'b')     // false
areThereDuplicates(1, 2, 2)             // true
areThereDuplicates('a', 'never', 'a')   // true
```

<details><summary><b>Решение</b></summary>
<p>

* **Сложность:** O(N log N)

```javascript
function areThereDuplicates(...args) {
  args = args.sort();

  let i = 0;

  for (let k = 1; k < args.length; i++, k++) {
    if (args[i] === args[k]) {
      return true
    }
  }

  return false
}
```

</p>
</details>

<details><summary><b>Другое решение</b></summary>
<p>

Решение через `Set`.

```javascript
function areThereDuplicates() {
  return new Set(arguments).size !== arguments.length
}
```

</p>
</details>

---

##### 2. Решите задачу не превышая сложность O(N)
Напишите фукнцию, которая принимает отсортированный массив чисел `numbers`. Функция должна найти и вернуть первую пару чисел, сумма которых равна нулю.

```javascript
function sumZero(numbers) {}

sumZero([-3, -2, -1, 0, 1, 2, 3])     // [-3, 3]
sumZero([-2, 0, 1, 3])                // undefined
sumZero([1, 2, 3])                    // undefined
```

<details><summary><b>Неоптимальное решение</b></summary>
<p>

```javascript
function sumZero(numbers) {
  for (let i = 0; i < numbers.length; i++)
    for (let k = i + 1; k < numbers.length; k++)
      if (numbers[i] + numbers[k] === 0)
        return [numbers[i], numbers[k]]
}
```

</p>
</details>

<details><summary><b>Решение</b></summary>
<p>

* **Сложность:** O(N)

```javascript
function sumZero(numbers) {
  let left = 0
  let right = numbers.length - 1

  while (left < right) {
    let sum = numbers[left] + numbers[right]

    if (sum === 0) return [numbers[left], numbers[right]]
    else if (sum < 0) left++
    else right--
  }
}
```

</p>
</details>

---

##### 3. Решите задачу с помощью паттерна Multiple Pointers
Напишите функцию, которая принимает отсортированный массив чисел и возвращает число уникальных чисел в массиве.

```javascript
countUniqueValues([1, 1, 1, 2, 2])                  // 2, уникальные числа — 1, 2
countUniqueValues([-3, -2, -2, 0, 1, 1, 2, 3, 3])   // 6
countUniqueValues([])                               // 0
```

<details><summary><b>Решение 1</b></summary>
<p>

* **Сложность:** O(N)

```javascript
function countUniqValues(arr) {
  if (arr.length === 0) return 0

  let count = 1
  let i = 0
  for (let k = 1; k < arr.length; i++, k++) {
    if (arr[i] !== arr[k]) {
      count += 1
    }
  }

  return count
}
```

</p>
</details>

<details><summary><b>Решение 2</b></summary>
<p>

* **Сложность:** O(N)

```javascript
function countUniqValues(arr) {
  if (arr.length === 0) return 0

  let i = 0
  for (let k = 1; k < arr.length; k++)
    if (arr[i] !== arr[k])
      arr[++i] = arr[k]

  return i + 1
}
```

</p>
</details>

---

##### 4. Решите задачу не превышая сложности O(N)
Напишите функцию, которая принимает отсортированный массив чисел и целевое число. Функция должна вернуть `true`, если в массиве есть пара чисел, среднее значение которых равняется целевому числу.

```javascript
function averagePair(arr, val) {}

averagePair([1, 2, 3], 2.5)
// true, так как среднее значение 2 и 3 = 2.5
averagePair([1, 2, 3, 4, 5, 6, 7, 10, 11], 8)   // true
averagePair([1, 2, 3], 2.2)                     // false
averagePair([], 2)                              // false

```

<details><summary><b>Решение</b></summary>
<p>

* **Сложность**: O(N)

```javascript
function averagePair(arr, target) {
  let left = 0
  let right = arr.length - 1

  while (left < right) {
    let average = (arr[left] + arr[right]) / 2

    if (average === target) return true
    else if (average < target) left++
    else right--
  }

  return false
}
```

</p>
</details>

---

##### 5. Решите задачу используя паттерн Multiple Pointers
Напишите функцию, которая принимает подстроку и строку. Функция должна вернуть `true`, если в строке содержатся символы из подстроки. Между символами подстроки могут содержаться другие символы, но порядок подстроки не должен меняться.

```javascript
function isSubsequence(str1, str2) {}

isSubsequence('Hello', 'Hello world')     // true
isSubsequence('sing', 'sting')            // true, в 'sting' содержится 'sing'
isSubsequence('abc', 'acb')               // false, порядок букв важен
```

<details><summary><b>Решение</b></summary>
<p>

* **Сложность**: O(A + B)

```javascript
function isSubsequence(str1, str2) {
  if (!str1) return true

  let i = 0
  for (let k = 0; k < str2.length; k++) {
    if (i === str1.length - 1) return true
    if (str1[i] === str2[k]) i++
  }

  return false
}
```

</p>
</details>
