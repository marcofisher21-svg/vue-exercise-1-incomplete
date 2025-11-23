<script setup>
import CourseCard from './CourseCard.vue'  // <-- Add this

const props = defineProps({
  courses: Array
})

const emit = defineEmits(['save'])
</script>

<template>
  <div class="course-grid">
    <CourseCard
      v-for="course in props.courses"
      :key="course.id"
      :course="course"
      @save="emit('save', course)"
    />
  </div>
</template>


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
