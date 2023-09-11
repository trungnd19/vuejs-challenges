<script setup>
import { ref } from "vue"

const count = ref(0)

setInterval(() => {
  count.value++
}, 1000)
</script>

<template>
  <span v-once>Make it never change: {{ count }}</span>
</template>


// Read more
// https://vuejs.org/api/built-in-directives.html#v-once
