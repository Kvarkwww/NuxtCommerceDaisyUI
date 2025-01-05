<script setup lang="ts">
  // Instead of importing from a utility, reference a local static image
  const heroImageUrl = '/images/Slideshow-BoardGames50.jpg'; // Replace with the name of your image

  // Hero content
  const heroCaption = 'Welcome To';
  const heroTitle = 'Rent-a-game 4 All';
  const heroDescription = 'Fun for all at just a call.';
</script>

<template>
  <section>
    <!-- Background image wrapper that uses the heroImageUrl -->
    <BackgroundImageWrapper :image-url="heroImageUrl">
      <div
        class="pb-36 pt-2 px-6 relative rounded-3xl md:pb-48 lg:pb-72 lg:px-12"
      >
        <div
          class="-mx-4 flex flex-wrap items-center justify-center mt-24 space-y-6 lg:space-y-0"
        >
          <div class="px-4 text-center w-full md:w-8/12 xl:w-6/12">
            <!-- Hero heading -->
            <h3
              class="dark:text-secondary-200 font-bold font-serif lg:capitalize mb-1 text-primary-600 uppercase"
            >
              New Arrivals & Back in Stock!
            </h3>
            <!-- Call to action button -->
            <UButton
              label="Shop Now"
              to="/store"
              size="xl"
              trailing
              class="mt-4"
            />
          </div>
        </div>
      </div>
    </BackgroundImageWrapper>
  </section>
</template>

<style scoped></style>
