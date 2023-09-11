<script setup lang="ts">
import { shallowRef, watch } from "vue"

const state = shallowRef({ count: 1 })

// Does NOT trigger
watch(state, () => {
  console.log("State.count Updated")
}, { deep: true })

/**
 * Modify the code so that we can make the watch callback trigger.
*/
state.value = { count: 2 }

</script>

<template>
  <div>
    <p>
      {{ state.count }}
    </p>
  </div>
</template>

// Read more
// https://vuejs.org/api/reactivity-advanced.html#shallowref
// https://vuejs.org/guide/best-practices/performance.html#reduce-reactivity-overhead-for-large-immutable-structures
// Unlike ref(), the inner value of a shallow ref is stored and exposed as-is, and will not be made deeply reactive. Only the .value access is reactive.
// shallowRef() is typically used for performance optimizations of large data structures, or integration with external state management systems.
// Shallow APIs create state that is reactive only at the root level, and exposes all nested objects untouched
// updates can only be triggered by replacing the root state:

const shallowArray = shallowRef([
  /* big list of deep objects */
])

// this won't trigger updates...
shallowArray.value.push(newObject)
// this does:
shallowArray.value = [...shallowArray.value, newObject]

// this won't trigger updates...
shallowArray.value[0].foo = 1
// this does:
shallowArray.value = [
  {
    ...shallowArray.value[0],
    foo: 1
  },
  ...shallowArray.value.slice(1)
]
