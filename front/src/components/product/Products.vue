<template>
  <div class="row">
      <my-product
        v-for="product in products"
        :authenticatedUser="authenticatedUser"
        :product="product">
      </my-product>
  </div>
</template>
<script>
  import Product from './Product.vue'
  export default {
    data () {
      return {
        products: [],
      }
    },
    created () {
      this.$http.get('api/products')
          .then(response => {
            this.products = response.body
          })
    },
    computed: {
      authenticatedUser() {
        return this.$auth.getAuthenticatedUser()
      }
    },
    components: {
      'my-product': Product
    }
  }
</script>
<style></style>
