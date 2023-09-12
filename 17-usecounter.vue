<script setup lang='ts'>
import { ref } from 'vue'

interface UseCounterOptions {
  min?: number
  max?: number
}

/**
 * Implement the composable function
  * 1. inc (+)
  * 2. dec (-)
  * 3. reset 
  * 4. min & max opotion support
 * Make sure the function works correctly
*/
function useCounter(initialValue = 0, options: UseCounterOptions = {}) {
  const count = ref(initialValue)

  function inc() {
    if(options.max) {
      if (count.value < options.max) {
        count.value++
      }
    } else {
      count.value++
    }
  }

  function dec() {
    if(options.min) {
      if (count.value > options.min) {
        count.value--
      }
    } else {
      count.value--
    }
  }

  function reset() {
    count.value = initialValue
  }

  return { count, inc, dec, reset }
}

const { count, inc, dec, reset } = useCounter(0)

</script>

<template>
  <p>Count: {{ count }}</p>
  <button @click="inc">
    inc
  </button>
  <button @click="dec">
    dec
  </button>
  <button @click="reset">
    reset
  </button>
</template>
