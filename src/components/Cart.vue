<template>
  <div id="cart">
    <h1>Your shoping cart</h1>
    <ul>
      <template v-for="product in cart" :key="product.name">
        <li>
            <p>
                {{ product.count }}
                {{ product.name }}
            </p>
            <button class="right" v-on:click="remove(product)">X</button>
            <p class="right">
                {{ product.count*product.price }} Fr.
            </p>
        </li>
      </template>
    </ul>
    <div class="sum">
        <b>Sum <p class="right sum-number"> {{ sum(cart) }} Fr.</p></b>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Cart',
  props: {
    cart: Array,
    remove: Function
  },
    methods: {
        sum(cart) {
            let sum = 0

            for(var i = 0; i < this.cart.length; i++) {
                sum += cart[i].price*cart[i].count
            }

            return sum
    }
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
  margin: 0 0 0 10px;
  min-height: 30px;
}

p {
    display: inline;
    margin: 0;
}
b {
    margin: 10px;
}
button {

}

.right {
    float: right;
}
.sum {
    border-top: 1px solid;
}
.sum-number {
    border-bottom: double;
    position: relative;
    right: 23px;
}
</style>