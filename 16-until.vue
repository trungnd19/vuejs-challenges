<script setup lang='ts'>
import { ref, Ref, watch } from "vue"

const count = ref(0)

/**
 * Implement the until function
*/

function until(initial: Ref<number>) {
  function toBe(desiredValue: number) {
    return new Promise((resolve) => {
      const stopWatch = watch(initial, (newValue, _) => {
        if(initial.value === desiredValue) {
          resolve(initial.value);
          stopWatch()
        }
      })
    })
  }

  return {
    toBe,
  }
}

async function increase() {
  count.value = 0
  setInterval(() => {
    count.value++
  }, 1000)
  await until(count).toBe(3)
  console.log(count.value === 3) // Make sure the output is true
}

</script>

<template>
  <p @click="increase">
    Increase, {{ count }}
  </p>
</template>

// Read more
// https://github.com/webfansplz/vuejs-challenges/issues/790
// https://play.vuejs.org/#eNp9VMtu2zoQ/ZWBNpVTXTkXuatcO+gDXaRAH2iLdhFlocpjm4lEEiRlOzD87z18SFaLIgZsizOHM2dmzuiYvda63PWcXWcL2xihHVl2vaa2lpvlC2df3FRSdFoZR0cyvC7oi//Z167Z0onWRnVUZYhQZZWsZKOkddSoXjpaenx+OfP2+cVFJemCbjvdcsfwui0TUKKldS8bJxRQF3OPHc7RnQspnKjba594IfvuJ5ubGR0RbrxJTr3hfFe3PV9ThCQEgYPrjSTJe/oMssJynhu2qt1xAecDN25Gy5sBTiDvS7BO6R+hyGUsduBRUI5Y332uglS7Ck+/RyAS6xFEy+WSArWRUvwkErkzcP0/9Yy586n9NDye0NHzP8z+L5WZMvh+FMkbALV9ks25X0I2hmu0InEKAysDS9R76U2Qwa10bGDMATvXN8G+fBlyFPTv5aWfM1G9r4VLgwvAWRlmcxW8vrWq5bJVm+gdUqJFVzOaz+lD/chke8NBH6p3unckLPkmpVIW8yhUCBMHx1BU7RgnooWmV00rmsdllQ0lVllwEd0mQ0HHY1LoKfR0MdeALOaTUFmB+ys+lI6tK53FeoxL0MWrg/RfQfu4at0/PYq2fg1G6Io91Z9IKVxBfNAQW0E7MVkc4a/G3UnXsJGDt5yn9YyAcXwrbuun3ImO0aE/FP+M3qdTxHi/xfvnbUgBo6zwG9o91JBXWRhrlWEDzpGEg8NuVd+uaK/Mo3cHsf2hGb9TSNS34GudEXJzdw+p3d2fAUkZsO5EuZZ5jsMA/n3BYqBS93brQZN9mKbbm1prNogXRpajlyMi6jQhyjWGjTJ0lUGuRmw2bHAMSoJpeiN2/r9B7pSGmr//+uljGamK9ZNvKQjOkvir7M7r9z7FCq3FFyJzFlTXYlM+WCUhslAhMqtOi5bNJ+3HDU1dD7VXWd22av8+2HzQsOXhzpabx7/YH+zB26rsM0hhnaGl0edqs2Goz7vfff3IBzyPzk6t+hboZ5xfvHIge7y7A+xNL1egPcEFtnjpQ9hozTf77uBY2qGouNX+DRLrhtLfPlP6me5VeTW83bLTLyVcPM4=
// https://vuejs-challenges.netlify.app/questions/16-until/readme.html
