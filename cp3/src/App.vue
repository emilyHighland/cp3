<template>
<div id="app">
  <div id="menu">
    <div id="brand">
      <router-link to="/">
        <img src="../images/PNG/Open-Sign.png">
        <h1>em's designs</h1>
      </router-link>
    </div>
    <div id="side">
      <router-link to="/browse">
        <div class="menu-item browse">
          <img src="../images/PNG/Mouse.png">
        </div>
      </router-link>
      <router-link to="/cart">
        <div class="menu-item cart">
          <p v-if="numberOfItems != 0">{{numberOfItems}}</p>
          <img src="../images/PNG/Cart.png">
        </div>
      </router-link>
    </div>
  </div>
  <router-view />
  <div class="github">
    <a href="https://github.com/emilyHighland/cp3.git" alt="github"><img src="../images/PNG/github.png" width="50px"></a>
  </div>
</div>
</template>

<script>
export default {
  computed: {
    numberOfItems() {
      return this.$root.$data.cart.length;
    }
  },
}
</script>

<style>
* {
  box-sizing: border-box;
}

body {
  margin: 50px 100px;
}

a, img {
  text-decoration: none;
}

#menu {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  grid-column-gap: 5px;
  grid-template-areas: "none brand side";
  margin-bottom: 50px;
}

#menu a {
  color: #B84901;
}

#brand {
  grid-area: brand;
  display: flex;
  justify-content: center;
}

#brand img {
  height: 200px;
}

#side {
  grid-area: side;
  display: flex;
  justify-content:flex-end;
}

#side img {
  width: 50px;
}

.menu-item {
  display: flex;
  flex-direction: column;
}

.menu-item p {
  margin: 0px;
  color: #800000;
}

.browse {
  margin-right: 50px;
}

.cart {
  margin-top: 25px;
}

h1 {
  color: #222a22;
  font-style: italic;
  text-align: center;
}

.github {
  display: flex;
  align-content: center;
  justify-content: center;
  font-weight: lighter;
  padding-top: 5%;
}
</style>
