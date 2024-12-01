<template>
  <ul class="product-list">
    <li v-for="product in products" :key="product.id">
      <ProductListItem :product="product" />
    </li>
  </ul>
</template>

<script setup>
import { ref } from 'vue'
import ProductListItem from './ProductListItem.vue'

const products = ref([
  {
    id: 1,
    title: '30ml Natural Vitamin C Serum Liquid Hyaluronic Acid Essence Moisturizing Anti Agi',
    image: 'https://i.ebayimg.com/images/g/hX0AAOSwHTlfmWhd/s-l500.webp',
    price: 8.25,
    condition: 'Brand New',
    shipping: 4.97,
    location: 'Italy',
    seller: {
      name: 'naturalproducts10',
      rating: '81.5%',
      reviews: 128,
      avatar: 'https://picsum.photos/id/64/30/30'
    }
  },
  {
    id: 2,
    title: 'Organic Vitamin E Serum with Natural Aloe Vera Extract',
    image: 'https://picsum.photos/id/145/500/500',
    price: 12.99,
    condition: 'Brand New',
    shipping: 3.99,
    location: 'United States',
    seller: {
      name: 'organicbeauty',
      rating: '94.2%',
      reviews: 256,
      avatar: 'https://picsum.photos/id/65/30/30'
    }
  },
  {
    id: 3,
    title: 'Premium Hyaluronic Acid Serum with Collagen Boost Formula',
    image: 'https://picsum.photos/id/175/500/500',
    price: 15.50,
    condition: 'Brand New',
    shipping: 5.99,
    location: 'France',
    seller: {
      name: 'beautyessentials',
      rating: '88.7%',
      reviews: 432,
      avatar: 'https://picsum.photos/id/66/30/30'
    }
  }
])
</script>

<style scoped>
.product-list {
  list-style: none;
  padding: 0;
  margin: 0;
  display: flex;
  flex-direction: column;
  gap: 12px;
  max-width: 1200px;
  margin: 0 auto;
}

.product-list li {
  background: #fff;
  border-radius: 4px;
  border: 1px solid #e8e8e8;
}

.product-list li:hover {
  box-shadow: 0 1px 4px rgba(0, 0, 0, 0.1);
}
</style>