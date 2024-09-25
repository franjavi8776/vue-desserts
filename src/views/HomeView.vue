<template>
  <div class="container-fluid">
    <div class="row my-5">
      <div class="col-9">
        <h2>Desserts</h2>
        <div class="d-flex flex-wrap justify-content-center">
          <div v-for="(postre, i) in postres" :key="i" class="p-2">
            <Card :postre="postre" @add-to-cart="addToCart" />
          </div>
        </div>
      </div>
      <div class="col-3">
        <ShoppingCart :cartItems="cartItems" />
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";
import Card from "../components/Card.vue";
import ShoppingCart from "@/components/ShoppingCart.vue";
// importart la data que era un json
import data from "../data/data.js";

//console.log(data);

const postres = ref(
  data.map((el) => {
    return {
      name: el.name,
      category: el.category,
      price: el.price,
      stock: el.stock,
      image: el.image.desktop,
      imageModal: el.image.thumbnail,
      quantity: 1,
    };
  })
);
//console.log(postres.value);

const cartItems = ref([]);

const addToCart = (postre) => {
  const itemEnCarrito = cartItems.value.find(
    (item) => item.name === postre.name
  );
  if (itemEnCarrito) {
    itemEnCarrito.quantity++;
  } else {
    cartItems.value.push({ ...postre });
  }
  //console.log(cartItems.value);
};
</script>

<style scoped>
h2 {
  margin-left: 165px;
}
</style>
