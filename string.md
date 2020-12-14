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

##### 2. Валидные скобки
Напишите функцию, которая принимает скобки и определяет валидность порядка скобок.

```javascript
"()"              =>  true
")(()))"          =>  false
"("               =>  false
"(())((()())())"  =>  true
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
