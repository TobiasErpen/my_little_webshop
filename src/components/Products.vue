<template>
  <div id="products">
    <h1>Products</h1>
    <ul>
      <template v-for="product in products" :key="product.name">
        <li>
          <Product :product="product" :addToChart="addToChart" />
        </li>
      </template>
    </ul>
  </div>
</template>

<script>
import Product from '@/components/Product.vue'

export default {
  name: 'Products',
  components: {
    Product
  },
  props: {
    products: Array,
    addToChart: Function
  }
}
</script>

<style scoped>
h1 {
    text-align: center;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  margin: 0 10px;
  min-height: 80px;
}
</style>