<div align="center">

<h1>Задачи по Javascript: String</h1>

<a href="https://github.com/dollaween/javascript-tasks">На главную</a> | <a href="https://github.com/dollaween/javascript-questions">Вопросы</a> | <a href="https://github.com/dollaween/javascript-tests">Тесты</a>

</div>

---

##### 1. Переставьте слова местами
```javascript
function rearrangeWords(str) {
  /** ВАШ КОД */
}
rearrangeWords('Bruce Willis')
```
**Результат**
```bash
Willis Bruce
```

<details><summary><b>Решение 1</b></summary>
<p>

```javascript
function rearrangeWords(str) {
  return str.split(' ').reverse().join(' ')
}
```

</p>
</details>

<details><summary><b>Решение 2</b></summary>
<p>

```javascript
function rearrangeWords(str) {
  return str.replace(/(Bruce) (Willis)/, '$2 $1')
}
function rearrangeWords(str) {
  return str.replace(/[A-Za-z]*[A-Za-z]*/, '$2 $1')
}
```

</p>
</details>

---

##### 2. Замените все слова другим словом
Замените все слова в предложении словом 'wrond'. Знаки препинания оставьте без изменений.

```javascript
replaceWords('Hello world, чудесный новый мир!')
// => wrong wrong, wrong wrong wrong!
```

<details><summary><b>Решение</b></summary>
<p>

```javascript
function replaceWords(str) {
  // Достаем слова целиком
  const regExp = /(\w+|[А-Яа-я]+)/g
  const res = str.replace(regExp, 'wrong')
}
```

</p>
</details>

---


##### 3. Неправильная латиница
Передвиньте первую букву в конец слова и добавьте 'ay' после нее. Знаки препинания оставьте нетронутыми.

```javascript
wrongLatin('Wrong latin is cool')
// => rongWay atinlay siay oolcay

wrongLatin('Hello world !')
// => elloHay orldway !
```

<details><summary><b>Решение 1</b></summary>
<p>

```javascript
function wrongLatin(str){
  return str.replace(/(\w)(\w*)(\s|$)/g, "\$2\$1ay\$3")
}
```

</p>
</details>

<details><summary><b>Решение 2</b></summary>
<p>

```javascript
function wrongLatin(str) {
  return str.replace(/\w+/g, (w) => {
    return w.slice(1) + w[0] + 'ay';
  });
}
```

</p>
</details>

---

##### 4. Валидные скобки
Напишите функцию, которая принимает скобки и определяет валидность порядка скобок.

```javascript
"()"              // =>  true
")(()))"          // =>  false
"("               // =>  false
"(())((()())())"  // =>  true
```

<details><summary><b>Решение 1</b></summary>
<p>

```javascript
function validParentheses(parens){
  var n = 0;
  for (var i = 0; i < parens.length; i++) {
    if (parens[i] == '(') n++;
    if (parens[i] == ')') n--;
    if (n < 0) return false;
  }
  
  return n == 0;
}
```

</p>
</details>

<details><summary><b>Решение 2</b></summary>
<p>

```javascript
function validParentheses(parens){
  var indent = 0;
  
  for (var i = 0 ; i < parens.length && indent >= 0; i++) {
    indent += (parens[i] == '(') ? 1 : -1;    
  }
  
  return (indent == 0);
}
```

</p>
</details>

*Источник: Codewars*

---

##### 5. Является ли строка A анаграммой строки B?

```javascript
anagram('friend', 'finder')                       // => true
anagram('hello', 'bye')                           // => false
anagram('Eleven, plus two', 'Twelve plus one!')   // => true
anagram('Аз есмь строка, живу я, мерой остр', 'За семь морей ростка я вижу рост')   // => true
```

<details><summary><b>Решение 1</b></summary>
<p>

```javascript
function cleanString(str) {
  return str
    .replace(/[^\wА-я]/g, '')
    .toLowerCase()
    .split('')
    .sort()
    .join('');
}

function anagram(strA, strB) {
  return cleanString(strA) === cleanString(strB);
}
```

</p>
</details>

<details><summary><b>Решение 2</b></summary>
<p>

```javascript
function buildCharObj(str) {
  const charObj = {};
  str = str.replace(/[^\wА-я+]/g, '').toLowerCase();
  for (let char of str) {
    charObj[char] = charObj[char] + 1 || 1;
  }
  return charObj;
}

function anagram(strA, strB) {
  const aCharObj = buildCharObj(strA);
  const bCharObj = buildCharObj(strB);

  if (Object.keys(aCharObj).length !== Object.keys(bCharObj).length) {
    return false;
  }

  for (let char in aCharObj) {
    if (aCharObj[char] !== bCharObj[char]) {
      return false;
    }
  }

  return true;
}
```

</p>
</details>
