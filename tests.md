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

---

##### 5. Напишите валидные тесты

```javascript
const arr1 = [1, 2, 3, 4, 5]
const arr2 = [1, 2, 3, 4, 5]
const arr3 = [3, 4]

it('arr1 should be equal arr2', () => {})
it('arr1 should not be equal arr3', () => {})
it('arr1 should contain arr3', () => {})
it('arr3 should not contain arr1', () => {})
```

<details><summary><b>Решение</b></summary>
<p>

```javascript
const arr1 = [1, 2, 3, 4, 5]
const arr2 = [1, 2, 3, 4, 5]
const arr3 = [3, 4]

it('arr1 should be equal arr2', () => {
  expect(arr1).toEqual(arr2)
})

it('arr1 should not be equal arr3', () => {
  expect(arr1).not.toEqual(arr3)
})

it('arr1 should contain arr3', () => {
  expect(arr1).toEqual(expect.arrayContaining(arr3))
})

it('arr3 should not contain arr1', () => {
  expect(arr3).not.toEqual(expect.arrayContaining(arr1))
})
```

</p>
</details>

---

##### 6. Напишите валидные тесты

```javascript
const good1 = { title: 'shirt', color: 'blue' }
const good2 = { title: 'shirt', color: 'blue' }
const good3 = { title: 'shirt' }

it('good1 should be equal good2', () => {})
it('good1 should contain good3', () => {})
it('good3 should not contain good1', () => {})
```

<details><summary><b>Решение</b></summary>
<p>

```javascript
const good1 = { title: 'shirt', color: 'blue' }
const good2 = { title: 'shirt', color: 'blue' }
const good3 = { title: 'shirt' }

it('good1 should be equal good2', () => {
  expect(good1).toEqual(good2)
})

it('good1 should contain good3', () => {
  expect(good1).toEqual(expect.objectContaining(good3))
})

it('good3 should not contain good1', () => {
  expect(good3).not.toEqual(expect.objectContaining(good1))
})
```

</p>
</details>

---

##### 7. Напишите валидные тесты

```javascript
const house = {
  forSale: true,
  rooms: 5,
  bedroom: {
    area: 24,
    wallColor: ['white', 'grey', 'red'],
    'ceiling.height': 3
  },
  'wall.type': 'wood'
}

it('house should have property forSale', () => {})
it('house should have property wall.type', () => {})
it('house should have property rooms and it should be equal 5', () => {})
it('bedroom should have area equals 24', () => {})
it('bedroom should have ceiling.height equals 3', () => {})
it('bedroom should have wallColor equal ["white", "grey", "red"]', () => {})
```

<details><summary><b>Решение</b></summary>
<p>

```javascript
const house = {
  forSale: true,
  rooms: 5,
  bedroom: {
    area: 24,
    wallColor: ['white', 'grey', 'red'],
    'ceiling.height': 3
  },
  'wall.type': 'wood'
}

it('house should have property forSale', () => {
  expect(house).toHaveProperty('forSale')
})

it('house should have property wall.type', () => {
  expect(house).toHaveProperty(['wall.type'])
})

it('house should have property rooms and it should be equal 5', () => {
  expect(house).toHaveProperty('rooms', 5)
})

it('bedroom should have area equals 24', () => {
  expect(house).toHaveProperty('bedroom.area', 24)
  expect(house).toHaveProperty(['bedroom', 'area'], 24)
})

it('bedroom should have ceiling.height equals 3', () => {
  expect(house).toHaveProperty(['bedroom', 'ceiling.height'], 3)
})

it('bedroom should have wallColor equal ["white", "grey", "red"]', () => {
  expect(house).toHaveProperty('bedroom.wallColor', ['white', 'grey', 'red'])
})
```

</p>
</details>

---

##### 8. Напишите валидные тесты
Проверьте, что функция `getSomething` вообще хоть что-то возвращает (не обязательно `true`), а функция `emptyFunc` не возвращает ничего.

```javascript
const getSomething = () => true
const emptyFunc = () => {}

it('getSomething should return something', () => {})
it('emptyFunc should not return anything', () => {})
```

<details><summary><b>Решение</b></summary>
<p>

```javascript
const getSomething = () => true
const emptyFunc = () => {}

it('getSomething should return something', () => {
  expect(getSomething()).toBeDefined()
})

it('emptyFunc should not return anything', () => {
  expect(emptyFunc()).not.toBeDefined()
})
```

</p>
</details>
