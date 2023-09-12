// Read more
// https://vuejs.org/api/reactivity-advanced.html#effectscope
// https://vuejs-challenges.netlify.app/questions/8-effect-scope/readme.html

// Note
// - effectScope: Creates an effect scope object which can capture the reactive effects (i.e. computed and watchers) created within it so that these effects can be disposed together.
// (Nôm na: tạo ra 1 "vùng" gom reactive effects để sau cần "dọn" thì dọn 1 nhát được hết luôn)
// 2 methods cơ bản là run() và stop()

<script setup lang="ts">
import { ref, computed, watch, watchEffect, effectScope } from "vue"

const counter = ref(1)
const doubled = computed(() => counter.value * 2)

// use the `effectScope` API to make these effects stop together after being triggered once
const scope = effectScope();

scope.run(() => {
  watch(doubled, () => console.log(doubled.value))
  watchEffect(() => console.log(`Count: ${doubled.value}`))
})

counter.value = 2

setTimeout(() => {
  scope.stop()
  counter.value = 4
})


</script>

<template>
  <div>
    <p>
      {{ doubled }}
    </p>
  </div>
</template>
