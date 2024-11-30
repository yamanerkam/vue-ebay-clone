<template>
  <div class="product-card">
    <div class="image-container">
      <img :src="product.imageUrl" :alt="product.name" class="product-image">
      <button class="favorite-button" @click="toggleFavorite">
        <span v-if="isFavorite">♥</span>
        <span v-else>♡</span>
      </button>
    </div>
    <h2 class="product-name">{{ product.name }}</h2>
    <p class="product-price">{{ formatPrice(product.price) }}</p>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const props = defineProps({
  product: {
    type: Object,
    required: true
  }
});

const isFavorite = ref(false);

const toggleFavorite = () => {
  isFavorite.value = !isFavorite.value;
};

const formatPrice = (price) => {
  return `$${price.toFixed(2)}`;
};
</script>

<style scoped>
.product-card {
  padding: 16px;
  width: 250px;
  flex: 0 0 auto;
}

.image-container {
  position: relative;
}

.product-image {
  width: 100%;
  height: 250px;
  object-fit: cover;
  border-radius: 20px;
}

.favorite-button {
  position: absolute;
  top: 8px;
  right: 8px;
  background-color: white;
  border: none;
  border-radius: 50%;
  width: 32px;
  height: 32px;
  font-size: 20px;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
}

.product-name {
  font-size: 14px;
  margin: 12px 0 8px;
  font-weight: 600;
  overflow:auto;
  text-overflow: ellipsis;
}

.product-name:hover {
  text-decoration: underline;
}

.product-price {
  font-size: 16px;
  font-weight: bold;
  color: #333;
}
</style>

