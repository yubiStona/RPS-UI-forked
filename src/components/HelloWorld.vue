<script setup>
defineProps({
  // msg: {
  //   type: String,
  //   required: true,
  // },
})
import { ref, computed } from 'vue'
const name = ref('name here')
const uppercasedName = computed(() => name.value.toUpperCase())
</script>

<template>
  <div class="flex flex-col items-center justify-center min-h-screen">
    <h1 class="font-semibold text-4xl text-center mt-2 mb-4">
      this is the Result processing System frontend made in vue the dynamic system for the result
      processing and report generation

      test
      test
      tesst
      tesst
      tesst
      
    </h1>

    <input type="text" v-model="name" />
    <h1>{{ uppercasedName }}</h1>
  </div>
</template>
