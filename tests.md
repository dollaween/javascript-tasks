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

it('str1 should not equal str3', () => {
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

---

##### 3. Напишите валидный тест

```javascript
const num1 = 0.1
const num2 = 0.2

it('expression num1 + num2 should be equal 0.3', () => {})
```

<details><summary><b>Решение</b></summary>
<p>

Для float-чисел вместо `.toBe` нужно использовать `.toBeCloseTo`.

```javascript
const num1 = 0.1
const num2 = 0.2

it('expression num1 + num2 should be equal 0.3', () => {
  expect(num1 + num2).toBeCloseTo(0.3)
})
```

</p>
</details>

---

##### 4. Напишите валидные тесты

```javascript
const str = 'Pink clouds'
const arr = [1, 2, 3]

it('length of str should be 11', () => {})
it('length of arr should be 3', () => {})
```

<details><summary><b>Решение</b></summary>
<p>

```javascript
const str = 'Pink clouds'
const arr = [1, 2, 3]

it('length of str should be 11', () => {
  expect(str).toHaveLength(11)
})

it('length of arr should be 3', () => {
  expect(arr).toHaveLength(3)
})
```

</p>
</details>
