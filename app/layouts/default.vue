<script setup lang="ts">
import { useHead } from '@vueuse/head'

// Add Snipcart scripts and styles to the head
useHead({
  script: [
    {
      src: 'https://cdn.snipcart.com/themes/v3.3.3/default/snipcart.js',
      async: true,
    },
  ],
  link: [
    {
      rel: 'stylesheet',
      href: 'https://cdn.snipcart.com/themes/v3.3.3/default/snipcart.css',
    },
  ],
})
</script>

<template>
  <div>
    <!-- Snipcart div for cart functionality -->
    <div
      id="snipcart"
      data-config-modal-style="side"
      data-api-key="NzZiNGUxOGUtYWE0OC00NzJkLThhZGEtZTg3Y2I1ODk2MzJiNjM4MDYzOTA1NzAyOTA4OTMw"
    ></div>

    <div class="min-h-screen flex flex-col bg-white dark:bg-neutral-950 text-neutral-900 dark:text-neutral-50">
      <NavBar />
      <main>
        <slot />
      </main>
      <Footer />
    </div>
  </div>
</template>

<style></style>
