<div align="center">

<h1>Задачи по Javascript: Алгоритмы</h1>

<a href="https://github.com/dollaween/javascript-tasks">На главную</a> | <a href="https://github.com/dollaween/javascript-questions">Вопросы</a> | <a href="https://github.com/dollaween/javascript-tests">Тесты</a>

</div>

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
  for (let i = 2; i <= n; i*=2) {
    console.log(i)
  }
}
```

</p>
</details>

---

##### 4. Решите задачу не превышая сложность O(N)
Напишите функцию, которая принимает два массива чисел и возвращает true, если второй массив содержит те же числа, но в квадрате (порядок чисел значения не имеет).

```javascript
function same(arr1, arr2) {}

same([1, 2, 3], [4, 1, 9])    // true
same([1, 2, 3], [1, 4])       // false, количество элементов не совпадает
same([1, 2, 1], [4, 4, 1])    // false, должна быть та же частота
```

<details><summary><b>Неоптимальное решение через цикл</b></summary>
<p>

Данное решение неоптимально, так как имеет сложность O(N^2).

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

<details><summary><b>Решение с помощью алгоритма Frequency counter</b></summary>
<p>

Более выгодное решение, имеет сложность O(N).

```javascript
function same (arr1, arr2) {
  if (arr1.length !== arr2.length) {
    return false
  }

  let counter1 = {}
  let counter2 = {}
  for (let val of arr1) {
    counter1[val] = (counter1[val] || 0) + 1
  }
  for (let val of arr2) {
    counter2[val] = (counter2[val] || 0) + 1
  }

  for (let key in counter1) {
    let exponented = key ** 2
    if (!exponented in counter2) {
      return false
    }
    if (counter2[exponented] !== counter1[key]) {
      return false
    }
  }

  return true
}
```

</p>
</details>

---

##### 5. Решите задачу не превышая сложность O(N)
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

<details><summary><b>Неоптимальное решение через вложенные циклы</b></summary>
<p>

Сложность: O(N^2)

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

<details><summary><b>Решение с помощью алгоритма Frequency counter</b></summary>
<p>

Сложность: O(N)

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

##### 6. Решите задачу с помощью алгоритма Frequency counter
Напишите функцию, которая принимает два числа и возвращает `true`, если числа имеют одинаковую частоту цифр.

```javascript
function sameFrequency(num1, num2) {}

sameFrequency(246, 462)       // true
sameFrequency(83965, 35689)   // true
sameFrequency(81, 38)         // false
sameFrequency(11, 111)        // false
```

<details><summary><b>Решение</b></summary>
<p>

Сложность: O(N)

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

##### 7. Решите задачу несколькими способами
Напишите функцию, которая принимает неограниченное количество аргументов и возвращает `false`, если среди аргументов нет повторяющихся.

```javascript
function areThereDuplicates(...args) {}

areThereDuplicates(1, 2, 3)             // false
areThereDuplicates(56, 'some', 'b')     // false
areThereDuplicates(1, 2, 2)             // true
areThereDuplicates('a', 'never', 'a')   // true
```

<details><summary><b>Решение с помощью алгоритма Frequency counter</b></summary>
<p>

Сложность: O(N)

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

<details><summary><b>Решение с помощью алгоритма Multiple Pointers</b></summary>
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

##### 8. 
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
