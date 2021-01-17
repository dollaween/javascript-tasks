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
const str1 = 'Winter is coming'
const str2 = 'Winter is coming'
const str3 = 'is coming'

it('str1 should equal str2', () => {})
it('str1 should not equal str3', () => {})
it('str1 should contain str3', () => {})
it('str3 should not contain str1', () => {})
it('length of str1 should be 11', () => {})
```

<details><summary><b>Решение</b></summary>
<p>

```javascript
const str1 = 'Winter is coming'
const str2 = 'Winter is coming'
const str3 = 'is coming'

it('str1 should equal str2', () => {
  expect(str1).toBe(str2)
})

it('str1 should not equal str3', () => {
  expect(str1).not.toBe(str3)
})

it('str1 should contain str3', () => {
  expect(str1).toContain(str3)
  expect(str1).toMatch(new RegExp(str3))
  expect(str1).toEqual(expect.stringContaining(str3))
})

it('str3 should not contain str1', () => {
  expect(str3).not.toContain(str1)
  expect(str3).not.toMatch(new RegExp(str1))
  expect(str3).not.toEqual(expect.stringContaining(str1))
})

it('length of str1 should be 11', () => {
  expect(str1).toHaveLength(16)
})
```

</p>
</details>

---

##### 2. Напишите валидный тест

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

##### 3. Напишите валидные тесты

```javascript
const arr1 = [1, 2, 3, 4, 5]
const arr2 = [1, 2, 3, 4, 5]
const arr3 = [3, 4]
const num = 5

it('arr1 should be equal arr2', () => {})
it('arr1 should not be equal arr3', () => {})
it('arr1 should contain num', () => {})
it('arr1 should contain arr3', () => {})
it('arr3 should not contain arr1', () => {})
it('length of arr1 should be 5', () => {})
```

<details><summary><b>Решение</b></summary>
<p>

```javascript
const arr1 = [1, 2, 3, 4, 5]
const arr2 = [1, 2, 3, 4, 5]
const arr3 = [3, 4]
const num = 5

it('arr1 should be equal arr2', () => {
  expect(arr1).toEqual(arr2)
  expect(arr1).toMatchObject(arr2)
})

it('arr1 should not be equal arr3', () => {
  expect(arr1).not.toEqual(arr3)
})

it('arr1 should contain num', () => {
  expect(arr1).toContain(num)
})

it('arr1 should contain arr3', () => {
  expect(arr1).toEqual(expect.arrayContaining(arr3))
})

it('arr3 should not contain arr1', () => {
  expect(arr3).not.toEqual(expect.arrayContaining(arr1))
})

it('length of arr1 should be 5', () => {
  expect(arr1).toHaveLength(5)
})
```

</p>
</details>

---

##### 4. Напишите валидные тесты

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
  expect(good1).toMatchObject(good2)
})

it('good3 should not contain good1', () => {
  expect(good3).not.toEqual(expect.objectContaining(good1))
})
```

</p>
</details>

---

##### 5. Напишите валидные тесты

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

##### 6. Напишите валидные тесты

```javascript
const turtles1 = [
  { name: 'Leo' },
  { name: 'Don' },
  { name: 'Raph', features: { color: 'red' } },
]
const turtles2 = [{ name: 'Leo' }, { name: 'Don' }]
const turtles3 = [{ name: 'Leo' }, { name: 'Raph' }]
const leo = { name: 'Leo' }
const raph = { name: 'Raph' }

it('turtles1 should contain leo', () => {})
it('turtles1 should contain raph', () => {})
it('turtles1 should contain turtles2', () => {})
it('turtles1 should contain turtles3', () => {})
```

<details><summary><b>Решение</b></summary>
<p>

```javascript
const turtles1 = [
  { name: 'Leo' },
  { name: 'Don' },
  { name: 'Raph', features: { color: 'red' } },
]
const turtles2 = [{ name: 'Leo' }, { name: 'Don' }]
const turtles3 = [{ name: 'Leo' }, { name: 'Raph' }]
const leo = { name: 'Leo' }
const raph = { name: 'Raph' }

it('turtles1 should contain leo', () => {
  expect(turtles1).toContainEqual(leo)
})

it('turtles1 should contain raph', () => {
  expect(turtles1).toContainEqual(expect.objectContaining(raph))
})

it('turtles1 should contain turtles2', () => {
  expect(turtles1).toEqual(expect.arrayContaining(turtles2))
})

it('turtles1 should contain turtles3', () => {
  turtles3.forEach((turtle) => {
    expect(turtles1).toContainEqual(expect.objectContaining(turtle))
  })
})
```

</p>
</details>

---

##### 7. Напишите валидные тесты
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

---

##### 8. Напишите валидные тесты

```javascript
const errorMessage = 'do you wanted it?'

function getError() {
  throw new Error(errorMessage)
}

it('function getError should throw error', () => {})
it('function getError should throw error and message should be errorMessage', () => {})
```

<details><summary><b>Решение</b></summary>
<p>

```javascript
const errorMessage = 'do you wanted it?'

function getError() {
  throw new Error(errorMessage)
}

it('function getError should throw error', () => {
  expect(() => getError()).toThrow()
})

it('function getError should throw error and message should be errorMessage', () => {
  expect(() => getError()).toThrow(errorMessage)
  expect(() => getError()).toThrow(new RegExp(errorMessage))
  expect(() => getError()).toThrow(new Error(errorMessage))
})
```

</p>
</details>

---

##### 9. Исправьте тесты так, чтобы они стали валидными
Функции `it` изменять нельзя.

```javascript
describe('Test context', () => {
  let context = { login: 'Arnold' }

  it('should can change login', () => {
    context.login = 'Simon'
    expect(context.login).toBe('Simon')
  })

  it('default login should be Arnold', () => {
    expect(context.login).toBe('Arnold')
  })
})
```

<details><summary><b>Решение</b></summary>
<p>

```javascript
describe('Test context', () => {
  let context = { login: 'Arnold' }

  beforeEach(() => {
    context = { login: 'Arnold' }
  })

  it('should can change login', () => {
    context.login = 'Simon'
    expect(context.login).toBe('Simon')
  })

  it('default login should be Arnold', () => {
    expect(context.login).toBe('Arnold')
  })
})
```

</p>
</details>

---

##### 10. Напишите валидный тест
Даны несколько массивов цифр. Напишите тест, который проверяет что arr[0] + arr[1] равняется arr[2]. Для решения используйте только одну функцию `it`.

```javascript
[1, 1, 2]
[1, 2, 3]
[2, 1, 3]
```

<details><summary><b>Подсказка</b></summary>
<p>

Для решения используйте метод `it.each`.

</p>
</details>

<details><summary><b>Решение 1</b></summary>
<p>

```javascript
it.each`
  a    | b    | expected
  ${1} | ${1} | ${2}
  ${1} | ${2} | ${3}
  ${2} | ${1} | ${3}
`('$a + $b should return $expected', ({ a, b, expected }) => {
  expect(a + b).toBe(expected);
});
```

</p>
</details>

<details><summary><b>Решение 2</b></summary>
<p>

```javascript
it.each([
  [1, 1, 2],
  [1, 2, 3],
  [2, 1, 3],
])('$a + $b should return $expected', (a, b, expected) => {
  expect(a + b).toBe(expected);
});
```

</p>
</details>
