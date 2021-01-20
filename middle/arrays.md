<div align="center">

# Задачи среднего уровня по массивам

[Вопросы](https://github.com/dollaween/javascript-questions)
|
[Тесты](https://github.com/dollaween/javascript-tests)
|
[Задачи](https://github.com/dollaween/javascript-tasks)

</div>

---

##### 1. Извлеките из массива только уникальные значения

```javascript
uniqueValues([1, 1, 2, 3, 4, 2, 3, 7, 5, 5, 7, 8])
// => [1, 2, 3, 4, 7, 5, 8]
```

<details><summary><b>Подсказка</b></summary>
<p>

Попробуйте использовать `new Set()`.

</p>
</details>

<details><summary><b>Решение</b></summary>
<p>

```javascript
function uniqueValues(arr) {
  return [...new Set(arr)]
}
```

</p>
</details>

---

##### 2. Перемешайте элементы в массиве

```javascript
shuffle([1, 2, 3, 4, 5, 6, 7])
// => [6, 4, 1, 7, 5, 2, 3]
```

<details><summary><b>Подсказка</b></summary>
<p>

Попробуйте использовать метод `Array.sort()` и `Math.random()`.

</p>
</details>

<details><summary><b>Решение</b></summary>
<p>

```javascript
function shuffle(arr) {
  return arr.sort(() => Math.random() - 0.5)
}
```

</p>
</details>

---

##### 3. Найдите все анаграммы в строке
Напишите функцию, которая принимает строку и находит все анаграммы в ней. Функция должна вернуть массив, который содержит массивы с анаграммами.

```javascript
function getAnagrams(str) {}

getAnagrams('адрес карм кума мир мука парк рим среда стук рост сорт трос')
// [
//   [ 'адрес', 'среда' ],
//   [ 'кума', 'мука' ],
//   [ 'мир', 'рим' ],
//   [ 'рост', 'сорт', 'трос' ]
// ]
```

<details><summary><b>Решение</b></summary>
<p>

```javascript
function getAnagrams(str) {
  const words = str.split(' ')
  const result = []
  const freqCounter = {}

  function sort(str) {
    return str.split('').sort().join('')
  }

  for (let val of words) {
    freqCounter[sort(val)] = []
  }

  for (let i = 0; i < words.length; i++) {
    let alphabetVal = sort(words[i])
    if (freqCounter[alphabetVal]) {
      freqCounter[alphabetVal].push(words[i])
    }
  }

  for (let val in freqCounter) {
    if (freqCounter[val].length > 1) {
      result.push(freqCounter[val])
    }
  }

  return result
}
```

</p>
</details>
