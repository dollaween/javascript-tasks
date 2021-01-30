<div align="center">

# Задачи по дизайн-системе

[Вопросы](https://github.com/dollaween/javascript-questions)
|
[Тесты](https://github.com/dollaween/javascript-tests)
|
[Задачи](https://github.com/dollaween/javascript-tasks)

</div>

---

**Цель задач:** Практика разработки дизайн-систем.

---

##### 1. Разработайте парковочную систему для стоянки
Парковка имеет три типа мест: `big`, `medium`, `small`.

Условия:
* Количество мест для каждого типа машин ограничено и указывается в конструкторе `ParkingSystem(big, medium, small)`
* Машина определенного типа может занять только то место, которое соответствует её типу (машина типа `big` может стоять только на месте типа `big`)
* Метод `addCar(carType)` должен проверить наличие свободного места для переданного типа машины и занять его. Функция должна вернуть `true`, если место есть и `false` — если места нет

```js
const parkingSystem = new ParkingSystem(1, 1, 0)
parkingSystem.addCar(1)
// true, так как есть одно свободное парковочное место для big-типа машин
parkingSystem.addCar(1)
// false, места закончились
parkingSystem.addCar(2)
// true
parkingSystem.addCar(3)
// false
parkingSystem.addCar(2)
// false
```

<details><summary><b>Решение 1</b></summary>
<p>

```js
const ParkingSystem = function(big, medium, small) {
  this.places = {
    1: big,
    2: medium,
    3: small
  }
};

ParkingSystem.prototype.addCar = function(carType) {
  if (!this.places[carType]) {
    return false
  }
  this.places[carType] -= 1
  return true
};
```

</p>
</details>

<details><summary><b>Решение 2</b></summary>
<p>

```js
const ParkingSystem = function(big, medium, small) {
    this.parking = [big, medium, small]
};

ParkingSystem.prototype.addCar = function(carType) {
    this.parking[carType - 1] -= 1
    return this.parking[carType - 1] >= 0
};
```

</p>
</details>


