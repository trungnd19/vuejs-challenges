// Read more
// https://play.vuejs.org/#eNqtVE1PGzEQ/StTXzaJ0k0pN5pQoAKplQpV4YY5mM1kMXFsy/YmQVH+e8f2JlnUFvXQQ7Ky33vz+XY37NzactkgO2FjXzlpA3gMjQUldD0pgi9OuZYLa1yADTicwRZmziygIFHxiWuuR4MB1zCArwurcIE6gIDKkMSLR4Uwa3QVpNEQnkSAYOpaoacDgg8iYJJ+F3NMV3vyyrg5RXEOq6BeuB6MuN6Djce7FKcntQxSqNsYCSYwE8pjHzYUlMTaUzMtQpW/IvdT6dCpLgdsxZCF5VKoJsrfdY4R32Z1zGEUlsrUvfssGbaR4KGfOY7G6TT8Bkc0hcmF3r+CHyjnocvcVuSOR3lJtBQ6BKSRk4pOAGN7mjo7gc2mbfszFDfXBZzQ4+qqgO12PLItF84qJav5hLOckLMEAOSU+91AloxHnVxsyKSe4roM6EMZPHln75CFacgArUc4OyOXkNSH902QynPWMdMUYy+P1LMMQ8C1pVUflEsZZVGwl5BVd2g5an2bCbtQPc72U+NsCLTOyWneqAwEtrPPzREu/IuuOqSda1ZOWIuOlpD66VEyGv8Bt0cEtaRyRsM4V4rCW8769x9osx3mx78zj1pmbr1nj2ig69Dr98tgLmIv7T5peUTPbgIQKyFj3DI4WdfoiJdWmSj/FO76v0Zri6N3gv7jj+wRPHU/k3X57I0me6ThUmT6KkiF7sbGV47cQF7NWTgTSpnVt3QXXIPD3X31hNX8D/fPfh3vOPvh0KNbxn3usCBcjeSdCF/eXlPdHXBhpk10xxvgT6S3mgxrdKZdNHpKZXd4qVr64JEtpa7v/OU6oPa7pmKhaSKJT15u8MsbrR/KPS6P26/Llm1/ATL33n4=

<script setup lang='ts'>
import { ref } from 'vue';

/**
 * Implement a composable function that toggles the state
 * Make the function work correctly
*/
function useToggle(initialState = false) {
  const state = ref(initialState);

  function toggle() {
    state.value = !state.value
  }

  console.log([ state, toggle ])

  return [ state, toggle ]

}

const [state, toggle] = useToggle(false)

</script>

<template>
  <p>State: {{ state ? 'ON' : 'OFF' }}</p>
  <p @click="toggle">
    Toggle state
  </p>
</template>
