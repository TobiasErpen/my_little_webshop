<template>
  <div id="app">
    <div class="container">
      <SearchBar :search="filterProducts"/>
    </div>
    <div class="container">
      <Products :products="products" :addToChart="addToChart"/> 
    </div>
    <div class="container">
      <Cart :cart="cart" :remove="reomveFormCart"/>
    </div>
  </div>
</template>

<script>
import SearchBar from '@/components/SearchBar.vue'
import Products from '@/components/Products.vue'
import Cart from '@/components/Cart.vue'

export default {
  name: 'App',
  components: {
    SearchBar,
    Products,
    Cart
  },
  data() {
    return {
      products: [],
      fullProductsList: [
        { id: 1,
        name: "Schiff",
        img: "",
        price: 1000.0,
        count: 4 },
        { id: 2,
        name: "Auto",
        img: "",
        price: 220.0,
        count: 3 },
        { id: 3,
        name: "Velo",
        img: "",
        price: 30.0,
        count: 10 }
      ],
      cart: [
      ]
    }
  },
  created() {
    this.products = this.fullProductsList
  },
  methods: {
    productIsInChart(product, cart) {
      for (var i = 0; i < cart.length; i++) {
        if (cart[i].id == product.id){
          return true
        }
      }

      return false
    },
    filterProducts(filterName) {
      if (filterName === undefined ){
        this.products = this.fullProductsList
      } else {
        this.products = []
        let inputUpper = filterName.toUpperCase()
        for (var i = 0; i < this.fullProductsList.length; i++){
          if (this.fullProductsList[i].name.toUpperCase().includes(inputUpper)){
            this.products.push(this.fullProductsList[i])
          }
        }
      }
    },
    addToChart(product) {
      if (product.count > 0){
        product.count -= 1

        if (this.productIsInChart(product, this.cart)){
          for (var i = 0; i < this.cart.length; i++) {
            if (this.cart[i].id == product.id){
              this.cart[i].count++
          }
        }
        } else {
          let productForCart = {
            id: product.id,
            name: product.name,
            img: product.img,
            price: product.price,
            count: 1
          }

          this.cart.push(productForCart)
        }

      } else {
        alert(`Product ${ product.name } is not available`)
      }
    },
    reomveFormCart(product) {
      let index = this.cart.indexOf(product)
      
      if (index > -1) {
        this.cart.splice(index, 1);

        for (var i = 0; i < this.fullProductsList.length; i++) {
            if (this.fullProductsList[i].id == product.id){
              this.fullProductsList[i].count++
          }
      }
      }
    }
  }
}

</script>



<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}

.container {
  float: left;
  width: 33.3%
}
</style>
