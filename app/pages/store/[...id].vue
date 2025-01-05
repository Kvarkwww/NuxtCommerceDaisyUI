<script setup lang="ts">
definePageMeta({
  name: 'store',
  title: 'Store',
  description: `Shop 'til You Drop: Your E-Commerce Haven!`,
  navOrder: '3',
  hidden: true,
  type: 'primary',
  icon: 'i-mdi-home',
})

const route = useRoute()
const { id: productId } = route.params

// Fetch the product details using the product ID
const { fetchProduct } = await useProduct(+productId)
const { id, title, price, description, image, rating, badge, shipping } =
  fetchProduct()

useHead({
  title: title || '',
})

useServerSeoMeta({
  description: () => description || '',
})

// Options for renting durations
const durations = [
  { id: 1, name: '1 day', multiplier: 1 },
  { id: 2, name: '3 days', multiplier: 3 },
  { id: 3, name: '1 week', multiplier: 7 },
  { id: 4, name: '2 weeks', multiplier: 14 },
]

const selected = ref(durations[0].id)

// Compute the currently selected duration
const current = computed(() =>
  durations.find((duration) => duration.id === selected.value),
)

// Compute the price based on duration
const calculatedPrice = computed(() =>
  (parseFloat(price) * (current.value?.multiplier || 1)).toFixed(2),
)
</script>

<template>
  <section class="mx-4 my-16 product-details">
    <!-- Product Image -->
    <div class="flex justify-center max-h-96 xl:max-h-[600px]">
      <div class="-m-4 bg-white p-8 rounded-lg">
        <NuxtImg :src="image" class="max-h-full" />
      </div>
    </div>

    <!-- Product Details -->
    <div class="mt-8 md:mt-0 md:mx-8">
      <div class="relative">
        <UBadge v-if="badge" :label="badge" class="-top-7 absolute" />
        <h3>{{ title }}</h3>
      </div>

      <!-- Ratings and Reviews -->
      <div class="flex items-center justify-between mt-2">
        <div class="flex">
          <StarsRate class="mt-0.5 w-24" :value="rating.rate" />
          <div class="ml-2 text-sm">{{ rating.count }} reviews</div>
        </div>
        <div class="md:mr-4 text-xs text-primary-500 dark:text-primary-400">
          {{ shipping }}
        </div>
      </div>

      <!-- Price and Vendor -->
      <div class="flex items-center justify-between mt-4">
        <div>
          <span class="font-bold text-xl">${{ calculatedPrice }}</span>
        </div>
        <div class="md:mr-4"><span>Best Deals Inc.</span></div>
      </div>

      <!-- Rental Duration Selector -->
      <div class="mt-4">
        <USelectMenu
          v-model="selected"
          :options="durations"
          option-attribute="name"
          value-attribute="id"
          size="xl"
        >
          <template #label>
            <span>{{ current.name }}</span>
          </template>
        </USelectMenu>
      </div>

      <!-- Add to Cart Button -->
      <div class="mt-4 w-full">
        <button
          class="btn btn-primary rounded-lg w-full snipcart-add-item"
          :data-item-id="id"
          :data-item-name="title"
          :data-item-price="calculatedPrice"
          :data-item-url="`/store/${id}`"
          :data-item-image="image"
          :data-item-description="description"
          :data-item-custom1-value="current.name"
          :data-item-custom1-name="'Rental Duration'"
        >
          Add To Cart
        </button>
      </div>

      <!-- Product Description -->
      <div class="mt-8">
        <p>{{ description }}</p>
      </div>
    </div>
  </section>
</template>

<style scoped>
.product-details {
  display: grid;
  grid-template-columns: 1fr;
  grid-template-rows: auto auto;
  grid-template-areas: 'image' 'details';
}
@media (min-width: 768px) {
  .product-details {
    grid-template-columns: 1fr 1fr;
    grid-template-rows: auto;
    grid-template-areas: 'image details';
  }
}
</style>
