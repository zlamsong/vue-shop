<template>
  <div class="card my-5">
    <div class="card-body">
      <h4 class="text-center card-title">{{product.title}}</h4>
      <p class="text-center card-text text-muted display-4">${{product.price}}</p>
      <button :disabled="isInCart" @click="$emit('add-to-cart', product)" class="btn btn-primary form-control">
          {{isInCart ? 'Added to Cart':'Add to Cart'}}
      </button>
    </div>
  </div>
</template>
<script>
export default {
    props: ['product', 'isInCart']
}
</script>
