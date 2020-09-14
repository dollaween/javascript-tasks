# Typescript задачи

---

##### 1. Протипизируйте список элементов
```typescript
export const Countries: ICountries[] = [
  {
    title: 'Страны',
    items: [
      {
        title: 'Россия',
        items: [
          { title: 'Москва'},
          { title: 'Санкт-Петербург' }
        ]
      },
      {
        title: 'Европа',
        items: [
          { title: 'Испания' },
          {
            title: 'Италия',
            items: [
              { title: 'Рим' },
              { title: 'Милан' }
            ]
          }
        ]
      }
    ]
  }
]
```

<details><summary><b>Решение</b></summary>
<p>

```typescript
interface ICountries {
  title?: string,
  items?: IList[]
}
```

</p>
</details>

---
