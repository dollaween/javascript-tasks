<div align="center">

<h1>Задачи по Javascript: Циклы, рекурсии</h1>

<a href="https://github.com/dollaween/javascript-questions">Вопросы</a> | <a href="https://github.com/dollaween/javascript-tests">Тесты</a> | <a href="https://github.com/dollaween/javascript-tasks">Задачи</a>

</div>

---

##### 1. Выведите в консоль первый символ строки

<details><summary><b>Решение</b></summary>
<p>

```javascript
const str = 'My string'
console.log(str[0])
console.log(str.charAt(0))
```

</p>
</details>

---

##### 2. Выведите в консоль `true`, если в строке есть указанный символ

```javascript
const str = 'My string'
let char = 's'

console.log(/* code... */)
// true

char = 'd'
console.log(/* code... */)
// false
```

<details><summary><b>Решение</b></summary>
<p>

```javascript
str.includes(str, char)
```

</p>
</details>
