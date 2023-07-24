<template>
  <main class="wrapper">
    <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(250px, 1fr)); gap: 10px;" class="recommended">

      <div
        class="card"
        v-for="(product) in inventory"
        :key="product.id"
      >
        <div class="card-title">
          {{ product.name }}
        </div>
        <div class="card-body">
          <i :class="`icofont-10x icofont-${product.icon}`"></i>
          <form>
            <div class="row">
              <div class="cell">
                <label>Tipo:</label>
              </div>
              <div class="cell">
                <em>{{ product.type }}</em>
              </div>
            </div>
            <div class="row">
              <div class="cell">
                <label>Precio:</label>
              </div>
              <div class="cell">
                ${{ product.price.USD }}
              </div>
            </div>
            <div class="row">
              <div class="cell">
                <label>Cantidad:</label>
              </div>
              <div class="cell">
                <!-- <input
                  @keyup.enter.prevent="addToCart(product.name, index)"
                  type="number"
                  min="1"
                  v-model.number="product.quantity"
                /> -->
              </div>
            </div>
          </form>
        </div>
        <div class="card-footer">
          <!-- <button @click.prevent="addToCart(product.name, index)" class="btn btn-light">
            Add to cart
          </button> -->
        </div>
      </div>

    </div>

  </main>

  <footer>
  </footer>
</template>

<script>
import food from '../food.json'
export default {
  name: 'Products',
  data () {
    return {
      inventory: food
    }
  }
}
</script>
