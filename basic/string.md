<div align="center">

# Базовые задачи по строкам

[Вопросы](https://github.com/dollaween/javascript-questions)
|
[Тесты](https://github.com/dollaween/javascript-tests)
|
[Задачи](https://github.com/dollaween/javascript-tasks)

</div>

---

<div align="center">

### Поиск по строкам

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

##### 2. Выведите в консоль последний символ строки

<details><summary><b>Решение</b></summary>
<p>

```javascript
const str = 'My string'
console.log(str[str.length - 1])
```

</p>
</details>

---

##### 3. Выведите в консоль `true`, если в строке есть указанный символ

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

---

##### 4. Выведите в консоль индекс первого вхождения указанного символа/слова

```javascript
const str = 'After a storm comes a calm'

let char = 'r'
console.log(/* code... */)
// 4

let word = 'storm'
console.log(/* code... */)
// 8
```

<details><summary><b>Решение</b></summary>
<p>

```javascript
str.indexOf(char)
str.indexOf(word)
```

</p>
</details>
