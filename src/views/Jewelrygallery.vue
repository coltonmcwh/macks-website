<template>
  <div class="gallery-section">
    <div class="section-header">
      <h2 class="section-title chrome-text">The Work</h2>
      <div class="ornate-divider"><span>gallery</span></div>
    </div>

    <div class="scroll-hint">
      <span>scroll</span>
      <div class="scroll-arrow">——→</div>
    </div>

    <div class="gallery-track-wrap">
      <div class="gallery-track" ref="track">
        <div
          class="gallery-item"
          v-for="(item, index) in images"
          :key="index"
        >
          <div class="gallery-img-wrap">
            <img :src="item.src" :alt="item.caption" />
            <div class="gallery-overlay">
              <div class="overlay-inner">
                <div class="overlay-ornament">✦</div>
                <p class="overlay-caption">{{ item.caption }}</p>
              </div>
            </div>
            <div class="corner-ornament tl"></div>
            <div class="corner-ornament tr"></div>
            <div class="corner-ornament bl"></div>
            <div class="corner-ornament br"></div>
          </div>
        </div>
      </div>

      <!-- fade edges -->
      <div class="fade-left"></div>
      <div class="fade-right"></div>
    </div>
  </div>
</template>

<script setup>
// ─────────────────────────────────────────────
//  TO ADD YOUR IMAGES:
//  Replace the placeholder entries below with your own.
//  - src: path to image file in your /public folder
//         e.g. '/gallery/ring1.jpg'
//         OR a full URL to a hosted image
//  - caption: short label shown on hover
//
//  Example:
//  { src: '/gallery/silver-ring.jpg', caption: 'Sterling Talon Ring' },
// ─────────────────────────────────────────────
const images = [
  { src: '/gallery/jewels1.png', caption: 'Cunty' },
  { src: '/gallery/jewels2.png', caption: 'Slay' },
  { src: '/gallery/jewels3.png', caption: 'Cunt' },
  { src: '/gallery/jewels4.png', caption: 'hell yeah' },
]
</script>

<style scoped>
.gallery-section {
  padding: 5rem 0;
  overflow: hidden;
}

.section-header {
  text-align: center;
  padding: 0 3rem;
  margin-bottom: 1rem;
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
  font-size: clamp(1.8rem, 4vw, 3rem);
  font-weight: 700;
  letter-spacing: 0.05em;
  margin-bottom: 1rem;
}

/* ── Scroll hint ── */
.scroll-hint {
  display: flex;
  align-items: center;
  justify-content: flex-end;
  gap: 0.6rem;
  padding: 0 3rem;
  margin-bottom: 1.5rem;
  font-family: 'Cinzel', serif;
  font-size: 0.6rem;
  letter-spacing: 0.3em;
  color: #333;
  text-transform: uppercase;
}

.scroll-arrow {
  letter-spacing: -0.05em;
  animation: nudge 2s ease-in-out infinite;
}

@keyframes nudge {
  0%, 100% { transform: translateX(0); }
  50% { transform: translateX(6px); }
}

/* ── Track wrapper ── */
.gallery-track-wrap {
  position: relative;
}

.gallery-track {
  display: flex;
  justify-content: center;
  gap: 1rem;
  overflow-x: auto;
  overflow-y: hidden;
  padding: 1rem 3rem 2rem;
  scroll-snap-type: x mandatory;
  scrollbar-width: none; /* Firefox */
  -webkit-overflow-scrolling: touch;
  cursor: grab;
}

.gallery-track:active {
  cursor: grabbing;
}

.gallery-track::-webkit-scrollbar {
  display: none;
}

/* ── Fade edges ── */
.fade-left,
.fade-right {
  position: absolute;
  top: 0;
  bottom: 0;
  width: 80px;
  pointer-events: none;
  z-index: 2;
}

.fade-left {
  left: 0;
  background: linear-gradient(90deg, #080808, transparent);
}

.fade-right {
  right: 0;
  background: linear-gradient(-90deg, #080808, transparent);
}

/* ── Individual item ── */
.gallery-item {
  flex: 0 0 auto;
  scroll-snap-align: start;
  width: 400px;
}

.gallery-img-wrap {
  position: relative;
  overflow: hidden;
  height: 500px;
  border: 1px solid #1e1e1e;
  background: #0a0a0a;
}

.gallery-img-wrap img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  filter: grayscale(30%) contrast(1.1);
  transition: transform 0.7s cubic-bezier(0.25, 0.46, 0.45, 0.94),
              filter 0.5s ease;
  display: block;
}

.gallery-item:hover .gallery-img-wrap img {
  transform: scale(1.06);
  filter: grayscale(0%) contrast(1.05);
}

/* ── Overlay ── */
.gallery-overlay {
  position: absolute;
  inset: 0;
  background: linear-gradient(
    to top,
    rgba(0, 0, 0, 0.85) 0%,
    rgba(0, 0, 0, 0.2) 50%,
    transparent 100%
  );
  opacity: 0;
  transition: opacity 0.4s ease;
  display: flex;
  align-items: flex-end;
  padding: 1.5rem;
}

.gallery-item:hover .gallery-overlay {
  opacity: 1;
}

.overlay-inner {
  transform: translateY(8px);
  transition: transform 0.4s ease;
}

.gallery-item:hover .overlay-inner {
  transform: translateY(0);
}

.overlay-ornament {
  font-size: 0.6rem;
  color: #888;
  margin-bottom: 0.4rem;
  letter-spacing: 0.3em;
}

.overlay-caption {
  font-family: 'Cinzel', serif;
  font-size: 0.75rem;
  letter-spacing: 0.2em;
  color: #e0e0e0;
  text-transform: uppercase;
}

/* ── Corner ornaments (inherited from global but scoped override) ── */
.corner-ornament {
  position: absolute;
  width: 16px;
  height: 16px;
  border-color: #333;
  border-style: solid;
  opacity: 0;
  transition: opacity 0.4s ease;
  z-index: 3;
}

.gallery-item:hover .corner-ornament {
  opacity: 1;
  border-color: #666;
}

.corner-ornament.tl { top: 8px; left: 8px; border-width: 1px 0 0 1px; }
.corner-ornament.tr { top: 8px; right: 8px; border-width: 1px 1px 0 0; }
.corner-ornament.bl { bottom: 8px; left: 8px; border-width: 0 0 1px 1px; }
.corner-ornament.br { bottom: 8px; right: 8px; border-width: 0 1px 1px 0; }
</style>