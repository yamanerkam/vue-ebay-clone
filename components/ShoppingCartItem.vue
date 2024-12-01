<template>
    <div class="product-card">
      <div class="seller-info">
        <img :src="seller.logo" :alt="seller.name" class="seller-logo" />
        <div class="seller-details">
          <h2>{{ seller.name }}</h2>
          <span class="feedback">{{ seller.feedback }} positive feedback</span>
        </div>
        <div class="shipping-request" @click="$emit('requestShipping')">
          Request combined shipping
          <span class="info-icon">ⓘ</span>
        </div>
      </div>
  
      <div class="product-details">
        <img :src="product.image" :alt="product.title" class="product-image" />
        <div class="product-info">
          <span v-if="product.lastOne" class="last-one">LAST ONE</span>
          <h3>{{ product.title }}</h3>
          <span class="condition">{{ product.condition }}</span>
        </div>
        <div class="right-section">
          <div class="price-quantity">
            <div class="quantity">Qty {{ quantity }}</div>
            <div class="current-price">US ${{ product.currentPrice.toLocaleString() }}</div>
            <div v-if="product.originalPrice" class="original-price">
              US ${{ product.originalPrice.toLocaleString() }}
            </div>
          </div>
          <div class="shipping-info">
            <div>{{ shipping.method }}</div>
            <div>{{ shipping.location }}</div>
            <div class="shipping-benefits">
              <div v-if="shipping.free">Free shipping</div>
              <div v-if="shipping.freeReturns">Free returns</div>
            </div>
          </div>
          <div class="actions">
            <button class="save" @click="$emit('save')">Save for later</button>
            <button class="remove" @click="$emit('remove')">Remove</button>
          </div>
        </div>
      </div>
  
      <div v-if="offer" class="offer-section">
        <span class="check-icon">✓</span>
        <span>Offer applied</span>
        <span class="savings">{{ offer.savings }}</span>
        <span class="arrow">›</span>
      </div>
    </div>
  </template>
  
  <script setup>
  defineProps({
    seller: {
      type: Object,
      required: true,
      // Expected shape: { name, logo, feedback }
    },
    product: {
      type: Object,
      required: true,
      // Expected shape: { title, image, condition, currentPrice, originalPrice, lastOne }
    },
    shipping: {
      type: Object,
      required: true,
      // Expected shape: { method, location, free, freeReturns }
    },
    quantity: {
      type: Number,
      default: 1
    },
    offer: {
      type: Object,
      default: null,
      // Expected shape: { savings }
    }
  })
  
  defineEmits(['save', 'remove', 'requestShipping'])
  </script>
  
  <style scoped>
  .product-card {
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Arial, sans-serif;
    max-width: 900px;
    border: 1px solid #e5e5e5;
    border-radius: 16px;
    background: white;
    margin-left: 100px;
    margin-top: 200px;
  }
  
  .seller-info,
  .product-details,
  .offer-section {
    padding: 16px 24px;
  }
  
  .seller-info {
    display: flex;
    align-items: center;
    gap: 16px;
  }
  
  .seller-logo {
    width: 40px;
    height: 40px;
    border-radius: 50%;
  }
  
  .seller-details h2 {
    font-size: 16px;
    font-weight: bold;
    margin: 0;
  }
  
  .feedback {
    color: #767676;
    font-size: 14px;
  }
  
  .shipping-request {
    margin-left: auto;
    color: #0066cc;
    cursor: pointer;
    font-size: 14px;
  }
  
  .info-icon {
    display: inline-block;
    width: 16px;
    height: 16px;
    border: 1px solid #0066cc;
    border-radius: 50%;
    text-align: center;
    line-height: 16px;
    font-size: 12px;
    margin-left: 4px;
  }
  
  .product-details {
    display: grid;
    grid-template-columns: 160px 1fr auto;
    gap: 24px;
    padding: 20px 24px;
    /* remove this line */
    /* border-top: 1px solid #e5e5e5; */
  }
  
  .product-image {
    width: 160px;
    height: 160px;
    object-fit: contain;
  }
  
  .product-info {
    max-width: 400px;
  }
  
  .right-section {
    display: flex;
    flex-direction: column;
    gap: 16px;
    text-align: right;
  }
  
  .shipping-info {
    color: #767676;
    font-size: 16px;
    line-height: 1.5;
  }
  
  .shipping-benefits {
    margin-top: 4px;
  }
  
  .shipping-benefits div:first-child {
    color: #00a65a;
  }
  
  .shipping-benefits div:last-child {
    color: #767676;
  }
  
  .price-quantity {
    margin-bottom: 24px;
  }
  
  .quantity {
    font-size: 16px;
    color: #111111;
  }
  
  .current-price {
    font-size: 24px;
    font-weight: 500;
    line-height: 1.2;
  }
  
  .original-price {
    color: #767676;
    font-size: 16px;
    text-decoration: line-through;
  }
  
  .actions {
    display: flex;
    gap: 16px;
    justify-content: flex-end;
    margin-top: 16px;
  }
  
  .last-one {
    display: inline-block;
    background: white;
    color: #ff4444;
    padding: 2px 8px;
    border: 1.5px solid #ff4444;
    border-radius: 4px;
    font-size: 12px;
    font-weight: 500;
    margin-bottom: 8px;
  }
  
  .product-info h3 {
    font-size: 18px;
    font-weight: bold;
    margin: 0 0 4px 0;
  }
  
  .condition {
    color: #767676;
    font-size: 14px;
  }
  
  .actions button {
    background: none;
    border: none;
    color: #0066cc;
    cursor: pointer;
    padding: 0;
    font-size: 14px;
    text-decoration: underline;
  }
  
  .offer-section {
    display: flex;
    align-items: center;
    gap: 12px;
    border-top: 1px solid #e5e5e5;
    font-size: 14px;
  }
  
  .check-icon {
    color: #00a65a;
  }
  
  .savings {
    color: #0066cc;
  }
  
  .arrow {
    margin-left: auto;
    font-size: 20px;
    color: #0066cc;
  }
  
  @media (max-width: 768px) {
    .product-details {
      grid-template-columns: 1fr;
    }
  
    .right-section {
      text-align: left;
    }
  
    .actions {
      justify-content: flex-start;
    }
  }
  </style>
  
  