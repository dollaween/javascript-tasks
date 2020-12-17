<div align="center">

<h1>Задачи по Javascript: Условия</h1>

<a href="https://github.com/dollaween/javascript-tasks">На главную</a> | <a href="https://github.com/dollaween/javascript-questions">Вопросы</a> | <a href="https://github.com/dollaween/javascript-tests">Тесты</a>

</div>

---

##### 1. Что будет с моим кошельком?

Напишите функцию, которая вычитает текущий баланс и стоимость товара, и выдает небольшую информацию о балансе.

**Дополнительно:** попробуйте решить задачу без условных конструкций `if ... else`, `switch`, `.. ? .. : ..`.

```javascript
whatWillWithWallet(1000, 200)
// => После покупки баланс будет положительным

whatWillWithWallet(1000, 1500)
// => После покупки баланс будет отрицательным

whatWillWithWallet(1000, 1000)
// => После покупки баланс будет нулевым
```

<details><summary><b>Подсказка</b></summary>
<p>

Попробуйте создать массив с вариантами и использовать `Math.sign`.

</p>
</details>

<details><summary><b>Решение</b></summary>
<p>

```javascript
function whatWillWithWallet(balance, cost) {
  const options = ['отрицательным', 'нулевым', 'положительным']
  const text = options[Math.sign(balance - cost) + 1]
  return `После покупки баланс будет ${text}`
}
```

</p>
</details>

---
