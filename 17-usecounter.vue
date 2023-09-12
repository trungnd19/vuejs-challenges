// Read more
// https://play.vuejs.org/#eNq1Vk1v4zYQ/SsDHWrFUeQ4Ti+u7e5mG6Atmm7RbttD1YMs0w43FCWQVOLA8H/vI6kvL7xOusAebImcNzNvPjjULnhblvFjxYJpMNOZ4qUhzUxVkkjlZj4werBIJM/LQhnakWJr2tNaFTkNoDRIJITSMLVOM0Z/avauqOzyfWl4ITXtEkmUc/n9lGSVL5ly63TbW++tjdFwCMmQfspLwXImDZl7RlkBvzpdCkbrSmbWpNUf0jgmLjMKz8/8+iqmFcP6ol5PYjBFGOSX17HlQN9Yz1SUhTVEuiptUM7tXfrAsKGYc9v4oqdCPWiwUIplRjwncjhKZCut2mhDLrnhqfgrFRWjOV1G8OISMD2Skznt9mc+MxnWBv+QYxvJPbCEYCyodYiQw1qRiK/D2keMqNptK6DQWYwfHZ1Zw+UTnPXeos7Pm22Uwz2ICc069BGsQ7rq9TiiDMc5cnmC46LjeIA78Htx8XqODfYoR9caHcs+kTmS3BWgp6xwJpTECXDoyNYissFGdaMB5pC+op+HwUOvby5diWcjf/Bw0LAwDGcgNQwrolm5cNgp7WqbtN/PRqUXLitjEM+bTPDsYZ4E8JYEToQU491iRh50XAHMWgX7/qKCi6JV8atDpdmoF0AQgdOKbWPDtImNxpBpR0nuo/HDJAneYJxAVZuLynChk6A3dVbMJmjJkE/klG1LHMeIlmxdKHabZvedlUduTfSUzXOJDqEf3t/9rdKyZOqkx1YNQ7GBxaN6QnpAqp8xedpeMopvNky9s/kJTao2DLXqvM1+/HD3y43Lza0fbIuIDM+ZHQPjugURBoUC3cHt7PgOj5nH4PXcjzii9CnlCMd5iGuvYRK4wiQBQK79mkxB0rVZEkSEdp8vvDvr6cnTcw16Y6TrUfd0JXVvhm1RW6vQJTrsmaHGCEi7WobIU03WW4WghsRrtMFbIUDLNwoY/3P5b9t4L4PHNbjh9wL8qobbID6BAle6hOFs1xOWG2zq+6ISKzfzbcJcnQ/C9X0XWpPo5y0myFlsihub6/qMXtZ222r1m6PJ9HUNednc9SlzTcGuXm3u6mjU/hZ092MqV/aG/KrRj799Nd/xSYNt/HaG/j+CvQQMmvhdXw2+YuCTV9OcnDLX9P8XBW1/GMlG45Za8038URcSI9kFilGCry0u2u+UJMCl470kQSpE8fSz2zOqYlGzn92z7OHI/keNNpri5TdLWD1ieLYyP8O8+PaPX+2Y6YR5saoE0CeEvzNdCIxse9It7KaSK9Du4RxbfEqisFxuPujbrWFSN0FZoi4jDo87o8Kg/HzoHd1JPKm/CPbB/j8erLGg

<script setup lang='ts'>
import { ref } from 'vue'

interface UseCounterOptions {
  min?: number
  max?: number
}

/**
 * Implement the composable function
  * 1. inc (+)
  * 2. dec (-)
  * 3. reset 
  * 4. min & max opotion support
 * Make sure the function works correctly
*/
function useCounter(initialValue = 0, options: UseCounterOptions = {}) {
  const count = ref(initialValue)

  function inc() {
    if(options.max) {
      if (count.value < options.max) {
        count.value++
      }
    } else {
      count.value++
    }
  }

  function dec() {
    if(options.min) {
      if (count.value > options.min) {
        count.value--
      }
    } else {
      count.value--
    }
  }

  function reset() {
    count.value = initialValue
  }

  return { count, inc, dec, reset }
}

const { count, inc, dec, reset } = useCounter(0)

</script>

<template>
  <p>Count: {{ count }}</p>
  <button @click="inc">
    inc
  </button>
  <button @click="dec">
    dec
  </button>
  <button @click="reset">
    reset
  </button>
</template>
