<div align="center">

# Базовые задачи по строкам

[Вопросы](https://github.com/dollaween/javascript-questions)
|
[Тесты](https://github.com/dollaween/javascript-tests)
|
[Задачи](https://github.com/dollaween/javascript-tasks)

</div>

---

**Цель задач:** Знать о наличии и уметь применять встроенные методы `String`.

Найти все методы можно здесь:
* [MDN. String](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/String)

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
str.includes(char)
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

---

##### 5. Выведите в консоль `true`, если строка начинается со слова `We`

```javascript
const str = 'We rob banks'
console.log(/* code */)
// true
```

<details><summary><b>Решение</b></summary>
<p>

```javascript
console.log(str.startsWith('We'))
```

</p>
</details>

---

##### 6. Выведите в консоль `true`, если строка заканчивается словом `banks`

```javascript
const str = 'We rob banks'
console.log(/* code */)
// true
```

<details><summary><b>Решение</b></summary>
<p>

```javascript
console.log(str.endsWith('banks'))
```

</p>
</details>

---

##### 7. Замена слова в строке
Дана строка `'Jax Briggs'`, замените слово `'Jax'` на `'Jacqui'` и выведите в консоль

<details><summary><b>Решение</b></summary>
<p>

```javascript
const str = 'Jax Briggs';
console.log(str.replace('Jax', 'Jacqui'));
```

</p>
</details>

---

##### 8. Замена всех слов в строке
Дана строка `'Rainy Rainy Rainy'`. Замените все слова на `'Sunny Sunny Sunny'`

<details><summary><b>Решение</b></summary>
<p>

```javascript
const str = 'Rainy Rainy Rainy'
console.log(str.replaceAll('Rainy', 'Sunny'))
```

</p>
</details>

---

##### 9. Извлечение части строки
Дана строка `'Winter is coming'`. С помощью метода `slice`, выведите в консоль слово `'coming'`.

<details><summary><b>Решение</b></summary>
<p>

```javascript
const str = 'Winter is coming'
str.slice(-6)
```

</p>
</details>

---

##### 10. Разбиение строки на массив
Дана строка `'January February March April'`. Разбейте строку на массив слов и выведите в консоль.

<details><summary><b>Решение</b></summary>
<p>

```javascript
const str = 'January February March April'
console.log(str.split(' '))
```

</p>
</details>

---

##### 11. Удаление лишних пробельных символов
Дана строка `'  where is end\r\n'`. Удалите из нее лишние пробельные символы с начала и конца строки.

<details><summary><b>Решение</b></summary>
<p>

```javascript
const str = '  where is end\r\n'
console.log(str.trim())
```

</p>
</details>

---

##### 12. Вывод строки в необработанном виде
Дана строка `'where is\n end'`. Выведите эту строку в консоль в необработанном виде (в данном случае, чтобы не было переносила на вторую строчку)

<details><summary><b>Решение</b></summary>
<p>

```javascript
console.log('where is\\n end')
console.log(String.raw`where is\n end`)
```

</p>
</details>

---

##### 13. Приведение к верхнему регистру первых букв
Дана строка `'snap out of it'`. Выведите эту строку в консоль, приведя первую букву к верхнему регистру.

```javascript
const str = 'snap out of it'
console.log(/* code... */)
// 'Snap out of it'
```

<details><summary><b>Решение</b></summary>
<p>

```javascript
const str = 'snap out of it'
console.log(str[0].toUpperCase() + str.slice(1))
```

</p>
</details>

---

##### 14. Приведение к строке
Дано число `123`. Приведите это число к строке и выведите в консоль

<details><summary><b>Решение</b></summary>
<p>

```javascript
const num = 123
console.log(num.toString())
console.log(num + '')
```

</p>
</details>
