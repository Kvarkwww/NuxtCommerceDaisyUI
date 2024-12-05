<template>
    <form class="form-control w-full max-w-lg" @submit.prevent="submitForm">
      <div>
        <label class="label"><span class="label-text">Name</span></label>
        <input type="text" placeholder="Your Name" class="input input-bordered" v-model="name" required />
      </div>
      <div>
        <label class="label"><span class="label-text">Email</span></label>
        <input type="email" placeholder="Your Email" class="input input-bordered" v-model="email" required />
      </div>
      <div>
        <label class="label"><span class="label-text">Message</span></label>
        <textarea placeholder="Your Message" class="textarea textarea-bordered" v-model="message" required></textarea>
      </div>
      <button class="btn btn-primary mt-4">Send</button>
    </form>
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