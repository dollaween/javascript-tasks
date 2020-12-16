<div align="center">

<h1>Задачи по Javascript: Строки</h1>

<a href="https://github.com/dollaween/javascript-tasks">На главную</a> | <a href="https://github.com/dollaween/javascript-questions">Вопросы</a> | <a href="https://github.com/dollaween/javascript-tests">Тесты</a>

</div>

---

##### 1. Переставьте слова местами
```javascript
function rearrangeWords(str) {
  /** ВАШ КОД */
}

rearrangeWords('Bruce Willis')
// => Willis Bruce

rearrangeWords('Арнольд Шварценеггер')
// => Шварценеггер Арнольд
```

<details><summary><b>Подсказка</b></summary>
<p>

Используйте такие методы массива, как `split`, `join`, `reverse`. Либо воспользуйтесь регулряными выражениями и методом `replace`.
</p>

</details>

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
  return str.replace(/([\wА-я]+) ([\wА-я]+)/, '$2 $1')
}
```

</p>
</details>

---

##### 2. Замените все слова в строке другим словом
Замените все слова в предложении словом 'wrong'. Знаки препинания оставьте без изменений.

```javascript
replaceWords('Hello world, чудесный новый мир!')
// => wrong wrong, wrong wrong wrong!
```

<details><summary><b>Подсказка</b></summary>
<p>

С помощью регулярного выражения достаньте все слова и при помощи метода `replace` замените их на `wrong`.
</p>

</details>

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

<details><summary><b>Подсказка</b></summary>
<p>

Воспользуйтесь регулярными выражениями и методом `replace`.

</p>
</details>

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
    return w.slice(1) + w[0] + 'ay'
  })
}
```

</p>
</details>

---

##### 4. Валидные скобки
Напишите функцию, которая принимает скобки, и определяет валидность их порядка.

```javascript
validParentheses('()')              // =>  true
validParentheses(')(()))')          // =>  false
validParentheses('(')               // =>  false
validParentheses('(())((()())())')  // =>  true
```

<details><summary><b>Подсказка</b></summary>
<p>

Создайте счетчик от нуля. С помощью цикла пройдитесь по каждому символу строки и добавляйте +1 (для скобки `'('`) или -1 (для скобки `')'`). Если счетчик хоть раз стал отрицательным — возвращайте `false`. Если после перебора всей строки значение не равно нулю — возвращайте `false`.

</p>
</details>

<details><summary><b>Решение</b></summary>
<p>

```javascript
function validParentheses(parens){
  let n = 0

  for (let i = 0; i < parens.length; i++) {
    parens[i] === '(' ? n++ : n--
    if (n < 0) return false
  }

  return n === 0
}
```

</p>
</details>

---

##### 5. Является ли строка A анаграммой строки B?
*Анаграмма* — это слово или словосочетание, образованное путём перестановки букв, составляющих другое слово.

```javascript
anagram('friend', 'finder')                       // => true
anagram('hello', 'bye')                           // => false
anagram('Eleven, plus two', 'Twelve plus one!')   // => true
anagram('Аз есмь строка, живу я, мерой остр', 'За семь морей ростка я вижу рост')   // => true
```

<details><summary><b>Подсказка</b></summary>
<p>
Удалите из строки все лишние символы, приведите к единому регистру. Отсортируйте строку по алфавиту. Сделайте то же самое со второй строкой и сравните их.
</p>
</details>

<details><summary><b>Решение 1</b></summary>
<p>

```javascript
function cleanString(str) {
  return str
    .replace(/[^\wА-я]/g, '')
    .toLowerCase()
    .split('')
    .sort()
    .join('')
}

function anagram(strA, strB) {
  return cleanString(strA) === cleanString(strB)
}
```

</p>
</details>

<details><summary><b>Решение 2</b></summary>
<p>

```javascript
function buildCharObj(str) {
  const charObj = {}
  str = str.replace(/[^\wА-я+]/g, '').toLowerCase()
  for (let char of str) {
    charObj[char] = charObj[char] + 1 || 1
  }
  return charObj
}

function anagram(strA, strB) {
  const aCharObj = buildCharObj(strA)
  const bCharObj = buildCharObj(strB)

  if (Object.keys(aCharObj).length !== Object.keys(bCharObj).length) {
    return false
  }

  for (let char in aCharObj) {
    if (aCharObj[char] !== bCharObj[char]) {
      return false
    }
  }

  return true
}
```

</p>
</details>

---

##### 6. Проверьте строку на палиндром
*Палиндром* — это слово, которое читается одинаково слева направо.

```javascript
palindrome('Anna')                  // true
palindrome('Never, odd or even!')   // true
palindrome('More work?')            // false
```

<details><summary><b>Подсказка</b></summary>
<p>
Удалите из строки все лишние символы, приведите слова к единому регистру. Сравните получившуюся строку с ней же, но в обратном порядке.
</p>
</details>

<details><summary><b>Решение 1</b></summary>
<p>

```javascript
function palindrome(str) {
  str = str.replace(/[\W]/g, '').toLowerCase()
  return str === str.split('').reverse().join('')
}
```

</p>
</details>

<details><summary><b>Решение 2</b></summary>
<p>

```javascript
function palindrome(str) {
  str = str.replace(/[\W]/g, '').toLowerCase()
  const length = str.length
  for (let i = 0; i <= length / 2; i++) {
    if (str[i] !== str[length - 1 - i]) {
      return false
    }
  }
  return true
}
```

</p>
</details>

---

##### 7. Напишите функцию, которая будет выдавать количество гласных в строке

```javascript
vowelsCount('For the king!')     // 3
```

<details><summary><b>Подсказка</b></summary>
<p>

Вариант 1: Создайте массив с гласными и счетчик от нуля. С помощью цикла, пройдитесь по всем символам строки. Если символ совпадает с одним из массива с гласными — добавляйте счетчику +1.

Вариант 2: Воспользуйтесь регулярным выражением и методом `match`.

</p>
</details>

<details><summary><b>Решение 1</b></summary>
<p>

```javascript
function findVowels(str) {
  let count = 0
  const vowels = ['a', 'e', 'i', 'o', 'u']

  for (let char of str.toLowerCase()) {
    if (vowels.includes(char)) {
      count++;
    }
  }

  return count
}
```

</p>
</details>

<details><summary><b>Решение 2</b></summary>
<p>

```javascript
function findVowels(str) {
  return str.match(/[aeiou]/gi).length || 0
}
```

</p>
</details>

---

##### 8. Напишите функцию, которая будет сжимать повторяющиеся символы до формата: Символ + количество повторений подряд

```javascript
stringCompression('AAABbbbBcCCC')
// => 'A3Bb3BcC3'

stringCompression('A: AAAAA; T: TTTTTTT')
// => 'A: A5; T: T7'
```

<details><summary><b>Подсказка</b></summary>
<p>

С помощью регулярного выражения найдите в строке символы, повторяющиеся два или более раз. Воспользуйтесь методом `replace`, чтобы заменить найденные символы.

</p>
</details>

<details><summary><b>Решение</b></summary>
<p>

```javascript
function stringCompression() {
  const regexp = /(.)\1+/g
  return str.replace(regexp, (letters, letter) => letter + letters.length)
}
```

</p>
</details>

---

##### 9. Напишите функцию, которая будет генерировать строку указанной длины со случайными символами

```javascript
generateRandomString(10)
// => AmnUJiOPQl
```

<details><summary><b>Подсказка</b></summary>
<p>

Составьте список нужных символов. Для генерации случайного символа из списка воспользуйтесь методами `charAt`, `Math.floor` и `Math.random`.

</p>
</details>

<details><summary><b>Решение 1</b></summary>
<p>

```javascript
function generateRandomString(length) {
  let result = ''
  let characters = 'ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789'
  let charactersLength = characters.length

  for (let i = 0; i < length; i++) {
    result += characters.charAt(Math.floor(Math.random() * charactersLength))
  }

  return result
}
```

</p>
</details>

<details><summary><b>Решение 2</b></summary>
<p>

```javascript
function dec2hex (dec) {
  return dec.toString(16).padStart(2, "0")
}

function generateRandomString(length){
  let arr = new Uint8Array((length || 40) / 2)
  window.crypto.getRandomValues(arr)
  return Array.from(arr, dec2hex).join('')
}
```

</p>
</details>

<details><summary><b>Решение 3</b></summary>
<p>

Решение для строк в которых содержится не более 11 символов.
```javascript
function generateRandomString(length){
  return Math.random().toString(36).substr(2, length)
}
```

</p>
</details>

---

##### 10. В переданной строке найдите только повторяющиеся символы и верните их количество

```javascript
countDuplicates('abracadabra')
// => { a: 5, b: 2, r: 2 }

countDuplicates('another')
// => {}
```

<details><summary><b>Подсказка</b></summary>
<p>

Создайте пустой объект. Пройдитесь по каждому символу строки: если в объекте не содержится итерируемого символа — добавьте его со значением 1, иначе увеличьте количество на единицу.

</p>
</details>

<details><summary><b>Решение 1</b></summary>
<p>

```javascript
function countDuplicates() {
  let obj = {}

  for (let i = 0; i < str.length; i++) {
    obj[str[i]] = Object.keys(obj).includes(str[i])
      ? obj[str[i]] + 1
      : 1
  }

  for (key in obj) {
    if (obj.hasOwnProperty(key) && obj[key] === 1) {
      delete obj[key]
    }
  }

  return obj
}
```

</p>
</details>

<details><summary><b>Решение 2</b></summary>
<p>

```javascript
function countDuplicates() {
  let result = {}

  let arr = str
    .toLowerCase()
    .split('')
    .sort()
    .join('')
    .match(/(.)\1+/g)

  arr && arr.forEach(element => {
    result[element[0]] = element.length
  });

  return result
}
```

</p>
</details>

---

##### 11. Найдите первый неповторяющийся символ в строке

```javascript
firstNonRepeatingCharacter('akwpaoonwpqkskmqy')
// => n

firstNonRepeatingCharacter('abracadabra')
// => c

firstNonRepeatingCharacter('aabbbccddddd')
// => null
```

<details><summary><b>Подсказка</b></summary>
<p>

Попробуйте использовать метод `str.indexOf()`.

</p>
</details>

<details><summary><b>Решение</b></summary>
<p>

`str.indexOf()` возвращает индекс первого вхождения указанного значения в строке или `-1`, если значение не найдено. Проверяем вхождение значения, начиная от следующего (`i + 1`) — если не найдено, то значит символ уникален.
```javascript
function firstNonRepeatingCharacter(str) {
  for (let i = 0; i < str.length; i++) {
    let char = str[i]
    if (str.indexOf(char) === i && str.indexOf(char, i + 1) === -1) {
      return char
    }
  }

  return null
}
```

</p>
</details>

---

##### 12. Напишите функцию, которая будет возвращать массив, состоящий из всех возможных перестановок символов передаваемой строки

```javascript
permute('ABC')
// => ["ABC", "ACB", "BAC", "BCA", "CAB", "CBA"]
```

<details><summary><b>Подсказка</b></summary>
<p>

Используйте рекурсию: передавайте в рекурсию каждый раз всё более и более обрезанную версию строки, соединяя на выходе текущий символ с результатами перестановок из рекурсии.

</p>
</details>

<details><summary><b>Решение</b></summary>
<p>

```javascript
function permute() {
  if (str.length < 2) return str

  // Массив будет хранить наши перестановки
  let permutations = []

  for (let i = 0; i < str.length; i++) {
    let char = str[i]

    // Не итерируем текущий символ
    if (str.indexOf(char) !== i)
      continue

    // Обрезаем строку
    let remainingString = str.slice(0, i) + str.slice(i + 1, str.length)

    // Объединяем результат рекурсии с текущим символом
    for (let subPermutation of second(remainingString))
      permutations.push(char + subPermutation)
  }

  return permutations
}
```

</p>
</details>

---

##### 13. Напишите функцию, которая прячет часть email адреса
Отобразите только первые три символа логина email. Если количество символов в логине меньше четырех — отобразите только первый символ email.

```javascript
hideEmail('learner@gmail.com')
// => 'lea...@gmail.com'

hideEmail('teo@gmail.com')
// => 't...@gmail.com'
```

<details><summary><b>Решение</b></summary>
<p>

```javascript
function hideEmail(str) {
  const parts = str.split('@')
  return parts[0].slice(0, parts[0].length < 4 ? 1 : 3) + '...@' + parts[1]
}
```

</p>
</details>

---

##### 14. Напишите функцию, которая меняет регистр букв на противоположный

```javascript
swapCase('aAbbbBBCCcd')
// => 'AaBBBbbccCD'
```

<details><summary><b>Решение</b></summary>
<p>

```javascript
function swapCase(str) {
  return str.replace(/([a-z]+)|([A-Z]+)/g, function(match, char) {
    return char ? match.toUpperCase() : match.toLowerCase()
  })
}
```

</p>
</details>

---

##### 15. Напишите функцию, которая разобьет строку на массив из строк указанной длины

```javascript
stringChop('abracadabra', 2)
// => ['ab', 'ra', 'ca', 'da', 'br', 'a']

stringChop('abracadabra', 3)
// => ['abr', 'aca', 'dab', 'ra']
```

<details><summary><b>Решение</b></summary>
<p>

```javascript
function stringChop(str, size) {
  if (str == null) return []

  return size > 0
    ? str.match(new RegExp('.{1,' + size + '}', 'g'))
    : [str]
}
```

</p>
</details>
