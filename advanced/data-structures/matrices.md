<div align="center">

# Задачи по матрицам

[Вопросы](https://github.com/dollaween/javascript-questions)
|
[Тесты](https://github.com/dollaween/javascript-tests)
|
[Задачи](https://github.com/dollaween/javascript-tasks)

</div>

---

**Цель задач:** Практика построения и изменения матриц.

---

##### 1. Создайте простую матрицу.
Создайте класс `SubrectangleQueries`, который получает прямоугольник `rectangle`, состоящий из строк и столбцов `rows x cols`. Класс должен содержать следующие методы:
1. `getValue(row, col)`
  * Возвращает значение из `rectangle` по координатам `row` и `col`.
2. `updateSubrectangle(row1, col1, row2, col2, newValue)`
  * Изменяет все значения на `newValue` по координатам: `row1, col1` от верхнего левого угла до `row2, col2` правого нижнего угла.

```js
const SubrectangleQueries = function(rectangle) {}
SubrectangleQueries.prototype.updateSubrectangle = function(row1, col1, row2, col2, newValue) {}
SubrectangleQueries.prototype.getValue = function(row, col) {}

const obj = new SubrectangleQueries([[1, 2, 3], [4, 5, 6], [7, 8, 9], [10, 11, 12]])
obj.getValue(2, 2)
// 9, так как 2-ой ряд, 2-ая колонка — значение 9
obj.updateSubrectangle(0, 0, 1, 1, 0)
// После применения, наша матрица будет иметь следующее содержание:
// 0  0  3
// 0  0  6
// 7  8  9
// 10 11 12
```

<details><summary><b>Решение</b></summary>
<p>

```javascript
const SubrectangleQueries = function(rectangle) {
  this.rectangle = rectangle
}

SubrectangleQueries.prototype.updateSubrectangle = function(row1, col1, row2, col2, newValue) {
  for (let i = row1; i <= row2; i++) {
    for (let k = col1; k <= col2; k++) {
      this.rectangle[i][k] = newValue
    }
  }
};

SubrectangleQueries.prototype.getValue = function(row, col) {
  return this.rectangle[row][col]
};
```

</p>
</details>
