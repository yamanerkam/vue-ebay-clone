<template>
  <div class="product-page">
    <div class="product-container">
      <div class="image-gallery">
        <div class="thumbnails">
          <div 
            v-for="(image, index) in images" 
            :key="index"
            class="thumbnail"
            :class="{ active: currentImageIndex === index }"
            @mouseenter="currentImageIndex = index"
          >
            <img :src="image" :alt="`Rolex watch view ${index + 1}`">
          </div>
        </div>
        <div class="main-image">
          <img :src="images[currentImageIndex]" alt="Rolex Oyster Perpetual">
          <div class="views-badge">
            VIEWED IN THE LAST 24 HOURS
          </div>
        </div>
      </div>

      <div class="product-details">
        <div class="title-container">
          <h1>Rolex Datejust ref. 116233 - Racing Silver Dial - Jubilee - Full Set</h1>
          <a href="#" class="show-original">show original title</a>
        </div>
        
        <div class="seller-info">
          <div class="seller-avatar">
            <img src="https://i.ebayimg.com/images/g/VjcAAOSwUipnH7Kh/s-l1600.webp" alt="">
          </div>
          <div class="seller-details">
            <div class="seller-name-container">
              <a href="#" class="seller-name">Debonar Watches</a>
              <span class="seller-rating">(210)</span>
            </div>
            <div class="seller-links">
              <a href="#">100% positive</a>
              <span class="separator">·</span>
              <a href="#">Seller's other items</a>
              <span class="separator">·</span>
              <a href="#">Contact seller</a>
            </div>
          </div>
        </div>

        <div class="price-section">
          <div class="price">EUR 10,290.00</div>
          <div class="converted-price">Approximately US $10,883.73</div>
          <div class="best-offer">or Best Offer</div>
        </div>

        <div class="condition">
          <span class="label">Condition:</span>
          <span class="value">Pre-owned</span>
          <button class="info-button">ⓘ</button>
        </div>

        <div class="action-buttons">
          <button class="buy-now">Buy It Now</button>
          <button class="add-cart">Add to cart</button>
          <button class="make-offer">Make offer</button>
          <button class="add-watchlist">
            <span class="heart-icon">♡</span>
            Add to watchlist
          </button>
        </div>

        <div class="shipping-section">
          <div class="shipping-row">
            <span class="label">Shipping:</span>
            <div class="shipping-details">
              <span class="shipping-cost">EUR 125.00 (approx US $132.21)</span>
              <span class="shipping-service">FedEx internazionale.</span>
              <a href="#" class="see-details">See details</a>
              <p class="shipping-note">
                International shipment of items may be subject to customs processing and additional charges.
                <button class="info-button">ⓘ</button>
              </p>
              <p class="location">Located in: Kraków, Poland</p>
            </div>
          </div>
          
          <div class="delivery-row">
            <span class="label">Delivery:</span>
            <div class="delivery-details">
              <div class="delivery-estimate">
                <span class="delivery-icon">📦</span>
                Estimated between Mon, Dec 9 and Mon, Dec 16
                <button class="info-button">ⓘ</button>
              </div>
              <p class="handling-time">
                Includes <strong>5 business days</strong> handling time after receipt of cleared payment.
              </p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const images = [
  'https://i.ebayimg.com/images/g/VjcAAOSwUipnH7Kh/s-l1600.webp',
  'https://i.ebayimg.com/images/g/LykAAOSw2yBlTWic/s-l1600.webp',
  'https://i.ebayimg.com/images/g/NTcAAOSwsH1m8pwy/s-l1600.webp',
  'https://i.ebayimg.com/images/g/MFUAAOSwBslnPAiv/s-l1600.webp'
]

const currentImageIndex = ref(0)
</script>

<style scoped>
.product-page {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
  max-width: 1200px;
  margin: 0 auto;
  padding: 20px;
}

.product-container {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 40px;
}

.image-gallery {
  display: flex;
  gap: 20px;
}

.thumbnails {
  display: flex;
  flex-direction: column;
  gap: 10px;
}

.thumbnail {
  width: 60px;
  height: 60px;
  border: 1px solid #e8e8e8;
  cursor: pointer;
  padding: 2px;
}

.thumbnail.active {
  border-color: #0053a0;
}

.thumbnail img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.main-image {
  position: relative;
  flex-grow: 1;
}

.main-image img {
  width: 100%;
  height: auto;
}

.views-badge {
  position: absolute;
  top: 10px;
  left: 10px;
  background: #dc0000;
  color: white;
  padding: 4px 8px;
  font-size: 12px;
  border-radius: 4px;
}

.title-container {
  margin-bottom: 20px;
}

h1 {
  font-size: 28px;
  font-weight: 700;
  color: #111;
  margin-bottom: 8px;
}

.show-original {
  color: #666;
  text-decoration: none;
  font-size: 14px;
}

.seller-info {
  display: flex;
  align-items: center;
  gap: 12px;
  margin-bottom: 24px;
}

.seller-avatar {
  width: 48px;
  height: 48px;
  border-radius: 50%;
  overflow: hidden;
  background: #f8f8f8;
}

.seller-avatar img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.seller-details {
  display: flex;
  flex-direction: column;
  gap: 4px;
}

.seller-name-container {
  display: flex;
  align-items: center;
  gap: 8px;
}

.seller-name {
  color: #111;
  text-decoration: none;
  font-weight: 500;
}

.seller-rating {
  color: #666;
}

.seller-links {
  display: flex;
  align-items: center;
  gap: 8px;
  font-size: 14px;
}

.seller-links a {
  color: #3665f3;
  text-decoration: none;
}

.separator {
  color: #666;
}

.price-section {
  margin: 24px 0;
}

.price {
  font-size: 32px;
  font-weight: 700;
  color: #111;
}

.converted-price {
  color: #666;
  font-size: 16px;
  margin-top: 4px;
}

.best-offer {
  color: #111;
  font-size: 16px;
  margin-top: 4px;
}

.condition {
  display: flex;
  align-items: center;
  gap: 8px;
  margin-bottom: 24px;
}

.condition .label {
  color: #666;
}

.condition .value {
  color: #111;
}

.action-buttons {
  display: flex;
  flex-direction: column;
  gap: 8px;
  margin-bottom: 24px;
}

.action-buttons button {
  width: 100%;
  padding: 12px;
  border-radius: 24px;
  font-size: 16px;
  font-weight: 500;
  cursor: pointer;
  border: none;
  transition: background-color 0.3s, color 0.3s;
}

.buy-now {
  background: #3665f3;
  color: white;
}

.buy-now:hover {
  background: #2b4fa3;
}

.add-cart, .make-offer {
  background: white;
  color: #3665f3;
  border: 1px solid #3665f3 !important;
}

.add-cart:hover, .make-offer:hover {
  background: #f0f5ff;
}

.add-watchlist {
  background: white;
  color: #3665f3 !important;;
  border: 1px solid #3665f3 !important;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 8px;
}

.add-watchlist:hover {
  background: #f8f8f8;
}

.heart-icon {
  font-size: 20px;
}

.shipping-section {
  border-top: 1px solid #e5e5e5;
  padding-top: 24px;
}

.shipping-row, .delivery-row {
  display: flex;
  gap: 16px;
  margin-bottom: 16px;
}

.label {
  color: #666;
  min-width: 80px;
}

.shipping-details, .delivery-details {
  flex: 1;
}

.shipping-cost {
  font-weight: 500;
}

.shipping-service {
  margin-left: 8px;
}

.see-details {
  color: #3665f3;
  text-decoration: none;
  margin-left: 8px;
}

.shipping-note {
  color: #666;
  font-size: 14px;
  margin-top: 8px;
}

.location {
  color: #666;
  font-size: 14px;
  margin-top: 8px;
}

.delivery-estimate {
  display: flex;
  align-items: center;
  gap: 8px;
}

.delivery-icon {
  font-size: 20px;
}

.handling-time {
  color: #666;
  font-size: 14px;
  margin-top: 8px;
}

.info-button {
  background: none;
  border: none;
  color: #666;
  cursor: pointer;
  padding: 0;
  font-size: 16px;
}

@media (max-width: 768px) {
  .product-container {
    grid-template-columns: 1fr;
  }
  
  .image-gallery {
    flex-direction: column;
  }
  
  .thumbnails {
    flex-direction: row;
    overflow-x: auto;
  }
}
</style>