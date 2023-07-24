<template>
  <div class="home">
    <h1>Home</h1>
    <div class="splash-container">
        <div class="splash">
          <h1>yummi</h1>
        </div>
      </div>

      <main class="wrapper">

        <h1 style="margin-bottom: 25px;">Recommended</h1>
        <br>

        <div class="recommended">

          <div
            class="card"
            v-for="(product, index) in inventory.slice(0, 3)"
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
                    <label>Type:</label>
                  </div>
                  <div class="cell">
                    <em>{{ product.type }}</em>
                  </div>
                </div>
                <div class="row">
                  <div class="cell">
                    <label>Price:</label>
                  </div>
                  <div class="cell">
                    ${{ product.price.USD }}
                  </div>
                </div>
                <div class="row">
                  <div class="cell">
                    <label>Quantity:</label>
                  </div>
                  <div class="cell">
                    <input @keyup.enter.prevent="addToCart(product.name, index)" type="number" min="1" v-model.number="product.quantity">
                  </div>
                </div>
              </form>
            </div>
            <div class="card-footer">
              <button @click="addToCart(product.name, index)" class="btn btn-light">
                Add to cart
              </button>
            </div>
          </div>
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

export default {
  name: 'Home',
  components: {
  }
}
</script>
