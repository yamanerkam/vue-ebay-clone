<template>
    <div class="watch-carousel">
      <h2 class="section-title">Wristwatches</h2>
      <p class="subtitle">Recommended for you</p>
      
      <div class="carousel-container">
        <button @click="prevSlide" class="nav-button prev" :disabled="currentIndex === 0">
          <i class="fa fa-chevron-left"></i>
        </button>
        
        <div class="carousel-wrapper" ref="carouselWrapper">
          <div class="carousel-content" :style="{ transform: `translateX(-${currentIndex * cardWidth}px)` }">
            <ProductCard
              v-for="product in products"
              :key="product.id"
              :product="product"
            />
          </div>
        </div>
        
        <button @click="nextSlide" class="nav-button next" :disabled="currentIndex === maxIndex">
          <i class="fa fa-chevron-right"></i>
        </button>
      </div>
    </div>
  </template>
  
  <script setup>
  import { ref, computed, onMounted, onUnmounted } from 'vue';
  import ProductCard from './ProductCard.vue';
  
  const products = [
    {
      id: '116233',
      name: 'Rolex Datejust ref. 116233 - Racing Silver Dial - Jubilee - Full Set',
      price: 10883.73,
      imageUrl: 'https://i.ebayimg.com/images/g/jn8AAOSwIqpnRGnM/s-l1600.webp'
    },
    {
      id: '114060',
      name: 'Rolex Submariner No Date - Black Dial - Oyster',
      price: 13250.00,
      imageUrl: 'https://i.ebayimg.com/images/g/8CYAAOSwwU9nRFpJ/s-l1600.webp'
    },
    {
      id: '126710BLNR',
      name: 'Rolex GMT-Master II "Batman" - Blue/Black Bezel',
      price: 17995.00,
      imageUrl: 'https://i.ebayimg.com/images/g/LykAAOSw2yBlTWic/s-l1600.webp'
    },
    {
      id: 'SPB143J1',
      name: 'Seiko Prospex 62MAS Reinterpretation - Grey Dial',
      price: 1200.00,
      imageUrl: 'https://i.ebayimg.com/images/g/igUAAOSw1-hm-vcx/s-l1600.webp'
    },
    {
      id: 'PAM01312',
      name: 'Panerai Luminor Marina - 44mm - White Dial',
      price: 7100.00,
      imageUrl: 'https://i.ebayimg.com/images/g/7HMAAOSwPjBmAJxW/s-l1600.webp'
    },
    {
      id: 'IW327001',
      name: 'IWC Pilots Watch Mark XVIII - Black Dial',
      price: 4350.00,
      imageUrl: 'https://i.ebayimg.com/images/g/OIIAAOSwp1Zjf7th/s-l1600.webp'
    },
    {
      id: '215.30.44.21.01.001',
      name: 'Omega Seamaster Diver 300M - Black Dial - Co-Axial Master Chronometer',
      price: 5200.00,
      imageUrl: 'https://i.ebayimg.com/images/g/GUwAAOSwj6NmBDWK/s-l960.webp'
    },
    
  ];
  
  const currentIndex = ref(0);
  const cardWidth = 270;
  const carouselWrapper = ref(null);
  const containerWidth = ref(0);
  
  const updateContainerWidth = () => {
    if (carouselWrapper.value) {
      containerWidth.value = carouselWrapper.value.offsetWidth;
    }
  };
  
  onMounted(() => {
    updateContainerWidth();
    window.addEventListener('resize', updateContainerWidth);
  });
  
  onUnmounted(() => {
    window.removeEventListener('resize', updateContainerWidth);
  });
  
  const visibleCards = computed(() => Math.floor(containerWidth.value / cardWidth));
  
  const maxIndex = computed(() => Math.max(0, products.length - visibleCards.value));
  
  const nextSlide = () => {
    if (currentIndex.value < maxIndex.value) {
      currentIndex.value++;
    }
  };
  
  const prevSlide = () => {
    if (currentIndex.value > 0) {
      currentIndex.value--;
    }
  };
  </script>
  
  <style scoped>
  @import url('https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css');
  
  .watch-carousel {
    max-width: 1200px;
    margin: 0 auto;
    padding: 20px;
  }
  
  .section-title {
    font-size: 24px;
    margin-bottom: 8px;
  }
  
  .subtitle {
    color: #666;
    margin-bottom: 24px;
  }
  
  .carousel-container {
    position: relative;
    display: flex;
    align-items: center;
  }
  
  .carousel-wrapper {
    overflow: hidden;
    width: 100%;
  }
  
  .carousel-content {
    display: flex;
    transition: transform 0.3s ease;
    gap: 20px;
  }
  
  .nav-button {
    background: #f0f0f0;
    border: none;
    font-size: 18px;
    padding: 10px;
    cursor: pointer;
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
    z-index: 1;
  }
  
  .nav-button:disabled {
    opacity: 0.5;
    cursor: not-allowed;
  }
  
  .nav-button.prev {
    left: -20px;
  }
  
  .nav-button.next {
    right: -20px;
  }
  </style>
  
  