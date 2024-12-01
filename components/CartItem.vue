<template>
  <div class="shopping-cart">
    <h1>{{ title }}</h1>

    <div class="cart-item">
      <div class="product-image">
        <img :src="product.image" :alt="product.name">
      </div>
      <div class="product-details">
        <h2>{{ product.name }}</h2>
        <div class="price-quantity">
          <span class="price">AU ${{ product.price }}</span>
          <span class="quantity">Qty: {{ product.quantity }}</span>
        </div>
        <span class="shipping">{{ product.shipping }}</span>
      </div>
      <button class="trash-button">
        <trash-icon size="18" />
      </button>
    </div>

    <div class="total-section">
      <div class="total">
        <span>Total</span>
        <span>AU ${{ total }}</span>
      </div>
    </div>

    <button class="checkout-button">Checkout</button>
    <button class="view-cart-button">View cart</button>
  </div>
</template>

<style scoped>
.shopping-cart {
  width: 400px;
  margin: 0 auto;
  padding: 20px;
  background: white;
  border-radius: 12px;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.08);
}

h1 {
  font-size: 28px;
  font-weight: 600;
  margin-bottom: 20px;
  color: #111;
}

.cart-item {
  display: grid;
  grid-template-columns: 100px 1fr 40px;
  gap: 16px;
  padding: 16px 0;
  border-bottom: 1px solid #e5e5e5;
}

.product-image {
  width: 100px;
  height: 100px;
  padding: 4px;
  border: 1px solid #e5e5e5;
  border-radius: 4px;
}

.product-image img {
  width: 100%;
  height: 100%;
  object-fit: contain;
}

.product-details h2 {
  font-size: 16px;
  line-height: 1.4;
  margin-bottom: 12px;
  color: #111;
}

.price-quantity {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 6px;
}

.price {
  font-size: 22px;
  font-weight: 500;
}

.quantity {
  color: #707070;
  font-size: 16px;
}

.shipping {
  display: block;
  color: #707070;
  font-size: 14px;
}

.trash-button {
  align-self: start;
  margin-top: 4px;
  background: none;
  border: none;
  padding: 8px;
  color: #767676;
  cursor: pointer;
  opacity: 0.8;
  transition: opacity 0.2s;
}

.trash-button:hover {
  opacity: 1;
}

.total-section {
  background: #fafafa;
  margin: 0 -20px;
  padding: 20px;
}

.total {
  display: flex;
  justify-content: space-between;
  align-items: center;
  font-size: 22px;
  font-weight: 500;
  color: #111;
}

.checkout-button,
.view-cart-button {
  width: 100%;
  height: 48px;
  border-radius: 24px;
  font-size: 16px;
  font-weight: 500;
  cursor: pointer;
  transition: all 0.2s;
}

.checkout-button {
  background: #3665f3;
  color: white;
  border: none;
  margin: 20px 0 12px;
}

.checkout-button:hover {
  background: #2b4fa3;
}

.view-cart-button {
  background: white;
  color: #3665f3;
  border: 1px solid #3665f3;
}

.view-cart-button:hover {
  background: #f5f7ff;
}
</style>

<script setup>
import { TrashIcon } from 'lucide-vue-next'

defineProps({
  title: {
    type: String,
    default: 'Shopping cart'
  },
  product: {
    type: Object,
    required: true
  },
  total: {
    type: String,
    required: true
  }
})
</script>