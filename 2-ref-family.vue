// Read more
// https://play.vuejs.org/#eNqNVl1v2zYU/SsXeomcOHKdDAOqOlnXoANWYO3QZk9RgCoy7TCRSYGknBie//sOLyVZcpuuD7b5ce+534feRr9XVbKuRZRGM1sYWTmywtUVlblaXmSRs1l0mSm5qrRxtCUjFmP67L+MyAsn12JM0vKB0/xTK8jQjhZGryiLgJ1FmcpUoZV1JJV0Mi/pwiPF01ej9qLQtXLNsT/N1GRCV/d5WQq1FDRN6Z9qnjvhBTK1qBWMa0U1H8brvKzFiLaZIoIe3C2TJPE7xk34Huj8m6kd4x8fQ+C4Z+QsxUYUjyQX5O4FfWXlrwiQcm+X9N2DKJzHPaa/8kfBUrp2Ve3oDk5m6ngSAtKlSEq9jHsO0W80pZRe+SNOWczwo/Z8TEfF3pWjTIUsfOPlOVKhnkxehVR83xVnfJzemy5VTeqvvNGQsJRUvboThv71JZ2FzeU+jS/i+rTuY+SKtyW4uLigqY+lb+4IoXDOBz40mxfC/CXlgwJ9hqqH/C+0waoyuhLGbQhB5WR1bQrfFqEdBzW6hu8BYM76KKTdqAK7J+nuSTrsg3qLGYyuapc7qZYc/IEEVMuy6Tu+55HI1ZzWshCna2Fs/mKH7MsSut7Cju/L1vuYU7/QOqXp2C/vcpPSGZa7blJwi2pBiQcuZgjkG8dHI181NJHPnzfczQFP0yAqn44QhA0+GrmUKi/RMIwfRubkZNjObCyBBNf5rJ3TAXKLRHlp9cAG92sHcYjdt8vw5ww/mwReAgth4wRCAgB2RLO5XPMCy6pZYGmrXNHbopTFIxisYQietdPpCHR2CkiIdArbbcM+O/To/2KcMMbJAGM2CeZnk+DRbNLzMxpHUs3Fc4I0uMRZUG1Dp25TCXCqr+YhX3aEuwqetddvcQ9w605rJ0uQc090Lnym7jwjuzGJ5wpzMEZX9sClVw183KjB+B/5SpabViaZNE9CI6acMIscA9BJXrPbHbmmffJgcgtz/c15yGJKQ/IBZVzSWst5T5X54VDwkKWgFtZekbsqpS2PTjh+E4YnbLiyocMO/GJealMXZ1EXZhaNKWYzHKt0uGzGnrmo4dUDsUCNjjxBgy8wplzBuIMdvQlicSORrFeUWzybj0o/gdDsMNGjpGm+169/xTx4zVDZ+KcBwjOTOP1uj+LppIvK3uu6BCdq8/hCNEbYukRFrDMY85tbhHVzuxdoRtg/sDJZqDjGphXug1EDlFS1vfdCTUTeG/97mKpBvB++fPqYBEy52MQBadTEdXB509qb4n8JOHfwHe5uR10i/AdT6ixiWchl8mC1wpSy01lU6FUlS2E+Vb7cGDm0WYDIIjxW+ukDn/WgoeP/Rnzn/ME++7Ms+hvuC7PGkHV3LjdLgeH01++/fBTPWHeXKz2vS0j/4PKzQB3ACr4lvdi7Ws3hdk+Ovf2T5x55urbvn51Qtg2qfdp3LM9MdPWD0PfunifnrIdERrv/AN1MdxQ=
// https://vuejs.org/api/reactivity-utilities.html#unref

<script setup lang="ts">
import { ref, Ref, reactive, isRef, toRef, unref } from "vue"

const initial = ref(10)
const count = ref(0)

// Challenge 1: Update ref
function update(value) {
  // impl...
  count.value = value
}

/**
 * Challenge 2: Check if the `count` is a ref object.
 * Make the output be 1
*/
console.log(
  // impl ? 1 : 0
  isRef(count) ? 1 : 0, 'challenge 2'
)

/**
 * Challenge 3: Unwrap ref
 * Make the output be true
*/
function initialCount(value: number | Ref<number>) {
  // Make the output be true
  console.log(unref(value) === 10, 'initialCount')
}

initialCount(initial)

/**
 * Challenge 4:
 * create a ref for a property on a source reactive object.
 * The created ref is synced with its source property:
 * mutating the source property will update the ref, and vice-versa.
 * Make the output be true
*/
const state = reactive({
  foo: 1,
  bar: 2,
})
const fooRef = toRef(state, 'foo') // change the impl...

// mutating the ref updates the original
fooRef.value++
console.log(state.foo === 2)

// mutating the original also updates the ref
state.foo++
console.log(fooRef.value === 3)

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
