<template>
  <div id="searchbar">
    <h1>Search</h1>
    <input type="text" v-model="searchText">
    <button v-on:click="search(searchText)">Search</button>
    <button v-on:click="search('')">Clear Search</button>
  </div>
</template>

<script>
export default {
  name: 'SearchBar',
  props: {
      search: Function
  },
  methods: {
      popUp(str) {
          alert(str)
      }
  }
}
</script>

<style scoped>
h1 {
    text-align: center;
}
</style>