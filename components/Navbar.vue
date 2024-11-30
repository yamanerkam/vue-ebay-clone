<template>
  <header class="search-header">
    <div class="container">
      <div class="logo-category">
        <img class="logo" src="./logo2.png" alt="">
        <div class="category-dropdown">
          <button @click="toggleCategoryDropdown" class="category-button" :aria-expanded="isCategoryDropdownOpen">
            Shop by category
            <svg
              xmlns="http://www.w3.org/2000/svg"
              width="16"
              height="16"
              viewBox="0 0 24 24"
              fill="none"
              stroke="currentColor"
              stroke-width="2"
              stroke-linecap="round"
              stroke-linejoin="round"
              :class="{ 'rotate': isCategoryDropdownOpen }"
            >
              <path d="m6 9 6 6 6-6" />
            </svg>
          </button>
          <div v-if="isCategoryDropdownOpen" class="category-dropdown-content">
            <div class="mega-menu">
              <div class="category-column">
                <h3>Collectibles & art</h3>
                <a href="#">Collectibles</a>
                <a href="#">Antiques</a>
                <a href="#">Sports memorabilia</a>
                <a href="#">Art</a>
              </div>
              <div class="category-column">
                <h3>Home & garden</h3>
                <a href="#">Yard, garden & outdoor</a>
                <a href="#">Crafts</a>
                <a href="#">Home improvement</a>
                <a href="#">Pet supplies</a>
              </div>
              <div class="category-column">
                <h3>Sporting goods</h3>
                <a href="#">Outdoor sports</a>
                <a href="#">Team sports</a>
                <a href="#">Exercise & fitness</a>
                <a href="#">Golf</a>
              </div>
              <div class="category-column">
                <h3>Electronics</h3>
                <a href="#">Computers & tablets</a>
                <a href="#">Cameras & photo</a>
                <a href="#">TV, audio & surveillance</a>
                <a href="#">Cell phones & accessories</a>
              </div>
              <div class="category-column">
                <h3>Auto Parts & Accessories</h3>
                <a href="#">GPS & Security Devices</a>
                <a href="#">Radar & Laser Detectors</a>
                <a href="#">Care & Detailing</a>
                <a href="#">Scooter Parts & Accessories</a>
              </div>
              <div class="category-column">
                <h3>Toys & hobbies</h3>
                <a href="#">Radio control</a>
                <a href="#">Kids toys</a>
                <a href="#">Action figures</a>
                <a href="#">Dolls & bears</a>
              </div>
              <div class="category-column">
                <h3>Fashion</h3>
                <a href="#">Women</a>
                <a href="#">Men</a>
                <a href="#">Jewelry & watches</a>
                <a href="#">Shoes</a>
              </div>
              <div class="category-column">
                <h3>Musical instruments & gear</h3>
                <a href="#">Guitar</a>
                <a href="#">Pro audio equipment</a>
                <a href="#">String</a>
                <a href="#">Stage lighting & effects</a>
              </div>
              <div class="category-column">
                <h3>Other categories</h3>
                <a href="#">Video games & consoles</a>
                <a href="#">Health & beauty</a>
                <a href="#">Baby</a>
                <a href="#">Business & industrial</a>
              </div>
              <a href="#" class="see-all">See all categories</a>
            </div>
          </div>
        </div>
      </div>
      <div class="search-container">
        <div class="search-input-container">
          <input
            type="search"
            placeholder="Search for anything"
            class="search-input"
          />
          <select class="category-select">
            <option value="all">All Categories</option>
            <option value="antiques">Antiques</option>
            <option value="art">Art</option>
            <option value="baby">Baby</option>
            <option value="books">Books</option>
            <option value="business">Business & Industrial</option>
            <option value="cameras">Cameras & Photo</option>
            <option value="cell-phones">Cell Phones & Accessories</option>
            <option value="clothing">Clothing, Shoes & Accessories</option>
            <option value="coins">Coins & Paper Money</option>
            <option value="collectibles">Collectibles</option>
            <option value="computers">Computers/Tablets & Networking</option>
            <option value="consumer-electronics">Consumer Electronics</option>
            <option value="crafts">Crafts</option>
            <option value="dolls">Dolls & Bears</option>
            <option value="dvds">DVDs & Movies</option>
            <option value="entertainment">Entertainment Memorabilia</option>
            <option value="gift-cards">Gift Cards & Coupons</option>
            <option value="health">Health & Beauty</option>
            <option value="home">Home & Garden</option>
            <option value="jewelry">Jewelry & Watches</option>
            <option value="music">Music</option>
            <option value="musical-instruments">Musical Instruments & Gear</option>
            <option value="pet-supplies">Pet Supplies</option>
            <option value="pottery">Pottery & Glass</option>
            <option value="real-estate">Real Estate</option>
            <option value="specialty-services">Specialty Services</option>
            <option value="sporting-goods">Sporting Goods</option>
            <option value="sports-mem">Sports Mem, Cards & Fan Shop</option>
            <option value="stamps">Stamps</option>
            <option value="tickets">Tickets & Experiences</option>
            <option value="toys">Toys & Hobbies</option>
            <option value="travel">Travel</option>
            <option value="video-games">Video Games & Consoles</option>
            <option value="everything-else">Everything Else</option>
          </select>
        </div>
        <button class="search-button">
          Search
        </button>
        <a href="#" class="advanced-link">Advanced</a>
      </div>
    </div>
  </header>
</template>

<script setup>
import { ref } from 'vue';

const isCategoryDropdownOpen = ref(false);

const toggleCategoryDropdown = () => {
  isCategoryDropdownOpen.value = !isCategoryDropdownOpen.value;
};
</script>

<style scoped>
.search-header {
  width: 100%;
  border-bottom: 1px solid #e5e5e5;
  padding: 8px 0;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 20px;
  display: flex;
  align-items: center;
  gap: 20px;
}

.logo-category {
  display: flex;
  align-items: center;
  gap: 20px;
}

.logo {
  width: 100px;
}

.category-dropdown {
  position: relative;
}

.category-button {
  display: flex;
  align-items: center;
  gap: 5px;
  background: none;
  border: none;
  cursor: pointer;
  font-size: 12px;
  color: #333;
  padding: 8px 12px;
  border-radius: 4px;
}

.category-button:hover {
  background-color: #f5f5f5;
}

.category-button svg {
  transition: transform 0.2s ease;
}

.category-button svg.rotate {
  transform: rotate(180deg);
}

.category-dropdown-content {
  position: absolute;
  top: calc(100% + 5px);
  left: 0;
  background-color: #fff;
  border: 1px solid #e5e5e5;
  border-radius: 4px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.15);
  z-index: 1000;
  min-width: 800px;
}

.mega-menu {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 24px;
  padding: 24px;
  position: relative;
}

.category-column {
  display: flex;
  flex-direction: column;
  gap: 8px;
}

.category-column h3 {
  font-size: 14px;
  font-weight: 700;
  color: #333;
  margin-bottom: 4px;
}

.category-column a {
  text-decoration: none;
  color: #767676;
  font-size: 12px;
  line-height: 1.4;
}

.category-column a:hover {
  color: #3665f3;
  text-decoration: underline;
}

.see-all {
  grid-column: 1 / -1;
  text-decoration: none;
  color: #3665f3;
  font-size: 14px;
  padding-top: 16px;
  border-top: 1px solid #e5e5e5;
  margin-top: 8px;
}

.see-all:hover {
  text-decoration: underline;
}

.search-container {
  display: flex;
  flex: 1;
  align-items: center;
  gap: 10px;
}

.search-input-container {
  display: flex;
  flex: 1;
  border: 2px solid #41413f;
  border-radius: 50px;
  overflow: hidden;
}

.search-input {
  flex: 1;
  height: 40px;
  padding: 0 16px 0 40px;
  border: none;
  font-size: 16px;
  background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='16' height='16' viewBox='0 0 24 24' fill='none' stroke='currentColor' stroke-width='2' stroke-linecap='round' stroke-linejoin='round'%3E%3Ccircle cx='11' cy='11' r='8'/%3E%3Cpath d='m21 21-4.3-4.3'/%3E%3C/svg%3E");
  background-repeat: no-repeat;
  background-position: 16px center;
  background-size: 16px;
}

.category-select {
  width: 180px;
  height: 40px;
  border: none;
  border-left: 1px solid #e5e5e5;
  padding: 0 30px 0 16px;
  font-size: 16px;
  background-color: #fff;
  cursor: pointer;
  appearance: none;
  background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='16' height='16' viewBox='0 0 24 24' fill='none' stroke='currentColor' stroke-width='2' stroke-linecap='round' stroke-linejoin='round'%3E%3Cpath d='m6 9 6 6 6-6'/%3E%3C/svg%3E");
  background-repeat: no-repeat;
  background-position: right 10px center;
  background-size: 16px;
}

.search-button {
  height: 40px;
  padding: 0 20px;
  background-color: #3665f3;
  color: white;
  border: none;
  border-radius: 50px;
  font-size: 16px;
  font-weight: 700;
  cursor: pointer;
}

.search-button:hover {
  background-color: #2b4fb4;
}

.advanced-link {
  color: #767676;
  text-decoration: none;
  font-size: 12px;
}

.advanced-link:hover {
  text-decoration: underline;
}
</style>