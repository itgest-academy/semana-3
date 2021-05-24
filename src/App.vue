<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">

    <div class="container">
      <div class="row row-cols-1 row-cols-sm-2 row-cols-md-3 g-3">
        <Product
          v-for="(product, index) in products"
          :key="product.id"
          :product="product"
          :index="index" />
      </div>
    </div>
  </div>
</template>

<script>
import Product from '@/components/Product.vue'

export default {
  name: 'App',

  components: {
    Product
  },

  data () {
    return {
      products: [
        {
          id: 1,
          photo: 'Rato-computador.jpg',
          name: 'Rato',
          quantity: 2,
          price: 10
        },
        {
          id: 2,
          photo: 'teclado-computador.jpg',
          name: 'Teclado',
          quantity: 10,
          price: 15
        },
        {
          id: 3,
          photo: 'ecra-monitor.png',
          name: 'Monitor',
          quantity: 2,
          price: 200
        }
      ]
    }
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
