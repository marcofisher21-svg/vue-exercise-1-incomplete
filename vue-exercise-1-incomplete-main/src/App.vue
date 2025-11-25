<template>
  <div>
    <HeaderBar :count="wishlist.length" />

    <CourseList 
      :courses="courses"
      @save="addToWishlist"
    />
  </div>
</template>

<script setup>
import { ref } from "vue"
import CourseList from "./components/CourseList.vue"
import HeaderBar from "./components/HeaderBar.vue"

const wishlist = ref([])

const courses = ref([
  { 
    id: 1,
    title: "Italian Pasta Mastery",
    chef: "Marco Rossi",
    price: "R219",
    skill: "Beginner",
    available: true,
    img: "https://i.postimg.cc/wTFCZSKq/images-q-tbn-ANd9Gc-Qc-Ad1V0f-VA3791Bi-JL1xl-VFOB5VX4h-XLJn-VQ-s.jpg"
  },
  { 
    id: 2,
    title: "Advanced Sushi Art",
    chef: "Yuki Tanaka",
    price: "R400",
    skill: "Expert",
    available: false,
    img: "https://i.postimg.cc/x1NhL1j3/a-chef-works-in-a-sushi-restaurant-tokyo-japan.jpg"
  },
  { 
    id: 3,
    title: "French Pastry Basics",
    chef: "Lyon Sin-clair",
    price: "R329",
    skill: "Intermediate",
    available: true,
    img: "https://i.postimg.cc/pXd8YFR0/images-q-tbn-ANd9Gc-TYb5dx-SEc61hz-LDmm-C6yac-MKVVba-X87VR509Y-Ejpkbpem45t-Zc-Aun-LI-s.jpg"
  },
  { 
    id: 4,
    title: "Advanced Dessert Art",
    chef: "James Ford",
    price: "R429",
    skill: "Expert",
    available: true,
    img: "https://i.postimg.cc/50bBvKPd/images-q-tbn-ANd9Gc-S7X0k-H-bjr-KN3u-VW-e-Barv-Cdb-Ldyzp-Sj3r-Tw-s.jpg"
  },
  { 
    id: 5,
    title: "Chinese Cuisine Mastery",
    chef: "Xiao Li",
    price: "R359",
    skill: "Intermediate",
    available: false,
    img: "https://i.postimg.cc/pV89xJk5/images-q-tbn-ANd9Gc-RL13TCD3c-Z98n-URe-Aw-L4PVHczru-VSy1Wsmjw-s.jpg"
  }
])

function addToWishlist(course) {
  // Prevent duplicates
  if (!wishlist.value.includes(course)) {
    wishlist.value.push(course)
  }
}
</script>

<style>
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
