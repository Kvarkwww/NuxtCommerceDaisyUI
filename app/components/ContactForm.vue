<template>

  </template>
  
  <script setup>
  import { ref } from 'vue'
  
  const name = ref('')
  const email = ref('')
  const message = ref('')
  
  const submitForm = () => {
    console.log({ name: name.value, email: email.value, message: message.value })
  }
  </script>