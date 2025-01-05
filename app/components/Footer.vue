<template>
  <footer class="footer bg-neutral text-neutral-content p-10">
    <div class="flex flex-wrap justify-between">
      <!-- Leftt: Contact Information -->
      <div class="w-full md:w-1/6 p-4">
      </div>
      <div class="md:w-2/5 bggrey p-4">
        <div class="space-y-4">
          <h3 class="footer-title text-gray">Our Address</h3>
          <p>123 Board Game Street, Fun City, Playland</p>
          <p>Email: <a href="mailto:contact@renta-a-game.com" class="text-primary">contact@renta-a-game.com</a></p>
        </div>
      </div>
      <!-- Right: Contact Form -->
      <div class="w-full md:w-1/3 bggrey p-4">
      <form class="form-control space-y-4" @submit.prevent="submitForm">
        <div>
          <h3 class="footer-title text-gray">Contact Us</h3>
          <label class="label"><span class="label-text text-white">Name</span></label>
          <input type="text" placeholder=" Your Name" class="input input-bordered w-full" v-model="name" required />
        </div>
        <div>
          <label class="label"><span class="label-text text-white">Email</span></label>
          <input type="email" placeholder=" Your Email" class="input input-bordered w-full" v-model="email" required />
        </div>
        <div>
          <label class="label"><span class="label-text text-white">Message</span></label>
          <textarea placeholder=" Your Message" class="textarea textarea-bordered w-full" v-model="message" required></textarea>
        </div>
        <button class="btn btn-primary w-full mt-4">Send</button>
      </form>
    </div>
  </div>
  </footer>
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
