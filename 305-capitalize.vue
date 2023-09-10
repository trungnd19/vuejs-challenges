// LINK
// https://play.vuejs.org/#eNqFVNtu2zAM/RXBL3YwV9nQtywtekGBdUC3Yt32Mu/Bs+lGrWwJuiTpgvz7SDpOXCDoAiSxSR6S55DSJrm0Vi4jJLNk7iunbBAeQrTnhSs61VrjgtgIB43YisaZVqQYnI6cdy+3nY1h55TT3TvlTD9SHH0r0/kglqWOIM4oW1YkRTIh13zal+WCbAjQWl0GYIsQ86HC8qQ1NWhZlVaFUqu/cFYknLNIzudDYUbNp6+SJHmiuhrWMoAPMngku6fWmtiFgVyRXGDfCPbhJAalPbZ5UKEGavUP5EKFXMDaQjVCLhXBCLCHoLaDV053QvcBQyrU4UCnSHKRTcTZudgQcRXQ6xcm6lqsjHsmd+lfumoUI0Qv7cqV1oJDcZlPhsUmvb9clWrvlw3qkKWKhEonEif9k/TDOgvQ2tBIGNRzy46jQEMLHU6YoBMZzBUl+DRKsMVf+qLuwWODjXqUT950qDt3jaRNa5UG99UGhQSKZDbwKZISE60+sy24CPlgrxZQPR+xP/k12Yrk3oEHtyQdB18o3SPgUMh98/AF1vi8d+I6RY3Rbzi/gTcaN8F0fdhV7GpsexTH3d7yvFX3+N3frAN0fiBFjbIiHI9LEuH6DeqHdk/lKeNQSFRxdKiOHtR+Cawz1uMK1IADg3t6yzb9IeKTw7OeiYfgsNN85LgztWoUOI+tELqMOsx2q5htcJxbQdE40lfnGVrcrKHcDb747FcabY3HbnYomP7ew5rYVUSakf3mwQTZcydCaDjcESB7Lfot44uEQlSTMUv5uu/RnTDKR58hH//LalG6y5C9p639Qat9XXpAnu92fq9VBdkHbpjQ2+GBGs6OcMt7IAM4+P/XGR8jEV4sXV+Bl07MOAu+H1Kj9YJD0bqXC43TYxccX3Lbf2Qj/LI=

// DOC
// https://vuejs.org/guide/components/v-model.html#handling-v-model-modifiers

// Some notes:
// For this to actually work though, the <CustomInput> component must do two things:

Bind the value attribute of a native <input> element to the modelValue prop
When a native input event is triggered, emit an update:modelValue custom event with the new value
Here's that in action:

<!-- CustomInput.vue -->
<script setup>
defineProps(['modelValue'])
defineEmits(['update:modelValue'])
</script>

<template>
  <input
    :value="modelValue"
    @input="$emit('update:modelValue', $event.target.value)"
  />
</template>
  
Now v-model should work perfectly with this component:

template
<CustomInput v-model="searchText" />
