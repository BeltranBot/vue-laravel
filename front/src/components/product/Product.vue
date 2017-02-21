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

          <hr>

          <p v-if="product.user_id == authenticatedUser.id">
            <button @click="deleteProduct" class="btn btn-danger">
              Delete
            </button>
          </p>
        </p>
      </div>
    </div>
  </div>
</template>
<script>
  import swal from 'sweetalert'
  export default {
    props: ['product', 'authenticatedUser'],

    methods: {
      deleteProduct() {
        swal({
          title: "Are you sure?",
          text: "You will not be able to recover this product!",
          type: "warning",
          showCancelButton: true,
          confirmButtonColor: "#DD6B55",
          confirmButtonText: "Yes, delete it!",
          closeOnConfirm: false
        },
        function(){
          this.$http.delete('api/products/' + this.product.id)
              .then(response => {
                console.log(response)
                swal("Deleted!", "Your product has been deleted.", "success")
              })
        }.bind(this)
      );
      }
    }
  }
</script>
<style>
</style>
