<script setup lang="ts">
defineProps({
  type: {
    validator(value: string) {
      return ['primary', 'ghost', 'dashed', 'link', 'text', 'default'].includes(value)
    },
    default: 'default'
  },
})
</script>

<template>
  <button>Button</button>
</template>

// Read more
// https://vuejs-challenges.netlify.app/questions/323-prop-validation/README.html
// https://vuejs.org/guide/components/props.html#prop-validation
// https://qiita.com/kawabata324/items/5c8d3a789e080a426285
