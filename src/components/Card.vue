<template>
  <div class="card">
    <img :src="postre.image" :alt="postre.name" width="350px" />
    <div class="card-body">
      <button
        @click="$emit('add-to-cart', postre)"
        class="btn btn-outline-danger bg-white text-danger position-absolute top-265 left-90"
      >
        Add to cart
      </button>
      <div>{{ postre.category }}</div>
      <div>{{ postre.name }}</div>
      <div>{{ postre.price }}</div>
    </div>
  </div>
</template>

<script setup>
defineProps({
  postre: Object,
  required: true,
});
</script>

<style scoped>
.top-265 {
  top: 315px;
}
.left-90 {
  left: 120px;
}
</style>
