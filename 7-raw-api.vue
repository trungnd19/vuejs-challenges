// Read more
// https://vuejs.org/api/reactivity-advanced.html#markraw
// https://vuejs-challenges.netlify.app/questions/7-raw-api/readme.html
// https://github.com/webfansplz/vuejs-challenges/issues/1696

// Note:
// toRaw(): toRaw() can return the original object from proxies created by reactive(), readonly(), shallowReactive() or shallowReadonly().
// markRaw(): Marks an object so that it will never be converted to a proxy. Returns the object itself.

<script setup lang="ts">
import { reactive, isReactive, toRaw, markRaw } from "vue"

const state = { count: 1 }
const reactiveState = reactive(state)

/**
 * Modify the code so that we can make the output be true.
*/
console.log(toRaw(reactiveState) === state) // true

/**
 * Modify the code so that we can make the output be false.
*/
const info = markRaw({ count: 1 })
const reactiveInfo = reactive(info)

console.log(isReactive(reactiveInfo)) // false

</script>

<template>
  <div>
    <p>
      {{ reactiveState.count }}
    </p>
  </div>
</template>
