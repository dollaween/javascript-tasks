<div align="center">

# Задачи по алгоритму Frequency counter

[Вопросы](https://github.com/dollaween/javascript-questions)
|
[Тесты](https://github.com/dollaween/javascript-tests)
|
[Задачи](https://github.com/dollaween/javascript-tasks)

</div>

---

**Цель задач:** Практика применения алгоритма Frequency counter.

---

##### 1. Решите задачу с помощью алгоритма Frequency counter
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

##### 2. Решите задачу с помощью алгоритма Frequency counter
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

##### 4. Решите задачу с помощью алгоритма Frequency counter
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

##### 5. Решите задачу с помощью алгоритма Frequency counter
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
