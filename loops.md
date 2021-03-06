<div align="center">

<h1>Задачи по Javascript: Циклы, рекурсии</h1>

<a href="https://github.com/dollaween/javascript-tasks">На главную</a> | <a href="https://github.com/dollaween/javascript-questions">Вопросы</a> | <a href="https://github.com/dollaween/javascript-tests">Тесты</a>

</div>

---

##### 1. Напишите рекурсивную функцию обхода дерева объектов
Функция должна обойти каждый элемент в дереве объектов и вывести его `title` в консоль.

```javascript
treeTraversal(tree)
// => A
// => B
// => C
// => D
// => E
// => F
```

<details><summary><b>Исходные данные</b></summary>
<p>

```javascript
const tree = {
  title: 'A',
  children: [
    {
      title: 'B',
      children: [
        {
          title: 'C'
        },
        {
          title: 'D'
        },
        {
          title: 'E'
        }
      ]
    },
    {
      title: 'F'
    }
  ]
}
```

</p>
</details>

<details><summary><b>Решение</b></summary>
<p>

```javascript
function treeTraversal(node) {
  console.log(node.title)

  if (node.children) {
    node.children.forEach((child) => {
      treeTraversal(child)
    })
  }
}

treeTraversal(tree)
```

</p>
</details>

---

##### 2. Напишите рекурсивную функцию обхода дерева объектов
Функция должна вернуть массив объектов, содержащих `title` и уровень вложенности каждого элемента дерева.

```javascript
const result = treeTraversal(tree)
console.log(result)
// [
//   { title: 'A', nesting: 0 },
//   { title: 'B', nesting: 1 },
//   { title: 'C', nesting: 2 },
//   { title: 'D', nesting: 2 },
//   { title: 'E', nesting: 2 },
//   { title: 'F', nesting: 1 }
// ]
```

<details><summary><b>Исходные данные</b></summary>
<p>

```javascript
const tree = {
  title: 'A',
  children: [
    {
      title: 'B',
      children: [
        {
          title: 'C'
        },
        {
          title: 'D'
        },
        {
          title: 'E'
        }
      ]
    },
    {
      title: 'F'
    }
  ]
}
```

</p>
</details>

<details><summary><b>Решение</b></summary>
<p>

```javascript
function treeTraversal(node, nesting = 0) {
  let output = [{ title: node.title, nesting: nesting++ }]

  if (node.children) {
    node.children.forEach((child) => {
      output = [...output, ...treeTraversal(child, nesting)]
    })
  }

  return output
}

const result = treeTraversal(tree)
console.log(result)
```

</p>
</details>

---

##### 3. Напишите рекурсивную функцию, которая будет возвращать элемент дерева с указанным `id`
Функция должна вернуть объект элемента дерева.

```javascript
const id = 5
const result = treeTraversal(tree, id)
console.log(result)
// => { id: 5, title: 'E' }
```

<details><summary><b>Исходные данные</b></summary>
<p>

```javascript
const tree = {
  id: 1,
  title: 'A',
  children: [
    {
      id: 2,
      title: 'B',
      children: [
        {
          id: 3,
          title: 'C'
        },
        {
          id: 4,
          title: 'D'
        },
        {
          id: 5,
          title: 'E'
        }
      ]
    },
    {
      id: 6,
      title: 'F'
    }
  ]
}
```

</p>
</details>

<details><summary><b>Решение</b></summary>
<p>

```javascript
function treeTraversal(node, target) {
  if (node.id === target) {
    return node
  }

  let targetNode;

  if (node.children) {
    node.children.some((child) => {
      const result = treeTraversal(child, target)
      if (result) {
        return targetNode = result
      }
    })
  }

  return targetNode
}

const result = treeTraversal(tree, 5)
console.log(result)
```

</p>
</details>

---

##### 4. Напишите рекурсивную функцию, которая будет возвращать родительский элемент элемента с указанным `id`
Функция должна вернуть родительский элемент объекта.

```javascript
let result = treeTraversal(tree, 4)
console.log(result)
// {
//   id: 2,
//   title: 'B',
//   children: [
//     { id: 3, title: 'C' },
//     { id: 4, title: 'D', children: [Array] },
//     { id: 5, title: 'E' }
//   ]
// }

result = treeTraversal(tree, 7)
console.log(result)
// => { id: 4, title: 'D', children: [ { id: 7, title: 'G' } ] }
```

<details><summary><b>Исходные данные</b></summary>
<p>

```javascript
const tree = {
  id: 1,
  title: 'A',
  children: [
    {
      id: 2,
      title: 'B',
      children: [
        {
          id: 3,
          title: 'C'
        },
        {
          id: 4,
          title: 'D',
          children: [
            {
              id: 7,
              title: 'G'
            }
          ]
        },
        {
          id: 5,
          title: 'E'
        }
      ]
    },
    {
      id: 6,
      title: 'F'
    }
  ]
}
```

</p>
</details>

<details><summary><b>Решение</b></summary>
<p>

```javascript
function treeTraversal(node, target, parent) {
  if (node.id === target) {
    return parent
  }

  let targetNode;

  if (node.children) {
    node.children.some((child) => {
      const result = treeTraversal(child, target, node)
      if (result) {
        return targetNode = result
      }
    })
  }

  return targetNode
}

const result = treeTraversal(tree, 7)
console.log(result)
```

</p>
</details>

---

##### 5. Напишите рекурсивную функцию, которая будет возвращать всю цепь `id` элементов от начала до указанного
Функция должна вернуть строку с `id` от рутового объекта до указанного.

```javascript
let result = treeTraversal(tree, 5)
console.log(result)
// => '1 -> 2 -> 5'

result = treeTraversal(tree, 7)
console.log(result)
// => '1 -> 2 -> 4 -> 7'
```

<details><summary><b>Исходные данные</b></summary>
<p>

```javascript
const tree = {
  id: 1,
  title: 'A',
  children: [
    {
      id: 2,
      title: 'B',
      children: [
        {
          id: 3,
          title: 'C'
        },
        {
          id: 4,
          title: 'D',
          children: [
            {
              id: 7,
              title: 'G'
            }
          ]
        },
        {
          id: 5,
          title: 'E'
        }
      ]
    },
    {
      id: 6,
      title: 'F'
    }
  ]
}
```

</p>
</details>

<details><summary><b>Решение</b></summary>
<p>

```javascript
function treeTraversal(node, target) {
  if (node.id === target) {
    return node.id
  }

  let targetNode;

  if (node.children) {
    node.children.some((child) => {
      const result = treeTraversal(child, target)
      if (result) {
        return targetNode = node.id + ' -> ' + result
      }
    })
  }

  return targetNode
}

const result = treeTraversal(tree, 4)
console.log(result)
```

</p>
</details>

---

##### 6. Сумма всех чисел
Напишите функцию, которая принимает число и возвращает сумму всех чисел от 1 до переданного числа.

Например, `sumNumbers(3)` вернет `6`, так как `1 + 2 + 3 = 6`.

```javascript
const result = sumNumbers(5)
console.log(result)
// => 15
```

<details><summary><b>Решение через рекурсию</b></summary>
<p>

```javascript
function sumNumbers(num) {
  if (num === 1) return 1

  return num + sumNumbers(num - 1)
}

const result = sumNumbers(5)
console.log(result)
```

</p>
</details>

<details><summary><b>Математическое решение</b></summary>
<p>

```javascript
function sumNumbers(num) {
  return num * (num + 1) / 2
}

const result = sumNumbers(5)
console.log(result)
```

</p>
</details>

---

##### 7. Возведение в степень
Напишите рекурсивную функцию, которая будет возводить число `base` в степень `exponent`. Если степень 0 — верните `1`.

```javascript
function power(base, exponent) {}

power(2, 4)     // => 16
power(2, 3)     // => 8
power(2, 2)     // => 4
power(2, 1)     // => 2
power(2, 0)     // => 1
```

<details><summary><b>Решение</b></summary>
<p>

```javascript
function power(base, exponent) {
  if (exponent < 1) return 1

  return base * power(base, exponent - 1)
}

const result = power(2, 4)
console.log(result)
```

</p>
</details>

---

##### 8. Вычислите факториал
Напишите рекурсивную функцию, которая будет вычислять факториал числа `num`. Факториал числа 1 — `1`.

```javascript
function factorial(num) {}

factorial(5)     // 5 * 4 * 3 * 2 * 1 === 120
factorial(7)     // 5040
```

<details><summary><b>Решение через цикл</b></summary>
<p>

```javascript
function factorial(num) {
  let total = 1

  for (let i = num; i > 0; i--) {
    total *= i
  }

  return total
}
```

</p>
</details>

<details><summary><b>Решение</b></summary>
<p>

```javascript
function factorial(num) {
  if (num < 1) return 1

  return num * factorial(num - 1)
}
```

</p>
</details>

---

##### 9. Поиск примитивного значения в объекте
Напишите рекурсивную функцию, которая принимает объект `obj` и примитивное значение `value`, и возвращает `true`, если объект содержит в себе переданное значение.

```javascript
function contains(obj, value) {}

const nestedObject = {
  data: {
    info: {
      person: {
        name: 'Andrew',
        age: 22
      }
    }
  }
}

contains(nestedObject, 22)            // true
contains(nestedObject, 'Andrew')      // true
contains(nestedObject, 'something')   // false
```

<details><summary><b>Решение</b></summary>
<p>

```javascript
function contains(obj, value) {
  for (key in obj) {
    if (obj[key] === value) {
      return true
    }
    if (typeof obj[key] === 'object') {
      return contains(obj[key], value)
    }
  }
  return false
}

const result = contains(nestedObject, 22)
console.log(result)
```

</p>
</details>

---

##### 10. Посчитайте количество чисел в массиве
Напишите рекурсивную функцию, которая принимает массив `array` и возвращает общее количество целых чисел хранящихся в нем и его вложенных массивах.

```javascript
function totalIntegers(array) {}

const array = [[[6, 12, 3], [4, 'next']], 9, 'some', [100, 'bar', [[56]]]]

totalIntegers(array)
// => 7
```

<details><summary><b>Решение</b></summary>
<p>

```javascript
function totalIntegers(array) {
  if (array.length === 0) return 0

  let total = 0
  let first = array.shift()

  if (Array.isArray(first)) {
    total += totalIntegers(first)
  } else if (Number.isInteger(first)) {
    total += 1
  }

  return total + totalIntegers(array)
}

const result = totalIntegers(array)
console.log(result)
```

</p>
</details>

---

##### 11. Найдите наибольший общий делитель двух положительных чисел
Напишите рекурсивную функцию, которая принимает два положительных числа и возвращает наибольший общий делитель.

```javascript
gcd(140, 120)
// => 20
```

<details><summary><b>Решение</b></summary>
<p>

```javascript
function gcd(a, b) {
  if (!b) return a

  return gcd(b, a % b)
}

const result = gcd(140, 130)
console.log(result)
```

</p>
</details>

---

##### 12. Выведите диапазон чисел между указанными числами
Напишите рекурсивную функцию, которая принимает два числа и возвращает массив целых чисел между ними.

```javascript
range(1, 9)
// => [2, 3, 4, 5, 6, 7, 8]
```

<details><summary><b>Решение</b></summary>
<p>

```javascript
function range(cur, end) {
  if (end <= cur + 1) return []

  let list = range(cur, end - 1)
  list.push(end - 1)

  return list
}

const result = range(1, 9)
console.log(result)
```

</p>
</details>

---

##### 13. Вычислите сумму чисел всех элементов массива
Напишите рекурсивную функцию, которая принимает массив чисел и возвращает их сумму.

```javascript
sumNumbers([1, 2, 3, 4, 5])
// => 15
```

<details><summary><b>Решение</b></summary>
<p>

```javascript
function sumNumbers(arr) {
  if (arr.length === 1) return arr[0]
  return arr.shift() + sumNumbers(arr)
}

const result = sumNumbers([1, 2, 3, 4, 5])
console.log(result)
```

</p>
</details>

---

##### 14. Напишите функцию, которая возвращает n-ую запись в последовательности Фибоначчи

Последовательность Фибоначчи — это ряд чисел, где каждое последующее является суммой двух предыдущих. Первые десять чисел: `[0, 1, 1, 2, 3, 5, 8, 13, 21, 34]`.

```javascript
fibonacci(3)    // 2
fibonacci(9)    // 34
```

<details><summary><b>Подсказка</b></summary>
<p>

Создайте массив состоящий из первых двух чисел последовательности Фибоначчи. При помощи цикла от 2 до N (нужное значение) в каждой итерации добавляйте в конец массива число, равное сумме двух последних чисел массива.

</p>
</details>

<details><summary><b>Решение циклом</b></summary>
<p>

```javascript
function fibonacci(num) {
  const result = [0, 1]

  for (let i = 2; i <= num; i++) {
    result.push(result[i - 1] + result[i - 2])
  }

  return result[num]
}
```

</p>
</details>

<details><summary><b>Решение рекурсией</b></summary>
<p>

Работает очень медленно:

```javascript
function fibonacci(num) {
  if (num < 2) {
    return num
  }
  return fibonacci(num - 1) + fibonacci(num - 2)
}
```

</p>
</details>

---

##### 15. Сложение цифр числа
Напишите функцию, которая принимает число и складывает все цифры в числе до тех пор, пока не останется одна цифра.

```javascript
function digitsSum(num) {}

digitsSum(89)
// 89 => 8 + 9 = 17
//    => 1 + 7 = 8
//    => 8

digitsSum(84712)
// 84712 => 8 + 4 + 7 + 1 + 2 = 22
//       => 2 + 2 = 4
//       => 4
```

<details><summary><b>Решение циклом</b></summary>
<p>

```javascript
function digitsSum(num) {
  let nums = num.toString().split('')

  while (nums.length > 1) {
    nums = nums
      .reduce((acc, cur) => acc + Number(cur), 0)
      .toString()
      .split('')
  }

  return Number(nums[0])
}
```

</p>
</details>

<details><summary><b>Решение рекурсией</b></summary>
<p>

```javascript
function digitsSum(num) {
  const nums = num.toString().split('')

  const res = nums.reduce((acc, cur) => acc + Number(cur), 0)

  return res >= 10
    ? getSum(res)
    : res
}
```

</p>
</details>
