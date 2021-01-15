<div align="center">

<h1>Задачи по Javascript: Регулярные выражения</h1>

<a href="https://github.com/dollaween/javascript-tasks">На главную</a> | <a href="https://github.com/dollaween/javascript-questions">Вопросы</a> | <a href="https://github.com/dollaween/javascript-tests">Тесты</a>

</div>

---

##### 1. Выберите только буквы (включая русские) и пробелы

<details><summary><b>Решение</b></summary>
<p>

```javascript
/[A-Za-zА-я\s]/g
```

</p>
</details>

---

##### 2. Выберите только цифры

<details><summary><b>Решение</b></summary>
<p>

```javascript
/\d/g
```

</p>
</details>

---

##### 3. Выберите все, кроме букв (включая русские) и цифр

<details><summary><b>Решение</b></summary>
<p>

```javascript
/[^\A-Za-zА-я0-9+]/g

// В состав \w и A-z входит нижнее подчеркивание, поэтому пишем A-Za-z
```

</p>
</details>

---

##### 4. Напишите функцию, которая убирает из строки все символы, кроме букв, цифр, пробелов, запятой и точки

```javascript
cleanString('Восхитительная весна$, а следом — лето. (And we go again 123 :()')
// => Восхитительная весна, а следом  лето. And we go again 123
```

<details><summary><b>Решение</b></summary>
<p>

```javascript
function cleanString(str) {
  return str.replace(/[^\wА-я,.\s]/g, '')
}
```

</p>
</details>

---

##### 5. Напишите функцию, которая заменяет два и более пробелов подряд одним пробелом

```javascript
removeExtraSpaces('Matches between  one   and unlimited     times')
// => Matches between one and unlimited times
```

<details><summary><b>Решение</b></summary>
<p>

```javascript
function removeExtraSpaces(str) {
  return str.replace(/\s\s+/g, ' ');
}
```

</p>
</details>

---

##### 6. Напишите функцию, которая заменяет два и более подряд идущих одинаковых символов одним символом

```javascript
removeExtraSymbols('Heeere we goo aaagain...')
// => 'Here we go again.'
```

<details><summary><b>Решение</b></summary>
<p>

```javascript
function removeExtraSymbols(str) {
  return str.replace(/(.)\1+/g, (_, sym) => sym)
}
```

</p>
</details>

---

##### 7. Парсинг чисел
Напишите функцию, принимающую строку и возвращающую массив чисел из этой строки. Отрицательные и дробные числа (через точку) должны быть в итоговом варианте.

```javascript
getNumbers('1.5 0, -12. NaN 123.4. 70-50')
// => ["1.5", "0", "-12", "123.4", "70", "-50"]
```

<details><summary><b>Решение</b></summary>
<p>

```javascript
function getNumbers(str) {
  return str.match(/-?\d+(\.\d+)?/g)
}
```

</p>
</details>

---

##### 8. Уберите из строки все теги

```javascript
cleanString('<prod><name>drill</name><prx>99</prx><qty>5</qty></prod>')
// => drill 99 5
```

<details><summary><b>Решение</b></summary>
<p>

```javascript
function cleanString(str) {
  return str.replace(/<.*?>/g, ' ').trim()
}
```

</p>
</details>

---

Ссылки:
* [Регулярные выражения](https://learn.javascript.ru/regular-expressions)
