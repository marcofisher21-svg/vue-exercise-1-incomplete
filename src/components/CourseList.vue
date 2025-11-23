<script setup>
import CourseCard from './CourseCard.vue'  // <-- Add this

const props = defineProps({
  courses: Array
})

const emit = defineEmits(['save'])
</script>

<template>
  <div>
    <CourseCard
      v-for="course in props.courses"
      :key="course.id"
      :course="course"
      @save="emit('save', course)"
    />
  </div>
</template>

<style scoped>
.course-card {
  border: 1px solid #ccc;
  padding: 10px;
  margin: 10px;
  cursor: pointer;
}
</style>
