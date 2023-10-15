
<script setup>
import { ref,reactive } from 'vue';

      const currentIndex = ref(0)
      const images =reactive([
        'https://images.unsplash.com/photo-1697179426932-f9b744ca0c1d?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1470&q=80',
        'https://images.unsplash.com/photo-1697179426897-75090343fe83?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1470&q=80',
        'https://images.unsplash.com/photo-1697179426879-f9d536826c21?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1470&q=80',
        'https://plus.unsplash.com/premium_photo-1687419118871-da57d3f06edf?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1488&q=80',
      ]);

   function nextSlide() { 
      currentIndex.value = (currentIndex.value + 1) % images.length;
    };
    function prevSlide() {
      currentIndex.value = (currentIndex.value - 1 + images.length) % images.length;
    };

</script>
<template>
  <div class="carousel">
    <!-- {{ currentIndex }} -->
    <div class="carousel-container">
      <transition name="slide-fade" mode="out-in">
        <div :key="currentIndex" class="carousel-item">
          <img :src="images[currentIndex]" alt="Carousel Item" />
        </div>
      </transition>
    </div>
    <div class="carousel-controls">
      <button @click="prevSlide()" class="control-button">Previous</button>
      <button @click="nextSlide()" class="control-button">Next</button>
    </div>
  </div>


</template>


<style>
.carousel {
  text-align: center;
}

.carousel-container {
  position: relative;
  max-width: 100%;
  overflow: hidden;
}

.carousel-item {
  display: block;
}

.carousel-item img {
  width: 100%;
  height: auto;
}

.carousel-controls {
  margin-top: 10px;
}

.control-button {
  padding: 10px 20px;
  background-color: #007BFF;
  color: #fff;
  border: none;
  cursor: pointer;
}

.slide-fade-enter-active,
.slide-fade-leave-active {
  transition: opacity 0.5s;
}

.slide-fade-enter, .slide-fade-leave-to /* .slide-fade-leave-active in <2.1.8 */ {
  opacity: 0;
}
</style>