<template>
  <div class="home">
    <div class="splash-container">
        <div class="splash">
          <h1>yummi</h1>
        </div>
      </div>

      <main class="wrapper">

        <h1 style="margin-bottom: 25px;">Recommended</h1>
        <br>

        <div class="recommended">
          <ProductCard
            v-for="(product) in inventory.slice(0, 3)"
            :key="product.id"
            :product="product"
            :addToCart="addToCart"
          />
        </div>

        <section style="margin: 80px;">
          <header>
            <h1>Know which fruits and vegetables you can find according to their seasonality.</h1>
          </header>
          <article>
            <h3>Autumn-Winter</h3>
            <p>Olives, chard, chicory, celery, celeriac, sweet potato, watercress, broccoli, cardoon,
              cauliflower, green onion, string beans, endive, spinach, fennel, turnip, rutabaga, leek,
              radish, radicchio, beet, cabbage, Brussels sprouts, carrot, pumpkin, squash, banana, plum,
              peach, lemon, tangerine, melon, quince, orange, avocado, peach, pear, grapefruit.
            </p>
          </article>
          <article>
            <h3>Spring</h3>
            <p>Beets, zucchini, radicchio, parsley, leek, beans, lettuce, turnip, turnip, chard, celery,
              artichoke, asparagus, strawberry, raspberry, cherry, blueberry, apple, orange, avocado, pineapple,
              banana, strawberry, lemon.
            </p>
          </article>
          <article>
            <h3>Summer</h3>
            <p>Squash, pumpkin, radish, tomato, asparagus, bell bell pepper, onion, string beans, cucumber, chard,
              eggplant, corn, raspberry, blackberry, apple, watermelon, grape, lemon, peach, pear, blueberry,
              strawberry, fig, fig, cantaloupe, melon, orange, pineapple, plum, cherry, apricot, peach.
            </p>
          </article>
        </section>
      </main>

      <footer>
      </footer>

  </div>
</template>

<script>
// @ is an alias to /src
import ProductCard from '../components/ProductCard.vue'

export default {
  name: 'Home',
  props: ['inventory', 'addToCart'],
  data () {
  },
  components: {
    ProductCard
  }
}
</script>
