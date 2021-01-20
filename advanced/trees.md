<div align="center">

# Задачи по дереву объектов

[Вопросы](https://github.com/dollaween/javascript-questions)
|
[Тесты](https://github.com/dollaween/javascript-tests)
|
[Задачи](https://github.com/dollaween/javascript-tasks)

</div>

---

**Цель задач:** Практика применения алгоритмов поиска и изменения деревьев объектов

Для решения этих задач нужно разбираться в:
* Рекурсии
* Breadth First Search
* Depth First Search

---

##### 1. Breadth First Search
Напишите функцию, которая принимает дерево объектов (или массив деревьев) и id искомого объекта. Функция должна проходить по дереву алгоритмом Breadth First Search и возвращать искомый объект, или `undefined`, если объект не найден. Каждый проходимый элемент должен быть выведен в консоль.

```javascript
function BFS(tree, target) {}

BFS(tree, 7)
// Current node is: 0
// Current node is: 12
// Current node is: 1
// Current node is: 6
// Current node is: 7
// { id: 7 }
```

<details><summary><b>Исходные данные</b></summary>
<p>

```javascript
const tree = [{
  id: 0,
  children: [
    {
      id: 1,
      children: [
        { id: 2 },
        { id: 3 },
        {
          id: 4,
          children: [
            { id: 5 }
          ]
        }
      ]
    },
    { id: 6 },
    { id: 7 },
    {
      id: 8,
      children: [
        { id: 9 },
        { id: 10 },
        { id: 11 }
      ]
    }
  ]
}, {
  id: 12
}]
```

</p>
</details>

<details><summary><b>Решение</b></summary>
<p>

```javascript
function BFS(tree, target) {
  let queue = []

  Array.isArray(tree)
    ? tree.forEach((child) => queue.push(child))
    : queue.push(tree)

  while(queue.length > 0) {
    let currentNode = queue[0]
    console.log('Current node is: ' + currentNode.id)

    if (currentNode.id === target) {
      console.log('Finded!')
      return currentNode
    }

    if (currentNode.children) {
      currentNode.children.forEach((child) => {
        queue.push(child)
      })
    }

    queue.shift()
  }

  console.log('Not found')
  return
}
```

</p>
</details>
