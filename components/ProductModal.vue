<template>
  <div v-if="show" class="modal-overlay" @click="$emit('close')">
    <div class="modal-container" @click.stop>
      <button class="close-button" @click="$emit('close')">
        <x-icon size="24" />
      </button>

      <div class="modal-content">
        <div class="image-gallery">
          <div class="thumbnail-list">
            <img 
              :src="product.image" 
              :alt="product.title"
              class="thumbnail"
            />
          </div>
          <div class="main-image-container">
            <button class="nav-button prev" aria-label="Previous image">
              <chevron-left-icon size="24" />
            </button>
            <div class="main-image">
              <img :src="product.image" :alt="product.title" />
              <button class="favorite-button" @click="toggleFavorite">
                <heart-icon 
                  :fill="isFavorite ? '#4666ff' : 'none'" 
                  :stroke="isFavorite ? '#4666ff' : '#4666ff'" 
                  size="24" 
                />
              </button>
            </div>
            <button class="nav-button next" aria-label="Next image">
              <chevron-right-icon size="24" />
            </button>
          </div>
        </div>

        <div class="product-info">
          <h2 class="title">{{ product.title }}</h2>
          
          <div class="seller-section">
            <img 
              :src="product.seller?.avatar" 
              class="seller-avatar"
              alt=""
            />
            <div class="seller-info">
              <span class="seller-name">{{ product.seller?.name }}</span>
              <span class="feedback">{{ product.seller?.rating }} positive feedback</span>
            </div>
          </div>

          <div class="price-section">
            <div class="price">
              <span class="currency">AU $</span>
              <span class="amount">{{ product.price?.toFixed(2) }}</span>
            </div>
            <div class="approx-price">Approximately US ${{ (product.price * 0.65).toFixed(2) }}</div>
            <div class="shipping">Free shipping</div>
            <div class="delivery">Est. delivery Thu, Dec 19 - Fri, Jan 10</div>
          </div>

          <div class="condition">
            <span class="label">Condition:</span>
            <span class="value">{{ product.condition }}</span>
          </div>

          <div class="actions">
            <select class="variant-select">
              <option disabled selected>Select:</option>
            </select>
            <button class="buy-now">Buy It Now</button>
            <button class="add-cart">Add to cart</button>
            <button class="see-details">See all details</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import { HeartIcon, XIcon, ChevronLeftIcon, ChevronRightIcon } from 'lucide-vue-next'

defineProps({
  product: {
    type: Object,
    required: true
  },
  show: {
    type: Boolean,
    required: true
  }
})

const isFavorite = ref(false)
const toggleFavorite = () => {
  isFavorite.value = !isFavorite.value
}
</script>

<style scoped>
.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0, 0, 0, 0.7);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 1000;
}

.modal-container {
  background: white;
  width: 90%;
  max-width: 1200px;
  border-radius: 16px;
  padding: 32px;
  position: relative;
  box-shadow: 0 4px 24px rgba(0, 0, 0, 0.1);
}

.close-button {
  position: absolute;
  top: -48px;
  right: -48px;
  background: white;
  border: none;
  border-radius: 50%;
  width: 40px;
  height: 40px;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
}

.modal-content {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 32px;
}

.image-gallery {
  display: flex;
  gap: 16px;
}

.thumbnail-list {
  width: 80px;
}

.thumbnail {
  width: 100%;
  border-radius: 4px;
  cursor: pointer;
}

.main-image-container {
  flex: 1;
  display: flex;
  align-items: center;
  gap: 16px;
}

.main-image {
  position: relative;
  flex: 1;
}

.main-image img {
  width: 100%;
  height: auto;
  object-fit: contain;
}

.nav-button {
  background: none;
  border: none;
  cursor: pointer;
  color: #666;
}

.favorite-button {
  position: absolute;
  top: 16px;
  right: 16px;
  background: white;
  border: none;
  border-radius: 50%;
  width: 40px;
  height: 40px;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.title {
  font-family: "Helvetica Neue", sans-serif;
  font-size: 20px;
  line-height: 1.4;
  margin-bottom: 16px;
  color: #111;
}

.seller-section {
  display: flex;
  align-items: center;
  gap: 8px;
  margin: 16px 0;
  padding: 12px 0;
  border-top: 1px solid #e5e5e5;
  border-bottom: 1px solid #e5e5e5;
}

.seller-avatar {
  width: 32px;
  height: 32px;
  border-radius: 50%;
  object-fit: cover;
}

.seller-info {
  display: flex;
  flex-direction: column;
}

.seller-name {
  font-size: 14px;
  color: #0066cc;
}

.feedback {
  color: #666;
  font-size: 14px;
}

.price-section {
  background: #fafafa;
  padding: 16px;
  border-radius: 12px;
  margin: 20px 0;
}

.price {
  display: flex;
  align-items: baseline;
  gap: 4px;
}

.currency {
  font-size: 18px;
  color: #111;
}

.amount {
  font-size: 32px;
  font-weight: 600;
  color: #111;
}

.approx-price,
.shipping,
.delivery {
  font-size: 14px;
  color: #707070;
  margin-bottom: 8px;
}

.condition {
  margin-bottom: 24px;
}

.actions {
  display: flex;
  flex-direction: column;
  gap: 12px;
}

.variant-select,
.buy-now,
.add-cart,
.see-details {
  width: 100%;
  padding: 12px 16px;
  border: 1px solid #e5e5e5;
  border-radius: 24px;
  font-size: 16px;
  margin-bottom: 16px;
  cursor: pointer;
  appearance: none;
  background-image: url("data:image/svg+xml,%3Csvg width='16' height='16' viewBox='0 0 16 16' fill='none' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath d='M4 6L8 10L12 6' stroke='%23666' stroke-width='2' stroke-linecap='round' stroke-linejoin='round'/%3E%3C/svg%3E");
  background-repeat: no-repeat;
  background-position: right 16px center;
}

.buy-now,
.add-cart,
.see-details {
  width: 100%;
  padding: 16px;
  border-radius: 24px;
  font-size: 16px;
  font-weight: 500;
  cursor: pointer;
  transition: all 0.2s;
}

.buy-now {
  background: #3665f3;
  color: white;
  border: none;
}

.buy-now:hover {
  background: #2b4fa3;
}

.add-cart {
  background: white;
  border: 1px solid #3665f3;
  color: #3665f3;
}

.add-cart:hover {
  background: #f5f7ff;
}

.see-details {
  background: white;
  border: 1px solid #e5e5e5;
  color: #111;
}

.see-details:hover {
  background: #f5f5f5;
}

@media (max-width: 768px) {
  .modal-content {
    grid-template-columns: 1fr;
  }
}
</style>