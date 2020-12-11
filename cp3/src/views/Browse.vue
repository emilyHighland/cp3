<template>
<div>
  <div class="pure-menu pure-menu-horizontal">
    <ul class="pure-menu-list">
      <li class="pure-menu-item"><a @click="select('Tops')" href="#" class="pure-menu-link"><img src="../../images/PNG/Shirt.png"></a></li>
      <li class="pure-menu-item"><a @click="select('Bottoms')" href="#" class="pure-menu-link"><img src="../../images/PNG/Skirt-2.png"></a></li>
      <li class="pure-menu-item"><a @click="select('Shoes')" href="#" class="pure-menu-link"><img src="../../images/PNG/Boots.png"></a></li>
      <li class="pure-menu-item"><a @click="select('Sale')" href="#" class="pure-menu-link"><img src="../../images/PNG/Sale.png"></a></li>
      <li class="pure-menu-item2"><a @click="select('Accessories')" href="#" class="pure-menu-link"><img src="../../images/PNG/Watch.png"></a></li>
    </ul>
  </div>
  <ProductList :products="products" />
</div>
</template>

<script>
import ProductList from "../components/ProductList.vue"
export default {
  name: 'Browse',
  components: {
    ProductList
  },
  data() {
    return {
      type: '',
    }
  },
  computed: {
    products() {
      return this.$root.$data.products.filter(product => product.type === this.type);
    }
  },
  methods: {
    select(type) {
      this.type = type;
    }
  }
}
</script>

<style scoped>
.pure-menu {
  justify-content: center;
  align-items: center;
}

.pure-menu-list {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
}

.pure-menu-item {
  list-style: none;
  margin-left: 10px;
  margin-right: 10px;
  justify-content: space-around;
  align-items: center;
}

img {
  width: 150px;
}

.pure-menu-item2 img{
  width: 70%;
}

button {
  background-color: inherit;
  border: none;
}
</style>
