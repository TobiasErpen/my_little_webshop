<template>
    <div id="product">
        <h3>
            {{ product.name }}
        </h3>
        <p class="right">
            price: {{ product.price }}
        </p>
        <br/>
        <p class="right">
            available: {{ product.count }}
        </p>
        <br/>
        <button v-on:click="addToChart(product)" class="right">Add to Cart</button>
    </div>
</template>

<script>
export default {
  name: 'Product',
  props: {
    product: Object,
    addToChart: Function
  }
}
</script>


<style scoped>
h3 {
    float: left;
    margin: 0;
}
.right {
    margin: 0;
    float: right;
}
</style>