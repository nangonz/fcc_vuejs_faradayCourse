<template>
  <main class="wrapper">
    <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(250px, 1fr)); gap: 10px;" class="recommended">

      <ProductCard
        v-for="(product) in inventory"
        :key="product.id"
        :product="product"
        :addToCart="addToCart"
      />

    </div>

  </main>

  <footer>
  </footer>
</template>

<script>
import ProductCard from '../components/ProductCard.vue'

export default {
  name: 'Products',
  props: ['inventory', 'addToCart'],
  components: {
    ProductCard
  }
}
</script>
