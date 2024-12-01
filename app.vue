<template>
  <div class="home">
    <div class="sidebar">
      <button class="sidebar-button" @click="updateState(0)"> Erkam 1 </button>
      <button class="sidebar-button" @click="updateState(1)"> Erkam 2 </button>
      <button class="sidebar-button" @click="updateState(2)"> Erkam 3 </button>
      <button class="sidebar-button" @click="updateState(3)"> Erkam 4 </button>
      <button class="sidebar-button" @click="updateState(4)"> Erkam 5 </button>
      <button class="sidebar-button" @click="updateState(5)"> Zal 1 </button>
      <button class="sidebar-button" @click="updateState(6)"> Zal 2 </button>
      <button class="sidebar-button" @click="updateState(7)"> Zal 3 </button>
      <button class="sidebar-button" @click="updateState(8)"> Zal 4 </button>
      <button class="sidebar-button" @click="updateState(9)"> Zal 5 </button>
      <span> index: {{ state }}</span>
    </div>

    <!-- Erkam -->
    <div class="main-section" v-if="state === 0">
      <NavbarTop />
      <Navbar />
    </div>
    <div class="main-section" v-if="state === 1">
      <SignIn />
    </div>
    <div class="main-section" v-if="state === 2">
      <Carousel />
    </div>
    <div class="main-section" v-if="state === 3">
      <ProductsGallery />
    </div>
    <div class="main-section" v-if="state === 4">
      <ProductPage />
    </div>

    <!-- Zal -->
    <div class="main-section" v-if="state === 5">
      <ProductList />
    </div>
    <div class="main-section" v-if="state === 6">
      <ProductModal :show="true" :product="{
        id: 1,
        title: 'Iron 650mg - Immune System Boost, Relieve Anemia, Anti-fatigue - Vitamin C',
        image: 'https://i.ebayimg.com/images/g/hX0AAOSwHTlfmWhd/s-l500.webp',
        price: 14.53,
        shipping: 'Free',
        condition: 'New',
        estimatedDelivery: 'Thu, Dec 19 - Fri, Jan 10',
        seller: {
          name: 'xemenry nutrition',
          rating: '100%',
          reviews: 42,
          avatar: 'https://i.ebayimg.com/images/g/3~wAAOSwPzVf3rV~/s-l30.jpg'
        }
      }" />
    </div>
    <div class="main-section" v-if="state === 7">
      <ShoppingCartItem :seller="{
        name: 'BRAND OFF TOKYO Hong Kong',
        logo: 'https://i.ebayimg.com/images/g/NTcAAOSwsH1m8pwy/s-l225.webp',
        feedback: '98.9%'
      }" :product="{
        title: 'ROLEX Datejust 36mm Automatic Watch 116233 18K Yellow Gold/Stainless Steel Gold',
        image: 'https://i.ebayimg.com/images/g/NTcAAOSwsH1m8pwy/s-l225.webp',
        condition: 'Pre-owned',
        currentPrice: 8211.00,
        originalPrice: 9660.00,
        lastOne: true
      }" :shipping="{
        method: 'Expedited Shipping',
        location: 'from Greater China to worldwide',
        free: true,
        freeReturns: true
      }" :offer="{
        savings: '15%'
      }" v-model="quantity" @save="handleSave" @remove="handleRemove" @requestShipping="handleShippingRequest" />
    </div>
    <div class="main-section" v-if="state === 8">
      <CartItem :product="{
        name: 'ROLEX Datejust 36mm Automatic Watch',
        image: 'https://i.ebayimg.com/images/g/NTcAAOSwsH1m8pwy/s-l225.webp',
        price: '$8,211.00',
        shipping: 'Free Shipping',
        quantity: 1
      }" title="Your Shopping Cart" total="$8,211.00" checkoutButtonText="Proceed to Checkout"
        viewCartButtonText="View Full Cart" />
    </div>
    <div class="main-section" v-if="state === 9">
      <RecommendedSellers />
    </div>
  </div>
</template>

<script>
import ProductModal from './components/ProductModal.vue'
import ProductList from './components/ProductList.vue'
import CartItem from './components/CartItem.vue'
import RecommendedSellers from './components/RecommendedSellers.vue'

export default {
  components: {
    ProductModal,
    ProductList,
    CartItem,
    RecommendedSellers
  },
  data() {
    return {
      state: 0,
    }
  },
  methods: {
    updateState(index) {
      this.state = index
    },
  },
}
</script>

<style>
/* Mevcut stiller... */

/* Global font ayarları */
:root {
  --ebay-font: -apple-system, BlinkMacSystemFont, "Helvetica Neue", "Helvetica", "Roboto", "Arial", sans-serif;
}

body {
  font-family: var(--ebay-font);
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  width: 100vw;
  height: 100vh;
  margin: 0;
  padding: 0;
  overflow: hidden;
}

/* Modern font stilleri için ek sınıflar */
h1,
h2,
h3,
h4,
h5,
h6 {
  font-family: var(--ebay-font);
  font-weight: 600;
  letter-spacing: -0.2px;
}

button,
input,
select,
textarea {
  font-family: var(--ebay-font);
}

.title {
  letter-spacing: -0.3px;
}

.price {
  letter-spacing: -0.5px;
}

/* Diğer mevcut stiller... */

.home {
  width: 100%;
  height: 100vh;
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: start;
}

.main-section {
  width: 90%;
  height: 100%;
}

.sidebar {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-evenly;
  width: 10%;
  height: 100%;
  border-right: 1px solid #ccc;
  background-color: beige;
}

.sidebar-button {
  background-color: #0d080f;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  width: 80px;
  height: 70px;
}

.sidebar-button:hover {
  background-color: #6c6c6c;
}

.current-state {
  margin-top: 20px;
  font-weight: bold;
}
</style>