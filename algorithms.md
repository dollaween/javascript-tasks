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

##### 4.
Напишите функцию, которая принимает два массива чисел и возвращает true, если второй массив содержит те же числа, но в квадрате (порядок чисел значения не имеет).

Сложность решения не должна превышать O(N).

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
