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
      <a @click="toggleSidebar" href="#" class="top-bar-cart-link">
        <i class="icofont-cart-alt icofont-1x"></i>
        <span>Cart items ({{ totalQuantity }})</span>
      </a>
    </header>
  <router-view :inventory="inventory" />

  <Sidebar 
    v-if="showSidebar" 
    :toggle="toggleSidebar" 
    :cart="cart"
    :inventory="inventory"
    :remove="removeItem"
  />

</template>

<script>
import food from './food.json'
import Sidebar from './components/Sidebar.vue';

export default {
  components: {
    Sidebar
  },
  data () {
    return {
      showSidebar: false,
      inventory: food,
      cart: {}
    }
  },
  computed:{
    totalQuantity() {
        return Object.values(this.cart).reduce((acc, curr)=>{
          return acc + curr
        }, 0)
      }
  },
  methods: {

    addToCart (name, index) {
      if(this.inventory[index].quantity <= 0 ) {
          alert('Not valid quantity')
      }
      if(!this.cart[name]) this.cart[name] = 0
      this.cart[name] += this.inventory[index].quantity
      this.inventory[index].quantity = 0
      this.showSidebar = true
      console.log(this.cart)
    },

    toggleSidebar () {
      this.showSidebar = !this.showSidebar
    },

    removeItem (name) {
      delete this.cart[name]
    }
  }
}
</script>
