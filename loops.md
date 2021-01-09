<div align="center">

<h1>Задачи по Javascript: Циклы, рекурсии</h1>

<a href="https://github.com/dollaween/javascript-tasks">На главную</a> | <a href="https://github.com/dollaween/javascript-questions">Вопросы</a> | <a href="https://github.com/dollaween/javascript-tests">Тесты</a>

</div>

---

##### 1. Напишите рекурсивную функцию обхода дерева объектов
Функция должна обойти каждый объект в дереве объектов и вывести его `title` в консоль.

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
Функция должна вернуть массив с `title` каждого элемента дерева.

```javascript
const result = treeTraversal(tree)
console.log(result)
// => [ 'A', 'B', 'C', 'D', 'E', 'F' ]
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
  let output = [node.title]

  if (node.children) {
    node.children.forEach((child) => {
      output = [...output, ...treeTraversal(child)]
    })
  }

  return output
}

const result = treeTraversal(tree)
console.log(result)
```

</p>
</details>
