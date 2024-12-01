<template>
  <div class="product-item">
    <div class="product-image-container">
      <img 
        :src="product.image" 
        :alt="product.title"
        class="product-image"
      />
      <div class="top-actions">
        <button 
          @click="toggleFavorite" 
          class="action-button"
          :aria-label="isFavorite ? 'Remove from favorites' : 'Add to favorites'"
        >
          <heart-icon 
            :fill="isFavorite ? '#000' : 'none'" 
            :stroke="isFavorite ? '#000' : '#000'" 
            size="20"
          />
        </button>
      </div>
      
      <div class="bottom-actions">
        <button 
          @click="showModal = true" 
          class="action-button"
          aria-label="Zoom image"
        >
          <search-icon size="20" />
        </button>
      </div>
    </div>
    
    <!-- Modal -->
    <ProductModal 
      v-if="showModal" 
      :show="showModal"
      :product="product"
      @close="showModal = false"
    />
    
    <div class="product-details">
      <div class="main-info">
        <h2 class="title">{{ product.title }}</h2>
        <p class="condition">{{ product.condition }}</p>
        
        <div class="pricing">
          <div class="price">
            <span class="currency">$</span>
            <span class="amount">{{ product.price.toFixed(2) }}</span>
          </div>
          <p class="offer">or Best Offer</p>
          <p class="shipping">+${{ product.shipping.toFixed(2) }} shipping</p>
          <p class="location">from {{ product.location }}</p>
        </div>
      </div>
      
      <div class="seller">
        <span class="seller-name">{{ product.seller.name }}</span>
        <span class="seller-rating">({{ product.seller.reviews }}) {{ product.seller.rating }}</span>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import { HeartIcon, SearchIcon } from 'lucide-vue-next'
import ProductModal from './ProductModal.vue'

const props = defineProps({
  product: {
    type: Object,
    required: true
  }
})

const isFavorite = ref(false)

const toggleFavorite = () => {
  isFavorite.value = !isFavorite.value
}

const showModal = ref(false)
</script>

<style scoped>
.product-item {
  display: flex;
  gap: 16px;
  padding: 12px;
}

.product-image-container {
  position: relative;
  width: 200px;
  flex-shrink: 0;
}

.product-image {
  width: 100%;
  height: 200px;
  object-fit: contain;
  border-radius: 4px;
}

.top-actions {
  position: absolute;
  top: 8px;
  right: 8px;
}

.bottom-actions {
  position: absolute;
  bottom: 8px;
  right: 8px;
}

.action-button {
  background: rgba(255, 255, 255, 0.9);
  border: none;
  border-radius: 50%;
  width: 32px;
  height: 32px;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  transition: transform 0.1s ease-in-out;
}

.action-button:hover {
  transform: scale(1.1);
}

.action-button:active {
  transform: scale(0.9);
}

.product-details {
  flex: 1;
  display: flex;
  justify-content: space-between;
  min-width: 0;
}

.main-info {
  flex: 1;
  min-width: 0;
}

.title {
  font-size: 16px;
  color: #333;
  margin: 0 0 4px 0;
  font-weight: normal;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}

.condition {
  color: #666;
  font-size: 13px;
  margin: 0 0 12px 0;
}

.pricing {
  margin-bottom: 12px;
}

.price {
  display: flex;
  align-items: baseline;
  margin-bottom: 2px;
}

.currency {
  font-size: 14px;
  margin-right: 1px;
}

.amount {
  font-size: 20px;
  font-weight: bold;
}

.offer,
.shipping,
.location {
  color: #666;
  margin: 2px 0;
  font-size: 13px;
}

.seller {
  text-align: right;
  margin-left: 16px;
  min-width: 150px;
}

.seller-name {
  color: #0066cc;
  text-decoration: none;
  margin-right: 8px;
  font-size: 13px;
}

.seller-rating {
  color: #666;
  font-size: 13px;
}

@media (max-width: 640px) {
  .product-item {
    flex-direction: column;
  }

  .product-image-container {
    width: 100%;
  }

  .product-details {
    flex-direction: column;
  }

  .seller {
    text-align: left;
    margin-left: 0;
    margin-top: 12px;
  }
}
</style>