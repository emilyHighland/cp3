<template>
<div class="wrapper">
  <div class="products">
    <div class="product" v-for="product in multipleProducts" :key="product.id">
      <div class="image">
        <img :src="'/images/products/'+product.image">
      </div>
      <div class="quantities">
        <div class="info">
          <h2>{{product.name}}</h2>
          <p>{{product.type}}</p>
        </div>
        <div class="price">
          <h3>Price: {{product.price}}</h3>
          <h3>Quantity: {{product.quantity}}</h3>
        </div>
        <button @click="removeFromCart(product)" class="auto">Remove From Cart</button>
      </div>
    </div>
  </div>
</div>
</template>

<script>
export default {
  name: "CartList",
  props: {
    products: Array
  },
  computed: {
    multipleProducts(){
      var multProducts = [];
      this.products.forEach((item) => {
        var index = multProducts.indexOf(item);
        if (index === -1) {
          item.quantity = 1;
          multProducts.push(item);
        } else {
          multProducts[index].quantity++;
        }
      });
      return multProducts;
    }
  },
  methods: {
    removeFromCart(product) {
      const index = this.$root.$data.cart.indexOf(product);
      this.$root.$data.cart.splice(index,1);
    }
  }
};
</script>

<style scoped>
.wrapper {
  display: flex;
  flex-flow:wrap;
}

.products {
  margin-top: 20px;
  display: flex;
  flex-flow: column;
  justify-content: space-around;
  align-items: center;
}

.product {
  margin: 10px;
  margin-top: 50px;
  width: 200px;
  display: inline-flex;
  justify-content: flex-start;
}

.product img {
  border: 2px solid #333;
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
  color: #000;
  padding-left: 10%;
  height: 100px;
  width: 150px;
  text-align: left;
}

.info h2 {
  font-size: 20px;
  text-align: left;
  font-style: italic;
}

.info p {
  font-size: 10px;
  font-style: italic;
}

.price {
  padding-left: 10%;
}

.price h3 {
  font-size: 16px;
}

button {
  height: 50px;
  width: 130px;
  background: #000;
  color: white;
  border: 5px;
}

.auto {
  margin-left: auto;
}
</style>
