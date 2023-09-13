<script setup lang="ts">
import { onMounted, onUnmounted, ref} from "vue"
// Implement ...
function useEventListener(target: EventTarget, event: string, callback) {
  onMounted(() => target.addEventListener(event, callback))
  onUnmounted(() => target.removeEventListener(event, callback))
}

// Implement ...
function useMouse() {
  const x = ref(0)
  const y = ref(0)

  useEventListener(window, "mousemove", (event) =>{
    x.value = event.pageX
    y.value = event.pageY
  })

  return { x, y }
}
const { x, y } = useMouse()
</script>

<template>
  Mouse position is at: {{ x }}, {{ y }}
</template>

// Read more
// https://vuejs.org/guide/reusability/composables.html#mouse-tracker-example
// https://play.vuejs.org/#eNqdVF1r2zAU/SsXPTngKdn6FtqydfRhY19sHbSgF9e+SdTYkpHk2CXkv+9Ksh1nCx0UEmzdz3PPPdaefahrvmuQLdmlzY2sHVh0TQ1lptZXgjkr2LVQsqq1cbAHrb7qRjksUnr9rarhYHB1gJXRFQhG5QQTaj6HT1VdYoXKAedcqFWjcie1gsbi7Y7MX6R1qNAkLjNrdEsI1rtwSAH9YQnWGanWKeRZWT5m+XYGe6HgiCRJZnB1DbEEz4ritHSoMsmexeQR+2m6wUrv/gJ3psJBqP8NSOgsUu0ANtfKOujgyhOVLAKGaHue2Lz1H2paqQrdpsQrAbYBnmApRFQeemgA0PFdVjZI5YKH19ka76Pr+YzrwbsOfVNDKzeK1tulBIiGo1+EN5go9ziTUJfzKBaSBh0cEg2ZQzoBhBiotZWBCWkhoyXuqRAcDql/oXJU/3I+SWMpozGx4w6t486SHEfJhT0Rgl5d70lelGrdm8bJkuQ5UWeBHtYjpiC9froa80nmTvq0kwSFnbuT+XYSFMU7xtD3Mbj4vP9YYsDQLBFsoCYsJsgpLEU68tmNbsoCWm223p3ZZ5VPYgYdtCarazTEc5g3oVZBJdCPkfQBfOOqMpnNuNM3vvV5uhcpLATrtzu0GPVDTRS2cVNBbFTnRFw9MgCaEFHdL+HtIj21PSzh3dGWl5LKnMZF2zTOy80/o6R5IW2duXwTIYwARtRZm0k3rsjL7rV0ECpCEQiJKPyfNOcsMbOSa/5ktSLNhbkFy3VVyxLN99oXIYmRfmNzwegS0O3nYHOmwX4yytlgvj1jf7Kdtwn2w6BFE/gdfPHOie7bX99o0Imz0kVTUvQLzp9odUlfgVYx7KZRBcGexAW0dEmRkukOvbO3HV0qdhjKAw2MhPig/Y8vjH6Ee8EvQh4RyQ5/AO4EGXY=
  
// Note
// a composable can also hook into its owner component's lifecycle to setup and teardown side effects.
