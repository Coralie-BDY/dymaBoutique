<template>
  <div class="d-flex flex-column p-5">
    <h5 class="border-bottom pb-3">Mon panier</h5>
    <cart-product-item v-for="item in cart" :key="item.id" :item="item"></cart-product-item>
    <template v-if="cart.length > 0">
      <hr class="w-100">
      <span>Total : {{ total | price }}</span>
    </template>
  </div>
</template>

<script>
import CartProductItem from './CartProductItem';

export default {
  props: ['cart'],
  components: {
    CartProductItem
  },
  computed: {
    total() {
      return this.cart.reduce((acc, v) => {
        acc += v.price;
        return acc;
      }, 0);
    }
  }
}
</script>

<style>

</style>