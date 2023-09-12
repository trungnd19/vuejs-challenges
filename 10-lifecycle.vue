// Read more
// https://play.vuejs.org/#eNqtVk1v2zgQ/StcnWTUldLNLXCCboMukEW7W7Re9KKLLI1sJhQpkJRlw/V/7wxJfdht2hTNIQjN4Qxn5j2+0SH6q2mSbQvRVbQwheaNZQZs2zCRy/V1FlmTRTeZ5HWjtGUHpqGas0arLS+BHVmlVc2yCANk0XDqdsNF2ZuS1P2kO+hIJgsljWVbbvhKALumiLHVLcx6k+U16GCQrRCDoVCttMFwgbshjRizJJcsmnvfE5NzIpNboCmTVSsLy5VkVq3XAuIZO2SS9Skl21y0lNgfJxuZPGZykfoeYUfwh4W6EbkF/MXYouRbt8Clb8D2Ja+wgyFKFrG0tzdhgctVay1m8roQvHigfruUXM/9CcaWbit09VZhjyVgSX2E1IfoY6c++CL1+SzSSZbRPBrAeCrgSr6nxkE5V/J/WYc14/IeCsvmH6E6Z8EJjld4YCHbeoWQfmGtLKHiEsob7K8PMaJ3ivNTHAO2DtQhzxjxvL7xkKYpW24gMKrjQrBO6QeWr6TSdS7EnnUbQB7gmcK1t+jby7gJ9CgT9g6sYRXfMW4TCuviDTzpuCxVl2AX7/B+jdvTFJgvx59+8YK2jnP26uKCGHwMqQ+NnXoWAnI9hJzcOTg+kY4j3c44dMUOh/Cqjsjun/AH2YOVwi6xYGxiDTJoYIlLf9SD10gFdDT2ZWu5QEZNCFUCJb0C5JCdM9g1xKORQ5zcPI2CyzteQbHHbvydI1B6FJYgXZPow9EfS9AgACWIfO9aq1rshqdbkAONr0JLJqFjHzAONxDHGowSW5iii7AvvX9v9SqEG4gRgk1ouWoIySovgN05/i73DQSgHd/D7QO/xg3n3rcNaT9USbI2IQynN/H7fKeoudnL4ozF9DQrB8FnnTeN02iHe3yGkKu793D3jA4nARJ80uXAxjGMg+skSpDJ7/ljzd7qhIBcPKfi6c0J7LixJp7NEqvewFK3drOP3SMij7zLuQ1sCE9zUjPXxrpgt2EAnYbe1tguVKgHqTpJyxHfWeIlaprWWThK6H2OG3dSoMB9knljNoqQfBWUbUzQ15lYzddr0CSANDWeWLdU+Gh/tXYD+L90eDxL8efxnr/6XyDY75DCbrh+xr6chXu8LX9+05bHWKtabTfPl+F5vMdTvAyQOOXDP5wb1mBSFV8n90ZJnBtOU2h+1w0XoP9rSI1xTOBA8pdmEaqV6v5xe/R1OO/3iw0UD9/Zvzc72suiDyjDODJJHHubzfUacKiQ+e2nf2FHH4S9sVZlS1L6A+NHEnacZKQxdOwNfo5g2pNzLts7N4S4XC/N250FafqiKFE/+H3dOIiIlI+VPqZ7mVw6P2xkdPwKaqUFaA==
// https://vuejs.org/api/composition-api-lifecycle.html#onunmounted

<script setup lang="ts">
import { onMounted,onUnmounted, inject ,Ref} from "vue"

const timer:Ref<number | undefined> = inject("timer")
const count:Ref<number | undefined> = inject("count")

onMounted(() => {
  // The timer will work abnormally when the child component is toggled. Lets fix it.
  timer.value = window.setInterval(() => {
    count.value++
  }, 1000)
})

onUnmounted(() => {
  clearInterval(timer.value)
})

</script>

<template>
  <div>
    <p>
      Child Component: {{ count }}
    </p>
  </div>
</template>

// Note
// A component is considered unmounted after:
// + All of its child components have been unmounted.
// + All of its associated reactive effects (render effect and computed / watchers created during setup()) have been stopped.
// => Use this hook to clean up manually created side effects such as timers, DOM event listeners or server connections.
