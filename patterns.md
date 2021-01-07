<div align="center">

<h1>Задачи по Javascript: Паттерны проектирования</h1>

<a href="https://github.com/dollaween/javascript-tasks">На главную</a> | <a href="https://github.com/dollaween/javascript-questions">Вопросы</a> | <a href="https://github.com/dollaween/javascript-tests">Тесты</a>

</div>

---

##### 1. Напишите пример паттерна проектирования "Стратегия"

<details><summary><b>Подсказка</b></summary>
<p>

**Паттерн "Стратегия"** — определяет семейство схожих алгоритмов и помещает каждый из них в собственный класс, после чего алгоритмы можно взаимозаменять прямо во время исполнения программы.

</p>
</details>

<details><summary><b>Решение</b></summary>
<p>

```javascript
// Объединяющий класс, который будет воспроизводить заданную стратегию
class Delivery {
  constructor(strategy) {
    this.strategy = strategy
  }

  setStrategy(strategy) {
    this.strategy = strategy
  }

  calculate(cost) {
    return this.strategy.calculate(cost)
  }
}

// Расчет стоимости доставки от компании A
class StrategyCompanyA {
  calculate(cost) {
    return cost * 2
  }
}

// Расчет стоимости доставки от компании B
class StrategyCompanyB {
  calculate(cost) {
    return cost * 3
  }
}

// Задаем стратегию компании А
const delivery = new Delivery(new StrategyCompanyA)
console.log(delivery.calculate(1000))
// => 2000

// Задаем стратегию компании B
delivery.setStrategy(new StrategyCompanyB)
console.log(delivery.calculate(1000))
// => 3000
```

</p>
</details>
