<script setup lang="ts">
import { ref, watch } from "vue"

const count = ref(0)

/**
 * Challenge 1: Watch once
 * Make sure the watch callback only triggers once
*/
const unwatch = watch(count, () => {
  console.log("Only triggered once")
  unwatch()
})

count.value = 1
setTimeout(() => count.value = 2)

/**
 * Challenge 2: Watch object
 * Make sure the watch callback is triggered
*/
const state = ref({
  count: 0,
})

watch(state, () => {
  console.log("The state.count updated")
}, {
  deep: true

})

state.value.count = 2

/**
 * Challenge 3: Callback Flush Timing
 * Make sure visited the updated eleRef
*/

// user-created watcher callbacks are called before Vue component updates
// This means if you attempt to access the DOM inside a watcher callback, 
// the DOM will be in the state before Vue has applied any updates.
// If you want to access the DOM in a watcher callback after Vue has updated it, 
// you need to specify the flush: 'post' option:
const eleRef = ref()
const age = ref(2)
watch(age, () => {
  // Khi watch callback được gọi => vue dom chưa được update => eleRef là undefined
  // Sau khi thêm flush: 'post' => eleRef.value là <p>18</p>
  console.log(eleRef.value, 'ele ref') 
}, { flush: 'post'})
age.value = 18

// Cách khác
//watch(age, () => {
//  nextTick(() => {
//    console.log(eleRef.value);
//  });
//});
</script>

<template>
  <div>
    <p>
      {{ count }}
    </p>
    <p ref="eleRef">
      {{ age }}
    </p>
  </div>
</template>


// Read more
// https://vuejs.org/guide/essentials/watchers.html#callback-flush-timing
// https://play.vuejs.org/#eNqFVs1u20YQfpUBL6YMhbLjS6DKbhvXQZPWsREb7cH0YU0txbWoXYK7lCwYeoQe+gYteusp9xxd5D3yJv32hxLt2I4Bg9zd2Zn5vvk4o9vox6pK5g2PhtFIZ7WoDGlumopKJif7aWR0Gh2kUswqVRu6pZrnfVowkxW0orxWM0ojXE+jVKYyU1IbylQjDe1b03inZ/cH29uppG06LFhZcjnhtDuk350TJTPuzo7ZlJNuak6m4CFCBvMrlk1hVS7J1GIy4bUOd7YHbcBGevN9fy12CfQp7tH+Ad3CO1KSWpU8KdUkTqOTjjc+9u4iJEqtpxiLlcvcuUrmrGw43O+mEuScixlXjYm9//sWL5/A+3KN9+qaZ+bbiIXeZNjFqg0zNpAlN0BD/CHt9NuUPQJn9wwH5wjpbBJfrqYaYzF2PKz6/saY82qINFBe+PXe/R0HN9wE6Mcx7w3psIXzpmx0QWBOyMkD8HOhBSI7EkIWxEv+geceN1wPqNG8fpHV3J06hLxek6WJwY9d4fCK5wqr31COTEG1kq/RaefqvAC3M86kJpHTUjXEjOEzCN8oYlnGNahHLj+dHJOQWow5sa9C9sn5au0WoiwRGfZuyxepk0nBkGNVlQIJMrls80mck7c+iwVDoo+l8Eh4YrnBsnXd0iageufS+pPckqpIVzwTOQQPh7ktw5C2KqXNFqnKCCWHrbQ86UFbKLbfZaik37La9uLC3j1pIeIvhXgo4f/+/Pzxy6d/Mpp8+fSHsMZoFDRGy8iKzx/Z5tynbw1CCuXdX/gUxzwX0qrfBThjDU0RxBR3/84eAFnfDN+hvT+qDnZfjQYVmtd97Xct+7SFpUW31QNzVvj3XVvRA+2mA7wKgjy8+xtYpwUedv0YL7BCEW7QL7JpaBZh9+mEet95i5V/cY/RwDdmIMHCSrUEXQ7XaCzm7gWvHqn9u70NPXi1CmeBBmtlwaKvhy/M9vb1JVvqh1dGAx9iNOgEjvqRQHluEmjYJEZjeKwHxMxHbmfDD6g5rmrzojGixDDpzJIxt8CuwJkVLr+BUPGci85kQWfQxg+XcA3zqj1NBmF4eYO8kZkVNPyWbBkb36aHJJvZFa97Xqo1hlstUZcFncKL0DyOa45azPlGz2RnYNvmw2mfgkM3KKwuwFQKFjwGtFTf4N8wNLlymUb3vhBhYKAL1ZRoX6qe2mOmlzLr2HhVGKSomxJ5awwAObm4hOwuLjcGQTbYnYskl3GMRWvcdWaxWkdJBT1bo+8To86cWdzDey1mcc+B8XDs0xUvBqthzRZMmMDn7s6OneZ225cqfnd28j7xgdFgLFEI1+shzGv+8PCiTeqJ8Yvx1Z4/OZo6Nhd+jtLP58e/nrKaTWpWFUcln6HbX64tLz0+Vyz8Q7ZGg8JcTJJrrSRk67hKIzspRMnrE9cRodJhy2IaoZ2pxTu3Z0dhcI07Bc+mj+xf6xu7l0anIITX8w04/Jpi9YRDz/b46Ow9mkPncKbGTQnrZw4/WC3iQ1LSm71Gl0TaHTuX7Vv3qYD5c310YziGWADlZzkYcfbul9vhM9A36e4le+4eiIxW/wMRxW+U
