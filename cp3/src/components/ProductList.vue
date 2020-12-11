<template>
<div class="wrapper">
  <div class="products">
    <div class="product" v-for="product in products" :key="product.id">
      <div class="info">
        <h2>{{product.name}}</h2>
        <p>{{product.type}}</p>
      </div>
      <div class="image">
        <img :src="'../../images/products/'+product.image">
      </div>
      <div class="price">
        <!-- <img src="../../images/PNG/Tag-2.png" height="50px"> -->
        <h2>{{product.price}}</h2>
        <button @click="addToCart(product)" class="auto">Add to Cart</button>
      </div>
    </div>
  </div>
</div>
</template>

<script>
import router from "../router"
export default {
  name: "ProductList",
  props: {
    products: Array
  },
  methods: {
    addToCart(product) {
      this.$root.$data.cart.push(product);
      router.push("Cart");
    }
  }
};
</script>

<style scoped>
.wrapper {
  color: #222a22;
  display: flex;
  align-items: center;
  justify-content: center;
}

.products {
  margin-top: 20px;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
}

.product {
  margin: 10px;
  margin-top: 50px;
  width: 200px;
}

.product img {
  border: 2px solid #222a22;
  height: 250px;
  width: 200px;
  object-fit: cover;
}

.product .image {
  display: flex;
  justify-content: center;
  margin-bottom: 5px;
}

.info {
  color: #222a22;
  text-align: left;
  align-items: left;
}

.info h2 {
  font-size: 15px;
  font-family:monospace;
}

.info p {
  font-style: italic;
  margin-bottom: 5px;
  font-size: 12px;
}

.price {
  display: flex;
  align-items: center;
  justify-content: center;
}

.price img {
  border: none;
  height: 50px;
  width: 20px;
}

button {
  height: 30px;
  background: #000;
  color: white;
  border: 5px;
}

.auto {
  margin-left: auto;
}
</style>
