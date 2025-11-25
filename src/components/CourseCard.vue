<template>
  <div class="card" :class="{ soldout: !course.available }">
    <div class="img-wrapper">
      <img :src="course.img" :alt="course.title" />
      <div v-if="!course.available" class="sold-out-banner">
        SOLD OUT
      </div>
    </div>

    <h3 class="title">{{ course.title }}</h3>

    <p class="detail">👨‍🍳 <strong>Chef:</strong> {{ course.chef }}</p>
    <p class="detail">💲 <strong>Price:</strong> {{ course.price }}</p>
    <p class="detail">📈 <strong>Skill:</strong> {{ course.skill }}</p>

    <!-- Wishlist Button -->
    <button 
      class="save-btn"
      :disabled="!course.available"
      @click="saveToWishlist"
    >
      {{ isInWishlist ? '💔 Remove from Wishlist' : '❤️ Add to Wishlist' }}
    </button>

    <!-- Book Button -->
    <button 
      class="book-btn"
      :disabled="!course.available"
      @click="bookCourse"
    >
      📚 Book Course
    </button>
  </div>
</template>

<script setup>
const props = defineProps({
  course: Object,
  isInWishlist: Boolean
})

const emit = defineEmits(['toggleWishlist'])

// Emit to parent to toggle course in wishlist
function toggleWishlist() {
  emit('toggleWishlist', props.course)
}

// Handle add/remove wishlist with proper alert messages
function saveToWishlist() {
  if (!props.isInWishlist) {
    const confirmed = confirm(`Do you want to add: ${props.course.title} to your wishlist?`)
    if (confirmed) {
      toggleWishlist()
      alert(`You added: ${props.course.title} to your wishlist! ❤️`)
    }
  } else {
    const confirmed = confirm(`Do you want to remove: ${props.course.title} from your wishlist?`)
    if (confirmed) {
      toggleWishlist()
      alert(`You removed: ${props.course.title} from your wishlist ❌`)
    }
  }
}

// Booking confirmation
function bookCourse() {
  const confirmed = confirm(`Do you want to book: ${props.course.title}?`)
  if (confirmed) {
    alert(`You successfully booked: ${props.course.title} 🎉`)
  } else {
    alert(`Booking cancelled ❌`)
  }
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

/* Buttons */
.save-btn,
.book-btn {
  display: block;
  width: 100%;
  margin-top: 10px;
  padding: 10px;
  border: none;
  border-radius: 8px;
  font-size: 1rem;
  cursor: pointer;
  transition: 0.2s;
}

.save-btn {
  background: #ff4d4d;
  color: white;
}

.save-btn:hover {
  background: #ff1f1f;
}

.save-btn:disabled {
  background: #bbb;
  cursor: not-allowed;
}

.book-btn {
  background: #4CAF50;
  color: white;
}

.book-btn:hover {
  background: #45a049;
}

.book-btn:disabled {
  background: #bbb;
  cursor: not-allowed;
}
</style>
