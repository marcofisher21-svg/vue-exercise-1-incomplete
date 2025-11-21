<template>
  <div class="card" :class="{ soldout: !course.available }">
    <h3>{{ course.title }}</h3>
    <p>👨‍🍳 Chef: {{ course.chef }}</p>
    <p>💲 Price: {{ course.price }}</p>
    <p>📈 Skill: {{ course.skill }}</p>

    <p class="status" :class="{ unavailable: !course.available }">
      {{ course.available ? "Available" : "Sold Out" }}
    </p>

    <button 
      :disabled="!course.available"
      @click="saveToWishlist"
    >
      ❤️ Save
    </button>
  </div>
</template>

<script setup>
const props = defineProps({
  course: Object
})

const emit = defineEmits(['save'])

function saveToWishlist() {
  emit('save', props.course)
}
</script>

<style scoped>
.card {
  border: 1px solid #ddd;
  padding: 16px;
  border-radius: 8px;
  background: white;
}
.soldout {
  opacity: 0.6;
}
.status {
  font-weight: bold;
}
.unavailable {
  color: red;
}
button {
  margin-top: 10px;
}
</style>
