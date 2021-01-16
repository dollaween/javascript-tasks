<div align="center">

# Задачи по тестированию на Jest

[Вопросы](https://github.com/dollaween/javascript-questions)
|
[Тесты](https://github.com/dollaween/javascript-tests)
|
[Задачи](https://github.com/dollaween/javascript-tasks)

</div>

---

**Цель задач:** Практика применения инструмента тестирования Jest

---

##### 1. Напишите валидные тесты

```javascript
const str1 = 'Another great day'
const str2 = str1
const str3 = 'Another great week'

it('str1 should equal str2', () => {})
it('str1 should not equal str3', () => {})
```

<details><summary><b>Решение</b></summary>
<p>

```javascript
const str1 = 'Another great day'
const str2 = str1
const str3 = 'Another great week'

it('str1 should equal str2', () => {
  expect(str1).toBe(str2)
})

it('str1 should equal str3', () => {
  expect(str1).not.toBe(str3)
})
```

</p>
</details>

---

##### 2. Напишите валидные тесты

```javascript
const str1 = 'Rainy day'
const str2 = 'day'

it('str1 should contain str2', () => {})
it('str2 should not contain str1', () => {})
```

<details><summary><b>Решение</b></summary>
<p>

```javascript
const str1 = 'Rainy day'
const str2 = 'day'

it('str1 should contain str2', () => {
  expect(str1).toEqual(expect.stringContaining(str2))
})

it('str2 should not contain str1', () => {
  expect(str2).toEqual(expect.not.stringContaining(str1))
})
```

</p>
</details>
