<template>
    <div class="carousel-container">
      <div class="carousel" :style="{ transform: `translateX(-${currentSlide * 100}%)` }">
        <!-- First Slide -->
        <div class="carousel-slide">
          <div class="slide-content">
            <div class="text-content">
              <div class="refurbished-badge">
                <span>REFURBISHED</span>
              </div>
              <h1>There are lots of ways to save</h1>
              <p>Choose savings and sustainability with refurbished tech.</p>
              <button class="cta-button">Save on tech</button>
            </div>
            <div class="image-content">
              <img 
                src="https://i.ebayimg.com/images/g/N40AAOSw1HxnPzXw/s-l960.webp" 
                alt="Black Friday Tech Deals"
                class="slide-image"
              />
            </div>
          </div>
        </div>
  
        <!-- Second Slide -->
        <div class="carousel-slide">
          <div class="slide-content">
            <div class="text-content">
              <h1>Refurbished is the right choice</h1>
              <p>Take part in a circular economy and save with refurbished tech.</p>
              <button class="cta-button">Save now</button>
            </div>
            <div class="product-grid">
              <div class="product-item">
                <img 
                  src="https://i.ebayimg.com/images/g/9AQAAOSwk3VnLKRW/s-l300.webp" 
                  alt="iPhone"
                />
                <p>Consumer electronics ›</p>
              </div>
              <div class="product-item">
                <img 
                  src="https://i.ebayimg.com/images/g/u1kAAOSw5EBnLKRa/s-l300.webp" 
                  alt="Kitchen Appliance"
                />
                <p>Kitchen appliances ›</p>
              </div>
              <div class="product-item">
                <img 
                  src="https://i.ebayimg.com/images/g/pb4AAOSw~yVnLKRc/s-l300.webp" 
                  alt="Speaker"
                />
                <p>Smart home ›</p>
              </div>
            </div>
          </div>
        </div>
      </div>
  
      <!-- Navigation -->
      <div class="carousel-nav">
        <div class="carousel-dots">
          <button 
            v-for="n in 2" 
            :key="n"
            :class="['dot', { active: currentSlide === n - 1 }]"
            @click="goToSlide(n - 1)"
          ></button>
        </div>
        <div class="nav-buttons">
          <button class="nav-button prev" @click="prevSlide">
            <i class="w3-icon">&#10094;</i>
          </button>
          <button class="nav-button next" @click="nextSlide">
            <i class="w3-icon">&#10095;</i>
          </button>
          <button class="nav-button pause" @click="toggleAutoplay">
            <i v-if="isPlaying" class="w3-icon">&#10074;&#10074;</i>
            <i v-else class="w3-icon">&#9658;</i>
          </button>
        </div>
      </div>
    </div>
  </template>
  
  <script setup>
  import { ref, onMounted, onUnmounted } from 'vue'
  
  const currentSlide = ref(0)
  const isPlaying = ref(true)
  const autoplayInterval = ref(null)
  const AUTOPLAY_DELAY = 2000
  
  const nextSlide = () => {
    currentSlide.value = (currentSlide.value + 1) % 2
  }
  
  const prevSlide = () => {
    currentSlide.value = currentSlide.value === 0 ? 1 : 0
  }
  
  const goToSlide = (index) => {
    currentSlide.value = index
  }
  
  const startAutoplay = () => {
    if (!autoplayInterval.value) {
      autoplayInterval.value = setInterval(nextSlide, AUTOPLAY_DELAY)
    }
  }
  
  const stopAutoplay = () => {
    if (autoplayInterval.value) {
      clearInterval(autoplayInterval.value)
      autoplayInterval.value = null
    }
  }
  
  const toggleAutoplay = () => {
    isPlaying.value = !isPlaying.value
    if (isPlaying.value) {
      startAutoplay()
    } else {
      stopAutoplay()
    }
  }
  
  onMounted(() => {
    startAutoplay()
  })
  
  onUnmounted(() => {
    stopAutoplay()
  })
  </script>
  
  <style scoped>
  .carousel-container {
    margin-top: 100px;
    position: relative;
    width: 100%;
    overflow: hidden;
    height: 50%;
    background-color: #f6f7f6;
  }
  
  .carousel {
    display: flex;
    transition: transform 0.5s ease-in-out;
  }
  
  .carousel-slide {
    min-width: 100%;
    height: 400px;
  }
  
  .slide-content {
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: space-between;
    height: 100%;
    max-width: 1200px;
    margin: 0 auto;
    padding: 0 2rem;
  }
  
  .text-content {
    flex: 1;
    padding-right: 2rem;
  }
  
  .image-content {
    flex: 1;
    display: flex;
    justify-content: center;
    align-items: center;
  }
  
  .refurbished-badge {
    display: inline-block;
    padding: 0.5rem 1rem;
    background: #000;
    color: #fff;
    border-radius: 20px;
    margin-bottom: 1rem;
  }
  
  h1 {
    font-size: 2.5rem;
    font-weight: bold;
    margin-bottom: 1rem;
    color: #000;
  }
  
  p {
    font-size: 1.1rem;
    color: #666;
    margin-bottom: 2rem;
  }
  
  .cta-button {
    padding: 0.8rem 1.5rem;
    background: #000;
    color: #fff;
    border: none;
    border-radius: 25px;
    font-size: 1rem;
    cursor: pointer;
    transition: background-color 0.3s;
  }
  
  .cta-button:hover {
    background: #333;
  }
  
  .slide-image {
    max-width: 100%;
    height: auto;
  }
  
  .product-grid {
    display: flex;
    justify-content: space-between;
    gap: 1rem;
  }
  
  .product-item {
    text-align: center;
    flex: 1;
  }
  
  .product-item img {
    width: 100%;
    max-width: 150px;
    height: auto;
    margin-bottom: 0.5rem;
  }
  
  .product-item p {
    font-size: 0.9rem;
    margin-bottom: 0;
  }
  
  .carousel-nav {
    position: absolute;
    bottom: 1rem;
    left: 0;
    right: 0;
    padding: 0 2rem;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  
  .carousel-dots {
    display: flex;
    gap: 0.5rem;
  }
  
  .nav-buttons {
    display: flex;
    gap: 0.5rem;
  }
  
  .nav-button {
    background: rgba(255, 255, 255, 0.8);
    border: 1px solid #ddd;
    border-radius: 50%;
    width: 40px;
    height: 40px;
    display: flex;
    align-items: center;
    justify-content: center;
    cursor: pointer;
    transition: background-color 0.3s;
  }
  
  .nav-button:hover {
    background: #fff;
  }
  
  .w3-icon {
    font-style: normal;
    font-size: 24px;
    line-height: 1;
  }
  
  .dot {
    width: 10px;
    height: 10px;
    border-radius: 50%;
    background: #ddd;
    border: none;
    cursor: pointer;
    padding: 0;
  }
  
  .dot.active {
    background: #000;
  }
  
  @media (max-width: 768px) {
    .slide-content {
      flex-direction: column;
      text-align: center;
      padding: 1rem;
    }
  
    .text-content {
      padding-right: 0;
      margin-bottom: 1rem;
    }
  
    .image-content {
      margin-bottom: 1rem;
    }
  
    h1 {
      font-size: 2rem;
    }
  
    .product-grid {
      flex-direction: column;
    }
  
    .carousel-slide {
      height: auto;
      min-height: 500px;
    }
  }
  </style>
  
  