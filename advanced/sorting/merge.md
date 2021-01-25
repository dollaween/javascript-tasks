<div align="center">

# Задачи по сортировки слиянием (Merge Sort)

[Вопросы](https://github.com/dollaween/javascript-questions)
|
[Тесты](https://github.com/dollaween/javascript-tests)
|
[Задачи](https://github.com/dollaween/javascript-tasks)

</div>

---

**Цель задач:** Практика сортировки массива методом Merge Sort.

---

##### 1. Напишите функцию, которая будет сортировать массив чисел методом Merge Sort

```javascript
function mergeSort(arr) {}

mergeSort([1, 8, 2, 16, 0, -6, 4, 3])
// [-6, 0, 1,  2, 3, 4, 8, 16]
```

<details><summary><b>Решение</b></summary>
<p>

```javascript
function mergeSortedArrays(nums1, nums2) {
  const result = []
  let i = 0
  let k = 0

  while (i < nums1.length && k < nums2.length) {
    if (nums1[i] < nums2[k]) {
      result.push(nums1[i])
      i++
    } else {
      result.push(nums2[k])
      k++
    }
  }

  while (i < nums1.length) {
    result.push(nums1[i])
    i++
  }

  while (k < nums2.length) {
    result.push(nums2[k])
    k++
  }

  return result
};

function mergeSort(arr) {
  if (arr.length <= 1) return arr

  const mid = Math.floor(arr.length / 2)
  const left = mergeSort(arr.slice(0, mid))
  const right = mergeSort(arr.slice(mid))

  return mergeSortedArrays(left, right)
}
```

</p>
</details>
