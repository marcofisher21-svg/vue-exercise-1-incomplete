<script setup>
const props = defineProps({
  count: {
    type: Number,
    default: 0
  }
})
</script>

<template>
  <header>
    <h1>Wishlist Count: {{ count }}</h1>
  </header>
</template>

<style scoped>
header {
  text-align: center;
  margin-bottom: 20px;
}
</style>
