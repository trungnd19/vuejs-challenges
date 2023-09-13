// Read more
// https://vuejs-challenges.netlify.app/questions/19-v-focus/README.html
// https://play.vuejs.org/#eNqVVF1r2zAU/St3eokTXKesbyEpW0cHHWwrW9mTXpz4OlErS0a6ygcl/31Xsp1kMDoGbRLpnnt1dM6xX8XHti22AcVMzP3KqZbAI4UWdGnWixH50a00qmmtI3gFhzUcoXa2ASm4SwpppFlZ47mNSkJYRExWl9rjONamk4k0MIGHptXYoCGgDcIqeOIZlXK4IrXFBPlaviD44DBBlGkDAfZNteUW9NOlDs7DboMmgUbp0BEoD2TXa41VnCTNZHrm9etz7GVir1yD0FbcUc0gQ53DUplKmfUYFrddGUDVWb9bbEsdcDwUgMkUiUfGN4vrI+94/KMe+WVj/t0j4hd/8J80rOuDIXQ8NmPMcGS6QncWk3x3seS+HN5fX18nJefTzh/2gxeELCgjeQUw78TaXiV6CynSECmADi3yknBPUjB0Pr3oE7ngi+K+IPRUkOcInIxubGDVT1Z/YK+51dNVIKV9tP0ErTDyWmIOinLAfcuWXoRExbYuJ30LJ26oFtM+fh2gDobjYA3P1OUhI9WgDTQDE5olut4Jx/F0Bgzu4JGnKI9Z5tBbvWWvzj6y2k9d/1DNoR+Y7DvyZ7Jl4J8x2U5AKXK4MEgRl/zGBl3BzrqXWC79wawuMABd2HaubFt0bGRSMOPr5eeAlETlavNkZ1DxOTHYxdJWh7wPS7I5BSmJmPXDipptYgrJZCnGRf9QjAtj2Td7h9lpXJkep/se0E0rd6WiXtKbLk3/c8i/DkhC8j/HiTyrUKt18eyt4Tili0uxsk2rNLrvbTSX5Z0NkkhRam13X9IeuYC9FNyzwdXLX/af/T7uSfHIrvKzxMk51ah0a2TysXz/81sK/anY2CpoRr9R/BFzwgG3poPdBVMx7QtcYsuvMo4xvyCe/P2e0PjhUpFoUiTh0wvy0xtXP9O9KW6GF4U4/gYuIeBL
// https://vuejs.org/guide/reusability/custom-directives.html#directive-hooks

// Note:
// - Directive: Custom directives are mainly intended for reusing logic that involves low-level DOM access on plain elements. (logic liên quan đến DOM => vue directive)
// - Custom directive là 1 object có 7 lifecycle hooks: created, beforeMount, mounted, beforeUpdate, updated, beforeUnmount, unmounted
// - Directive hook có 4 arguments: el, binding, vnode, prevNode
// + el: the host element
// + binding.value: The value passed to the directive. For example in v-my-directive="1 + 1", the value would be 2.
// + arg: The argument passed to the directive, if any. For example in v-my-directive:foo, the arg would be "foo".
// + modifiers: An object containing modifiers, if any. For example in v-my-directive.foo.bar, the modifiers object would be { foo: true, bar: true }.

<script setup lang='ts'>
import { ref } from "vue"
const state = ref(false)

/**
 * Implement the custom directive
 * Make sure the input element focuses/blurs when the 'state' is toggled
*/

const VFocus = {
  updated: (el,binding) => binding.value?el.focus():el.blur()
}

setInterval(() => {
  state.value = !state.value
}, 2000)
</script>

<template>
  <input v-focus="state" type="text">
</template>
