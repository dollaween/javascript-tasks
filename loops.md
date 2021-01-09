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
