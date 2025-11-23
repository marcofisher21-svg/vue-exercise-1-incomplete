<template>
  <div class="card" :class="{ soldout: !course.available }">
    <div class="img-wrapper">
      <img :src="course.img" :alt="course.title" />

      <!-- Sold Out Banner -->
      <div v-if="!course.available" class="sold-out-banner">
        SOLD OUT
      </div>
    </div>

    <h3 class="title">{{ course.title }}</h3>

    <p class="detail">👨‍🍳 <strong>Chef:</strong> {{ course.chef }}</p>
    <p class="detail">💲 <strong>Price:</strong> {{ course.price }}</p>
    <p class="detail">📈 <strong>Skill:</strong> {{ course.skill }}</p>

    <button 
      class="save-btn"
      :disabled="!course.available"
      @click="saveToWishlist"
    >
      ❤️ Add to Wishlist
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
  background: #fff;
  border-radius: 14px;
  box-shadow: 0 4px 12px rgba(0,0,0,0.08);
  overflow: hidden;
  padding: 14px;
  max-width: 330px;
  transition: 0.2s;
}

.card:hover {
  transform: translateY(-4px);
  box-shadow: 0 6px 16px rgba(0,0,0,0.12);
}

.img-wrapper {
  position: relative;
  width: 100%;
  height: 180px;
  border-radius: 12px;
  overflow: hidden;
  margin-bottom: 12px;
}

img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.sold-out-banner {
  position: absolute;
  bottom: 10px;
  right: 10px;
  background: rgba(200, 0, 0, 0.85);
  color: white;
  font-weight: bold;
  padding: 6px 10px;
  border-radius: 6px;
}

.title {
  margin: 6px 0;
  font-size: 1.2rem;
  font-weight: bold;
}

.detail {
  color: #555;
  margin: 3px 0;
}

.save-btn {
  width: 100%;
  margin-top: 10px;
  padding: 10px;
  border: none;
  border-radius: 8px;
  background: #ff4d4d;
  color: white;
  font-size: 1rem;
  cursor: pointer;
  transition: 0.2s;
}

.save-btn:hover {
  background: #ff1f1f;
}

.save-btn:disabled {
  background: #bbb;
  cursor: not-allowed;
}

body {
  font-family: Arial, sans-serif;
  background: #f7f7f7;
  padding: 20px;
}

.wishlist-ping-enter-active {
  animation: pop 0.3s ease-out;
}

@keyframes pop {
  0%   { transform: scale(1); }
  50%  { transform: scale(1.4); }
  100% { transform: scale(1); }
}

</style>