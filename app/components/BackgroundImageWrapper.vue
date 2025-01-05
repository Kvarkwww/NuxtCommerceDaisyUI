<script setup lang="ts">
  const props = defineProps({
    imageUrl: {
      type: String,
      required: true, // Make this required to ensure an image URL is always passed
    },
    alt: {
      type: String,
      default: 'hero', // Default alt text
    },
    cover: {
      type: Boolean,
      default: true, // Default to cover styling
    },
    placeholder: {
      type: [Boolean, String],
      default: false, // Placeholder disabled by default
    },
  })

  // Define the computed background styles based on the provided imageUrl
  const bgStyles = computed(() => ({
    backgroundImage: `url('${props.imageUrl}')`,
    backgroundSize: props.cover ? 'cover' : 'contain',
    backgroundPosition: 'center',
    backgroundRepeat: 'no-repeat',
  }))
</script>

<template>
  <div class="bg-center bg-cover bg-no-repeat z-0" :style="bgStyles">
    <slot />
  </div>
</template>

<style scoped>
/* Optional additional styles if needed */
</style>
