<script setup lang="ts">
  const route = useRoute()
  const { category } = route.params

  const { fetchCategory } = await useProducts()
  const products = fetchCategory(category?.toString())

  const productsWithBadges = products.filter((product) => product.badge)
</script>
<template>
  <div>
    <UContainer class="py-8">
      <div
        class="-tracking-wide flex font-bold items-center justify-center text-5xl"
      >
        <span class="text-center text-primary">New Arrivals & Back in Stock</span>
        <UIcon name="i-twemoji-fire" class="ml-2" width="28px" />
      </div>
      <section
        data-pg-name="Products"
        class="flex flex-wrap justify-center mt-8"
      >
        <ProductCard
          v-for="(product, index) in productsWithBadges"
          :key="index"
          v-bind="product"
        />
      </section>
    </UContainer>
  </div>
</template>
<style scoped></style>
