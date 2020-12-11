<template>
<div>
  <h1> Your Cart </h1>
  <p v-if="cart.length === 0">Your cart is empty.</p>
  <CartList v-else :products="cart" />
</div>
</template>

<script>
import CartList from "../components/CartList.vue"
export default {
  name: 'Cart',
  components: {
    CartList
  },
  data() {
    return {
    }
  },
  computed: {
    cart() {
      return this.$root.$data.cart;
    }
  },
  methods: {
  }
}
</script>
