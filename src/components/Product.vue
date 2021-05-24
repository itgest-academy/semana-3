<template>
  <div class="col">
    <div class="card shadow-sm">
      <img 
        alt="Vue logo" 
        :src="getPhoto(product)"
        height=200px>

      <div class="card-body">
        <h2>{{ index + 1 }} - {{ product.name }}</h2>
        
        <div class="d-flex justify-content-between align-items-center">
          <div class="btn-group">
            <span>{{ product.quantity }}</span>
          </div>
          <small class="text-muted">{{ product.price }} €</small>
        </div>

        <strong>{{ totalPrice }}</strong>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',

  props: {
    product: {
      type: Object,
      required: true
    },

    index: {
      type: Number
    }
  },

  computed: {
    totalPrice () {
      return this.product.quantity * this.product.price
    }
  },

  data () {
    return {
    }
  },

  methods: {
    getPhoto (product) {
      return require('@/assets/' + product.photo); 
     
    }
  },

  watch: {
  },

  created () {
  },

  mounted () {
  },
}
</script>

<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
