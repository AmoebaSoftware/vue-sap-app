<template>
  <div id="app">
    <ProductTable v-bind:products="products" v-if="!isLoading"/>
  </div>
</template>

<script>
import ProductTable from './components/ProductTable.vue'
import axios from 'axios';

export default {
  name: 'App',
  components: {
    ProductTable
  },
  data() {
    return {
      isLoading: true,
      products: null
    }
  },
  mounted () {
    axios
      .get('https://services.odata.org/Experimental/OData/OData.svc/Products')
      .then(response => (this.products = response.data.value))
      .then(() => this.isLoading = false)
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

  pre {
    text-align: left;
  }
</style>
