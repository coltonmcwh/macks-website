<template>
  <div class="home">

    <!-- Hero -->
    <section class="hero">
      <div class="hero-bg-grid"></div>
      <div class="hero-content">
        <p class="hero-eyebrow">✦ Est. 2024 ✦</p>
        <h1 class="hero-title chrome-text">MACKS<br>JEWELRY</h1>
        <p class="hero-sub">Handcrafted jewelry</p>
        <div class="ornate-divider"><span>collection</span></div>
        <RouterLink to="/shop" class="btn btn-primary">Baddies Only</RouterLink>
      </div>
      <div class="corner-ornament tl"></div>
      <div class="corner-ornament tr"></div>
      <div class="corner-ornament bl"></div>
      <div class="corner-ornament br"></div>
    </section>

    <!-- About strip -->
    <section class="about-strip">
      <div class="about-item">
        <span class="about-icon">✦</span>
        <span>Handcrafted</span>
      </div>
      <div class="about-sep">—</div>
      <div class="about-item">
        <span class="about-icon">✦</span>
        <span>Sterling Silver & Gold</span>
      </div>
      <div class="about-sep">—</div>
      <div class="about-item">
        <span class="about-icon">✦</span>
        <span>Limited / Custom Pieces</span>
      </div>
    </section>

    <!-- Pics -->
    <section class="pics-section">
      <JewelryGallery />
    </section>

  </div>
</template>

<script setup>
import JewelryGallery from './Jewelrygallery.vue'
import { RouterLink } from 'vue-router'
</script>

<style scoped>
/* ── Hero ── */
.hero {
  min-height: 90vh;
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;
  position: relative;
  padding: 4rem 2rem;
  overflow: hidden;
}

.hero-bg-grid {
  position: absolute;
  inset: 0;
  background-image:
    linear-gradient(rgba(192,192,192,0.03) 1px, transparent 1px),
    linear-gradient(90deg, rgba(192,192,192,0.03) 1px, transparent 1px);
  background-size: 60px 60px;
  mask-image: radial-gradient(ellipse at center, black 30%, transparent 80%);
}

.hero-content {
  position: relative;
  z-index: 1;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 1.2rem;
}

.hero-eyebrow {
  font-family: 'Cinzel', serif;
  font-size: 0.65rem;
  letter-spacing: 0.5em;
  color: #555;
  text-transform: uppercase;
}

.hero-title {
  font-family: 'Cinzel Decorative', cursive;
  font-size: clamp(4rem, 12vw, 9rem);
  font-weight: 900;
  line-height: 0.9;
  letter-spacing: -0.02em;
  margin: 0.5rem 0;
}

.hero-sub {
  font-family: 'Rajdhani', sans-serif;
  font-size: 0.9rem;
  letter-spacing: 0.3em;
  color: #666;
  text-transform: uppercase;
}

/* ── About strip ── */
.about-strip {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 2rem;
  padding: 1.5rem 3rem;
  border-top: 1px solid #1a1a1a;
  border-bottom: 1px solid #1a1a1a;
  background: #0a0a0a;
}

.about-item {
  display: flex;
  align-items: center;
  gap: 0.6rem;
  font-family: 'Cinzel', serif;
  font-size: 0.7rem;
  letter-spacing: 0.25em;
  text-transform: uppercase;
  color: #555;
}

.about-icon { color: #444; font-size: 0.5rem; }
.about-sep { color: #222; }

/* ── Instagram section ── */
.instagram-section {
  padding: 5rem 2rem;
  max-width: 600px;
  margin: 0 auto;
  text-align: center;
}

.section-eyebrow {
  font-family: 'Cinzel', serif;
  font-size: 0.6rem;
  letter-spacing: 0.5em;
  color: #444;
  text-transform: uppercase;
  margin-bottom: 0.5rem;
}

.section-title {
  font-family: 'Cinzel Decorative', cursive;
  font-size: 1.8rem;
  font-weight: 700;
  color: var(--silver-bright);
  letter-spacing: 0.1em;
}

.ig-wrap {
  margin-top: 2rem;
  border: 1px solid #1e1e1e;
  padding: 1rem;
  background: #0a0a0a;
}
</style>
