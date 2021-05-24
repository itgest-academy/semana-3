<template>
  <div class="col">
    <div class="card shadow-sm">
      <svg class="bd-placeholder-img card-img-top" width="100%" height="225" xmlns="http://www.w3.org/2000/svg" role="img" aria-label="Placeholder: Thumbnail" preserveAspectRatio="xMidYMid slice" focusable="false"><title>Placeholder</title><rect width="100%" height="100%" fill="#55595c"></rect><text x="50%" y="50%" fill="#eceeef" dy=".3em">Thumbnail</text></svg>

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
