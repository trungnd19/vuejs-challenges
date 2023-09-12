// Read more
// https://vuejs-challenges.netlify.app/questions/3-losing-reactivity/readme.html
// https://vuejs.org/api/reactivity-utilities.html#torefs

- Dùng toRefs(): Converts a reactive object to a plain object where each property of the resulting object is a ref pointing to the corresponding property of the original object.
Each individual ref is created using toRef().

- Usage: thường dùng khi return 1 reactive object trong composable function. Nếu dùng toRefs() khi return 1 reactive object => ở consuming component có thể destructure/ spread mà không bị losing reactivity
(toRefs is useful when returning a reactive object from a composable function so that the consuming component can destructure/spread the returned object without losing reactivity)

// Cách 1: Không destructuring, dùng state.count

<script setup lang="ts">
import { reactive, toRefs } from "vue"

function useCount() {
  const state = reactive({
    count: 0,
  })

  function update(value: number) {
    state.count = value
  }

  return {
    state,
    update,
  }
}

// Ensure the destructured properties don't lose their reactivity
const { state, update } = useCount()

</script>

<template>
  <div>
    <p>
      <span @click="update(state.count-1)">-</span>
      {{ state.count }}
      <span @click="update(state.count+1)">+</span>
    </p>
  </div>
</template>


// Cách 2: dùng toRefs với returned state

<script setup lang="ts">
import { reactive, toRefs } from "vue"

function useCount() {
  const state = reactive({
    count: 0,
  })

  function update(value: number) {
    state.count = value
  }

  return {
    state: toRefs(state),
    update,
  }
}

// Ensure the destructured properties don't lose their reactivity
const { state: { count }, update } = useCount()

</script>

<template>
  <div>
    <p>
      <span @click="update(count-1)">-</span>
      {{ count }}
      <span @click="update(count+1)">+</span>
    </p>
  </div>
</template>

