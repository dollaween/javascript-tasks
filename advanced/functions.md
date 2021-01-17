<div align="center">

# Продвинутые задачи по функциям

[Вопросы](https://github.com/dollaween/javascript-questions)
|
[Тесты](https://github.com/dollaween/javascript-tests)
|
[Задачи](https://github.com/dollaween/javascript-tasks)

</div>

---

**Цель задач:** Практика манипулирования функциями

---

##### 1. Создание конструктора конструкторов
Напишите функцию, которая возвращает конструктор и удовлетворяет нижеуказанным утверждениям

```javascript
function SomeConstructor() {}

const A = new SomeConstructor()
const B = new A()
const C = new B()
const D = new C()
// и так далее

console.log('B instanceof A (true) =>', B instanceof A)

console.log('C instanceof A (true) =>', C instanceof A)
console.log('C instanceof B (true) =>', C instanceof B)

console.log('D instanceof A (true) =>', D instanceof A)
console.log('D instanceof B (true) =>', D instanceof B)
console.log('D instanceof C (true) =>', D instanceof C)

console.log('---')

console.log('A instanceof B (false) =>', A instanceof B)

console.log('A instanceof C (false) =>', A instanceof C)
console.log('B instanceof C (false) =>', B instanceof C)

console.log('A instanceof D (false) =>', A instanceof D)
console.log('B instanceof D (false) =>', B instanceof D)
console.log('C instanceof D (false) =>', C instanceof D)
```

<details><summary><b>Решение</b></summary>
<p>

```javascript
function SomeConstructor() {
  let lastConstructor = null

  const funcCreator = prototype => {
    const F = function() {
      return funcCreator(lastConstructor)
    }

    Object.setPrototypeOf(F, prototype)
    F.prototype = Object.create(prototype)

    lastConstructor = F.prototype

    return F
  }

  return funcCreator(lastConstructor)
}
```

</p>
</details>
