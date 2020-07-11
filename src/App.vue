<template>
  <div id="app">
    <fd-shell-bar>
      <fd-shell-bar-group position="start">
        <fd-shell-bar-logo alt="SAP" src="'assets/sap-logo.png'" width="48" height="24" />
        <fd-shell-bar-product productTitle="Product Name" />
      </fd-shell-bar-group>
      <fd-shell-bar-group position="end">
        <fd-shell-bar-actions>
          <fd-shell-bar-action>
            <fd-shell-bar-user-menu ref="userMenu">
              <fd-menu>
                <fd-menu-list>
                  <fd-menu-item @click="closeUserMenu">
                    Settings
                  </fd-menu-item>
                  <fd-menu-item @click="closeUserMenu">
                    Sign out
                  </fd-menu-item>
                </fd-menu-list>
              </fd-menu>
            </fd-shell-bar-user-menu>
          </fd-shell-bar-action>
        </fd-shell-bar-actions>
      </fd-shell-bar-group>
    </fd-shell-bar>
    <fd-container centered>
      <ProductTable v-bind:products="products" v-if="!isLoading"/>
    </fd-container>
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
      .catch((err) => console.error(err))
  },
  methods: {
    closeUserMenu() {
      this.$refs.userMenu.close();
    }
  },
}
</script>

<style lang='scss'>
  @import "./scss/main.scss";
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
  }

  table {
    margin-top: 3rem;
  }
</style>

