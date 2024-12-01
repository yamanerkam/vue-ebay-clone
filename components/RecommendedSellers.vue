<template>
    <div>
        <!-- Trending Section -->
        <div class="trending-section">
            <h2 class="trending-title">Trending on eBay</h2>
            <div class="trending-grid">
                <div v-for="category in categories" :key="category.id" class="category-item">
                    <div class="category-circle">
                        <img :src="category.image" :alt="category.name" class="category-image">
                    </div>
                    <span class="category-name">{{ category.name }}</span>
                </div>
            </div>
        </div>

        <!-- Recommended Sellers Section -->
        <div class="recommended-sellers">
            <h2 class="section-title">Recommended Sellers</h2>
            <div class="sellers-grid">
                <div v-for="seller in sellers" :key="seller.id" class="seller-card">
                    <div class="product-grid">
                        <img v-for="(product, index) in seller.products" :key="index" :src="product.image"
                            :alt="product.name" class="product-image" />
                    </div>
                    <div class="seller-info">
                        <div class="seller-details">
                            <img :src="seller.avatar" :alt="seller.name" class="seller-avatar" />
                            <div class="seller-text">
                                <span class="seller-name">{{ seller.name }}</span>
                                <span class="follower-count">{{ seller.followers }} followers</span>
                            </div>
                        </div>
                        <button class="save-button" :class="{ 'saved': seller.isSaved }" @click="toggleSave(seller)">
                            <heart-icon :fill="seller.isSaved ? '#0053a0' : 'none'"
                                :stroke="seller.isSaved ? '#0053a0' : '#0053a0'" size="16" />
                            {{ seller.isSaved ? 'Saved' : 'Save' }}
                        </button>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup>
import { ref } from 'vue'
import { HeartIcon } from 'lucide-vue-next'

const categories = [
    {
        id: 1,
        name: 'Luxury',
        image: 'https://i.ebayimg.com/images/g/hX0AAOSwHTlfmWhd/s-l500.webp'
    },
    {
        id: 2,
        name: 'Sneakers',
        image: 'https://i.ebayimg.com/images/g/zRUAAOSwNjVmlOUO/s-l500.webp'
    },
    {
        id: 3,
        name: 'P&A',
        image: 'https://i.ebayimg.com/images/g/~ogAAOSwaYpnD4E9/s-l500.webp'
    },
    {
        id: 4,
        name: 'Refurbished',
        image: 'https://i.ebayimg.com/images/g/NTcAAOSwsH1m8pwy/s-l225.webp'
    },
    {
        id: 5,
        name: 'Trading cards',
        image: 'https://i.ebayimg.com/images/g/hX0AAOSwHTlfmWhd/s-l500.webp'
    },
    {
        id: 6,
        name: 'Pre-loved Luxury',
        image: 'https://i.ebayimg.com/images/g/zRUAAOSwNjVmlOUO/s-l500.webp'
    },
    {
        id: 7,
        name: 'Toys',
        image: 'https://i.ebayimg.com/images/g/~ogAAOSwaYpnD4E9/s-l500.webp'
    }
]

const sellers = ref([
    {
        id: 1,
        name: 'buporai shop',
        followers: '12',
        avatar: '/placeholder.svg?height=32&width=32',
        isSaved: false,
        products: [
            {
                name: 'Rhodiola Rosea',
                image: 'https://i.ebayimg.com/images/g/hX0AAOSwHTlfmWhd/s-l500.webp'
            },
            {
                name: 'Sea Moss',
                image: 'https://i.ebayimg.com/images/g/zRUAAOSwNjVmlOUO/s-l500.webp'
            },
            {
                name: 'Best Tall',
                image: 'https://i.ebayimg.com/images/g/~ogAAOSwaYpnD4E9/s-l500.webp'
            },
            {
                name: 'Ashwagandha',
                image: 'https://i.ebayimg.com/images/g/NTcAAOSwsH1m8pwy/s-l225.webp'
            }
        ]
    },
    {
        id: 2,
        name: 'xemenry vip',
        followers: '38',
        avatar: '/placeholder.svg?height=32&width=32',
        isSaved: false,
        products: [
            {
                name: 'Colostrum',
                image: 'https://i.ebayimg.com/images/g/hX0AAOSwHTlfmWhd/s-l500.webp'
            },
            {
                name: 'Mens Daily',
                image: 'https://i.ebayimg.com/images/g/zRUAAOSwNjVmlOUO/s-l500.webp'
            },
            {
                name: 'Magnesium',
                image: 'https://i.ebayimg.com/images/g/~ogAAOSwaYpnD4E9/s-l500.webp'
            },
            {
                name: 'D-Mannose',
                image: 'https://i.ebayimg.com/images/g/NTcAAOSwsH1m8pwy/s-l225.webp'
            }
        ]
    },
    {
        id: 3,
        name: 'xemenry',
        followers: '1612',
        avatar: '/placeholder.svg?height=32&width=32',
        isSaved: false,
        products: [
            {
                name: 'Citrus Bergamot',
                image: 'https://i.ebayimg.com/images/g/hX0AAOSwHTlfmWhd/s-l500.webp'
            },
            {
                name: 'Citrus Extract',
                image: 'https://i.ebayimg.com/images/g/zRUAAOSwNjVmlOUO/s-l500.webp'
            },
            {
                name: 'Garlic Extract',
                image: 'https://i.ebayimg.com/images/g/~ogAAOSwaYpnD4E9/s-l500.webp'
            },
            {
                name: 'Krill Oil',
                image: 'https://i.ebayimg.com/images/g/NTcAAOSwsH1m8pwy/s-l225.webp'
            }
        ]
    }
])

const toggleSave = (seller) => {
    seller.isSaved = !seller.isSaved
}
</script>

<style scoped>
/* Trending Section Styles */
.trending-section {
    padding: 24px;
    background: #fff;
    margin-bottom: 24px;
}

.trending-title {
    font-size: 24px;
    font-weight: 700;
    margin-bottom: 24px;
    color: #111;
}

.trending-grid {
    display: flex;
    gap: 16px;
    overflow-x: auto;
    padding: 8px 4px;
    scrollbar-width: none;
    -ms-overflow-style: none;
}

.trending-grid::-webkit-scrollbar {
    display: none;
}

.category-item {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 8px;
    min-width: 120px;
    cursor: pointer;
}

.category-circle {
    width: 120px;
    height: 120px;
    border-radius: 50%;
    background: #f7f7f7;
    overflow: hidden;
    display: flex;
    align-items: center;
    justify-content: center;
}

.category-image {
    width: 60%;
    height: 60%;
    object-fit: contain;
}

.category-name {
    font-size: 14px;
    color: #111;
    text-align: center;
    font-weight: 500;
}

/* Recommended Sellers Section Styles */
.recommended-sellers {
    padding: 24px;
    background: #fff;
}

.section-title {
    font-size: 24px;
    font-weight: 700;
    margin: 0 0 20px 0;
    color: #111;
}

.sellers-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
    gap: 24px;
}

.seller-card {
    border: 1px solid #e8e8e8;
    border-radius: 8px;
    overflow: hidden;
}

.product-grid {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 1px;
    background: #e8e8e8;
}

.product-image {
    width: 100%;
    height: 150px;
    object-fit: cover;
    background: #fff;
}

.seller-info {
    padding: 12px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    background: #fff;
}

.seller-details {
    display: flex;
    align-items: center;
    gap: 8px;
}

.seller-avatar {
    width: 32px;
    height: 32px;
    border-radius: 50%;
}

.seller-text {
    display: flex;
    flex-direction: column;
}

.seller-name {
    font-size: 14px;
    color: #111;
    font-weight: 500;
}

.follower-count {
    font-size: 12px;
    color: #707070;
}

.save-button {
    display: flex;
    align-items: center;
    gap: 4px;
    padding: 6px 12px;
    border: 1px solid #e8e8e8;
    border-radius: 20px;
    background: #fff;
    color: #0053a0;
    font-size: 14px;
    cursor: pointer;
    transition: all 0.2s ease;
}

.save-button:hover {
    border-color: #0053a0;
    background: #f5f9ff;
}

.save-button.saved {
    background: #f5f9ff;
    border-color: #0053a0;
}

@media (max-width: 768px) {
    .category-circle {
        width: 100px;
        height: 100px;
    }

    .category-item {
        min-width: 100px;
    }

    .sellers-grid {
        grid-template-columns: 1fr;
    }
}
</style>