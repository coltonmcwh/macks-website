<template>
  <div class="shop">

    <div class="shop-header">
      <p class="section-eyebrow">✦ Handcrafted ✦</p>
      <h1 class="shop-title chrome-text">The Collection</h1>
      <div class="ornate-divider"><span>select your piece</span></div>
    </div>

    <div class="product-grid">
      <div
        class="product-card"
        v-for="product in products"
        :key="product.id"
      >
        <div class="product-img-wrap">
          <img :src="product.image" :alt="product.name" />
          <div class="product-img-overlay">
            <button class="btn" @click="addToCart(product)">Add to Cart</button>
          </div>
        </div>
        <div class="product-info">
          <div class="product-name">{{ product.name }}</div>
          <div class="product-desc">{{ product.description }}</div>
          <div class="product-price">${{ product.price }}</div>
        </div>
        <div class="corner-ornament tl"></div>
        <div class="corner-ornament tr"></div>
        <div class="corner-ornament bl"></div>
        <div class="corner-ornament br"></div>
      </div>
    </div>

    <!-- Cart toast -->
    <Transition name="toast">
      <div v-if="showToast" class="cart-toast">
        <span class="toast-icon">✦</span>
        {{ toastMessage }}
      </div>
    </Transition>

  </div>
</template>

<script setup>
import { ref } from 'vue'

const products = ref([
  { id: 1, name: 'Obsidian Hoop Earrings', description: 'Blackened 925 silver with onyx inlay.', price: 49, image: 'https://placehold.co/400x400/0a0a0a/555?text=✦' },
  { id: 2, name: 'Serpent Chain Necklace', description: 'Sterling silver snake chain, 18".', price: 65, image: 'https://placehold.co/400x400/0a0a0a/555?text=✦' },
  { id: 3, name: 'Raven Claw Ring', description: 'Oxidized silver talon, adjustable.', price: 38, image: 'https://placehold.co/400x400/0a0a0a/555?text=✦' },
  { id: 4, name: 'Crescent Moon Pendant', description: 'Hammered silver with black rhodium.', price: 55, image: 'https://placehold.co/400x400/0a0a0a/555?text=✦' },
  { id: 5, name: 'Thorned Cuff Bracelet', description: 'Wide silver cuff with spike details.', price: 72, image: 'https://placehold.co/400x400/0a0a0a/555?text=✦' },
  { id: 6, name: 'Sigil Drop Earrings', description: 'Labradorite and oxidized silver.', price: 44, image: 'https://placehold.co/400x400/0a0a0a/555?text=✦' },
])

const cart = ref([])
const showToast = ref(false)
const toastMessage = ref('')
let toastTimer = null

function addToCart(product) {
  cart.value.push(product)
  toastMessage.value = `${product.name} added — ${cart.value.length} item${cart.value.length > 1 ? 's' : ''} in cart`
  showToast.value = true
  clearTimeout(toastTimer)
  toastTimer = setTimeout(() => { showToast.value = false }, 3000)
}
</script>

<style scoped>
.shop {
  padding: 4rem 3rem;
  max-width: 1400px;
  margin: 0 auto;
}

.shop-header {
  text-align: center;
  margin-bottom: 4rem;
}

.section-eyebrow {
  font-family: 'Cinzel', serif;
  font-size: 0.6rem;
  letter-spacing: 0.5em;
  color: #444;
  text-transform: uppercase;
  margin-bottom: 0.5rem;
}

.shop-title {
  font-family: 'Cinzel Decorative', cursive;
  font-size: clamp(2rem, 5vw, 3.5rem);
  font-weight: 700;
  letter-spacing: 0.05em;
  margin-bottom: 1rem;
}

.product-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(260px, 1fr));
  gap: 1.5rem;
}

/* ── Cart toast ── */
.cart-toast {
  position: fixed;
  bottom: 2rem;
  left: 50%;
  transform: translateX(-50%);
  background: #111;
  border: 1px solid #333;
  color: var(--silver-bright);
  font-family: 'Cinzel', serif;
  font-size: 0.7rem;
  letter-spacing: 0.2em;
  padding: 1rem 2rem;
  display: flex;
  align-items: center;
  gap: 0.8rem;
  z-index: 999;
  box-shadow: 0 8px 30px rgba(0,0,0,0.8);
}

.toast-icon { color: var(--chrome); }

.toast-enter-active, .toast-leave-active { transition: all 0.4s ease; }
.toast-enter-from, .toast-leave-to { opacity: 0; transform: translateX(-50%) translateY(1rem); }
</style>
