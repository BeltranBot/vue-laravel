<template>
  <div class="col-md-4">
    <div class="thumbnail">
      <img src="https://cdn2.iconfinder.com/data/icons/virtual-keyboard/512/barcode-ean-code-item-coding-product-512.png" alt="">
      <div class="caption">
        {{ product.user_id }}
        <h3>{{ product.name }}</h3>
        <p>{{ product.price }} </p>
        <p>
          <a href="#" class="btn btn-default">
            Wish List
          </a>
          <a href="#" class="btn btn-success">
            Buy
          </a>
        </p>
      </div>
    </div>
  </div>
</template>
<script>
  export default {
    props: ['product']
  }
</script>
<style>
</style>
