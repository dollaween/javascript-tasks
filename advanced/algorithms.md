<div align="center">

# Задачи по алгоритмам

[Вопросы](https://github.com/dollaween/javascript-questions)
|
[Тесты](https://github.com/dollaween/javascript-tests)
|
[Задачи](https://github.com/dollaween/javascript-tasks)

</div>

---

**Цель задач:** Практика применения Javascript-алгоритмов.

Для решения этих задач необходимо разбираться в **нотации О большое** и знать такие алгоритмы, как:
* Divide and Conquer
* Frequency counter
* Multiple Pointers
* Sliding Window

---

<div align="center">

### Frequency counter

</div>

---

##### 1. Решите задачу не превышая сложность O(N)
Напишите функцию, которая принимает два массива чисел и возвращает true, если второй массив содержит те же числа, но в квадрате (порядок чисел значения не имеет).

```javascript
function same(arr1, arr2) {}

same([1, 2, 3], [4, 1, 9])    // true
same([1, 2, 3], [1, 4])       // false, количество элементов не совпадает
same([1, 2, 1], [4, 4, 1])    // false, должна быть та же частота
```

<details><summary><b>Неоптимальное решение</b></summary>
<p>

**Сложность:** O(N^2)

```javascript
function same(arr1, arr2) {
  if (arr1.length !== arr2.length) {
    return false
  }

  for (let i = 0; i < arr1.length; i++) {
    let correctIndex = arr2.indexOf(arr1[i]**2)
    if (correctIndex === -1) {
      return false
    }
    arr2.splice(correctIndex, 1)
  }

  return true
}
```

</p>
</details>

<details><summary><b>Решение</b></summary>
<p>

* **Сложность:** O(N^2)
* **Алгоритм:** Frequency counter

```javascript
function same (arr1, arr2) {
  if (arr1.length !== arr2.length) {
    return false
  }

  let freqCounter = {}
  for (let val of arr1) {
    let squared = val ** 2
    freqCounter[squared] = (freqCounter[squared] || 0) + 1
  }

  for (let val of arr2) {
    if (!freqCounter[val]) {
      return false
    }
    freqCounter[val] -= 1
  }

  return true
}
```

</p>
</details>

---

##### 2. Решите задачу не превышая сложность O(N)
Напишите функцию, которая принимает массив элементов и массив исключений. Функция должна вернуть отфильтрованный массив, в котором не содержится ни одно из исключений.

```javascript
function filter(arr, exceptions) {}

filter([1, 2, 3, 4, 5], [2, 4])
// [1, 3, 5]
```

<details><summary><b>Неоптимальное решение</b></summary>
<p>

* **Сложность:** O(N^2)

```javascript
function filter(arr, exceptions) {
  return arr.filter((val) => {
    return exceptions.every((except) => except !== val)
  })
}
```

</p>
</details>

<details><summary><b>Решение</b></summary>
<p>

* **Сложность:** O(N)
* **Алгоритм:** Frequency counter

```javascript
function filter(arr, exceptions) {
  const freqCounter = {}
  for (let val of exceptions) {
    freqCounter[val] = val
  }
  return arr.filter((val) => {
    return val !== freqCounter[val]
  })
}
```

</p>
</details>

---

##### 3. Решите задачу с помощью алгоритма Frequency counter
Напишите функцию, которая принимает два числа и возвращает `true`, если числа имеют одинаковую частоту цифр.

```javascript
function sameFrequency(num1, num2) {}

sameFrequency(246, 462)       // true, так как во втором числе присутствуют те же цифры, что и в первом
sameFrequency(83965, 35689)   // true
sameFrequency(81, 38)         // false
sameFrequency(11, 111)        // false
```

<details><summary><b>Решение</b></summary>
<p>

* **Сложность:** O(N)
* **Алгоритм**: Frequency counter

```javascript
function same(num1, num2) {
  str1 = num1.toString()
  str2 = num2.toString()

  if (str1.length !== str2.length) {
    return false
  }

  const freqCounter = {}

  for (let val of str1) {
    freqCounter[val] = (freqCounter[val] || 0) + 1
  }

  for (let val of str2) {
    if (!freqCounter[val]) return false
    freqCounter[val] -= 1
  }

  return true
}
```

</p>
</details>

---

##### 4. Решите задачу не превышая сложность O(N)
Напишите функцию, которая принимает массив фильмов `movies` и длительность `flightLength` . Функция должна вернуть `true`, если массив содержит два фильма, суммарная длительность которых равна заданной длительности `flightLength`.

```javascript
function findTwoMovies(movies, flightLength) {}

const movies = [
  { title: 'The Shawshank Redemption', flight: 142 },
  { title: 'The Green Mile', flight: 189 },
  { title: 'Interstellar', flight: 169 },
  { title: 'Intouchables', flight: 112 }
]

findTwoMovies(movies, 311)    // true
findTwoMovies(movies, 100)    // false
```

<details><summary><b>Неоптимальное решение</b></summary>
<p>

* **Сложность**: O(N^2)

Проблема данного решения:
* 100 фильмов — 100 * 100 = 10 000 итераций
* 1000 фильмов — 1000 * 1000 = 1 000 000 итераций

```javascript
function findTwoMovies(movies, flightLength) {
  for (let i = 0; i < movies.length; i++) {
    for (let k = 0; k < movies.length; k++) {
      if (i === k) continue
      if (movies[i].flight + movies[k].flight === flightLength) {
        return true
      }
    }
  }
  return false
}
```

</p>
</details>

<details><summary><b>Решение</b></summary>
<p>

* **Сложность**: O(N)
* **Алгоритм**: Frequency counter

Преимущества по сравнению с решением через вложенный цикл:
* 100 фильмов — 100 итераций
* 1000 фильмов — 1000 итераций

```javascript
function findTwoMovies(movies, flightLength) {
  // В объекте будет хранится остаток времени после каждого фильма
  let results = {}
  for (let i = 0; i < movies.length; i++) {
    // Если время фильма совпадает с одним из значений в results, то задача выполнена
    if (results[movies[i].flight]) {
      return true
    }

    // Вычисляем сколько времени нам требуется еще добавить за счет другого фильма и добавляем в объект
    let result = flightLength - movies[i].flight
    results[result] = true
  }
  return false
}
```

</p>
</details>

---

##### 5. Решите задачу несколькими способами
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

* **Сложность**: O(N)
* **Алгоритм**: Frequency counter

```javascript
function areThereDuplicates(...args) {
  let freqCounter = {}

  for (let val of args) {
    if (freqCounter[val]) return true
    freqCounter[val] = (freqCounter[val] || 0) + 1
  }

  return false
}
```

</p>
</details>

---

<div align="center">

#### Multiple Pointers

</div>

---

##### 5. Решите задачу с помощью алгоритма Multiple Pointers
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

Сложность: O(N log N).

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

<details><summary><b>Решение 3</b></summary>
<p>

```javascript
function areThereDuplicates() {
  return new Set(arguments).size !== arguments.length
}
```

</p>
</details>

---

##### 6. Решите задачу не превышая сложность O(N)
Напишите фукнцию, которая принимает отсортированный массив чисел `numbers`. Функция должна найти и вернуть первую пару чисел, сумма которых равна нулю.

```javascript
function sumZero(numbers) {}

sumZero([-3, -2, -1, 0, 1, 2, 3])     // [-3, 3]
sumZero([-2, 0, 1, 3])                // undefined
sumZero([1, 2, 3])                    // undefined
```

<details><summary><b>Неоптимальное решение через вложенный цикл</b></summary>
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

<details><summary><b>Решение с помощью алгоритма Multiple Pointers</b></summary>
<p>

Сложность: O(N)

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

##### 7. Решите задачу не превышая сложность O(N)
Напишите функцию, которая принимает отсортированный массив чисел и возвращает число уникальных чисел в массиве.

```javascript
countUniqueValues([1, 1, 1, 2, 2])                  // 2, уникальные числа — 1, 2
countUniqueValues([-3, -2, -2, 0, 1, 1, 2, 3, 3])   // 6
countUniqueValues([])                               // 0
```

<details><summary><b>Решение 1 (Multiple Pointers)</b></summary>
<p>

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

<details><summary><b>Решение 2 (Multiple Pointers)</b></summary>
<p>

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

##### 8. Решите задачу не превышая сложности O(N)
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
* **Алгоритм**: Multiple Pointers

```javascript
function averagePair(arr, val) {
  let left = 0
  let right = arr.length - 1

  while (left < right) {
    let average = (arr[left] + arr[right]) / 2

    if (average === val) return true
    else if (average < val) left++
    else right++
  }

  return false
}
```

</p>
</details>

---

##### 9. Решите задачу используя алгоритм Multiple Pointers
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
* **Алгоритм**: Multiple Pointers

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
