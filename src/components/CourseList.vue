<!-- CourseList.vue -->
<template>
  <div class="course-grid">
    <CourseCard
      v-for="course in courses"
      :key="course.id"
      :course="course"
      :isInWishlist="wishlist.includes(course)"
      @toggleWishlist="forwardToggle"
    />
  </div>
</template>

<script setup>
import { defineProps, defineEmits } from 'vue'
import CourseCard from './CourseCard.vue'

const props = defineProps({
  courses: Array,
  wishlist: Array  // <-- add this
})

const emit = defineEmits(['toggleWishlist'])

function forwardToggle(course) {
  emit('toggleWishlist', course)
}
</script>

<style scoped>
.course-grid {
  display: grid;
  gap: 20px;
  padding: 20px;

  /* Mobile: 1 column */
  grid-template-columns: 1fr;
}

/* Tablet: 2 columns */
@media (min-width: 600px) {
  .course-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

/* Desktop: 3 columns */
@media (min-width: 900px) {
  .course-grid {
    grid-template-columns: repeat(3, 1fr);
  }
}

</style>