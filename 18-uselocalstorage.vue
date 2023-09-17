// Read more
// https://play.vuejs.org/#eNqtVcuKG0cU/ZVLb9waK9023gmN8AMvHPLCDvGmNzXdV5qyqquaqmqNhrEgJFkY8oAEQxJDTBIIJIuYZBcI/hvPyP4L31vVLWsGP8BYILpV95xz36Wj5ErTZIsWk1GS5/Dk8a/rB1+t/75/8tu9Qo9daWXjwaFvG1BCz3bPeXduUuhCy7ox1sNRaeqm9VgNweJ0CK0Oj9tWerGn8FpnvYnTFUytqaFIyFmRsES+s1No2IEbdaOwRu3B7yOwoHFMhmmrSy8NQQn1oZhjAPSncGDsHKZSI9vzQm8MrcMPTCnULW+smGE6x8MROG+lng1BaumlUJ8J1eIIhD4cjF4W7pgsEzgiaYpIO4oN6wZ2OctUbYlnM/Q3yMZOBnD37in9AdOprMf3/lrf/7MvFVCJiQXHP3xDlT355Y/jRw/X3/3TYU8efPHkv2+ffv7l05+/h/W//x8//PrZj4+e/f4T2y11wupQI1ZKQ3wApDaCdAC7k9iAlIMdDKORfJBxEXNlSEcCOJUHwfo8hrAIkfOHlbIFJ0PJL+Lpih8rgtBLoWN5StNqj5ZAZ6tfJJ2tSIZwgVjU+RxuU6eF5shPhQELKYA6NZuhpUpxvwlC5FF0ZBRmyszSTjJG1mte0RXrCuVMEKeU3iROkCje59E2lfCcayxnNwBbzs6fD3mP87gctAxjrpEiFr0DjPcvTo5oLQJltRrn9Duc77Xe03BeLpUs57tFEj0VySS+jPMIYMF8o5gME6krXGYenc+8ozXtNw9q9gGbvbpMi0VE599rvVSOd2wDrZCj3UMafz8EXDZYbjEXkmlxKTsK3Qq9Ncu7KyICeinq65lOc3+3qiY9Qdy+aVUVVpXNwh3qcgtDM0g9OrCiacLshJRS8tfNX4w07QAZLXtFok2RDKggS58O6GmucizXYsFHcIGMkSwOhNyI99xY5CAQB4Hnkzuyob2Fz4uBHOk9r9UxmbOGd5Nl9NhtIX1pTryjCZ7KWXbHGU1zEgrMy1c3UqH9uOG7kcZi1Je+SIRS5uD9cOZti92FQZx9LOcvOb/jlnxWJJ9YdGgX3PLe5oWlTY3m67c+ori3jLWpWkXo1xhvIi03TS43h2FXW11R2Fu4EC39WdB80k3+qbu+9KhdnxQHGioS8OFvhq/zV6X+ItxL2aXAo0Imq+cr5Xhm
// https://github.com/webfansplz/vuejs-challenges/issues/83
// https://vuejs.org/guide/reusability/composables.html

// Note
// WritableComputedRef
// unref
// computed with getter/ setter
// composable with computed and watch

<script setup lang='ts'>

import {computed, ref, unref, WritableComputedRef} from "vue"

/**
 * Implement the composable function
 * Make the function work fine
 */
function useLocalStorage(key: string, initialValue: any): WritableComputedRef<any> {
  const temp = ref(localStorage.getItem(key) || initialValue)

  return computed({
    get: () => unref(temp),
    set: (v: any) => {
      localStorage.setItem(key, v)
      temp.value = v
    }
  })
}

const counter = useLocalStorage("counter", 0)

// We can get localStorage via triggered the getter:
console.log(counter.value)

// And We also can set localStorage via triggered the setter:

const update = () => {
  counter.value++
}
</script>
<template>
  <h1>{{counter}}</h1>
  <button @click="update">update</button>
</template>
