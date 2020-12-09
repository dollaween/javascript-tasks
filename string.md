\<div align="center">

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
```

</p>
</details>

---
