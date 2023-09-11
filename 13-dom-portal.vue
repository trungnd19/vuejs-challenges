<script setup>

const msg = "Hello World"

</script>

<template>
  <!-- Renders it to a child element of the `body` -->
  <Teleport to="body">{{ msg }}</Teleport>
</template>


// Read more
// https://vuejs.org/guide/built-ins/teleport.html#basic-usage
