<template>
    <header class="top-bar spread">
      <nav class="top-bar-nav">
        <router-link to="/" class="top-bar-link">
          <i class="icofont-spoon-and-fork"></i>
          <span>Home</span>
        </router-link>
        <router-link to="/products" class="top-bar-link">
          <span>Products</span>
        </router-link>
        <router-link to="/past-orders" class="top-bar-link">
          <span>Past Orders</span>
        </router-link>
      </nav>
      <div @click="toggleSidebar" class="top-bar-cart-link">
        <i class="icofont-cart-alt icofont-1x"></i>
        <span>Cart items ({{ totalQuantity }})</span>
      </div>
    </header>
  <router-view :inventory="inventory" :addToCart="addToCart" :checkout="checkout" :pastOrders="pastOrders"/>

  <Sidebar
    v-if="showSidebar"
    :toggle="toggleSidebar"
    :cart="cart"
    :inventory="inventory"
    :remove="removeItem"
    :checkout="checkout"
  />

</template>

<script>
import food from './food.json'
import Sidebar from './components/Sidebar.vue'

export default {
  components: {
    Sidebar
  },
  data () {
    return {
      showSidebar: false,
      inventory: food,
      cart: {},
      pastOrders: {}
    }
  },
  computed: {
    totalQuantity () {
      return Object.values(this.cart).reduce((acc, curr) => {
        return acc + curr
      }, 0)
    }
  },
  methods: {

    addToCart (name, quantity) {
      if (!this.cart[name]) this.cart[name] = 0
      this.cart[name] += quantity
      this.showSidebar = true
      console.log(this.cart)
    },

    toggleSidebar () {
      this.showSidebar = !this.showSidebar
    },

    removeItem (name) {
      delete this.cart[name]
    },
    checkout (order) {
      alert('thanks for visiting Yummi')
      this.pastOrders = order
    }
  }
}
</script>
