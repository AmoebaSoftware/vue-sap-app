<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <ProductTable v-bind:products="products"/>
  </div>
</template>

<script>
import ProductTable from './components/ProductTable.vue'

export default {
  name: 'App',
  components: {
    ProductTable
  },
  data() {
    return {
      products: [
        {
          id: 1,
          name: 'Test Name 1',
          description: 'Test Description 1',
          rating: 1
        },
        {
          id: 2,
          name: 'Test Name 2',
          description: 'Test Description 2',
          rating: 2
        },
        {
          id: 3,
          name: 'Test Name 3',
          description: 'Test Description 3',
          rating: 3
        }
      ]
    }
  }
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
<style lang='scss'>
  @import "./scss/main.scss";
</style>
