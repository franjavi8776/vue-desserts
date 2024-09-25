<template>
  <div>
    <div class="card bg-white p-3">
      <div>Your Cart ({{ cartItems.length }})</div>
      <div v-if="cartItems.length === 0" class="text-center">
        <div>
          <i class="fa fa-shopping-bag fa-5x" aria-hidden="true"></i>
        </div>
        <span>Empty cart</span>
      </div>
      <div v-else>
        <div
          v-for="(item, i) in cartItems"
          :key="i"
          class="row align-items-center"
        >
          <div class="col-8 py-2">
            <div class="row">
              <div class="col-12">{{ item.name }}</div>
            </div>
            <div class="row">
              <div class="col-4">{{ item.quantity }}x</div>
              <div class="col-4">{{ item.price }}</div>
              <div class="col-4">{{ item.quantity * item.price }}</div>
            </div>
          </div>
          <div class="col-4">
            <button class="btn btn-outline-danger btn-sm">
              <i class="fa fa-trash" aria-hidden="true"></i>
            </button>
          </div>
        </div>
        <div class="row py-2 border-top border-1 border-black">
          <div class="col-6">Order Total</div>
          <div class="col-6">{{ totalAmount }}</div>
        </div>
        <div class="row">
          <button
            class="btn btn-outline-danger text-center"
            data-bs-toggle="modal"
            data-bs-target="#shoppingModal"
          >
            Confirm Order
          </button>
        </div>
      </div>
    </div>
    <ShoppingModal />
  </div>
</template>

<script setup>
import { computed } from "vue";
import ShoppingModal from "./ShoppingModal.vue";

const props = defineProps({
  cartItems: Array,
  required: true,
});
//console.log(props.cartItems);

const totalAmount = computed(() => {
  return props.cartItems.reduce(
    (total, item) => total + item.quantity * item.price,
    0
  );
});
</script>
