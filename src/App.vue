<template>
  <main>
    <HeaderBar :count="wishlist.length" />

    <CourseList 
      :courses="courses" 
      @save="addToWishlist" 
    />
  </main>
</template>

<script setup>
import { ref } from 'vue'
import HeaderBar from './components/HeaderBar.vue'
import CourseList from './components/CourseList.vue'

const wishlist = ref([])

const courses = ref([
  { id: 1, title: "Italian Pasta Mastery", chef: "Marco Rossi", price: "R250", skill: "Beginner", available: true  },
  { id: 2, title: "Advanced Sushi Art", chef: "Yuki Tanaka", price: "R450", skill: "Expert", available: false },
  { id: 3, title: "French Pastry Basics", chef: "Lyon Sin-clair", price: "R350", skill: "Intermediate", available: true }
])

  const imgsrc="https://i.postimg.cc/x1NhL1j3/a-chef-works-in-a-sushi-restaurant-tokyo-japan.jpg"
function addToWishlist(course) {
  if (!wishlist.value.includes(course)) {
    wishlist.value.push(course)
  }
}
</script>

<style scoped>
main {
  max-width: 800px;
  margin: 0 auto;
}
</style>
