<div align="center">

# Задачи по нотации О большое

[Вопросы](https://github.com/dollaween/javascript-questions)
|
[Тесты](https://github.com/dollaween/javascript-tests)
|
[Задачи](https://github.com/dollaween/javascript-tasks)

</div>

---

**Цель задач:** 

Узнать о нотации О большое можно здесь:
* [Youtube. Оценка сложности алгоритма. Сложность алгоритмов. Big O, Большое О](https://www.youtube.com/watch?v=ZRdOb4yR0kk)

---

##### 1. Расположите слелующие сложности нотации О большое в порядке от наиболее сложных к наименее

```javascript
2^(100 log n)
n*2^n
n^(log log n)
2^2^(n+1)
n log n
n^3
log n
n^100
log(n!)
2^2^n
n log n + n! / (2!(n - 2)!)
n^(1/(log n))
n^2
log^2 n
4^log n
n
Квадратный корень из n
Квадратный корень из 2 в степени log n
```

<details><summary><b>Решение</b></summary>
<p>

```javascript
// Больше чем 2^n
2^2^(n+1)
2^2^n
n*2^n

// Квазиполиномы
n^(log log n)

// Полиномы
n^100
2^(100 log n)
n log n + n! / (2!(n - 2)!)
n^3
n^2
4^log n
n log n
n
Квадратный корень из n
Квадратный корень из 2 в степени log n

// Логарифмы
log^2 n
log(n!)
log n

// Стремящиеся к константе
n^(1/(log n))
```

</p>
</details>

---

##### 2. Напишите пример функции равной сложности `O(N)`

<details><summary><b>Решение</b></summary>
<p>

```javascript
function example(n) {
  if (n === 1) return 1
  return n + example(n - 1)
}
```

</p>
</details>

---

##### 3. Напишите пример функции равной сложности `O(N^2)`

<details><summary><b>Решение</b></summary>
<p>

```javascript
function example(n) {
  for (let i = 0; i <= n; i++) {
    for (let k = 0; k <= n; k++) {
      console.log(i, k)
    }
  }
}
```

</p>
</details>

---

##### 4. Напишите пример функции равной сложности `O(log N)`

<details><summary><b>Решение</b></summary>
<p>

```javascript
function example(n) {
  for (let i = 2; i <= n; i *= 2) {
    console.log(i)
  }
}
```

</p>
</details>

---

##### 5. Напишите пример функции равной сложности `O(N log N)`

<details><summary><b>Решение</b></summary>
<p>

```javascript
function example(n) {
  for (let i = 0; i <= n; i++) {
    for (let k = 2; k <= n; k *= 2) {
      console.log(i, k)
    }
  }
}
```

</p>
</details>
