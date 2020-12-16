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

##### 2. Замените все слова другим словом
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
    return w.slice(1) + w[0] + 'ay';
  });
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
  let n = 0;

  for (let i = 0; i < parens.length; i++) {
    parens[i] === '(' ? n++ : n--;
    if (n < 0) return false;
  }

  return n === 0;
}
```

</p>
</details>

---

##### 5. Является ли строка A анаграммой строки B?

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

##### 7. Напишите функцию, которая возвращает n-ую запись в последовательности Фибоначчи

Последовательность Фибоначчи — это ряд чисел, где каждое последующее является суммой двух предыдущих. Первые десять чисел: `[0, 1, 1, 2, 3, 5, 8, 13, 21, 34]`.

```javascript
fibonacci(3)    // 2
fibonacci(9)    // 34
```

<details><summary><b>Подсказка</b></summary>
<p>

Создайте массив состоящий из первых двух чисел последовательности Фибоначчи. При помощи цикла от 2 до N (нужное значение) в каждой итерации добавляйте в конец массива число, равное сумме двух последних чисел массива.

</p>
</details>

<details><summary><b>Решение 1</b></summary>
<p>

```javascript
function fibonacci(num) {
  const result = [0, 1];

  for (let i = 2; i <= num; i++) {
    result.push(result[i - 1] + result[i - 2]);
  }

  return result[num];
}
```

</p>
</details>

<details><summary><b>Решение 2</b></summary>
<p>

Работает очень медленно:

```javascript
function fibonacci(num) {
  if (num < 2) {
    return num
  }
  return fibonacci(num - 1) + fibonacci(num - 2)
}
```

</p>
</details>

---

8. Напишите функцию, которая будет выдавать количество гласных в строке

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
  let count = 0;
  const vowels = ['a', 'e', 'i', 'o', 'u'];

  for (let char of str.toLowerCase()) {
    if (vowels.includes(char)) {
      count++;
    }
  }

  return count;
}
```

</p>
</details>

<details><summary><b>Решение 2</b></summary>
<p>

```javascript
function findVowels(str) {
  return str.match(/[aeiou]/gi).length || 0;
}
```

</p>
</details>

---

##### 9. Сжатие строки

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
  const regexp = /(.)\1+/g;
  return str.replace(regexp, (letters, letter) => letter + letters.length);
}
```

</p>
</details>
